---
version: "2.0"
created: 2026-11-13
updated: 2026-11-13
---

# Agent procedures, code and permission boundaries

**Version 2.0** · 2026-11-13

The canonical agent entry point directs tools to the operating contract, then
HOME, priorities, principles, the relevant hub and recent context. Skills supply
task-specific procedures; deterministic code handles operations such as validation,
state persistence, hashing, exports and synchronization. This describes the
inspected architecture; the complete private skill library is not published here.
[A1](evidence-and-status.md#a1).

## Procedure versus implementation

A skill defines when to run, required context, ordered steps, human seams,
verification and follow-up. Companion owner notes add source context; owner
annotations and review marks remain owner-controlled. A procedure can direct an
agent to run a validator, but a Markdown instruction alone does not enforce that
validator or constrain a credential. The [example skill](../examples/example-skill/SKILL.md)
is an invented illustration.

The private code includes workspace construction and manual publication tools,
sync/registry utilities, vault checks, log compliance, and the engagement engine.
Presence of source establishes implementation, not deployment health, schedule
activation or a successful live integration. This revision runs none of the private
publishers or live sync commands. Old fixed skill/engine counts have been removed.

## Four different boundaries

| Boundary | What establishes it | What does not establish it |
|---|---|---|
| Content selection | A reviewed collector policy, immutable source and checked output | A broad copy followed by deleting visible files |
| Repository access | A credential scoped to approved repositories and permissions | A role name or a prompt |
| Application access | Separately authorized connection, identity, scopes and destinations | Being granted a repository |
| Human release | The relevant owner review/acceptance process tied to the artifact | A model saying another model approved it |

Gitignore is a Git-selection mechanism, not a filesystem access-control list.
An agent with access to the original directory can still read ignored files if
the surrounding sandbox and authorization allow it. Think-time separation is an
operating rule; a filtered clone with scoped credentials is a stronger content
boundary for a remote employee. Account-wide applications require separate review.
[A1](evidence-and-status.md#a1), [A2](evidence-and-status.md#a2).

## Employee identity and collaboration

The employee's role instructions, model/provider, running process, Slack author
and repository credential are distinct identities. Saving role text does not
establish a running employee. A live route needs separately verified identity,
allowed workspace/channel/author, supported trigger, context access, delivery and
recovery. The published Employee Hub slice demonstrates an offline handoff and
event admission only. [A3](evidence-and-status.md#a3).

One roster peer can receive the visible lead message and one question. A receipt
prevents replayed events from re-executing the turn. This is at-most-once admission:
an uncertain send or later peer failure can leave a partial thread. Recovery needs
reconciliation, not a blind retry. Tests demonstrate these declared fixture paths;
they do not commission the hosted employees or prove a live peer round trip.

## Review and automation

The operating contract routes review by risk: a bounded documentation change,
routine code, a shared/privacy-sensitive change and an external action require
different controls. Builder, specialist checks, independent judge where required,
and owner merge authority have distinct responsibilities. Pressure testing and
citation checks are documented disciplines; their existence does not guarantee
universal compliance. [A1](evidence-and-status.md#a1).

Unattended work requires an explicitly governed owner/trigger and a manually
proven workflow first. A script, installed plugin or configured connector is not
evidence of a running schedule. No new schedule or permission grant is made by this
showcase. See [status limits](evidence-and-status.md).
