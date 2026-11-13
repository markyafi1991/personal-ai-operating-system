---
version: "2.0"
created: 2026-11-13
updated: 2026-11-13
---

# The vault that was built

**Version 2.0** · 2026-11-13

The vault combines a business knowledge graph with operating procedures and
engineering tools. Obsidian supplies navigation and views; the durable knowledge
contract is plain files plus typed metadata. These structural descriptions were
checked against the private conventions and selected source, rather than inferred
from the former showcase's counts. [Evidence A1](evidence-and-status.md#a1).

## Business structure

This is a selected structural map, not a recursive export. Confidential engagement
and restricted domains are omitted. No omission lists or actual record names are published.

```text
HOME.md                       current orientation and hub links
AGENTS.md -> CLAUDE.md         agent entry pointer and canonical operating contract
00_Context/                   durable business context, principles, conventions, tool notes
01_Operations/                procedures, decisions, ledgers, review and execution references
03_Proposals/                 proposal workflow; actual records stay private
04_Portfolio/                 project dossiers, specifications and synthetic/public proof
05_Marketing/                 approved outward narratives and report artifacts
06_Templates/                 reusable note, deliverable and project-kit starting points
07_Admin/                     administration; sensitive records stay private
08_Learning/                  resources, sources, MOCs, curricula and competency maps
11_Creative/                  a separately governed studio track
Bookmarks/                    business source pointers
Clippings/                    raw capture inbox
99_Archive/                   superseded reference
.claude/skills/               canonical agent procedures and selected build code
scripts/                      deterministic utilities, validation and integration code
```

The folder is a routing boundary and a statement of purpose. A hub is the entry
point inside an area. Some hubs use queries over metadata; others contain curated
links. It is inaccurate to describe every hub as a fully automatic dashboard.
The representation works as linked text even when a plugin-generated view is unavailable.

## Notes, identity and navigation

The documented note contract includes `type`, `status`, `created`, `updated` and
`tags`; stable IDs identify notes. Agent-authored documents also carry a version
and a visible date/version line, with documented exceptions for dated logs,
templates and regenerated execution references. Type-specific metadata extends
that shared contract. These are conventions to validate, not evidence that every
existing file already passes every check. [A1](evidence-and-status.md#a1).

Hubs route an agent to an area; MOCs index a subject or tool and link concepts to
their supporting resource notes. A resource note, a concept map, a project dossier
and a generated task reference serve different purposes. Keeping them distinct
allows a project to link reusable knowledge without making a captured source an
execution commitment. The [synthetic miniature](../examples/synthetic-vault/HOME.md)
shows these relationships with invented notes.

Markdown contains durable meaning and links. JSON/CSV and Python support schemas,
registries, hashes, receipts and state. Binary deliverables remain linked artifacts.
There is therefore machine state beyond the prose; agents do not operate solely
on Markdown, and a saved document is not the complete runtime state.

## Ownership across applications

| Surface | Canonical responsibility | Readback boundary |
|---|---|---|
| Vault | Knowledge, specifications, procedures, source-derived content and durable decisions | Source-owned fields remain upstream |
| Notion catalogs | Display plus explicitly named owner-review fields | Two-way authority is named per database and assigned per field |
| ClickUp | Business execution state | Generated execution references return to the vault |
| Linear | Engineering/software execution state | Same reference pattern; use the lane appropriate to the work |
| Slack | Conversation and handoffs | A message alone changes neither permissions nor release authority |
| GitHub | Scoped repositories, code review and pinned public evidence | Repository content and employee grants are separate decisions |

The current contract names the Tool Stack's owner-controlled review fields as a
two-way exception; that does not grant every Notion database writeback authority.
Other catalogs remain one-way unless explicitly amended. Learning enrollment has
a separate, narrowly scoped membership reconciliation rule; it does not make
resource-note bodies bidirectional. No current live round-trip was run in this
documentation review. [A1](evidence-and-status.md#a1).

## Access copies, backup and public evidence

The canonical vault, recovery backups, employee working copies and public
showcases have different purposes. Private material can have separately authorized
private backups or scoped working copies; exclusion from a business/public export
does not mean it never leaves one machine. This publication exposes no such records
or private repository inventory.

The workspace builder reads selected objects from a source commit, scans the same
bytes it commits, and starts a managed destination history without source parents.
The public fixture demonstrates selected transaction behavior, not the complete
live export policy or an audit of all employee grants. [A2](evidence-and-status.md#a2).

## Change and recovery

The operating contract calls for updating owning context, retaining decisions,
logging changed paths and verification, and recording external actions and risks.
Git preserves committed revisions; uncommitted edits are not thereby backed up.
Ordinary commit checks and the separately governed private snapshot/backup path
have different execution rules. No claim is made that every edit is a commit or
that every file has an off-machine copy. [A1](evidence-and-status.md#a1).

References: [evidence register](evidence-and-status.md),
[skills/access model](skills-system.md), [learning lifecycle](learning-system.md),
and [delivery workflow](consulting.md).
