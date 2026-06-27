# Systems Architecture

This system treats a plain-Markdown knowledge base as the operating environment for a business, and AI agents as the layer that reads and writes it under a fixed contract. The design goals are durability, auditability, and structural privacy.

## Source of truth: plain Markdown in git

Everything durable lives as plain Markdown, versioned in git. This is a deliberate choice over a database or a proprietary app:

- **Durability.** Plain text outlives any tool. The knowledge base opens in any editor, today or in ten years.
- **Auditability.** Every change is a commit. The history *is* the audit log.
- **Portability and graph navigation.** Notes link to each other with wiki-style links, forming a navigable graph; the same files are readable as flat documents.
- **Agent-friendliness.** Agents read and write the same files a human does — there is no hidden state.

Downstream display surfaces (e.g. Notion databases) are treated as **read-only mirrors**. The vault is canonical; mirrors are generated from it and never edited as a source. This "organize in the vault, display downstream" pattern keeps a single source of truth while still giving polished, shareable views.

## Tiered memory

The knowledge base is organized as a cognitive operating system with three memory tiers, which tells both humans and agents where to look first:

- **Hot memory** — active operations: today's logs and the current priority stack.
- **Warm memory** — active strategic context: in-flight work and near-term commitments.
- **Cold memory** — archived reference: completed work, learning archives, superseded material.

Twelve top-level domains each carry a **hub index** note — a single navigational entry point that an agent reads to orient before acting in that domain.

## The two-brain privacy wall

The hardest architectural constraint is privacy. The system runs as **separate brains behind a structural wall**:

- A **business brain** that connects freely across itself.
- A **job-search brain** that may read business context one-way but never writes back into business work.
- A **personal brain** that is git-ignored entirely — it never leaves the local machine — and connects only to itself.

The wall is **structural, not instructional** — the guiding principle is "keys, not prompts." Rather than telling an agent "please don't look," the boundary is enforced by what each context is allowed to read and write, and by git-ignoring the most sensitive zone so it can never be committed or pushed in the first place. There is also a **think-time** rule: when producing business work, the agent does not even *read* across the wall while reasoning — keeping private context out of the output is not enough if it shaped the thinking.

Narrow, explicitly-documented exceptions exist (for example, a personal assistant that spans finances and job-hunting), and each one is justified against the same "keys, not prompts" test: an exception is only safe if the boundary still holds structurally, not because an instruction asks it to.

## The operating contract

Agents operate under a written contract rather than ad-hoc prompts. The contract defines:

- **Role.** The agent acts as an operations partner — it pushes back on misalignment, sequences work by priority (prerequisites first), and enforces standing principles over any one-off request that conflicts with them.
- **Reading order.** A fixed sequence to orient at the start of any session (current state, priorities, principles, the relevant hub, recent logs).
- **Working style.** Direct, sequential, one step at a time.
- **Standing behaviors.** Certain disciplines are always-on, not on-request — for example, pressure-testing a new bet before building it, and verifying work before declaring it done.

## Write protocol and governance

Every change to the knowledge base follows an explicit protocol, which is what keeps the system auditable as it grows:

- Touch a note, update its metadata timestamp.
- Make a significant decision, create a **decision record** and log it in a decision index.
- Finish a work session, append to the day's log with a fixed set of ledgers (work done, changes made, how they were verified, external actions taken, and risks).
- Status changes update the owning context note, never just the log.

**Automation governance** follows the same discipline: nothing runs unattended without a row in a cadence register that names an owner, a trigger, and — critically — a manually-proven manual version *first*. Automation is earned by proving the manual workflow, not assumed.

## Why this matters

The combination — plain-text source of truth, tiered memory, a structural privacy wall, a written operating contract, and an enforced write protocol — turns a pile of notes into a system that can be operated by agents safely and at scale, while staying fully auditable and private by construction.
