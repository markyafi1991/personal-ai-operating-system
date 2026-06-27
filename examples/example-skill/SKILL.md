---
name: example-skill
description: Representative agent-skill definition showing the structure every skill in the system follows. A skill is a versioned, self-contained workflow an agent can execute consistently. This example is a sanitized illustration, not a working skill.
---

# Example Skill

> This file illustrates the shape of an agent skill in this system. Real skills
> follow the same structure: front-matter with a name, a description, and trigger
> phrases; ordered steps; explicit capability requirements; a verification step;
> and a feedback loop.

## Trigger phrases

Invoke when the user says: "/example-skill", "run the example workflow", or
describes the task this skill automates in natural language.

## Before proceeding

Load orienting context first: the current-state hub, the active priorities, and
any companion notes for the area this skill touches. Treat the operating
contract's standing principles as binding.

## Steps

1. **Load context.** Read the relevant hub note and recent operational logs so
   the work is grounded in current state, not assumptions.
2. **Do the work.** Execute the procedure as ordered, specific steps with
   explicit paths and decision points. Keep one step in progress at a time.
3. **Verify.** State how the result was checked — open the file, re-read the
   index row, re-run the numbers. Report "verified," not "asserted."
4. **Write protocol.** Update the touched note's timestamp and append a work
   session to the day's log with the standard ledgers (work, change,
   verification, external actions, risks).

## Capability requirements

Uses file read / write / edit, search, and shell capabilities available in the
current agent surface. Capabilities are named generically, not by product, so
the skill is portable across agent runtimes.

## Feedback loop

A skill is never finished. After a run, capture what worked and what did not in
the skill's companion note, and fold improvements back into this file in the
same session.
