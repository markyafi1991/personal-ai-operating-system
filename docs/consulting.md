---
version: "2.1"
created: 2026-11-13
updated: 2026-11-13
---

# From a project specification to accepted delivery

**Version 2.1** · 2026-11-13
Explore the detailed [architecture atlas: delivery phase contracts](atlas/delivery-engine.md).


The delivery architecture connects reusable knowledge to a project dossier,
structured intake, execution state, phase artifacts, verification and owner
acceptance. This page describes the operating design and separates its public
implementation evidence from later integration targets. [A1](evidence-and-status.md#a1).

## Specification and execution have different owners

The vault holds the project origin, intended outcomes, requirements and reusable
procedures. Business execution uses ClickUp; engineering/software execution uses
Linear. Generated references can reflect task state into the vault, while the work
surface remains authoritative for status, assignee, dates and discussion. A portfolio
publication lifecycle and the code work for that piece may be separate linked work;
they are not interchangeable status records.

## The delivery spine

The private Launch-Engagement implementation and procedures organize intake,
scaffolding, discovery, KPI design, applicable kit/build/QA/handoff work, readout,
value and closeout. Lane selection determines which phases apply. Reusable kits
are starting points; a deployed project owns its specific requirements and evidence.
The historical public extract has a narrower runnable surface than the private
engine and names that limit. [Historical public engine](https://github.com/markyafi1991/launch-engagement-automation).

The more recent [state evidence slice](https://github.com/markyafi1991/launch-engagement-automation/tree/f6de2227fa4ffbb50dbb07ea7d35180aa35e6cf1/evidence/2026-11-13) demonstrates separate project state
paths, atomic primary persistence, mode 0600 and opt-in stale-revision checks.
Callers must supply `expected_revision`; omitting it skips the comparison. Its
human-readable index is best-effort and is not a cross-project transactional
database. Nine tests cover the mapped slice, not the full phase chain. [A4](evidence-and-status.md#a4).

## Artifact identity and approvals

The delivery design uses definitions of done, receipts, current artifact hashes
and phase prerequisites so later work can detect changed inputs. Evidence binding,
approval attribution and actual external acceptance are different questions.
A name in a receipt is not cryptographic identity; an instruction to obtain a
human approval does not prove the approval happened. Public examples must not
inflate an internal attestation into independently observed acceptance.

The reproducible package target includes code, inputs/assumptions, saved tests and
expectations, dependency/environment instructions, artifacts, checksums, operating
instructions and a recovery path. Full fresh-operator reproduction and the first
accepted end-to-end v1 engagement remain acceptance work. A source archive for a
small code slice does not establish completion of that larger package contract.

## Decisions and outward work

Durable decisions record context, a choice and consequences; procedures describe
repeatable steps. Versions and visible dates identify authored deliverables.
Substantive changes and verification belong in the private change record. The
examples in this repository are newly invented, not excerpts from that record.

Portfolio intake permits synthetic or appropriately approved public data. This
showcase uses invented inputs throughout. Actual client information, private
proposals, operational records and restricted material are excluded. Provenance
and publication review are required for outward claims; a documented requirement
is not proof that every historical deliverable satisfied it.

## Current release meaning

The engine is **Beta**. The evidence snapshot identifiers and report editions
identify documents and code snapshots; they do not establish v1 shipment. The
[report crosswalk](current-evidence-architecture.md) identifies the exact public
proof supporting the narrative. [Evidence and status](evidence-and-status.md).
