---
type: decision
id: DEC-EXAMPLE-001
title: Use plain Markdown in git as the system's source of truth
status: decided
date: 2026-01-01
---

# DEC-EXAMPLE-001 - Plain Markdown in git as the source of truth

> Representative decision record. Significant decisions in this system are
> captured this way - context, decision, alternatives, consequences - and logged
> in a decision index. This is a sanitized illustration with synthetic content.

## Context

The system needs a durable, auditable, agent-friendly source of truth that will
outlive any single tool and keep a complete change history.

## Decision

Use plain-Markdown files versioned in git as the canonical store. Downstream
apps (such as a Notion display database) are generated, read-only mirrors and
are never treated as a source.

## Alternatives considered

- **A database-backed app.** Rejected: less portable, hides state from agents,
  and couples the source of truth to one vendor.
- **A notes app as source of truth with ad-hoc exports.** Rejected: no real
  version history, and drift between the app and any export becomes unmanageable.

## Consequences

- Every change is a commit; the git history is the audit log.
- Agents read and write the same files a human does, with no hidden state.
- A privacy zone can be enforced structurally by git-ignoring it, so it can
  never be committed or pushed.
- Display surfaces require a deterministic sync engine to stay in step with the
  canonical source - accepted as a worthwhile cost.

## Pressure test

Argued against before locking in: the main risk is that polished, relational
views are harder to build on flat files. Mitigated by the mirror pattern -
organize in Markdown, display downstream - which preserves the single source of
truth while still delivering shareable views.
