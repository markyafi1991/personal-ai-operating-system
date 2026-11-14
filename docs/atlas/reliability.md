---
version: "3.0"
created: 2026-11-13
updated: 2026-11-13
---

# 07 — Verification, failure and recovery as architecture

**Version 3.0** · 2026-11-13

The system contains several forms of evidence because source correctness,
destination state, human acceptance and operating continuity are different claims.
The architectural question is what a check observes and what lies outside it.

## Evidence ladder

| Evidence | Establishes | Does not by itself establish |
|---|---|---|
| Procedure definition | An intended workflow and its required checks | Successful execution |
| Source/configuration inspection | An implemented rule or available mechanism | Current deployment health or every effective grant |
| Unit/negative tests | Behavior for the declared fixtures and fault injections | General correctness or end-to-end service acceptance |
| Content hash and exact tree | Identity of the selected bytes/tree | The business truth of their contents |
| Destination readback | An observed remote object/ref at a time | Future freshness or all readers' effective access |
| Recorded human attestation | A stated review/acceptance event under its trust model | Cryptographic attribution or direct machine observation |
| Fresh-operator reproduction | Usability of the declared package/environment | Acceptance outside the tested scope |

## Failure catalog across subsystems

| Failure | Detection/control seam | Recovery expectation |
|---|---|---|
| Stale source description in a mirror | Defined payload hash versus registry checkpoint | Prepare a new plan and verify its destination application |
| Remote owner field overwritten | Field ownership contract and preservation checks | Restore through the owner-controlled side; fix the field map |
| Raw source promoted as fact | Provenance/citation and source-status checks | Source it, qualify it or remove the claim |
| Concurrent state writer | Explicit expected revision under the local state lock | Reload and retry with current state |
| Advisory state index malformed | Validation and best-effort handling | Preserve the accepted primary write; repair/rebuild the index separately |
| Unexpected workspace history | Branch versus managed-head check | Refuse further publication until the history is reconciled |
| File set differs after construction | Per-object tree readback | Reject before moving the published branch |
| Replayed Slack event | Durable admission receipt | Suppress repeated execution |
| Lead sent but peer failed | Bounded handoff plus preserved admission state | Inspect the partial thread before any new request |
| External write timed out | Exact destination readback | Classify as uncertain until observed; do not assume failure means nothing happened |
| Later artifact changed after approval | Recomputed bindings/prerequisite gates | Revalidate or reopen the affected stage |

Some controls reject work, some preserve work, and some report an uncertainty that
requires an operator. An architecture that treats all three outcomes as generic
"failure" makes recovery unsafe.

## Trace is metadata, not a transcript dump

The inspected trace source bounds record sizes and hash bindings, validates safe
field names/values and avoids storing raw source bodies, credentials or exception
text as the audit payload. This supports decision-level continuity without
making the trace another unrestricted copy of the working context.

A partial-history marker is useful evidence: it makes the observation boundary
explicit. Inventing earlier success records would make the trace appear complete
while destroying its value. Later append-safe records also should not invalidate
an older verified prefix merely because legitimate work continued.

## Verification inside the operating workflow

The procedure layer asks the builder to pin a definition of done, verify as work
is produced, challenge boundary cases and retain evidence. Risk routing determines
when an independent judge or specialist lens is required. Owner merge and release
authority remain separate. The governance design does not require every change
to pass through every available AI product.

Change records connect what was altered to why and how it was checked. Generated
references, templates, ordinary commits and private snapshot commits have different
documented treatment. It is inaccurate to claim that every edit is committed or
that a written logging rule alone proves a complete historical trail.

## Published proof and its limits

The linked public slices contain 17 workspace tests, 13 offline collaboration
tests and 9 state tests. Their source archives were verified and reproduced at
the evidence publication. Fault-injection tests for a tree mismatch and a rejected
compare-and-swap show the control's handling; they are not a live contention study.
The private engine's 366 source-defined tests are a different measurement, not an
additional public pass count.

Hosted CI, live app health and a complete v1 run have independent status. The
atlas does not infer an active schedule from installed code or an inactive plan
from a missing run record. A target can remain valid while implementation or
acceptance evidence is still pending.

**Evidence boundary:** [A1–A4](../evidence-and-status.md), selected engineering
source and explicit fixture proof. No production logs, private review transcripts,
real task state or client acceptance records are reproduced.
