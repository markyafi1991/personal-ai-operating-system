---
version: "3.0"
created: 2026-11-13
updated: 2026-11-13
---

# 08 — Three journeys through the architecture

**Version 3.0** · 2026-11-13

These journeys are invented walkthroughs assembled from the documented contracts.
They show the interactions and failure seams without reproducing actual operating
records. They are explanatory examples, not reports of a live execution.

## Journey A — A resource becomes a project requirement

1. A fictional resource pointer arrives. Its URL is a pointer, not yet a trusted
   source and not an enrollment commitment.
2. The applicable capture procedure extracts metadata and source material into
   the right artifact shape. A heavy source can have a parent index and page or
   chapter children. Capture completeness is recorded rather than presumed.
3. The resource note receives source/progress fields and an analysis. The MOC
   links a specific concept to the supporting note/location.
4. A synthetic project applies that concept to a bounded requirement: repeated
   messages should not execute the same operation twice.
5. The project specification owns that requirement. The execution task owns the
   assignee/status for implementing it. A generated reference reflects the task
   state without rewriting the specification.
6. A saved test supplies a duplicate event and checks the observed result. A
   source citation supports the concept; the test result supports the behavior.
7. An outward narrative cites the exact public code/test snapshot for the behavior.
   Finishing a resource never substitutes for evidence that the requirement passed.

**Failure seam:** if the source analysis is incomplete, the project can state an
assumption or hold that claim. It cannot convert a missing transcript into a
confident technical conclusion merely because a MOC link exists.

The [synthetic HOME](../../examples/synthetic-vault/HOME.md) contains the note-level
portion of this journey. [A3](../evidence-and-status.md#a3) contains actual runnable
duplicate-event fixture evidence for its own declared input.

## Journey B — A catalog description and an owner mark change together

The fictional row below is a data-contract illustration. Names and fields are
invented; the actual ownership of a real catalog follows its named contract.

```json
{
  "entity": "synthetic-tool",
  "vault_owned": {"description": "A fictional validation utility"},
  "review_surface_owned": {"review_decision": "needs owner review"},
  "identity": {"external_id": "fixture-row"},
  "checkpoint": {"last_synced_source_hash": "fixture-only"}
}
```

1. The source description changes and the owner updates the review decision.
2. The planner hashes only its defined source-owned payload and compares the
   previous source checkpoint. That identifies source drift without claiming to
   know every current remote edit.
3. The outgoing plan updates the description while preserving the owner's field.
4. Authorized owner-field readback handles the reverse direction separately.
5. Destination readback confirms what actually landed; the registry checkpoint
   records the relevant synchronized state under that workflow's contract.

**Failure seam:** a failed or uncertain remote write must not be represented as a
successful sync merely by updating a local hash. A missing row is also different
from an owner decision that the represented tool should be retired.

## Journey C — Approved context reaches an employee and produces reviewable evidence

1. The owner approves a content scope independently of the role's instructions.
2. A collector selects eligible content from a known source commit. The manifest
   identifies selected content without disclosing excluded compartments.
3. Validation checks the bytes that will be written. The destination commit is
   constructed and read back before the managed refs advance.
4. The scoped repository credential permits the intended employee to obtain that
   copy. Any application connection requires its own separate authorization.
5. In the offline conversation fixture, one allowed human event reaches the lead.
   Admission is recorded before model/send effects. The lead may hand one question
   and its visible message to one roster peer.
6. A replay is suppressed. If the peer fails after the lead post, the partial turn
   stays admitted. An operator inspects the result rather than blindly resending.
7. A delivery claim identifies the specific accepted artifact and test evidence;
   a public showcase receives only separately reviewed synthetic material.

**Failure seam:** a stale employee copy, a live connector with broader authority,
a missing provider, an uncertain send and a changed deliverable are different
problems. A green local Git test cannot clear all of them.

## Reproduce the published seams

In each linked evidence repository/slice, the documented commands are:

```sh
python3 -B -m unittest discover -s tests -v
python3 -B demo.py
```

Use the exact [workspace](../evidence-and-status.md#a2),
[collaboration](../evidence-and-status.md#a3) or
[state](../evidence-and-status.md#a4) snapshot and its own README. The state slice
lives under the engine repository's `evidence/2026-11-13/` directory. These commands
run the shipped synthetic seam, not the entire private operating system.

**Evidence boundary:** the journeys are synthetic explanations. Only the linked,
declared fixture code and its recorded tests are presented as observed execution.
