---
version: "3.0"
created: 2026-11-13
updated: 2026-11-13
---

# Design tradeoffs visible in the implementation

**Version 3.0** · 2026-11-13

These are engineering tradeoffs supported by the current contracts and source,
not an invented transcript of the owner's historical thought process.

| Choice | What it enables | Cost or remaining obligation |
|---|---|---|
| Plain files plus typed metadata | Cross-tool reading, links, inspectable diffs and explicit schemas | Validation, naming discipline and graph repair remain necessary |
| Hubs plus MOCs | Area orientation and concept-level reuse | Curated links and queries can drift or depend on plugin configuration |
| Source artifacts separate from analyzed notes | Retain provenance and multi-part source structure | More entity types and parent/link consistency to manage |
| Separate knowledge and execution authority | Preserve specifications while task state changes elsewhere | Explicit IDs, manifests, generated references and reconciliation |
| Single-owner fields in mixed-authority records | Preserve source updates and owner decisions | Field maps and adapter behavior must be maintained as schemas evolve |
| Deterministic planners before API writes | Inspect changes without invoking a model or remote mutation | Applying a plan and confirming the destination are separate steps |
| Selected private employee copies | Reduce accessible context and isolate repository history | Freshness, credential scope and separate app grants still need verification |
| Exact-tree transaction and managed history | Refuse unexpected bytes or unknown branch history | A corrupted/unmanaged destination cannot be silently healed by ordinary publication |
| At-most-once event admission | Avoid automatic repeated execution after uncertain sends | Partial admitted turns need operator reconciliation |
| Artifact-bound phase gates | Detect stale prerequisites and changed deliverables | Legitimate edits trigger revalidation or reopen work |
| Metadata-only trace | Retain decision continuity without dumping raw context | It does not prove business truth or cryptographic human attribution |
| Evidence snapshots separate from report editions | Preserve traceable code claims as the narrative evolves | A report and its code pins need explicit versioned crosslinks |

The architecture repeatedly chooses an inspectable seam over a universal magic
state. A procedure, source, registry, receipt, deployment and acceptance event each
contribute evidence at their own boundary. The benefit is a system that can explain
what changed and what remains uncertain; the cost is deliberate coordination.

That coordination is the complexity the showcase is intended to make visible.
The [worked journeys](worked-journeys.md) show it in motion, while
[reliability](reliability.md) explains where an apparently successful step still
needs another form of proof.

References: [component inventory](component-inventory.json),
[evidence register](../evidence-and-status.md), and the source/contract inspection
described in the [publication review](../publication-review.md).
