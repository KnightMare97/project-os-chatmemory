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

Phase 2 scope is defined and human-confirmed
(see Snapshot-013, DEC-019), and Open Question Q-011 is resolved.
The first Phase 2 canon write is complete
(see Snapshot-014):
`Faraz-OS-Canon/experience-architecture.md` defines
the Phase 2 framework — purpose, scope, governing boundary
test, all seven sub-items, non-goals, deferred items, and
cross-phase references.
It does not enumerate concrete surfaces, populate the
permission matrix, or define portal contents.

The Operating Surfaces sub-item is now written into canon
(see Snapshot-017): the Operating Surfaces section of
`experience-architecture.md` carries the granularity rule,
the naming convention, the persona reuse vocabulary
(Full / Scoped / Distinct surface / —), the Scoped marker
placement note, and the firm inventory of 16 surfaces with
primary persona and reuse pattern. The 5 flagged surfaces are
carried forward in that file's Open and Deferred Items and
remain explicitly flagged. Both renames are applied
(*Client Brain Surface*, *Agent & Workflow Monitor*).
The Permission Matrix remains unpopulated; portal contents
per persona and concrete Cross-Domain Views remain deferred.
This was execution of DEC-020 (Snapshot-016); it produced no
new decisions, findings, or open questions.

Portal contents per persona are now written into canon as well
(see Snapshot-018 / DEC-021): the Portals section enumerates, for
each of the five locked personas, which Operating Surfaces its
portal contains and in what reuse mode — a membership and
reuse-mode projection of the DEC-020 inventory, built from the 16
firm surfaces only. The 5 flagged surfaces remain flagged and are
noted as pending per portal where relevant. The Permission Matrix
and concrete Cross-Domain Views remain unpopulated; multi-role
reuse-mode overlap is deferred to the Permission Matrix.

The Cross-Domain Views sub-item (KNI-14 final) is now scoped
(see Snapshot-019 / DEC-022): 7 firm views across Operator,
Manager, Client, and Contractor (System Administrator none), with
a per-decision-context granularity rule and a decision/subject +
"View" naming convention. A view is a named multi-domain
composition rendered on an Operating Surface. Both flagged
surfaces are resolved: Reports & Analytics Surface → both (it
hosts two distinct views); Team Performance / Oversight Surface →
pure Cross-Domain View. The operator-finance gap stays flagged
(Engagement Health View names the composition; host deferred).
Entitlement stays with the Permission Matrix (deferred). The
canon write is the next deliverable.

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
- `Faraz-OS-Canon/domains.md`
- `Faraz-OS-Canon/experience-architecture.md`
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

1. write the Cross-Domain Views section of
   `Faraz-OS-Canon/experience-architecture.md` from the approved
   scope (Snapshot-019 / DEC-022), under plan → build → review,
   in a separate session. State the 7-view inventory, the two
   canon-worthy rules, the surface↔view relationship, and that
   Reports & Analytics Surface hosts two distinct views. After
   that write, KNI-14's content sub-items are complete;
   Permission Matrix population remains deferred until Phase 1
   Governance rules are concrete. Resolve the deferred host
   surfaces (Engagement Health View, Client Engagement Summary
   View) as a DEC-020 follow-up; do not silently fold flagged
   items into firm canon.
2. keep Phase 2 scope distinct from
   Phase 3 Capability Map and Phase 6 Workflow Design,
   per the governing boundary test in
   `Faraz-OS-Canon/experience-architecture.md`
3. carry the Future Personas placeholder and the deferred
   navigation sub-detail (notification routing, deep-linking)
   forward as marked future items
4. (optional) consider extending
   `workflows/sync-protocol.md` to formalize
   tracker-backfill as a standing close-out step
   (per R-025 / FIND-023 mitigation); would be its own decision
5. keep Claude Project input limited to high-signal current files
6. prepare later controlled handoff to Claude Code

Tracker drift surfaced in Snapshot-014 / FIND-023
is reconciled (see Snapshot-015):
Q-012, DEC-012 through DEC-018, and FIND-014 through FIND-018
are now present in the tracker files.
FIND-019, FIND-020, FIND-021 were deliberately not promoted
per the trackers' "active, still-relevant" rule;
they remain in their originating snapshots as historical record.

Open question Q-011 is resolved (see DEC-019 / Snapshot-013).
Open question Q-012 (Phase 7 ↔ Phase 8) is deferred
until Phase 6 is complete.
Open question Q-013 (AI / agent-surface home) is deferred
and not blocking Phase 2.
