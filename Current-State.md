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

**ALL ELEVEN PHASES NOW HAVE FIRST-WRITE ENTRIES. The Faraz OS
architecture-memory repository is complete as a design canon.**

Phase 11 Claude Code Operating System — `claude-operating-system.md` (824 lines) —
is the Phase 11 deliverable: the operating discipline for Claude Code build sessions
(four agent stances, three modes, session protocol, prompt handoff, provisioning
checklist, development rules, coding-standards framework, Build-Time CLAUDE.md
Template). DEC-050 mints the Phase 11 scope gate (four rulings: build snapshots
→ build repo, agent roles = stances + extensible, coding standards deferred to
build-repo CLAUDE.md, secret naming `faraz-os-{env}-{block}-{type}` with
plain-language provisioning checklist).

Phase 10 Build Roadmap — `roadmap.md` (589 lines) — is the Phase 10 deliverable:
a dependency-ordered Build Roadmap (Foundation → Core Layer → T1 Launch → V1 →
V2 → Future) on the six-field skeleton. DEC-049 mints the Phase 10 scope gate
(six rulings: MVP/V1 showcase framing, Q-006/Q-024 pre-build gates,
bilingual/IR-sensitivity as first-class T1 build constraints).

*(Prior active work — for historical context:)*
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
complete.** Q-016 (Client × Performance & Analytics View membership nuance) has
since been resolved by DEC-047: Client sees this view, scoped to own-engagement.
The 7-of-7 surface projection was never affected.

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
inherited Phase 1 questions (domains.md:1944-1945, :1946, :1947-1948) remain
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
(DEC-029 / Snapshot-040)**, which **fired Q-012's trigger**: Q-012 (Phase 7 ↔ Phase 8) moved
deferred → active, and the Phase 7 ↔ Phase 8 **scoping** became the open thread
(scoping only — no Phase-7/8 content before its own question-gate). **Q-012 is now
resolved (DEC-030 / Snapshot-041; commit `fdbe0fe`): Phase 7 = the cross-cutting
concern-views, Phase 8 = the layered assembly, one-way dependency (P7 first) — see
Current Next Focus.** Any future
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
is persisted in `CLAUDE.md` (commits `7f1cda3`, `e96b435`). **Q-017 resolved (DEC-048, 2026-06-09)**: workflows fixed-flow at T1; System Administrator
views execution state via Phase 2 Agent & Workflow Monitor (Full; no new surface); visual
editing/management deferred to v2 as multi-phase gated feature.

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

A new domain — **Media & Assets** — was added by DEC-033 (resolving Q-018):
it owns the **Client Asset** entity. **Service Agreement** was then made firm by DEC-034
(resolving Q-002): a first-class **Entity owned by CRM** (reference-addressable, not
absorbed into the Client Account entity; Aggregate-pending-Q-006). Then a new domain —
**Community** — was added by DEC-035 (resolving Q-019): it owns post-publish audience
engagement (Comment, Direct Message, Conversation/Thread, Engagement Reply as Entities;
Sentiment Signal left contested; B2C audience axis distinct from the B2B CRM/Client-Success
axes). Then **Brand** was made firm by DEC-036 (resolving Q-003): a **first-class Entity owned
by CRM** (reference-addressable, not absorbed into Client Account; mandatory Client reference,
1 Client : N Brand; aggregate placement draft/pending) — which **unblocks Q-004** (Client Brain
partitioning, still open). Then a new domain — **AI Operations** — was added by DEC-038
(resolving Q-021): it owns the per-job **UsageRecord** Entity (raw AI usage/cost; per-client cost
is derived → Intelligence; four-way seam P1-owns / P7-meters / Intelligence-margin /
Governance-cap + P4-enforce; Finance-sub-ledger carried fallback). Then **Ticket** was made a
first-class Entity in **Client Success** by DEC-039 (resolving Q-023): not a new domain (extend
test; Escalation Handling BC covers structured client issue intake); explicitly distinct from
Escalation Case and Coordination Request (non-collapse discipline, DEC-034 pattern); aggregate
placement pending Q-024. These are the **first six** of the ~10 Phase-1 entity reopenings the
non-canon gap analysis surfaced; **~4 remain** (Campaign, Ad-Account, Schedule, Consent); each
further reopening is its own explicit gated decision (domain truth is never re-discovered
wholesale). The Community Phase-3 capability / Phase-4 inbound-channel category / Phase-6
post-publish workflow, the Brand-Kit / brand-style / Brand-aggregate follow-ons, the
AI-Operations P7-metering / Intelligence-margin / Governance-cap / P4-enforcement /
prompt-versioning (Q-022 resolved — DEC-044) follow-ons, and the **Ticket P6-8th-flow /
P2-submit-surface / P4-inbound-channel / aggregate-boundary (Q-024)** follow-ons, are
separate later gates.

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

**Phase 11 Claude Code Operating System — FIRST WRITE COMPLETE.**
(Snapshot-050 / DEC-050 / 2026-06-10)

`Faraz-OS-Canon/claude-operating-system.md` (824 lines) is the Phase 11 deliverable.
It defines the operating discipline for Claude Code build sessions:
- Four agent stances: Architect Agent, Builder Agent, QA Agent, Review Agent
  (extensible model — add roles as build needs require)
- Three operating modes: Plan Mode, Build Mode, Review Mode (with transition table)
- Session protocol: start discipline, close-out discipline, GATED vs AUTO split
- Snapshot discipline: build snapshots belong in the build repo (not here)
- Prompt handoff format for cold-start session orientation
- Prerequisites / Provisioning Checklist: plain-language enumerated list of every
  GCP account, API, service account, IAM role, and secret Ali must provision
  before the Foundation stage gate; secret naming `faraz-os-{env}-{block}-{type}`
- Development rules (9 rules, technology-agnostic)
- Coding standards framework: universal rules + deferred pins for build-repo CLAUDE.md
- Appendix A: Build-Time CLAUDE.md Template (fenced code block spec; no real CLAUDE.md
  created in this repo; `./CLAUDE.md` untouched)

The build repo (separate from this architecture-memory repo) will be created at
build time. Architecture-memory repo stays pure design canon.

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
- Brand aggregate placement (Brand entity placement is resolved — DEC-036; only
  aggregate placement remains draft)
- final Service Agreement ownership
- final Aggregate boundaries (incl. Client Brain Aggregate vs Memory Object)
- some cross-domain operational boundaries

Note: Client Brain partitioning is now resolved — DEC-045 (per-Brand partitioning with
per-Client aggregation view). This draft area is closed.

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

**ALL ELEVEN PHASES COMPLETE. Architecture-memory repository is done as design canon.**

Phase 11 COMPLETE (Snapshot-050, 2026-06-10). DEC-050 minted;
`claude-operating-system.md` first write pushed and verified. **All eleven phases
(Phases 0–11) now have first-write entries.** Next recommended steps:

1. **Q-006 Phase-1 gate** — Service Agreement / Engagement Scope aggregate boundary;
   mandatory before CRM domain schema can be written in the build repo.
2. **Q-024 Phase-1 gate** — Ticket ↔ Escalation Case lifecycle coupling; mandatory
   before Client Success domain schema can be written in the build repo.
3. **Build-repo setup** — Create the separate build/code repository; instantiate
   the Build-Time CLAUDE.md Template (Appendix A of `claude-operating-system.md`);
   complete the provisioning checklist; pin coding standards in build-repo CLAUDE.md.
4. **Q-003 Phase-1 gate** — Brand aggregate placement; preferably before V1
   schema finalization.
5. **Foundation stage build** — Begin MVP Foundation stage per `roadmap.md`,
   once build repo is set up and provisioning checklist is complete.

Remaining open items (do not touch without explicit gate):
- Q-003 (Brand aggregate placement), Q-006, Q-007, Q-024 (`domains.md:1720`),
  insight→durable-knowledge threshold (`domains.md:1946`), 4 Phase-1 entity reopenings
  (Campaign, Ad-Account, Schedule, Consent), Agent Supervision/Observability deferred slot.

---
*(Prior Next Focus entries — preserved for historical record:)*

**Q-023 resolved (DEC-039): Ticket is a first-class Entity in Client Success** — extend test
(not a new domain); non-collapse from Escalation Case and Coordination Request explicit.
Lifecycle: submitted → routed → in-progress → resolved/closed. Aggregate placement pending
Q-024. **6th of the ~10 Phase-1 reopenings; ~4 remain** (Campaign, Ad-Account, Schedule,
Consent). **Q-024** (Ticket ↔ Escalation Case lifecycle coupling) registered open;
cross-references `domains.md:1720`. Separate later gates: P6 8th flow; P2 submit surface;
P4 inbound channel; Ticket ↔ Escalation Case aggregate boundary.

**Q-021 resolved (DEC-038): a new Phase-1 domain — AI Operations — owns the per-job UsageRecord
Entity** (raw AI usage/cost). The 5th of the ~10 reopenings. Per-client cost is derived
(Intelligence); four-way seam (P1-owns / P7-meters / Intelligence-margin / Governance-cap +
P4-enforce). **Q-022 resolved (DEC-044)**: Knowledge owns PromptTemplate.

**Dual-Path / Manual-Fallback recorded as a cross-phase principle (DEC-037).** Phase-6 4th
loop/exception pattern "Dual-Path / Manual-Fallback Routing" is written (Snapshot-045;
commit `2f9dd56`; KNI-33 Done). **Q-020 resolved (DEC-046)**: access-status/connection-health
is a Phase 4 Channel Model operational attribute (4th property).

**Q-003 resolved (DEC-036): Brand is a first-class Entity owned by CRM** (reference-addressable,
not absorbed into Client Account; mandatory Client reference, 1 Client : N Brand; aggregate
placement draft/pending) — extend pattern (DEC-034 mirror). **Unblocks Q-004** (Client Brain
partitioning, now unblocked-but-open). The **4th** of the ~10 Phase-1 reopenings; **~6 remain**
(Campaign, Cost-ledger / Prompt, Ticket, Ad-Account, Schedule, Consent — each its own gated
decision). Brand's identity-vs-memory seam (CRM identity vs Client-Brain/Knowledge voice-style
content) holds; Brand Kit → Media & Assets, brand-style enforcement → P3/Governance, Brand
aggregate placement = separate later gates.

**Q-019 resolved (DEC-035): a new Phase-1 domain — Community — owns post-publish audience
engagement (Comment / Direct Message / Conversation / Engagement Reply as Entities; Sentiment
Signal contested/draft).** The 3rd of the ~10 Phase-1 entity reopenings (Media & Assets / DEC-033
and Service Agreement / DEC-034 were 1st and 2nd). Community's
Phase-3 capability, Phase-4 inbound-channel category, and Phase-6 8th workflow (the post-publish
flow) are **separate later gates**, not yet taken.

**Phase 7 System Architecture Blueprint — first write COMPLETE (all seven concern-views;
Batches A–E; Snapshot-044).** `system-architecture-blueprint.md` carries Logical,
Application, Data, AI, Integration, Security, and Runtime Architecture on the six-field
skeleton + Non-goals / Open-and-deferred / Carried (DEC-031 scope realized at logical
altitude; KNI-27 → Done). **This is a first-write-complete milestone, NOT a phase-complete
declaration** (Phase-2 / Phase-6 precedent) — Phase 7 carries open *referenced* items
(the dual-path posture, deeper agent supervision) and a Phase-7 phase-complete call would
be a separate later gated decision. **The open program is the ~8 remaining Phase-1 entity
reopenings the non-canon gap analysis surfaced** (Engagement / Community, Brand [Q-003],
Campaign, Cost-ledger / Prompt, Ticket, Ad-Account, Schedule, Consent) — each its own
gated decision; **Q-018 (Client Asset → Media & Assets, DEC-033) and Q-002 (Service
Agreement → CRM-owned Entity, DEC-034) were the first two.** Phase 8 (Puzzle Board /
layered assembly) scope gate is **CLOSED (DEC-040)**: G-1…G-8 ruled; 7 layers
first-write firm; Core Layer (7 blocks) and AI Layer (5 blocks + 2 deferred slots)
named at altitude; Core↔Infrastructure + Experience↔AI cuts governed; Phase-6-not-Core
guard explicit. `architecture.md` **first write is COMPLETE (Snapshot-046; Batches A–C;
commits `967f285`/`1de08f7`/`9f01c6a`; KNI-39 Done)**. **All eight architecture content
phases (Phases 1–8) now have first-write entries** — first-write-complete milestone, NOT
a formal Phase-8-complete declaration (Phase-2/6/7 precedent). (P7↔P8 boundary: DEC-030.)

**Q-018 resolved (DEC-033): a new Phase-1 domain — Media & Assets — owns the Client
Asset entity; the Phase-7 Data Architecture view is now unblocked.** DEC-033 places the
Client Asset (one entity spanning raw / client-uploaded / AI-generated / produced media,
plus rights / provenance / retention-status) in a new accepted domain; Asset
Intelligence (P5) stays deferred. This is the **first of ~10 Phase-1 entity reopenings**
the non-canon gap analysis (`grounding/Gap-Analysis-and-Roadmap.md`) surfaced — the
others (Engagement / Community set, Service Agreement → firm [Q-002], Brand [Q-003],
Campaign, Cost-ledger / Prompt, Ticket, Ad-Account, Schedule, Consent) are upcoming, each
its own gated decision. **The Phase-7 content gate continues** (Logical + AI written; the
Data view can now reference Media & Assets; Integration / Security / Runtime are clean
"how").

**Phase 4 Feature Modules — firm (DEC-032). Phase 7 — SCOPED (DEC-031); the
Application/Logical prerequisite is cleared. Next: the Phase 7 content gate.** DEC-032
un-deferred Feature Modules (Option A first-class — a mountable unit of product
functionality that mounts on the base and may aggregate plugins, declared through the
Extension Contracts surface; composes Plugin Model + Extension Contracts, never re-defines
either), and the firm `extensibility.md` entry is written (commit `9c80bb3`); this
**satisfies the DEC-031 G-6(c) prerequisite** for the Phase 7 Application / Logical
Architecture view writes. Phase 7 System Architecture Blueprint is **scoped**
(DEC-031 / Snapshot-042): seven cross-cutting concern-views; AI Architecture the spine but
never AI-only; single-tenant (no multi-tenant isolation layer); **Q-013 resolved**
(architecture-home → Phase 7 AI Architecture, agent/subagent identity un-deferred into
Phase 7; surface rendering → Phase 2). The Phase 7 ↔ Phase 8 boundary is drawn (DEC-030 /
Snapshot-041; KNI-11 → Done): concern-views (P7) vs layered assembly (P8), one-way
dependency (P7 first). **The open path is the Phase 7 content gate — the full
`system-architecture-blueprint.md` write (KNI-27), all seven concern-views now unblocked,
in gated batches after Ali's go; no Phase-7 content before then.** Other fresh/gated
follow-ups: Q-017 resolved (DEC-048) — fixed-flow at T1, v2 visual editing deferred; the
**three** remaining Phase-4 deferred sub-items (Versioning & Compatibility, External
Integrations, Future Domains); Phase 5 Asset Intelligence un-defer.

**Phase 6 Workflow Design — complete at DEC-028's scope (DEC-029 / Snapshot-040).** `workflows.md`
is written (Batches A–C; `6eefd90` / `a7de5ef` / `a0fe15d`), under DEC-028, via
per-batch reviewer byte-reads (FIND-033), and consistency-reviewed **clean**
(Snapshot-038; zero meaning-level findings). DEC-029 declared Phase 6 complete at
DEC-028's scope (13/13 sub-items) and **fired Q-012's trigger** (now resolved by
DEC-030, above). Linear: **KNI-26 is Done** (Snapshot-037); **KNI-11 → Done**
(Q-012 resolved, DEC-030 verified on origin/main).

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
Candidate fresh threads: the three remaining Phase-4 deferred sub-items; Phase 5 Asset
Intelligence un-defer. (Phase 6 Workflow Design first write is complete — see the lead above.)

**Phase 4 Extensibility — first write complete; Feature Modules now firm (DEC-032).**
All eight in-scope `extensibility.md` entries are written (Snapshot-030, Batches A–C;
KNI-23 Done). **Feature Modules is un-deferred and written as a firm six-field entry**
(DEC-032 / Snapshot-043; commit `9c80bb3`) — Option A first-class (a mountable unit of
product functionality that may aggregate plugins, declared through Extension Contracts),
which satisfied the DEC-031 G-6(c) prerequisite for the Phase 7 Application / Logical
view writes. The **three** remaining deferred sub-items (Versioning & Compatibility,
External Integrations, Future Domains) remain flagged stubs; each becomes its own work
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
   inherited Phase 1 questions (domains.md:1944-1945, :1946, :1947-1948) stay
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
   - Q-016 resolved (DEC-047): Client sees Performance & Analytics View, scoped
     to own-engagement. No longer a carry-forward.
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
Open question Q-002 (Service Agreement ownership) is resolved
(see DEC-034): Service Agreement is a first-class Entity owned by CRM
(reference-addressable, not absorbed into Client Account; Aggregate-pending-Q-006);
Q-006 stays open.
Open question Q-018 (Client Asset domain ownership) is resolved
(see DEC-033): a new Phase-1 domain, Media & Assets, owns the Client Asset entity;
Asset Intelligence (P5) stays deferred.
Open question Q-019 (post-publish audience-engagement ownership) is resolved
(see DEC-035): a new Phase-1 domain, Community, owns comments/DMs/conversations/replies;
Sentiment Signal ownership left contested/draft.
Open question Q-003 (Brand placement) is resolved
(see DEC-036): Brand is a first-class Entity owned by CRM (reference-addressable, not
absorbed into Client Account; 1 Client : N Brand; aggregate placement draft/pending).
Open question Q-004 (Client Brain partitioning) is resolved (DEC-045, 2026-06-09):
per-Brand partitioning (primary unit) with a per-Client aggregation view for cross-brand
context. Ownership remains Knowledge (DEC-027).
Open question Q-020 (Phase-4 access-status / connection-health owner) is resolved
(DEC-046, 2026-06-09): access-status/connection-health is a Phase 4 Channel Model
operational attribute — the 4th channel-level property. Distinct from Governance
policy-enabled/disabled. Read by Dual-Path / Manual-Fallback routing (DEC-037).
Open question Q-021 (AI usage/cost ledger ownership) is resolved
(see DEC-038): a new Phase-1 domain, AI Operations, owns the per-job UsageRecord Entity;
per-client cost is derived (Intelligence).
Open question Q-022 (prompt/template versioning home) is resolved (DEC-044, 2026-06-09):
Knowledge domain owns PromptTemplate (reusable structured AI prompt artifact with version
history). Extend test passes against Knowledge Artifact / Knowledge Version shape.
Open question Q-023 (Ticket entity ownership) is resolved
(see DEC-039): Ticket is a first-class Entity in Client Success (extend test; 6th of ~10
reopenings; non-collapse from Escalation Case / Coordination Request; aggregate pending Q-024).
Open question Q-024 (Ticket ↔ Escalation Case lifecycle coupling) is registered and open
(see DEC-039): two-entity vs single-lifecycle; cross-references `domains.md:1720`; its own
gated Phase-1 decision.
Open question Q-015 (Publishing scheduling/queueing, P3 ↔ P6)
is resolved (see DEC-028 / Snapshot-036).
Open question Q-017 (system-administrator visual workflow viewing + management) is resolved
(DEC-048, 2026-06-09): workflows are fixed-flow at T1; visual editing deferred to v2 as
multi-phase gated feature (Phase 2 / 4 / 6 / 7 — own gate then).
Open question Q-016 (Client × Performance & Analytics View membership) is resolved
(DEC-047, 2026-06-09): Client sees the view, scoped to own-engagement data.
Open question Q-005 (CRM / Client Success domain boundary) is resolved
(DEC-043, 2026-06-09): CRM owns commercial account identity; Client Success owns active
post-conversion relationship lifecycle.
Open question Q-009 (Phase 9 coherence — Channel Model continuity) is resolved
(DEC-042, 2026-06-09): Snapshot-047 + DEC-046 together close the coherence concern.
Open question Q-012 (Phase 7 ↔ Phase 8) is resolved
(see DEC-030 / Snapshot-041; KNI-11 → Done): Phase 7 = the cross-cutting
concern-views, Phase 8 = the layered assembly, one-way dependency (P7 first).
The Phase 7 scope gate is closed (DEC-031); the open path is the Phase 7 content gate.
Open question Q-013 (AI / agent-surface home) is resolved
(see DEC-031 / Snapshot-042): architecture-home → Phase 7 AI Architecture
(agent/subagent identity un-deferred into Phase 7); surface rendering → Phase 2.
Phase 8 scope gate (G-1…G-8) is closed (DEC-040, 2026-06-09): 7 layers firm;
Core 7 blocks + AI 5 blocks + 2 deferred slots named at altitude; Core↔Infrastructure
+ Experience↔AI cuts governed; Phase-6-not-Core guard explicit. `architecture.md`
**first write COMPLETE (Snapshot-046; 2026-06-09; Batches A–C; KNI-39 Done).** All eight
architecture phases (1–8) now have first writes — milestone, not a phase-complete
declaration. Agent-supervision carried as deferred slot; Q-017 resolved (DEC-048).
Phase 9 Infrastructure Design: all-GCP stack approved (DEC-041, 2026-06-09) — Cloud SQL
(Persistent Store) · pg-boss (Job Queue / Event Bus) · Cloud Run (Worker / Job Runtime)
· Firebase Auth (Auth Backing Service) · GCP Secret Manager (Secret Store) · Cloud
Logging + Monitoring + Grafana Cloud (Observability) · Schema-per-client + RLS
(Per-Client Data Scoping Scheme). `infrastructure.md` **first write COMPLETE
(Snapshot-047; 2026-06-09; 706 lines; KNI-40 Done).**
**Reconciliation sweep COMPLETE (Snapshot-048; 2026-06-09):** DEC-042–DEC-048 minted;
Q-004/Q-005/Q-009/Q-016/Q-017/Q-020/Q-022 all resolved; G-01–G-05 content fixes landed.
**Phase 10 is now unblocked.** Remaining open: Q-003 (Brand aggregate placement), Q-006,
Q-007, Q-024, insight→durable threshold (`domains.md:1946`), and 4 Phase-1 entity
reopenings (Campaign, Ad-Account, Schedule, Consent) — each its own future gate.
