# Current State

## Purpose
This file provides a current,
curated view of the repository state for Faraz OS.

It is not the full architecture canon.

It is not the full historical archive.

It exists to help a reader or AI system
quickly understand:
- where the project is now
- what is currently active
- what files matter most
- what remains unresolved
- what should happen next

---

## Project Name
Faraz OS

## Repository Role
This repository is the structured architecture memory,
canon,
snapshot archive,
and handoff layer for Faraz OS.

It supports:
- architecture discovery
- continuity across sessions
- current decision visibility
- current open-question visibility
- controlled AI collaboration
- later handoff to Claude Code

---

## Current Architecture Position
The project is organized by explicit phases.

The canonical phase map is defined in `Faraz-OS-Canon.md`
and currently spans Phase 0 through Phase 11.

Phase 1 Domain Discovery is complete.
Its normalized model in `domains.md`
is the accepted Phase 1 reference.

The current most active work is:
- Phase 2 Experience Architecture

Phase 2 scope is now defined and human-confirmed
(see Snapshot-013), and Open Question Q-011 is resolved.
No Phase 2 content has been written yet;
`experience-architecture.md` is the next deliverable.

Phase 11 Claude Code Operating System
currently owns the operating method
for how Claude collaboration and later Claude Code execution
should be governed.

---

## Current Source of Truth
Interpret repository truth in this order:

1. latest relevant snapshot
2. `Faraz-OS-Canon.md`
3. current phase files in `Faraz-OS-Canon/`
4. refreshed root summary files

Do not treat stale bootstrap files,
historical drafts,
or archive files
as current truth
unless a newer snapshot explicitly points back to them.

---

## Current Most Important Files
The most important current files include:

- `Faraz-OS-Canon.md`
- `CLAUDE.md`
- `Current-State.md`
- `open-questions.md`
- `decisions.md`
- `findings.md`
- `snapshots.md`
- current relevant files in `Faraz-OS-Canon/`
- latest relevant files in `snapshots/`

At the current stage,
special importance should be given to:
- canon files
- recent snapshots
- Phase 1 definition and normalization files
- repository-level Claude operating rules

---

## Current Phase 1 Position
Phase 1 Domain Discovery is complete.
Normalization pass v1 on `domains.md`
has been applied and accepted (see Snapshot-010).

This does not mean every boundary is finalized.
Unresolved draft boundaries remain draft
until separately resolved.

`domains.md` is the accepted source of truth
for the Phase 1 domain model
and must not be re-normalized or re-discovered
without a new explicit decision.

---

## Normalization Status and Rules
Normalization pass v1 on `domains.md` is complete
and accepted (see Snapshot-010).

Any future normalization must continue to be treated
as a controlled architecture-editing task.

It should:
- remove duplicated definitions
- preserve one canonical definition for major concepts
- improve structural consistency
- improve wording consistency
- preserve explicit Assumption,
  Open Question,
  and Risk markers

It must not:
- invent new architecture
- silently finalize unresolved boundaries
- collapse meaningful distinctions
- erase useful ambiguity

The preferred later execution path
is Claude Code under explicit constraints
with human review.

---

## Current Phase 11 Position
Claude collaboration is now being made more explicit
through repository-level operating rules.

This includes:
- `CLAUDE.md`
- session discipline
- session close-out and sync discipline
- source-of-truth discipline
- plan/build/review mode discipline
- handoff-oriented repository behavior

Execution tracking is mirrored in Linear.
GitHub remains the source of truth;
Linear is execution tracking only,
reconciled against the latest snapshot at session close.

The executable runbook for this reconciliation
is `workflows/sync-protocol.md`
(the single canonical Linear ↔ GitHub sync procedure).

This separates architecture content ownership
from Claude operating behavior.

---

## Current Repository Reality
The repository contains a mix of:
- canonical files
- current summary files
- snapshots
- older bootstrap material
- historical draft material

This means not every file has equal freshness
or equal authority.

Canonical files and recent snapshots
should be trusted before stale summary material.

---

## Current Important Draft Areas
Some important architectural areas remain draft.

These include:
- final Client Brain ownership
- final Brand placement
- final Service Agreement ownership
- final Aggregate boundaries
- some cross-domain operational boundaries

These draft areas should remain visible
until explicitly resolved.

---

## Current Working Rule
Prefer:
- updating existing files
- minimal diffs
- canonical consolidation
- explicit change intent
- visible uncertainty

Avoid:
- parallel source-of-truth files
- broad speculative redesign
- silent structural reinterpretation
- hidden resolution of open questions

---

## Current Next Focus
The current recommended next focus is:

1. write `Faraz-OS-Canon/experience-architecture.md`
   from the approved Phase 2 scope (Snapshot-013),
   under plan -> build -> review,
   in a separate session
2. keep Phase 2 scope distinct from
   Phase 3 Capability Map and Phase 6 Workflow Design,
   per the governing boundary test in Snapshot-013
3. carry the Future Personas placeholder and the deferred
   navigation sub-detail forward as marked future items
4. keep Claude Project input limited to high-signal current files
5. prepare later controlled handoff to Claude Code

Open question Q-011 (Phase 2 ↔ Phase 3 boundary)
is now resolved (see Snapshot-013).
