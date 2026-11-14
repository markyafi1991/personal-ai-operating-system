---
version: "1.0"
created: 2026-11-14
updated: 2026-11-14
---

# Engineering review: follow the contracts into code

**Version 1.0** · 2026-11-14

AI OS is Mark Yafi / Algonquin Consult's knowledge and delivery engineering
project. Its central problem is coordinating agent work across files, repositories
and applications when context, permissions, state and approvals can change
independently. A repeated event, an unexpected export file or a stale project write
needs a defined outcome that a reviewer can inspect.

The engineering responsibilities span context selection, ownership of shared
fields, deterministic validation, state persistence and recovery. Language models
interpret and draft; Python tools check bounded contracts; operators resolve
uncertain effects and supply acceptance that code cannot observe. The
[agent/tool responsibility split](atlas/agent-runtime.md#division-of-responsibility-with-code)
and [delivery contracts](atlas/delivery-engine.md#phase-by-phase-artifact-contracts)
explain those interfaces. This page follows the smaller public code slices where
the behavior can be reproduced.

## Three claims to inspect

Every code link below names an immutable source revision. Use the
[reproduction guide](reproduce.md) to run the snapshots and the
[2026-11-14 verification receipt](../evidence/2026-11-14/verification.json) to inspect
the dated run. The [evidence register](evidence-and-status.md) separates public
demonstrations from inspected private implementation and pending acceptance.

| Claim | Immutable code and test evidence | What the proof does not establish |
|---|---|---|
| A workspace is constructed from committed, checked bytes; unexpected tree/history or reference-update failures cause refusal. | [Tree readback and reference transaction](https://github.com/markyafi1991/scoped-ai-workspaces/blob/99105caa3be9f9f2c243ef7d6d1ca3c23d91ac02/workspace_core.py#L331-L359) · [claim-to-test map](https://github.com/markyafi1991/scoped-ai-workspaces/blob/99105caa3be9f9f2c243ef7d6d1ca3c23d91ac02/evidence-map.json) | The collector is synthetic; secret signatures are finite. Injected failures establish selected refusal paths, not a real race benchmark or complete live access policy. |
| An admitted event is not automatically executed again after a replay or uncertain send. | [Admission and delivery code](https://github.com/markyafi1991/governed-slack-collaboration/blob/893cda33cdbddbc389e03ff18490abd10d5abc57/routing.py#L92-L108) · [replay test](https://github.com/markyafi1991/governed-slack-collaboration/blob/893cda33cdbddbc389e03ff18490abd10d5abc57/tests/test_collaboration.py#L40-L44) · [uncertain-send test](https://github.com/markyafi1991/governed-slack-collaboration/blob/893cda33cdbddbc389e03ff18490abd10d5abc57/tests/test_collaboration.py#L79-L86) | Admission is at most once while the receipt is retained. Delivery can remain incomplete. The fixture includes no live Slack transport, provider request or crash-recovery acceptance. |
| Project state is separated by engagement, supports explicit stale-revision refusal and preserves a primary write when its advisory index cannot be updated. | [State persistence code](https://github.com/markyafi1991/launch-engagement-automation/blob/f6de2227fa4ffbb50dbb07ea7d35180aa35e6cf1/evidence/2026-11-13/engagement_state.py#L201-L241) · [stale-write test](https://github.com/markyafi1991/launch-engagement-automation/blob/f6de2227fa4ffbb50dbb07ea7d35180aa35e6cf1/evidence/2026-11-13/tests/test_state.py#L25-L30) · [advisory-index test](https://github.com/markyafi1991/launch-engagement-automation/blob/f6de2227fa4ffbb50dbb07ea7d35180aa35e6cf1/evidence/2026-11-13/tests/test_state.py#L71-L77) | Callers must supply the expected revision. Local POSIX locking and atomic persistence do not establish cross-host consistency; the advisory index is best effort. |

## Case study: one launch question, then interrupted delivery

The [public fixture](https://github.com/markyafi1991/governed-slack-collaboration/blob/893cda33cdbddbc389e03ff18490abd10d5abc57/demo.py#L8-L20)
supplies event `EvFixture01`: an allowed human asks the `operations` role to review
a fictional launch. Its fixed reply asks the `risk` role for a support-readiness
check. These are invented messages and deterministic callbacks, not model output
from a live service.

1. **Admit before effects.** `deliver` inserts the event ID into SQLite and commits
   that admission before invoking the coordinator. An existing ID returns `False`
   before any completion or send callback runs.
2. **Bound the normal path.** The coordinator validates the handoff before the lead
   post, then supplies the lead's visible message and handoff question to one peer.
   The [handoff test](https://github.com/markyafi1991/governed-slack-collaboration/blob/893cda33cdbddbc389e03ff18490abd10d5abc57/tests/test_collaboration.py#L26-L38)
   checks calls in `operations`, `risk` order and two messages in the same thread.
3. **Replay the event.** The replay test replaces both effect callbacks with
   functions that fail if called. Delivery returns `False` without calling them.
4. **Interrupt it in two different places.** The uncertain-send test appends one
   synthetic message and then raises `OSError`; retrying the same event leaves the
   count at one. The separate
   [peer-failure test](https://github.com/markyafi1991/governed-slack-collaboration/blob/893cda33cdbddbc389e03ff18490abd10d5abc57/tests/test_collaboration.py#L99-L107)
   raises during the peer completion after the lead post. That also leaves one
   message, and replay does not finish the turn.

The result is a specific recovery obligation: inspect what happened before issuing
new work. Suppression prevents automatic repeated effects; it does not prove the
recipient received a complete answer. The tests use in-memory SQLite and injected
failures, so persistence across process loss and real transport uncertainty need
separate verification. The
[coordinator implementation](https://github.com/markyafi1991/governed-slack-collaboration/blob/893cda33cdbddbc389e03ff18490abd10d5abc57/coordinator.py#L84-L113)
makes the partial-delivery boundary visible in its control flow.

## Three design decisions worth discussing

- **Record admission before attempting delivery.** This avoids blindly repeating
  a model call or send after an uncertain result. It trades automatic completion
  for operator reconciliation: a failed first attempt still consumes the event ID.
  Receipt retention and an explicit recovery procedure therefore matter as much
  as the duplicate check. The public tests above expose both sides of that choice.
- **Use a checked Git transaction for scoped context.** Selecting one source commit,
  comparing the constructed tree and updating managed references together makes
  content identity inspectable. Unknown destination history causes refusal, which
  creates investigation work rather than silently absorbing it. A filtered copy
  still needs separate repository credentials and application grants.
  [Transaction and authority boundaries](atlas/permissions-and-publication.md).
- **Keep project state local and revision-aware.** Project-specific files and an
  explicit expected revision provide a small, inspectable persistence boundary.
  Preserving the primary write when the advisory index fails keeps a secondary
  convenience from invalidating accepted state. The cost is caller discipline,
  index repair and a consistency model limited to the supported local filesystem.
  [State and trace design](atlas/delivery-engine.md#per-project-state-and-run-traces).

## Follow the wider system

The [architecture atlas](atlas/README.md) connects these seams to the
[typed knowledge graph](atlas/knowledge-model.md),
[information lifecycle](atlas/information-lifecycle.md),
[field ownership and reconciliation](atlas/synchronization.md) and
[connected catalogs](atlas/connected-catalogs.md). The
[component catalog](atlas/component-catalog.md) records selected implementation
breadth; its definition and file counts are source measurements, not outcome or
test-pass metrics. The [synthetic note graph](../examples/synthetic-vault/HOME.md)
illustrates the schema without exposing operating records.

The public evidence establishes the declared synthetic behaviors. It supplies no
client impact, live employee commissioning or accepted end-to-end engagement.
Launch-Engagement remains Beta; its wider acceptance gates stay in the
[evidence register](evidence-and-status.md#acceptance-still-separate).


## Sources

The immutable implementation and test links in the claim matrix and case study
are the primary sources. The [source/asset pins](../report-evidence-pins.json),
[local verification receipt](../evidence/2026-11-14/verification.json) and
[publication review](publication-review.md) retain identity, run scope and review
limits. The tradeoff discussion is original analysis of those contracts.
