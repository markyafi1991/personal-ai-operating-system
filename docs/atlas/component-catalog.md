---
version: "3.0"
created: 2026-11-13
updated: 2026-11-13
---

# Selected component catalog and measured scope

**Version 3.0** · 2026-11-13

This catalog verifies existence and source structure for a finite business-only
selection. It is not a whole-vault inventory and does not assert that every defined
procedure is independently accepted or running unattended. Private record names,
restricted workflows, app IDs and live registry contents are omitted.

## 68 selected procedure definitions

The six families below are a presentation grouping. The canonical procedures
remain individual definitions; the catalog does not relocate or change them.
Definitions were checked against the publication guard's restricted-skill list.

### Capture and source preparation

`youtube-capture`, `webpage-capture`, `docs-capture`, `oreilly-capture`, `oreilly-book-source`, `epub-capture`, `local-video-capture`, `linkedin-learning-capture`, `social-post-capture`, `clipped-youtube-capture`, `clippings-curator`.

### Knowledge and learning design

`learn-first`, `vault-first`, `synthesis-scan`, `coursework`, `curriculum`, `academy`, `skill-tree`, `anki-cards`, `curriculum-review`.

### Strategy and decision support

`situation-assessment`, `strategic-options`, `decision-memo`, `assumption-audit`, `business-case-builder`, `competitive-intel`, `customer-segmentation`, `growth-barriers`, `initiative-prioritizer`, `kpi-architect`, `market-mapping`, `narrative-builder`, `operating-model-design`, `portfolio-review`, `pricing-strategy`, `profit-pool-analysis`, `risk-and-mitigation`, `stakeholder-alignment`, `transformation-roadmap`, `value-realization`, `war-gaming`.

### Delivery and artifact production

`launch-engagement`, `start-project`, `project-kit`, `report-builder`, `instructions-pdf`, `vault-manual`, `creative-project`, `tutorial-project`.

### Catalog and integration workflows

`skill-stack-sync`, `sop-stack-sync`, `moc-stack-sync`, `vault-map-sync`, `connector-stack-sync`, `tool-stack-sync`, `skill-tree-sync`, `learning-clickup-sync`, `addon-stack-sync`, `github-stars-sync`, `task-reconcile`.

### Verification and maintenance

`cite`, `verify-build`, `daily-log`, `session-handoff`, `vault-linter`, `sync-technical-docs`, `tool-audit`, `skill-audit`.


## 20 supporting engineering modules

| Family | Inspected module | Top-level function definitions | Physical lines |
|---|---|---:|---:|
| Catalog manifests | `skill_stack_sync.py` | 14 | 370 |
| Catalog manifests | `sop_stack_sync.py` | 6 | 157 |
| Catalog manifests | `moc_stack_sync.py` | 10 | 281 |
| Catalog manifests | `vault_map_sync.py` | 15 | 413 |
| Catalog manifests | `connector_stack_sync.py` | 9 | 220 |
| Catalog manifests | `tool_stack_sync.py` | 22 | 754 |
| Catalog manifests | `skill_tree_sync.py` | 11 | 233 |
| Catalog manifests | `learning_resources_sync.py` | 12 | 230 |
| Catalog manifests | `addon_stack_sync.py` | 9 | 253 |
| Catalog manifests | `github_stars_sync.py` | 11 | 205 |
| Reconciliation and drift | `task_reconcile.py` | 12 | 292 |
| Reconciliation and drift | `learning_clickup_sync.py` | 32 | 977 |
| Reconciliation and drift | `notion_mirror_drift.py` | 3 | 260 |
| Source curation and integrity | `clippings_catalog.py` | 19 | 802 |
| Source curation and integrity | `log_compliance_check.py` | 12 | 299 |
| Source curation and integrity | `engagement_trace.py` | 21 | 513 |
| Workspace construction | `agent_workspaces/build_workspace.py` | 44 | 987 |
| Workspace construction | `vault_publish.py` | 14 | 779 |
| Employee collaboration | `slack_employee_hub/coordinator.py` | 3 | 113 |
| Employee collaboration | `slack_employee_hub/run.py` | 9 | 259 |

These module paths identify private implementation components being described.
They are not promises that the modules ship in this public repository. Source
hashes are retained privately; the public case study contains newly authored
explanations rather than copies of the private implementations.

## Delivery engine subtree

| Scope | Python files | Physical lines | Declared test functions |
|---|---:|---:|---:|
| Launch-Engagement implementation directory | 41 | 13,914 | — |
| Its test/support directory | 17 | 7,901 | 366 |

Physical lines include comments and blank lines. Definitions are counted with
Python AST inspection and do not imply an execution result. The directory scopes
include support files. These counts are separate from the 39 tests in the three
pinned public evidence slices and overlap with selected modules/procedure families;
do not sum them into a total for the vault.

## Module decomposition inside delivery

The inspected source separates intake schema/normalization/readiness/command
planning, state and runtime, phase-specific contracts, phase executors, kit
metadata, evidence generation, readout/handoff artifact validation, closeout
attestation and metadata tracing. This is why a single phase name in a high-level
diagram represents a substantial contract boundary rather than one agent action.

## Measurement method and privacy scope

The [JSON inventory](component-inventory.json) retains the selected families,
counts and method. Collection reads only explicitly named business procedure and
engineering files plus the two delivery-code directories. It does not inspect
private operational registry values, restricted record folders or actual user
content. Counts describe inspected source at 2026-11-13; they are not continuously
updated metrics, quality scores or fleet-health indicators.
