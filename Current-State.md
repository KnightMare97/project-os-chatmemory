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
- Populated (7): Personas (with the Future Personas placeholder
  carried), Operating Surfaces, Portals, Cross-Domain Views,
  Navigation Model (surface-movement model; Snapshot-023),
  Channel Behaviors (per channel type; Snapshot-031 / KNI-18), and
  the Permission Matrix (read-only projection of the DEC-026
  authorization rules through the surface↔resource mapping;
  Snapshot-033 / KNI-14; reproduces the ratified DEC-020 exposure,
  zero divergence).
  Navigation Model's landing-surface designation, notification
  routing, and deep-linking stay deferred (marked future items).
- Parked flags (Operating Surfaces): Client Profile, System
  Configuration / Settings, Onboarding.

Phase 2 is therefore 7-of-7 populated — **Phase 2 Experience Architecture is
complete.** (One flagged Phase-2 view-membership nuance, Q-016, is tracked
separately and does not affect the 7-of-7 surface projection.)

The five populated Phase 2 sub-items (Personas, Operating Surfaces, Portals,
Cross-Domain Views, Navigation Model) were audited for internal consistency,
boundary adherence, and citation integrity (see Snapshot-026). They are clean
except for one drift: experience-architecture.md had asserted Phase 5 placement
for the Client Brain concept in three places while its ownership is an open
draft. That was corrected to reference altitude (commit edd4e55; FIND-027). The
"final Client Brain ownership" draft area is unchanged; that audit populated no
new sub-item (the count then stood at 5-of-7; it is now 7-of-7 — see the sub-item
status above).

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
naming altitude; Q-015 (since resolved, DEC-028 / Snapshot-036), while the
inherited Phase 1 questions (domains.md:1916-1917, :1918, :1919-1920) remain
open — referenced, not resolved. The FIND-026
examples-list touch-up (adding Video Creation to domains.md:184-191) is applied
as a separate called-out commit. New this phase: Q-015 (Publishing
scheduling/queueing P3 ↔ P6), FIND-026 (domains.md examples-list
reconciliation), R-027 (entry-writing must not silently resolve an inherited
Phase 1 question).

Phase 4 Extensibility Model scope is now defined (Snapshot-027 / DEC-025;
scoping only — no `extensibility.md` content written). DEC-025 records: an
in-scope core of eight sub-items (Permission, Extension Contracts, Plugin Model,
Provider Model, Channel Model, Model, AI Model Routing, Runtime vs Config-Time)
and four deferred-and-flagged (Versioning & Compatibility, External Integrations,
Feature Modules, Future Domains); the locked distinction set (Model and AI Model
Routing kept separate; Channel Model first-class but typed as a Provider-Model
specialization — recorded as a DEC-025 scoping inference, not pre-existing canon);
the closed boundary set (definition/altitude + six cross-phase boundaries, P6 and
P7 split, Phase 1 a single Governance boundary); the selection-vs-sequence test;
the grant-altitude rule (R-028); the six-field per-sub-item skeleton; the
non-goals (including human identity and implementation technology); and the
Channel-Model unblock-altitude scope with its verbatim acceptance test. DEC-025
itself wrote no canon content and resolved no Phase 1 question. Registered open
flags carried forward: agent/subagent identity (likely Phase 7), safety-controls
vocabulary, the optional philosophy-#7 annotation, and a repo-wide
inherited-question citation drift (FIND-028; since resolved).

All eight in-scope entries of `extensibility.md` are now written (Snapshot-030;
Batches A–C, commits 8e921a8, 1b148d4, 082b261): the file skeleton; the Provider
Model, Channel Model, Extension Contracts, Permission, Plugin Model, Model, and AI
Model Routing entries; the Runtime vs Config-Time Extensions framing section; the
deferred-sub-item stubs; non-goals; and open flags. The four deferred sub-items
(Versioning & Compatibility, External Integrations, Feature Modules, Future
Domains) remain flagged stubs per DEC-025. The Channel Model meets the DEC-025
acceptance test, so Phase 2 Channel Behaviors (KNI-18) is now unblockable pending
a gated reopen.

Phase 5 Knowledge & Memory Architecture is now scoped (Snapshot-034 / DEC-027). The
Phase 5 question-gate (G-1 → G-7) is closed: the structural frame (G-1 logical
altitude; G-2 closed seven-boundary set; G-3 six firm sub-items + Asset Intelligence
deferred stub; G-4 six-field skeleton; G-5 non-goals), the Q-001 resolution (G-6:
**Client Brain is owned by the Knowledge domain**, as a Memory Object / Shared
Service Artifact; Client Success contributes and CRM references, both non-owning),
and the carried items (G-6 Q-004 partitioning, entangled with Q-003; G-7
insight→durable-knowledge threshold, Phase-1 Intelligence truth pending, R-027). The
ownership resolution was landed as the isolated Phase-1 `domains.md` ownership update
(landing (i); commit `e44a201`, 13 sites) plus the `experience-architecture.md`
citation refresh (commit `4550d46`, four sites, reference altitude). The
`memory.md` first write (landing (ii)) is **complete** (Snapshot-035; commit
`89f5034`): six firm entries (Client Brain, Agency Brain, Knowledge Base, Decision
Logs, Learnings, Context Retrieval) on the six-field skeleton — Client Brain written
partition-agnostic, Asset Intelligence a deferred stub. Every Owner field is a
Phase-1 reference (Knowledge owns all six); authorization defers to DEC-026, physical
retrieval/storage to Phase 7.

Phase 6 Workflow Design is now scoped (Snapshot-036 / DEC-028) and its **first write
is complete** (Snapshot-037): `Faraz-OS-Canon/workflows.md` is written (428 lines;
Batches A `6eefd90`, B `a7de5ef`, C `a0fe15d`) and consistency-reviewed clean
(Snapshot-038). **Phase 6 is now complete at DEC-028's scope — 13/13 sub-items
(DEC-029)**, which **fires Q-012's trigger**: Q-012 (Phase 7 ↔ Phase 8) moves
deferred → active, and the Phase 7 ↔ Phase 8 **scoping** becomes the open thread
(scoping only — no Phase-7/8 content before its own question-gate). Any future
Q-017-driven Phase-6 increment is marked-future and does not reopen the phase. The
file carries the skeleton; the three framing/construct
sections (Human Approval Gates per G-6(a); Agent Chains per G-6(b) with the
role-vs-identity litmus verbatim; Workflow Runtime per G-6(c) with the P6↔P7 litmus
verbatim); the three loop/exception patterns (Escalation, Revision,
Failure/Exception); the seven flow entries on the six-field skeleton (Lead → Client,
Client → Strategy, Strategy → Production, Production → Approval, Approval →
Publishing, Publishing → Reporting, Learn → Memory Update); the non-goals; and the
open/inherited flags. Capabilities are referenced name-only; gates place but never
authorize (who-may-approve = Phase 1 / DEC-026); agent steps are at role altitude;
no memory structure, threshold (R-027), or engine is authored. The scope itself was
fixed by DEC-028 (commit `e9c9296`) with the Q-015 resolution and the isolated
`capabilities.md` refresh (commit `623960e`); the execution-mode operating contract
is persisted in `CLAUDE.md` (commits `7f1cda3`, `e96b435`). **Q-017** (new this
session, registered): system-administrator visual workflow viewing + management —
viewing partially covered by the Phase-2 Agent & Workflow Monitor surface, visual
editing/management multi-phase placement pending its own gated decision.

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
- Client Brain partitioning — per Client / per Brand (Q-004; entangled with Q-003).
  Client Brain *ownership* is resolved to Knowledge (DEC-027); only partitioning
  remains draft.
- final Brand placement
- final Service Agreement ownership
- final Aggregate boundaries (incl. Client Brain Aggregate vs Memory Object)
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

**Phase 6 Workflow Design — complete at DEC-028's scope (DEC-029).** `workflows.md`
is written (Batches A–C; `6eefd90` / `a7de5ef` / `a0fe15d`), under DEC-028, via
per-batch reviewer byte-reads (FIND-033), and consistency-reviewed **clean**
(Snapshot-038; zero meaning-level findings). DEC-029 declares Phase 6 complete at
DEC-028's scope (13/13 sub-items) and **fires Q-012's trigger**. **The next open
thread is the Phase 7 ↔ Phase 8 boundary scoping (Q-012; KNI-11 re-opens) — scoping
only, no Phase-7/8 content before its own question-gate.** Other fresh/gated
follow-ups: **Q-017** (system-administrator visual workflow management — multi-phase;
any Phase-6 increment is marked-future, does not reopen the phase); the four Phase-4
deferred sub-items; Phase 5 Asset Intelligence un-defer. Linear: **KNI-26 is Done**
(Snapshot-037); **KNI-11 re-opens** (after the verified push).

**Phase 5 Knowledge & Memory — first write complete (Snapshot-035).** `memory.md` is
written (landing (ii); commit `89f5034`). The Phase 5 question-gate was closed by DEC-027: the G-1–G-5 structural frame (logical altitude;
closed seven-boundary set; six firm sub-items + Asset Intelligence deferred stub;
six-field skeleton; non-goals); G-6 resolved **Q-001** (Client Brain owned by the
Knowledge domain, as Memory Object / Shared Service Artifact; Client Success
contributes and CRM references, both non-owning); G-7 carried the
insight→durable-knowledge threshold (Phase-1 Intelligence truth, pending; R-027).
Q-004 (Client Brain partitioning) is carried, entangled with Q-003; the eventual
`memory.md` entry is written partition-agnostic. The ownership resolution landed as
the isolated Phase-1 `domains.md` update (landing (i); commit `e44a201`) with the
`experience-architecture.md` citation refresh (commit `4550d46`). **Landing (ii) is
complete**: `memory.md` carries six firm entries (Client Brain, Agency Brain,
Knowledge Base, Decision Logs, Learnings, Context Retrieval) on the six-field
skeleton — Client Brain partition-agnostic (Q-004 carried), Learnings referencing
the insight→durable-knowledge threshold at altitude (R-027), every Owner a Phase-1
reference (Knowledge owns all six) — with Asset Intelligence a deferred-flagged stub.
The remaining Phase 5 items are carry-forwards, none blocking: Asset Intelligence
un-defer (its own gated decision); Q-004 partitioning (resolves with Q-003); the
Client Brain Aggregate-vs-Memory-Object and approval-before-durable canon flags.
Candidate fresh threads: the four Phase-4 deferred sub-items; Phase 5 Asset
Intelligence un-defer. (Phase 6 Workflow Design first write is complete — see the lead above.)

**Phase 4 Extensibility — first write complete.** All eight in-scope
`extensibility.md` entries are written (Snapshot-030, Batches A–C); KNI-23's
done-condition is met and it moves to Done after this close-out push is verified.
The four deferred sub-items (Versioning & Compatibility, External Integrations,
Feature Modules, Future Domains) remain flagged stubs; each becomes its own work
item if/when un-deferred. The next Phase 4 decisions are fresh, gated topics:
(a) the Phase 2 Channel Behaviors write against the now-landed Channel Model
(KNI-18 reopen — awaiting explicit green-light); (b) un-deferring any of the four
sub-items. Carry the registered open flags (agent/subagent identity;
safety-controls vocabulary; philosophy-#7 annotation) and
the inherited Phase 1 questions forward, unresolved.

The standing items below remain:

1. Phase 3 `Faraz-OS-Canon/capabilities.md` is written (all eight capabilities,
   Snapshot-025). Q-015 (Publishing scheduling/queueing altitude, P3 ↔ P6) is
   now **resolved** (DEC-028 / Snapshot-036; KNI-21 → Done): atomic push and the
   scheduled-publish when-parameter are firm Phase 3, cross-item queueing is
   Phase 6 orchestration. Phase 3 has no remaining open item of its own. The
   inherited Phase 1 questions (domains.md:1916-1917, :1918, :1919-1920) stay
   referenced, not resolved, pending their owning Phase 1 work.
2. **Phase 2 Experience Architecture is complete — 7-of-7 populated.** The
   Permission Matrix is populated (Snapshot-033 / KNI-14): a read-only projection
   of the DEC-026 authorization rules through the surface↔resource mapping
   (authors no rules; DEC-019 / FIND-022), reproducing the ratified DEC-020
   exposure with zero divergence. **Q-014 is fully resolved** (DEC-026 +
   the matrix population). Remaining Phase-2 carry-forwards are marked-future /
   parked, not blockers:
   - Navigation Model's landing-surface designation, notification
     routing, and deep-linking stay deferred (marked future items).
   - The three Operating-Surface flags (Client Profile, System
     Configuration / Settings, Onboarding) stay parked.
   - Q-016 (one Phase-2 view-membership nuance: Client × Performance & Analytics
     View) is tracked separately; it does not affect the 7-of-7 surface
     projection.
3. keep Phase 2 and Phase 3 scope distinct from each other and from
   Phase 6 Workflow Design, per the governing boundary test in
   `Faraz-OS-Canon/experience-architecture.md` and the closed six-boundary
   set in DEC-024
4. carry the Future Personas placeholder and the deferred
   navigation sub-detail (notification routing, deep-linking)
   forward as marked future items
5. **Done** (Snapshot-039): `workflows/sync-protocol.md` now formalizes
   tracker-backfill as a standing close-out step (Step 1; per R-025 / FIND-023
   mitigation), landed in the normalization-backlog thread alongside the
   Fixed-Coordinates milestone-id harmonization.
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
Open question Q-015 (Publishing scheduling/queueing, P3 ↔ P6)
is resolved (see DEC-028 / Snapshot-036).
Open question Q-017 (system-administrator visual workflow
viewing + management) is open and registered (see Snapshot-037);
multi-phase placement pending its own gated decision.
Open question Q-012 (Phase 7 ↔ Phase 8) is now active
(unblocked by DEC-029 — Phase 6 complete at DEC-028's scope);
Phase 7 ↔ Phase 8 scoping is the open thread (scoping only, not Phase-7/8 content).
Open question Q-013 (AI / agent-surface home) is deferred
and not blocking Phase 2.
