---
id: 9936eec7-dc37-4548-8752-67912dbeb1ca
tags: [operations, reference]
version: "2.0"
created: 2026-11-13
updated: 2026-11-13
type: decision
status: draft
synthetic: true
---

# Synthetic decision — separate content and task ownership

**Version 2.0** · 2026-11-13

This is an invented example, not an owner decision or operational record.

## Context

A fictional project uses a Markdown specification and an external execution board.
Reviewers need to know which side controls a changed requirement or task status.

## Decision

Keep the specification canonical in the synthetic vault. Let the chosen execution
surface own status and assignee. Treat a generated task reference as a view of that
execution state. Give any review application explicitly named fields, rather than
allowing both systems to overwrite the same field.

## Alternatives and tradeoffs

Copying all fields both ways is easy initially but makes conflicts ambiguous.
Single-owner fields need a mapping and reconciliation procedure. A stored task
reference can be stale, so a release decision needs current evidence.

## Verification and access

A mapping review can check ownership; a live round trip must test the integration.
Gitignore does not restrict local reads. Credentials and application permissions
need separate scoping. No service or permission is configured by this example.
