# Agent-Skill Framework and Automation

The core of the AI engineering in this system is a library of **70+ agent skills** plus a layer of **deterministic automation engines**. Together they let an agent do real, repeatable work — not one-off chat responses.

## What a skill is

A skill is a self-contained, versioned agent workflow stored as a Markdown file. It is a *procedure*, written so an agent can execute it consistently. Every skill carries:

- **A name and description** with explicit **trigger phrases** — the natural-language cues that should invoke it (e.g. "do X", "/skill-name", "handle Y").
- **Ordered steps** with explicit paths and decision points.
- **Capability requirements** stated as capabilities (read, write, search, shell), not product-specific tool names — so the skill is portable across agent surfaces.
- **A verification step** — how the result is checked before it is considered done.
- **A feedback loop** — skills are never "finished"; after each run, what worked and what didn't is captured and folded back into the skill.

This makes each skill a small, testable unit of agent capability with a clear contract — closer to a function with a docstring than to a prompt.

## Categories of skills

The library spans the full operating surface of the business:

- **Capture pipeline** — ingest a book, paper, video, web page, or documentation site into a cited source artifact (see [learning-system.md](learning-system.md)).
- **Decision and strategy** — structured frameworks for situation assessment, options analysis, pricing, risk, competitive intelligence, and pressure-testing.
- **Operations** — daily logging, session handoff, build verification, and consistency linting.
- **Synthesis** — surfacing non-obvious cross-domain connections within the business brain.
- **Downstream mirrors** — syncing the canonical vault into read-only display databases.

## Multi-agent patterns

The system uses more than a single agent calling tools in a loop:

- **Council-style review.** Before committing to a new product, offer, price, or strategy bet, a panel of distinct personas critiques the idea, and a *separate* judge renders a verdict (green-light / reshape / kill) plus the cheapest test to de-risk it. The separation of critics from judge is deliberate — it counteracts an agent's tendency to agree with whatever it is shown.
- **Devil's advocate.** A standing protocol that argues *against* a decision being logged, surfacing blind spots and second-order consequences.
- **Verify-before-done.** A discipline that pins an explicit definition of done, verifies against it, stress-tests the result, and reports "verified, not just asserted." An agent's own claim that it finished is never accepted as proof.

## Proactive behavior without brittle hooks

A recurring engineering question is how to make a behavior "automatic." This system's default answer is a **judgment-driven contract rule**, not a deterministic hook or gate — unless a hard guarantee is genuinely required. Standing behaviors (pressure-test before building, verify before done, cite before shipping) are written into the operating contract as always-on expectations the agent applies with judgment, reserving rigid enforcement for the few places that truly need a hard stop.

## MCP connectors

The agent runtime integrates external systems via MCP (Model Context Protocol) connectors — for example, mirroring the vault into a Notion display database. Connectors are tracked in a register so it is always clear which integrations are wired in versus merely available.

## Deterministic automation engines

Alongside the probabilistic agent layer sits a layer of **deterministic Python engines** — roughly a dozen scripts that do the work that must be exact and repeatable:

- **Mirror sync engines** diff the canonical vault against a registry of last-synced state and upsert changes into downstream display databases (create new rows, refresh drifted ones, mark removed ones deprecated, stamp a sync timestamp).
- **Drift detectors** flag when a downstream mirror has diverged from the source.
- **Compliance checks** enforce the write protocol (for example, that a work session was logged before a commit).
- **Watchdogs and monitors** run on a schedule under the cadence register to catch problems and surface new inputs.

The division of labor is the point: **agents handle judgment; deterministic scripts handle correctness.** Anything that must be exact, idempotent, and auditable is a script, not a prompt.

## The mirror pattern, generalized

The vault-to-display mirror is implemented the same way several times over (skills, procedures, folder maps, connectors) — a reusable pattern: a canonical Markdown source, a JSON registry of sync state, a deterministic diff-and-upsert engine, and a read-only downstream view. Establishing one robust pattern and instantiating it repeatedly is a core engineering theme of the system.
