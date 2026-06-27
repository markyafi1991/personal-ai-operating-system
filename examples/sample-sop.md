---
type: sop
title: SOP - Daily Log and Change Record
status: active
---

# SOP - Daily Log and Change Record

> Representative standard operating procedure. SOPs in this system are ordered,
> specific, and verification-bearing so the work can be executed consistently
> and handed off. This is a sanitized illustration.

## Purpose

Ensure every substantive working session leaves an auditable trail, so the state
of the system is always reconstructable from its own records.

## When to use

At the end of any work session that changed the knowledge base, and before any
commit that includes substantive changes.

## Procedure

1. **Open today's log.** If it does not exist, create it from the daily-log
   template.
2. **Record the work session.** One line per meaningful activity.
3. **Record changes.** List every auditable path that was created or modified.
   This ledger must cover everything being committed.
4. **Record verification.** State how each change was checked (file opened,
   numbers re-run, index row confirmed).
5. **Record external actions.** Note anything that left the system (a message
   sent, a deliverable shipped, a downstream mirror updated).
6. **Record risks.** Note anything that could bite later and how it is mitigated.

## Verification

Before committing, confirm the change ledger lists every path in the staged
diff. A commit whose changes are not fully reflected in the day's log does not
proceed.

## Notes

This SOP is mirrored into a read-only display surface for reference, but the
Markdown source here is canonical.
