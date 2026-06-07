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
Entitlement stays with the Permission Matrix (deferred).

The Cross-Domain Views section is now written into canon as well
(see Snapshot-020): experience-architecture.md enumerates the 7
firm views with their decision-context, composed domains, host
surface, and primary persona, plus the granularity rule, the
naming convention, and the surface-and-view relationship. With
this, KNI-14's content sub-items (Operating Surfaces, Portal
contents, Cross-Domain Views) are complete; only the deferred
Permission Matrix population remains.

The DEC-020 host follow-up is now resolved (see Snapshot-021 /
DEC-023): the Engagement Health View and the Client Engagement
Summary View are hosted on the Reports & Analytics Surface by
scoped reuse (no new surface; the firm inventory stays at
sixteen), so that surface now hosts four distinct views. The
operator-finance gap is resolved for the per-engagement
financial-context need (the operator reaches it via the
Engagement Health View) and is removed from the flagged list; a
cross-engagement financial rollup, if it surfaces, would be a new
item. Three Operating-Surface flags remain (Client Profile,
System Configuration / Settings, Onboarding). KNI-14 is unchanged
— only the deferred Permission Matrix population remains.

Phase 2 sub-item status (7 canon sub-items):
- Populated (5): Personas (with the Future Personas placeholder
  carried), Operating Surfaces, Portals, Cross-Domain Views,
  Navigation Model (surface-movement model; Snapshot-023).
  Navigation Model's landing-surface designation, notification
  routing, and deep-linking stay deferred (marked future items).
- Framework only, soft-blocked for per-channel population:
  Channel Behaviors (channel-agnostic patterns may be writable
  now, but naming behaviors per channel depends on the Phase 4
  Extensibility Channel Model becoming concrete; KNI-18).
- Structure-defined, blocked: Permission Matrix (population
  requires concrete Phase 1 Governance rules; the cross-phase
  dependency is tracked as Q-014 / KNI-16).
- Parked flags (Operating Surfaces): Client Profile, System
  Configuration / Settings, Onboarding.

Phase 2 is therefore 5-of-7 populated.

The five populated Phase 2 sub-items (Personas, Operating Surfaces, Portals,
Cross-Domain Views, Navigation Model) were audited for internal consistency,
boundary adherence, and citation integrity (see Snapshot-026). They are clean
except for one drift: experience-architecture.md had asserted Phase 5 placement
for the Client Brain concept in three places while its ownership is an open
draft. That was corrected to reference altitude (commit edd4e55; FIND-027). The
"final Client Brain ownership" draft area is unchanged, and the 5-of-7 count is
unchanged — no new sub-item was populated.

Phase 3 Capability Map is now scoped and written (Snapshot-024 / DEC-024 for
scope; Snapshot-025 for the write). A grill-me scoping session human-confirmed: the Capability
definition (a reusable, UI-independent functional ability; owns no domain
truth; not a sequence, not a surface; execution mode AI/human/hybrid is a
per-capability attribute, never narrowed to AI-only per Core Principle #1); a
closed six-boundary set (↔ Phase 2 presentation, ↔ Phase 6 sequence, ↔ Phase 1
domain truth, ↔ Phase 4 provider/plugin, ↔ Phase 5 memory/knowledge); five
operational rules (verb-test, sequence-test, workflow-agnostic,
naming-altitude, granularity); the six-field per-capability skeleton; the
non-goals; and the granularity rule (one capability per distinct reusable
ability). All eight sub-items are firm; Video Creation is resolved as a
genuine capability with its tooling deferred to Phase 4. `capabilities.md` now
records all eight capabilities on the six-field skeleton (commits 9be5cbc,
288969a); the header references the Governing Boundary Test and six-boundary
set rather than restating them; the Serves field is a Phase-3 inference at
naming altitude; Q-015 and the inherited Phase 1 questions (domains.md:1914-1915,
:1916, :1917-1918) remain open — referenced, not resolved. The FIND-026
examples-list touch-up (adding Video Creation to domains.md:184-191) is applied
as a separate called-out commit. New this phase: Q-015 (Publishing
scheduling/queueing P3 ↔ P6), FIND-026 (domains.md examples-list
reconciliation), R-027 (entry-writing must not silently resolve an inherited
Phase 1 question).

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

1. Phase 3 `Faraz-OS-Canon/capabilities.md` is written (all eight capabilities,
   Snapshot-025). The remaining Phase 3 open item is Q-015 (Publishing
   scheduling/queueing altitude, P3 ↔ P6) — a deliberate decision when it
   surfaces (KNI-21). The inherited Phase 1 questions (domains.md:1914-1915,
   :1916, :1917-1918) stay referenced, not resolved, pending their owning
   Phase 1 work.
2. Phase 2 is 5-of-7 populated; the Navigation Model is written
   (Snapshot-023, KNI-17). Remaining Phase 2 work:
   - Channel Behaviors is soft-blocked for per-channel population
     on the Phase 4 Extensibility Channel Model (KNI-18,
     Canceled-with-reopen).
   - Permission Matrix population is blocked on concrete Phase 1
     Governance rules (cross-phase dependency Q-014 / KNI-16); it
     remains KNI-14's open item, which keeps KNI-14 In Progress.
   - Navigation Model's landing-surface designation, notification
     routing, and deep-linking stay deferred (marked future items).
   - The three Operating-Surface flags (Client Profile, System
     Configuration / Settings, Onboarding) stay parked.
   No unblocked Phase 2 content remains: both remaining sub-items are blocked
   (Permission Matrix on Q-014 / KNI-16; Channel Behaviors on the Phase 4
   Channel Model / KNI-18). The five populated sub-items were audited clean
   (Snapshot-026), with the Client Brain placement drift corrected (FIND-027).
3. keep Phase 2 and Phase 3 scope distinct from each other and from
   Phase 6 Workflow Design, per the governing boundary test in
   `Faraz-OS-Canon/experience-architecture.md` and the closed six-boundary
   set in DEC-024
4. carry the Future Personas placeholder and the deferred
   navigation sub-detail (notification routing, deep-linking)
   forward as marked future items
5. (optional) consider extending
   `workflows/sync-protocol.md` to formalize
   tracker-backfill as a standing close-out step
   (per R-025 / FIND-023 mitigation); would be its own decision
6. keep Claude Project input limited to high-signal current files
7. prepare later controlled handoff to Claude Code

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
