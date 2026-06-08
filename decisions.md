# Decisions

## Purpose
This file tracks the current important architectural
and operating decisions for Faraz OS.

It is not a full historical transcript.

It should contain active,
still-relevant decisions
that shape current interpretation,
modeling,
or execution.

Historical decision detail
may remain in snapshots.

---

## Usage Rules
- Keep decisions current.
- Prefer one canonical entry per important decision.
- If a decision is superseded, mark it clearly.
- If a decision is only historical, keep it in snapshots.
- Do not let this file become a duplicate of snapshot history.

---

## Current Active Decisions

### DEC-001
`Faraz-OS-Canon.md` is the canonical phase map for the project.

Meaning:
- The project is organized by explicit phases.
- Each phase has a corresponding primary file.
- Phase interpretation should align with the canon unless a newer snapshot explicitly revises something.

Status:
- Active

---

### DEC-002
Source-of-truth priority is hierarchical, not flat.

Current order:
1. latest relevant snapshot
2. `Faraz-OS-Canon.md`
3. current phase files in `Faraz-OS-Canon/`
4. current planning or definition files referenced by newer snapshots

Meaning:
- Not every markdown file has equal authority.
- Stale bootstrap files and historical notes must not override newer canon or snapshots.

Status:
- Active

---

### DEC-003
Phase 1 Domain Discovery uses `domains.md`
as its active source of truth.

Meaning:
- Snapshots may record progress and interpretation.
- `domains.md` remains the main working file for the domain model.

Status:
- Active

---

### DEC-004
Phase 1 Domain Discovery is now far enough along
that the next major step is normalization,
not broad expansion.

Meaning:
- Remaining work is primarily about cleanup,
  deduplication,
  wording alignment,
  and canonicalization.
- This does not mean all boundaries are finalized.

Status:
- Active

---

### DEC-005
Normalization of `domains.md`
must be treated as a controlled pass.

Meaning:
- It should not happen as scattered ad hoc cleanup.
- It should preserve architecture intent,
  canonical distinctions,
  and visible draft ambiguity.

Status:
- Active

---

### DEC-006
Normalization should later be performed
with Claude Code assistance
under explicit constraints
and human review.

Meaning:
- Manual broad rewriting is not the preferred operating model.
- The safer pattern is controlled AI-assisted editing with review.

Status:
- Active

---

### DEC-007
Core concept distinctions must remain explicit.

The repository must preserve distinction between:
- Domain
- Subdomain
- Bounded Context
- Entity
- Candidate Aggregate
- Capability
- Workflow
- Plugin
- Provider
- Memory Object
- Shared Service / Shared Service Artifact
- Business Artifact
- Domain Artifact

Meaning:
- These are not interchangeable labels.
- Cleanup must not collapse them.

Status:
- Active

---

### DEC-008
Unresolved architectural boundaries
must remain visible as draft
until separately resolved.

Examples include:
- final Client Brain ownership
- final Brand placement
- final Service Agreement ownership
- final Aggregate boundaries

Meaning:
- Normalization must not silently finalize unresolved areas.
- Open questions remain legitimate parts of the current model.

Status:
- Active

---

### DEC-009
Claude operating behavior should be formalized
through repository-level operating rules,
not personal notes.

Meaning:
- `CLAUDE.md` should replace ad hoc personal instruction files.
- AI collaboration rules should be reusable and project-scoped.

Status:
- Active

---

### DEC-010
Phase ownership and execution ownership must remain distinct.

Meaning:
- Phase 1 owns domain content and domain normalization targets.
- Phase 9 owns the Claude Code operating model,
  including session discipline,
  handoff format,
  and mode-based execution behavior.

Status:
- Active

---

### DEC-011
Normalization of `domains.md` must produce a proposed normalized draft
plus a review summary
before any canonical file replacement occurs.

Meaning:
- Claude Code should not update `domains.md` directly during normalization.
- The proposed normalized version should exist as a separate artifact
  pending human review.
- The review summary should cover:
  - what was consolidated and why
  - what was left unchanged and why
  - any cases where normalization revealed a possible missing boundary
    or inconsistency, flagged as Open Question or Risk
- Human review and explicit approval are required
  before the proposed draft replaces the canonical file.

Basis:
- Resolves Q-008.
- Consistent with `CLAUDE.md` broad-task pattern:
  plan → constrained implementation → review summary.
- Consistent with Snapshot-006 DEC-023 direction.
- Consistent with the `Normalization Pass v1 Plan` constraint rules.

Status:
- Active

---

### DEC-012
The normalization execution checklist
is appended to the existing
`Faraz-OS-Canon/Normalization Pass v1 Plan for domains.md`
rather than created as a parallel file.

Meaning:
- The checklist lives in one canonical location
  with the rest of the normalization plan.
- A parallel "normalization checklist" file is rejected
  in favor of a minimal-diff append.

Basis:
- Preferred minimal diff over parallel file creation.
- Keeps normalization planning and execution constraints
  in one canonical location.
- Recorded in Snapshot-009.

Status:
- Active

---

### DEC-013
Normalization of `domains.md` is complete.

Meaning:
- The normalized draft was accepted and applied.
- `domains.md` reflects the normalized result.
- Normalization must not be rerun.

Basis:
- Recorded in Snapshot-010.

Status:
- Active

---

### DEC-014
`domains.md` is the current active source of truth
for Phase 1 Domain Discovery.

Meaning:
- `domains.md` is canonical for Phase 1.
- `domains-before-normalize.md` is the archived
  pre-normalization version and must not be treated
  as current.

Basis:
- Recorded in Snapshot-010 (DOC-008, DOC-009).

Status:
- Active

---

### DEC-015
`Faraz-OS-Canon.md` is updated to the Phase 0–11 structure.

Meaning:
- The authoritative phase map spans Phase 0 through Phase 11.
- All future work must use the updated phase numbering.
- Prior phase numbering from earlier snapshots is superseded.

Basis:
- Recorded in Snapshot-010 (DOC-010).

Status:
- Active

---

### DEC-016
Session close-out is a standing rule.

Meaning:
- At the close of any session that produced a decision,
  finding, structural change, or meaningful progress,
  a snapshot must be created,
  `Current-State.md` must be updated,
  and Linear must be reconciled against the snapshot.
- GitHub is the source of truth.
- Linear is execution tracking only.
- GitHub wins on any conflict.

Basis:
- Codified in `CLAUDE.md`
  (Session Close-Out and Sync Discipline section).
- Recorded in Snapshot-011 (DOC-011).
- Implemented procedurally in
  `workflows/sync-protocol.md` (see DEC-018).

Status:
- Active

---

### DEC-017
The Claude Code Operating System is canonically Phase 11.

Meaning:
- Earlier "Phase 9" references in `CLAUDE.md`
  and `Current-State.md` are superseded.
- The Phase Boundary Rule distinguishes
  architecture content phases (Phase 0 through Phase 10)
  from the Phase 11 operating-method layer.
- Domain truth still belongs specifically to Phase 1.

Basis:
- Recorded in Snapshot-011 (DOC-012).
- Reflected in current `CLAUDE.md` Phase Boundary Rule.

Status:
- Active

---

### DEC-018
`workflows/sync-protocol.md` is the single canonical
procedure for Linear ↔ GitHub reconciliation.

Meaning:
- Repository writes precede Linear writes.
- The human review gate sits between the repo draft
  and any commit.
- Linear is reconciled only after repo changes are approved.
- Decisions (`DEC-0NN`) and Findings (`FIND-0NN`)
  stay repo-only.
- Only Open Questions, actionable Risks, and work tasks
  become Linear issues.
- Deferral is expressed as a `Canceled` Linear issue
  with a re-open-trigger note, not a separate status.
- The Linear label taxonomy is locked to the two parent
  groups `Type` and `Phase`;
  new labels require an explicit decision.

Basis:
- Implements DEC-016 (Session Close-Out and Sync Discipline)
  and DEC-011 (draft-plus-review).
- Recorded in Snapshot-012 (DOC-015).

Status:
- Active

---

### DEC-019
The Phase 2 Experience Architecture scope
is defined and human-confirmed,
and Open Question Q-011 is resolved.

Meaning:
- Phase 2 designs the human experience layer only,
  for all human personas.
  AI / agent-facing surfaces are out of scope
  (they belong to AI Architecture,
  Phase 7 likely; see Q-013).
- Governing boundary test:
  presentation / surface / navigation → Phase 2;
  reusable functional ability → Phase 3 Capability Map;
  ordered cross-step flow and approval gates → Phase 6 Workflow Design.
- Operator-facing surfaces are in Phase 2 scope.
  Phase 2 owns where / to whom / how humans interact.
  Phase 2 does not own human identity (Workforce / Phase 1),
  capabilities (Phase 3),
  or authorization rules (Governance / Phase 1).
- Permission concerns sit at three altitudes:
  Phase 1 Governance owns authoritative permission and
  authorization rules;
  Phase 4 Extensibility owns extension, plugin, and provider
  capability grants;
  the Phase 2 Permission Matrix is a read-only projection
  of Governance rules onto the experience layer
  (rows = personas;
  columns = surfaces / portals / views;
  not capabilities).
  Phase 2 authors no rules.
- Locked persona set:
  Client (external),
  Contractor (external),
  Workforce / Operator (internal),
  Manager (internal),
  System Administrator (internal),
  plus a Future Personas placeholder.
  Contractor and Workforce / Operator are distinct personas.
- Portal = visual panel per persona group.
  A Portal contains Operating Surfaces.
  There is one portal definition per persona group.
  Multi-role humans receive one composed portal
  via role-based composition.
- Operating Surface = functional workspace,
  reusable across portals.
- Navigation Model = movement between surfaces inside a persona's
  composed portal.
  Notification routing and deep-linking are deferred future sub-detail.
- Cross-Domain Views = persona-facing presentation and composition
  of multi-domain information.
  They consume; they do not own or compute.
  KPI computation = Phase 3;
  the dashboard surface that displays it = Phase 2.
- Channel Behaviors in Phase 2 are narrowly scoped to
  rendering, preview, and notification UX.
  Channel integration belongs to Phase 4.
  Workflow belongs to Phase 6.
- Phase 2 ↔ Phase 8:
  Phase 2 is the design source;
  Phase 8 Puzzle Board "Experience Layer" positions it.

This decision records scope only.
It does not finalize any Phase 1 domain boundary
and it does not write Phase 2 canon content by itself.

Basis:
- Resolves Q-011 (both parts A and B).
- Recorded in
  `snapshots/Snapshot-013 - Phase 2 Experience Architecture Scope Defined.md`.
- Reflected in `Faraz-OS-Canon/experience-architecture.md`
  at framework level (per Snapshot-014).

Status:
- Active

---

### DEC-020
The Operating Surfaces inventory for Phase 2
is defined and human-confirmed.

Meaning:
- **Discovery method.** Persona-driven, starting with
  Workforce/Operator. Reuse across other personas is then
  mapped; persona-distinct emerging surfaces become separate
  inventory entries, not specializations of a parent.
- **Granularity rule (canon-worthy).** Operating Surfaces
  are sized at one surface per coherent work-mode,
  not one per task type.
- **Naming convention (canon-worthy).** Persona-facing
  surfaces are persona-prefixed; subject-facing surfaces
  use distinct subject words rather than persona names.
- **Persona reuse vocabulary (canon-worthy).** Four modes —
  **Full** (same surface, same content),
  **Scoped** (same surface, restricted content),
  **Distinct surface** (a different surface serves the same
  intent for that persona and is added to the inventory),
  **—** (no access).
- **Scoped marker placement.** Phase 2 records "Scoped" as
  a marker on the surface↔persona relationship. The rules
  that define what is scoped come from Phase 1 Governance
  and are projected via the Permission Matrix.
  Matrix population remains deferred until Governance rules
  are concrete.
- **Renames.**
  *Client Context Surface* → *Client Brain Surface*
  (anchors on the Phase 5 Knowledge & Memory concept;
  eliminates the "Client" subject-vs-persona ambiguity;
  scope deliberately narrowed to current-client strategic
  memory).
  *Workflow Control Panel* → *Agent & Workflow Monitor*
  (sharper separation from Phase 6 Workflow Design).
- **Firm inventory (16 surfaces).**
  Operator-anchored (8): Operator Inbox, Production Workspace,
  Review Queue, Client Brain Surface, Knowledge Workspace,
  Agent & Workflow Monitor, Reports & Analytics Surface
  (classification flag: possibly Cross-Domain View),
  Lead Workspace.
  Client persona (4): Client Notifications,
  Client Approval Queue, Client Deliverable Library,
  Client Billing / Invoices Surface.
  Contractor persona (1): Contractor Assignments.
  System Administrator (3): Admin Knowledge,
  Workflow & Agent Configuration, Credentials & Integrations.
- **Flagged (5, deferred).**
  *Client Profile* (tentative);
  *Team Performance / Oversight Surface* (possibly
  Cross-Domain View);
  *System Configuration / Settings*
  (depends on Phase 4 / Phase 9 maturity);
  *Operator-finance gap*;
  *Onboarding / first-time-use surfaces*.

This decision records scope only.
It does not modify `Faraz-OS-Canon/experience-architecture.md`,
does not finalize any Phase 1 domain boundary,
does not populate the Permission Matrix,
and does not enumerate Portals or Cross-Domain Views.

Basis:
- Captured in `brainstorms/2026-06-06-phase-2-operating-surfaces.md`.
- Recorded in Snapshot-016.
- Builds on DEC-019 / Snapshot-013 (Phase 2 scope) and
  Snapshot-014 (framework canon write).

Status:
- Active

---

### DEC-021
Portal contents per persona for Phase 2 are defined
and human-confirmed.

Meaning:
- For each of the five locked personas (Client, Contractor,
  Workforce / Operator, Manager, System Administrator), the
  Portals section of `experience-architecture.md` enumerates
  which Operating Surfaces the persona's portal contains
  and the reuse mode for each
  (Full / Scoped / Distinct surface / —).
- This is a projection of the DEC-020 Operating Surfaces
  inventory at membership + reuse-mode altitude.
  Reuse modes are taken verbatim from the inventory,
  including the disjunctive "Full or Scoped" for the Manager
  view of Agent & Workflow Monitor.
- Built from the 16 firm surfaces only. All 16 appear in at
  least one portal. The 5 flagged surfaces remain flagged and
  are noted as pending per portal where relevant; none added.
- Faithful-projection rule: where the inventory assigns no mode
  to a persona, the portal omits that surface (for example,
  Manager has no Production Workspace; Contractor has no Lead
  Workspace). These are projections, not new exclusion decisions.
- The projection is not the Permission Matrix. Authoritative
  per-surface entitlement, and the resolution of reuse mode when
  a surface is reached via more than one role, come from Phase 1
  Governance and are projected via the Permission Matrix
  (population deferred until Governance rules are concrete).
- Altitude bound: portal contents stop at membership + reuse
  mode. Surface ordering, landing/primary surface, and grouping
  are not introduced (they belong to the Navigation Model / UI).

Basis:
- Builds on DEC-019 (persona-to-portal rule) and DEC-020
  (Operating Surfaces inventory).
- Produced as plan-then-write (the approved plan was the scoping
  artifact; no separate grill-me brainstorm).
- Recorded in
  `snapshots/Snapshot-018 - Phase 2 Portal Contents Written.md`.

Status:
- Active

---

### DEC-022
Cross-Domain Views scope for Phase 2 is defined
and human-confirmed.

Meaning:
- Discovery method: persona-anchored, domain-keyed.
- A Cross-Domain View is a named multi-domain composition
  rendered on an Operating Surface. A surface may host more
  than one view. Views are not portal entries; the host
  surface is.
- Granularity rule (canon-worthy): one view per coherent
  persona decision-context composed from a stable domain-set.
- Naming convention (canon-worthy): decision/subject + "View";
  a persona word only when the composition is persona-specific.
- Inventory — 7 firm views:
  1. Client Brain View (host: Client Brain Surface)
  2. Lead Context View (host: Lead Workspace)
  3. Performance & Analytics View (host: Reports & Analytics Surface)
  4. Team Oversight View (host: Reports & Analytics Surface, manager scope)
  5. Engagement Health View (host deferred — DEC-020 follow-up)
  6. Client Engagement Summary View (host deferred — DEC-020 follow-up)
  7. Contractor Assignment-in-Context View (host: Contractor Assignments)
  System Administrator: no Cross-Domain View.
- Reports & Analytics Surface hosts two distinct, separately
  named views (#3 and #4), so the "both" classification does
  not collapse the two compositions.
- Flag resolutions:
  Reports & Analytics Surface → both (firm Operating Surface
  from DEC-020 unchanged; hosts views #3 and #4);
  Team Performance / Oversight Surface → pure Cross-Domain View
  (the Team Oversight View), hosted on the Manager's Reports &
  Analytics Surface; removed from the flagged-surface list.
- Boundary: views consume multi-domain info; they do not own
  (Phase 1) or compute (Phase 3). KPI: compute = P3, present = P2,
  own = P1. The Intelligence(P1)-vs-Phase-3 computation question
  is upstream and not resolved here.
- Entitlement (who is exposed to which view) is deferred to the
  Permission Matrix / Phase 1 Governance. This decision defines
  WHICH views exist, not WHO sees them.

Carried flags:
- Operator-finance gap (DEC-020) remains flagged — the
  Engagement Health View names the composition that will address
  it, but its host and the gap's resolution are deferred.
- Host surfaces for Engagement Health View and Client Engagement
  Summary View — DEC-020 follow-up.

Basis:
- Captured in brainstorms/2026-06-06-phase-2-cross-domain-views.md.
- Recorded in Snapshot-019.
- Builds on DEC-019 (Phase 2 scope), DEC-020 (Operating Surfaces),
  and DEC-021 (Portal contents).

Status:
- Active

---

### DEC-023
The two deferred Cross-Domain View host surfaces and the
operator-finance gap (the DEC-020 follow-up) are resolved
and human-confirmed.

Meaning:
- Engagement Health View → hosted on the Reports & Analytics
  Surface (operator / manager scope), by scoped reuse.
- Client Engagement Summary View → hosted on the Reports &
  Analytics Surface (client-scoped), by scoped reuse.
- No new Operating Surface was added. The firm inventory stays
  at sixteen surfaces; this is not a DEC-020 inventory amendment.
  A new firm surface was considered for each host and not chosen.
- Consequence: the Reports & Analytics Surface now hosts four
  distinct, separately named Cross-Domain Views — the
  Performance & Analytics View, the Team Oversight View, the
  Engagement Health View, and the Client Engagement Summary View.
- Operator-finance gap (DEC-020) → resolved for the
  per-engagement financial-context need. The operator reaches
  engagement revenue (Finance), contractor payment and effort
  (Workforce), delivery (Service Delivery), and health
  (Client Success) through the Engagement Health View on the
  Reports & Analytics Surface, a surface the operator already
  holds. The gap is removed from the flagged-surface list.
- A later cross-engagement financial-rollup need, if one
  surfaces, is a new item — not a reopening of this gap.

Out of scope / unchanged:
- The DEC-022 seven-view inventory, the granularity and naming
  rules, and the two already-resolved flags (Reports & Analytics
  Surface → both; Team Performance / Oversight Surface → pure
  Cross-Domain View) are untouched.
- The other flagged surfaces (Client Profile, System
  Configuration / Settings, Onboarding) stay flagged.
- Entitlement (who is exposed to which view) stays deferred to
  the Permission Matrix / Phase 1 Governance. This decides where
  the views live, not who sees them.
- No Phase 1 domain truth reinterpreted.

Basis:
- Resolved as plan-then-write with a question gate (no separate
  brainstorm; three bounded decisions).
- Recorded in Snapshot-021.
- Builds on DEC-020 (Operating Surfaces) and DEC-022
  (Cross-Domain Views).

Status:
- Active

---

### DEC-024
The Phase 3 Capability Map scope is defined and human-confirmed (scoping only):

- **Capability definition:** a reusable, UI-independent functional ability —
  a unit of "what the system can *do*" — invokable by multiple workflows,
  serving multiple domains, runnable across channels; owns no domain truth,
  prescribes no ordered sequence, tied to no surface. Faithful to
  `domains.md:177-180`. Execution mode (AI / human / hybrid) is a
  per-capability **attribute**, not part of the definition (Core Principle #1
  "AI-first, but not AI-only", `principles.md:3`) — never narrowed to AI-only.
- **Closed six-boundary set** (the entry-writing checklist):
  1. Capability definition.
  2. ↔ Phase 2 presentation: KPI computation = Phase 3, display = Phase 2;
     `capabilities.md` references `experience-architecture.md:564-571`, does
     not restate it.
  3. ↔ Phase 6 sequence: order-free, gate-free, workflow-agnostic.
  4. ↔ Phase 1 domain truth: serve, never own; inherits the unresolved
     P1 ↔ P3 source-of-truth-vs-computation line, does not resolve it.
  5. ↔ Phase 4 provider/plugin: per Extensibility Philosophy #5
     (`extensibility-philosophy.md:17`) and `domains.md:212-235`.
  6. ↔ Phase 5 memory/knowledge: names that an output *may become* durable
     knowledge; never defines storage / retention / memory structure.
- **Five reusable operational rules:** verb-test (if removing all UI leaves
  the ability intact, it is Phase 3); sequence-test (if defining it needs a
  predecessor/successor/gate, it is Phase 6); workflow-agnostic (a capability
  does not know its predecessor/successor; `capabilities.md` does not record
  ordering — a writing constraint, not a claim that no real-world sequence
  exists); naming-altitude (per-capability fields name the owning domain /
  store-of-record / durable-knowledge possibility only; never author the rule,
  describe data-paths (Phase 7), or define memory structure (Phase 5));
  granularity (one capability per distinct reusable ability).
- **Granularity rule:** one capability per distinct reusable ability (verb),
  not per output variant or per domain served (justifies Video Creation ≠
  Content Creation and Analytics ≠ Reporting). **Naming convention (light):**
  a capability is named for the ability, not the output, tool, or domain.
- **Sub-item set:** all **eight** are firm (Research, Strategy, Content
  Creation, Video Creation, Publishing, Analytics, Reporting, Lead Scoring);
  the phase map is authoritative over the illustrative `domains.md:184-191`
  examples list. **Video Creation** is resolved as a genuine capability
  ("produce a video asset"); its tool integration is Phase 4. No MVP subset —
  build-order is Phase 10 Build Roadmap.
- **Per-capability skeleton (six fields):** Definition; Domains served (name
  only); Execution mode (which mode it *can run in*, not the
  human-intervention/checkpoint policy, which is Phase 1 Governance);
  Produces; Provider dependency (deferred to Phase 4); Boundary notes /
  inherited flags. **No "Consumed by workflows" field** (it would import
  Phase 6 ordering — a capability that names its consuming workflows knows its
  successors).
- **Non-goals — `capabilities.md` will NOT contain:** UI / surfaces / views
  (Phase 2); ordered sequences or approval gates (Phase 6); domain-entity
  definitions, ownership, or authoritative meaning (Phase 1); provider/tool
  implementations or channel integration (Phase 4); data-paths / read-write
  mechanics / wiring (Phase 7); storage / retention / memory structure
  (Phase 5); permission / authorization / human-intervention-checkpoint rules
  (Phase 1 Governance); build order / MVP sequencing (Phase 10); and the
  resolution of ANY inherited Phase 1 open question.

This decision records scope only. It finalizes no Phase 1 boundary and writes
no Phase 2 or Phase 3 canon content.

Basis:
- Scoping session (grill-me); capture in
  `brainstorms/2026-06-07-phase-3-capability-map.md`.
- Backfilled from Snapshot-024; not created here.

Status:
- Active

---

### DEC-025
The Phase 4 Extensibility Model scope is defined and human-confirmed (scoping
only; resolves no boundary, writes no `extensibility.md` content). Settled in an
inline grill-me question-gate (OQ-E through OQ-M); every citation re-verified
against raw bytes before this record.

- **Phase 4 definition / altitude:** Phase 4 owns the *extensibility model* — the
  intentional extension points, their contracts, and the capability grants by
  which extensions, providers, channels, models, and (later) domains attach to a
  stable core. Phase 4 defines **what is swappable and how it attaches at
  altitude**; it authors no domain truth, no experience layer, no ordered
  workflow, no authoritative governance rule, and no implementation technology.
  Faithful to Extensibility Philosophy #1–#8 (`extensibility-philosophy.md:3-30`).

- **Sub-item set (canon lists twelve — `Faraz-OS-Canon.md:93-104`):**
  - **In-scope for the first write — eight:** Permission; Extension Contracts;
    Plugin Model; Provider Model; Channel Model; Model; AI Model Routing;
    Runtime vs Config-Time Extensions.
  - **Deferred-and-flagged — four:** Versioning & Compatibility; External
    Integrations; Feature Modules; Future Domains. Rationale: each is an
    evolution / registry / forward-looking concern that presupposes the core
    contract model this write establishes (Versioning ← Philosophy #11
    `:40-41`; External Integrations ← Philosophy #9 `:32-34` + `non-goals.md:11`;
    Feature Modules / Future Domains ← Philosophy #12 `:43-45`). Deferred items
    are recorded as flagged, not dropped. **Future Domains is a carried,
    marked-future placeholder and is not silently resolvable.**

- **Locked distinction set (so sub-items do not collapse):**
  1. **Model triad — kept as three distinct sub-items** (faithful to
     `Faraz-OS-Canon.md:96,98,99`): *Provider Model* = the contract for any
     swappable external provider (AI / media / channel / third-party);
     *Model* = the AI-model abstraction specifically (unit / tier);
     *AI Model Routing* = the policy that selects among models / providers /
     paths. Model and AI Model Routing stay **separate** (not clustered) —
     backed by both philosophies treating multi-model (`ai-philosophy.md:18-19`)
     and routing (`ai-philosophy.md:21-22`; `extensibility-philosophy.md:25-27`)
     as distinct principles.
  2. **Plugin vs Provider vs Channel:** *Plugin Model* is the orthogonal
     packaging / attachment axis — per Philosophy #5
     (`extensibility-philosophy.md:17-20`), a plugin *attaches* channels,
     providers, or integrations. *Channel Model* stays **first-class but is
     typed as a Provider-Model specialization** that reuses the provider
     contract and adds channel-specific elements; it does not duplicate
     provider contract machinery. *This typing is a DEC-025 scoping inference,
     not a literal pre-existing canon statement:* canon lists Channel Model and
     Provider Model as parallel sub-items (`Faraz-OS-Canon.md:96-97`) and #5/#6
     enumerate channels and providers in parallel; the specialization is
     reasoned from those principles plus Publishing's provider-dependency field
     naming "Channel / platform integrations" (`capabilities.md:82-83`), and is
     recorded as a decided distinction for this phase — not asserted as canon
     truth.

- **Closed boundary set — the definition/altitude plus six cross-phase
  boundaries** (mirrors the DEC-024 closed-set discipline, `decisions.md:689-700`):
  1. **↔ Phase 1 Governance:** respect authentication / authorization / policy;
     never author rules (Philosophy #8 `:29-30`; references DEC-019 / FIND-022).
     Phase 1 is a single Governance boundary here; human identity is a non-goal.
  2. **↔ Phase 2:** Phase 4 owns grants / contracts; authors no surfaces, views,
     portals, or the Permission Matrix (the experience projection is Phase 2 —
     `experience-architecture.md:514-515`).
  3. **↔ Phase 3:** Phase 4 owns provider / tool binding; the capability names
     the ability and Phase 4 names the tool (the inverse of DEC-024 boundary 5,
     `decisions.md:697-698`).
  4. **↔ Phase 5:** Phase 4 references memory / knowledge as a *consumer* of
     contracts; defines no storage / retention / memory structure.
  5. **↔ Phase 6:** Phase 4 owns routing / selection extensibility (order-free,
     policy-driven); orchestration / sequence / agent-chains / approval-gates /
     workflow-runtime are Phase 6 (`Faraz-OS-Canon.md` Phase 6 list). Governed
     by the **selection-vs-sequence test** below.
  6. **↔ Phase 7:** Phase 4 owns the extension *contract surface*; system
     wiring / data-paths / AI Architecture (the implementation blueprint) are
     Phase 7.

- **Reusable operational rules:**
  - **Selection-vs-sequence test (the sharpest altitude line, P4 ↔ P6):**
    *If it defines how the system selects among interchangeable providers /
    models / agents / execution paths by policy (cost, quality, latency,
    availability, risk, task-type) — the swappable, order-free selection
    mechanism — it is Phase 4. If it requires naming a predecessor, successor,
    gate, or step-sequence — what runs, in what order, with which hand-offs —
    it is Phase 6.* Litmus: remove all ordering — does it still hold? → Phase 4
    routing. Does it need a predecessor / successor / gate? → Phase 6
    orchestration. (Parallels the Phase 3 sequence-test, `decisions.md:701-704`.)
  - **Grant-altitude rule (R-028):** Phase 4 grants and contracts **reference**
    the Phase 1 Governance source-of-truth (and any open Governance question —
    e.g. Q-014) **at altitude**; they **may name** the governance touchpoint
    *categories* an extension must respect — *authentication, authorization,
    validation, auditability, safety controls, and policy enforcement*, sourced
    verbatim from Philosophy #8 (`extensibility-philosophy.md:30`) — but
    **never enumerate concrete policies, rules, or values** (those are
    Governance's to author, DEC-019 / FIND-022). Where Governance is
    unresolved, `extensibility.md` cites the open question rather than assuming a
    resolution (FIND-027 / R-028 precedent). *Provenance note:* of the six #8
    terms, three are also verbatim in the authoritative Governance source
    `domains.md` — policy enforcement (`:2182`), authorization (`:2183`; also
    Authorization Rule / Authorization Aggregate at `:2252` / `:2284`),
    auditability (`:2195`); three (authentication, validation, safety controls)
    are #8-only — see the registered vocabulary flag.
  - **Contract-altitude rule:** the Contract-surface field names how core and
    extension interact (APIs / events / permissions / schemas / versioned
    interfaces, Philosophy #4 `:13-15`) **at altitude** — it does not specify
    them.
  - **Runtime-vs-Config-Time attribute rule:** Runtime vs Config-Time is a
    cross-cutting per-sub-item **attribute** (Philosophy #10 `:36-38`), framed
    by its own canon sub-item section; naming the mode is the attribute, not the
    deployment / governance policy that decides it.

- **Per-sub-item skeleton (six fields):** Definition (intentional extension
  point, Philosophy #2 `:6-8`); Contract surface (Philosophy #4; named at
  altitude, includes versioned interfaces); Provider-agnostic note (what is
  swappable, Philosophy #6 `:22-23`); Governance touchpoints (the #8 categories,
  referenced per the grant-altitude rule, never authored); Runtime vs
  Config-Time (the attribute per Philosophy #10); Boundary notes / inherited
  flags (cross-phase deferrals + any inherited Phase 1 question, preserved
  unresolved). Versioning is **not** a separate field — "versioned interfaces"
  lives in the Contract-surface field; deep versioning belongs to the deferred
  Versioning & Compatibility sub-item.

- **Channel Model depth — unblock-altitude, with a recorded acceptance test.**
  The Channel Model is written only to the altitude that unblocks Phase 2
  Channel Behaviors / KNI-18, with deeper channel mechanics (credential / auth
  contracts, API binding, delivery / dispatch semantics, rate limits) deferred
  (largely to External Integrations). Required minimum content: (1) a minimal,
  evidence-grounded channel taxonomy of *typed categories* derived only from
  what domains / capabilities already reference (e.g. Publishing's
  channel / platform integrations) — platforms illustrative only, never
  core-hardcoded (`non-goals.md:9`); (2) the three experience attributes that
  map 1:1 to Phase 2's three dimensions (`experience-architecture.md:696-698`);
  (3) the Provider-Model-specialization statement; (4) an explicit deferral
  boundary. **Acceptance test (verbatim):** *"The Channel Model is deep enough
  iff Phase 2 can later write rendering / preview / notification behaviors for
  each channel type using only the taxonomy and the three experience attributes
  (format/media constraints · preview affordance · notification capability),
  with no further Phase 4 content required."*

- **Permission triad handling (hybrid):** `extensibility.md` states only the
  altitude Phase 4 owns (Permission = extension / plugin / provider capability
  grants via contracts; authors no authoritative rules) and **references**
  DEC-019 (`decisions.md:394-404`) / FIND-022 (`findings.md:331-335`) for the
  full three-altitude triad — it does not restate the triad (CLAUDE.md
  one-canonical-definition; precedent `capabilities.md:33-43`).

- **Philosophy → canon relationship:** `extensibility-philosophy.md` remains the
  standing Phase 0 canon principles doc (`Faraz-OS-Canon.md:8`);
  `extensibility.md` **references** it (cites principle numbers / lines) and does
  not fold or retire it (precedent: DEC-024 cites `extensibility-philosophy.md:17`).
  **Refinement reconciled to the phase map:** orchestration is owned by Phase 6
  (`Faraz-OS-Canon.md` Phase 6 list); `extensibility-philosophy.md:25` ("routing
  and orchestration are part of extensibility") is read, within the phase map, as
  the extensibility of routing / selection only — not ownership of workflow
  orchestration. Precedence = phase map; the principle stands as aspirational
  intent. Phase 4 edits no Phase 0 doc; the optional philosophy-doc annotation is
  a registered flag for a later normalization pass.

- **Non-goals — `extensibility.md` will NOT contain:** UI / surfaces / views /
  portals / the Permission Matrix (Phase 2); ordered sequences, approval gates,
  agent-chain orchestration, or workflow runtime (Phase 6); domain-entity
  definitions, ownership, or authoritative meaning (Phase 1); authoritative
  permission / authorization / policy rules (Phase 1 Governance); **human
  identity (Phase 1 Workforce)**; storage / retention / memory structure
  (Phase 5); data-paths / read-write mechanics / system wiring / AI Architecture
  implementation (Phase 7); capability *definitions* (Phase 3);
  **implementation technology — language, runtime, packaging, deployment —
  deferred to the build / handoff phase (flagged phase-map-general)**; build
  order / MVP sequencing (Phase 10); the deep content of the four deferred
  sub-items; and the resolution of ANY inherited Phase 1 open question
  (wording adapted from `decisions.md:734`, not verbatim).

- **Registered inbound flags (Phase 4 must satisfy; resolving them must NOT
  resolve any inherited Phase 1 question):**
  - **KNI-18** — Phase 2 Channel Behaviors per-channel population waits on the
    Phase 4 Channel Model (`Snapshot-026:36`; `Snapshot-022:127-128`); satisfied
    by the Channel Model above against its verbatim acceptance test.
  - **Capability provider-dependencies** — all eight `capabilities.md` entries
    defer their tool / provider to Phase 4 (entry Provider-dependency fields at
    `:83, :106, :128, :150, :166, :179, :199, :229`).
  - **Video Creation tooling** — deferred to Phase 4 (`decisions.md:717-718`).

- **Registered open flags (carried, not resolved here):**
  - **Agent / subagent identity** — Philosophy #7 / `ai-philosophy.md:24-25`
    place agents in routing's scope, but Workforce owns *human* identity
    (`experience-architecture.md:809`); agent identity is likely Phase 7 AI
    Architecture (`experience-architecture.md:821`). Open cross-phase question.
  - **Safety-controls vocabulary** — "safety controls" (#8,
    `extensibility-philosophy.md:30`) vs Governance's "safety constraints /
    safety rules / Safety Constraint" (`domains.md:2189, :2226, :2262`).
    Cross-doc alignment deferred to a later normalization pass.
  - **Philosophy #7 annotation** — optional pointer on
    `extensibility-philosophy.md:25` noting the DEC-025 orchestration refinement;
    a Phase 0 normalization edit, not done by Phase 4.
  - **Inherited Phase 1 questions**, referenced not resolved — under
    `domains.md` `### Open Questions` (`:1914`):
    `domains.md:1915-1916` (Intelligence vs Analytics/Reporting),
    `domains.md:1917` (when an insight becomes durable knowledge),
    `domains.md:1918-1919` (lead-scoring home), and Q-014 (Permission Matrix ↔
    Governance). *Note:* prior canon files cite these with off-by-one ranges
    (`capabilities.md:116/211` use `:1914-1915`; `:220/238` use `:1917-1918`);
    the byte-accurate ranges are used here and the repo-wide citation drift is
    registered as a minor normalization flag below.
  - **Citation-drift (repo-wide)** — the inherited-question line refs in
    `capabilities.md`, `Snapshot-025/026`, and `Current-State.md` are off by one
    against `domains.md` raw bytes; align in a later normalization pass, not by
    Phase 4.

This decision records scope only. It finalizes no Phase 1 boundary, resolves no
open question, and writes no `extensibility.md` content. The eventual write is to
be planned in batches (à la the Phase 3 A/B split) given eight in-scope
sub-items; batch sequencing is decided separately at write time.

Basis:
- Inline grill-me question-gate (OQ-E → OQ-M); capture to be created at
  `brainstorms/2026-06-07-phase-4-extensibility.md` on approval.
- Citations re-verified against raw bytes prior to this record; the earlier
  audit corrections are carried (three-altitude span is `decisions.md:394-404`
  under DEC-019; the capability provider-dependency list drops `:64` and `:78`
  as non-entry references; the inherited-Phase-1 non-goal quote is adapted, not
  verbatim).

Status:
- Active

---

### DEC-026
The Phase 1 Governance **authorization slice** is defined and made concrete to
unblock the Phase 2 Permission Matrix, resolving the Phase-1 half of Q-014. This
is Phase 1 owning-phase content (authorization rules are domain truth), settled in
an inline grill-me gate (G-1 through G-7); every citation re-verified against raw
bytes. It promotes only the authorization slice of `Governance Draft v1`; the rest
of that domain stays draft, untouched, markers preserved.

- **Slice boundary (G-1).** *In-slice:* concrete `subject × action × resource ×
  condition` authorization rules (per the Authorization Aggregate shape,
  `domains.md:2284-2294`) sufficient to determine each locked persona's exposure
  {Full / Scoped / —} to the sixteen firm Operating Surfaces and the portals/views
  projected from them, including the Scoped conditions; entities touched are
  `Authorization Rule` / `Permission Rule` / `Action Eligibility Rule` only as
  needed for access exposure (`domains.md:2251-2254`). *Out-of-slice (stays
  Governance Draft v1, untouched, markers preserved):* the other rule families in
  `domains.md:2216-2231` (policies, risk classification, checkpoints, approval/
  escalation/override, exceptions, safety rules, audit/traceability, policy-level
  routing, extension compliance) and the Authorization-Aggregate fields not needed
  for exposure (`validity window`, `linked policy refs`, `:2293-2294`), which an
  in-slice rule may **reference at altitude** but not concretize.
- **Slice-bleed risk — R-029 (new).** An in-slice authorization rule may reference
  a draft neighbor (a condition, a policy ref, a risk tier) at altitude but must
  not concretize it. If a needed exposure rule cannot be stated without finalizing
  a draft neighbor, that is slice-bleed → **escalate, never silently absorb** (the
  G-1 escalation rule).

- **Rule shape (G-2).**
  - *Altitude (G-2 Axis 1 = c):* authorization rules are authored at **data/action
    altitude by reference** — `resource` = the domain resource the surface presents
    (CRM, Service Delivery, Finance, Knowledge, Intelligence/Analytics, Client
    Brain, Governance-config, Extensibility-config), **named at reference altitude**
    (Governance references but does not own these, `domains.md:2233-2241`).
    **Phase 2 owns the surface↔resource mapping**; the Permission Matrix **derives**
    persona×surface exposure from the rules + that mapping. Phase-1 truth never
    names Phase-2 surfaces as the resource.
  - *Verb set (G-2 Axis 2 = b), closed and evidence-derived:* **view · edit ·
    approve · configure** — each traced to DEC-020 surface names/notes (view = all
    read surfaces; edit = Production Workspace / Knowledge Workspace authoring;
    approve = Review Queue / Client Approval Queue; configure = Workflow & Agent
    Configuration / Credentials & Integrations). New verbs enter only on new
    evidence + explicit decision (same growth discipline as the channel taxonomy
    and the condition set).
  - *Approve-verb vs approval-gate boundary (parallel to the selection-vs-sequence
    test):* **who *may* approve = Phase 1** (the `approve` authorization verb);
    **when approval occurs in an ordered flow = Phase 6** (approval gates). Phase 1
    authorizes the actor; Phase 6 sequences the gate.

- **Ratified derived-projection baseline + Step-B acceptance criterion (G-3).** The
  human-confirmed DEC-020 sixteen-surface reuse table (`experience-architecture.md:232-263`),
  the per-portal membership/reuse tables (`:303-406`), and the view-host
  relationships are **ratified as the expected *derived projection*** of the
  matrix — **not** as authoritative rules. **Acceptance criterion for the Step-B
  matrix population:** the matrix derived from the landed authorization rules + the
  surface↔resource mapping must reproduce this ratified table; divergence signals
  the rules or mapping are wrong (a verification check, parallel to the DEC-025
  Channel-Model acceptance test). No decided DEC-020 cell value is amended; the
  three previously ambiguous or under-specified cells are resolved here (see G-4).
  **Acceptance-criterion precision:** for a primary persona on its own surface, a
  rule-level subject-binding condition derives as the ratified table's "Full
  (primary persona)" — the table's Full describes surface exposure; cross-subject
  data scope lives in the rules; this is not divergence.

- **Condition set (G-4), closed and evidence-derived (3):**
  - **own-engagement** — defined at altitude as *"scoped to the engagement(s) the
    subject is a party to."* This single condition serves **both** previously
    under-specified Reports & Analytics Scoped cells (Contractor and Client,
    `experience-architecture.md:240`); **resolving those two cells is decided here,
    not pre-existing.**
  - **assigned-client** — Contractor Scoped to the assigned client (Client Brain
    Surface, `:237`).
  - **engagement-relevant** — Contractor Scoped to engagement-relevant content
    (Knowledge Workspace, `:238`).
  Each condition **references a domain scoping concept at altitude** (Engagement
  Scope `domains.md:2237`; client assignment) and is never redefined here. Growth
  rule: new conditions only on new evidence + explicit decision.
  - **Subject-binding on external personas (decided here):** the inherently
    subject-bound external-persona resources — a Client's own deliverables,
    approval items, notifications, and billing; a Contractor's own assignment
    records — carry `own-engagement` at the rule level, so the authoritative layer
    never authorizes cross-client or cross-contractor access. Unconditioned (Full)
    rules are reserved for internal personas by design. (Per the G-3
    acceptance-criterion precision, these still read as "Full (primary persona)"
    in the matrix cell — exposure, not data scope.)
  - **Manager · Agent & Workflow Monitor = Full at the `view` verb** (resolves the
    one ambiguous "Full or Scoped" cell, `:239`/`:338`). The System-Administrator
    distinction is carried by **verbs** (Manager `view`-Full vs SysAdmin
    `configure`), not by scope; least-privilege is preserved through the verb set.
    **`managed-scope` future-evidence door:** a `managed-scope` condition MAY enter
    the closed set per the growth rule **if/when Phase 1 Workforce concretely
    models the management relationship** — referenced as a future-evidence note,
    not created now. The condition set stays at **three**.

- **Multi-role overlap meta-rule (G-5).** When one human carries multiple roles,
  effective authorization is the **union of allows**, with **an explicit `denied`
  outcome beating any allow** — one rule at altitude, using the existing
  `allowed or denied outcome` field (`domains.md:2292`); **no new construct.** Each
  allow carries its own condition; **the union never widens an individual grant's
  condition.** This honors the human-confirmed portal-composition canon
  (`experience-architecture.md:293-295` "union of… entitlements"; intersection /
  most-restrictive was rejected as it would re-open that canon). **Zero deny rules
  are authored now** — denies are evidence-derived and explicit when needed, and
  deny edge-case semantics (e.g. condition-scoped denies) are defined when the
  first real deny rule is authored, not speculatively. Posture: **permissive by
  default per the union canon; strictness is applied surgically via explicit
  denies, not globally.**

- **Matrix cell shape (G-6).** Cells summarize to **{Full / Scoped / —}**
  (`experience-architecture.md:205-210`); "Distinct surface" is a separate
  column/row, never a cell value; **verb + condition detail lives in the rules,
  not the cell.** A cell is an *exposure summary, not the full entitlement* (e.g.
  Manager `view`-Full and SysAdmin `configure`-Full both read "Full"); the
  authoritative entitlement is the rule. **Acceptance-criterion precision:** for a
  primary persona on its own surface, a rule-level subject-binding condition
  derives as the ratified table's "Full (primary persona)" — the table's Full
  describes surface exposure; cross-subject data scope lives in the rules; this is
  not divergence.

- **Two-step promotion (G-7), phase-separated, never mixed.**
  - *Landing (i) — Phase 1:* one isolated commit = this DEC (`decisions.md`) **+**
    the explicitly-called-out `domains.md` Governance authorization-slice edit;
    then close-out (Snapshot-032 + Current-State; FIND/R backfilled same-commit).
    Resolves Q-014's Phase-1 half; **KNI-16** (the unblock dependency) closeable
    here.
  - *Landing (ii) — Phase 2:* a separate gated content read → the
    `experience-architecture.md` Permission Matrix population (projects the landed
    rules via the surface↔resource mapping; **authors no rules**, DEC-019 /
    FIND-022) → verifier against the G-3 acceptance criterion → close-out
    (Snapshot-033 + Current-State **Phase 2 → 7-of-7**) → Linear close **KNI-14**
    (+ KNI-16 if still open). Never combined with landing (i).

- **`domains.md` edit plan (landing (i); executed in the same commit as this DEC).**
  Promote the authorization slice of `Governance Draft v1` to a **scoped-accepted**
  state — a new clearly-marked "Authorization (accepted slice — DEC-026)"
  subsection, **plus one-line status pointers** on the existing Authorization
  Aggregate sketch (`domains.md:2284`) and the Access and Authorization Control
  bounded context (`:2352`) pointing to it — carrying the enumerated
  `subject × verb × resource × condition` authorization rules that **project the
  ratified DEC-020 baseline** at data/action altitude, plus the union+deny-override
  meta-rule. The rest of `Governance Draft v1` is **byte-untouched** and its
  `Draft v1` status preserved.

- **Discipline.**
  - **R-027 held:** this DEC resolves **no inherited Phase 1 open question** — the
    inherited Phase-1 Open Questions in `domains.md:1915-1919` (in the *Intelligence
    Draft v1* domain — Intelligence vs Analytics/Reporting, insight→durable
    knowledge, lead-scoring home, optimization auto-apply) are untouched. Q-014,
    the cross-phase dependency this DEC resolves, is not one of them.
  - **R-028 held:** reference altitude — domain resources are referenced, never
    redefined; the verb set and condition set are evidence-derived/closed.
  - **Client Brain access-vs-ownership line (held):** authorizing access to the
    Client Brain *Surface* (who may `view` it) is an authorization concern resolved
    here; Client Brain *ownership* (Q-001 / Q-004) is **untouched**.
  - **Q-001 / Q-004 and all other draft areas untouched.**

This decision resolves the **Phase-1 half of Q-014**: the Governance authorization
rules the Permission Matrix requires are decided here and made concrete in the
`domains.md` authorization slice (same commit). The Phase-2 matrix population
(Q-014's consuming half) completes at landing (ii). It resolves **no other open
question**, finalizes **no other Governance area**, and changes **no other Phase 1
domain truth**.

Basis:
- Inline grill-me question-gate (G-1 → G-7); capture in
  `brainstorms/2026-06-08-governance-authorization-slice.md`.
- Citations re-verified against raw bytes prior to this record.

Status:
- Active

---

### DEC-027
Client Brain ownership is resolved: **Client Brain is owned by the Knowledge
domain**, as a Memory Object / Shared Service Artifact. Client Success
**contributes** relationship-relevant content but does not own it; CRM
**references** it but does not own it. This resolves **Q-001** and is the
foundation for the Phase 5 Knowledge & Memory write.

Outcome of the Phase 5 question-gate (G-1 → G-7, run inline in grill-me form):

- **G-1 Definition & altitude.** `memory.md` defines the *logical* architecture of
  memory and knowledge — per sub-item: what it is, owner (Phase-1 reference),
  contents (category level), lifecycle/durability, and retrieval + update contract.
  Vocabulary reuses Memory Object / Shared Service Artifact / Knowledge Artifact /
  Retrieval Context. Physical storage, indexing, schema, and AI-retrieval = Phase 7.
- **G-2 Closed seven-boundary set.** ↔ P1 domain truth (Knowledge already owns
  Agency Brain / Knowledge Base / Decision Logs / durable learnings / retrieval
  structures — Phase 5 architects, does not re-own); ↔ P1 Governance (DEC-026 owns
  access authorization; Phase 5 authors none); ↔ P2 (surfaces render memory,
  name-only); ↔ P3 (capabilities produce "may become durable knowledge"; Phase 5
  owns what persists); ↔ P4 (consumer of memory contracts; storage/retention
  deferred here); ↔ P6 (Learn → Memory Update is the sequence; Phase 5 owns the
  target/contract); ↔ P7 (storage / wiring / data architecture — OUT).
- **G-3 In-scope.** Six firm (Client Brain, Agency Brain, Knowledge Base, Decision
  Logs, Learnings, Context Retrieval); Asset Intelligence `[ADDED]` =
  deferred-and-flagged stub (thin domain evidence).
- **G-4 Six-field skeleton.** Definition · Owner (Phase-1 ref) · Contents (category
  level) · Lifecycle/durability · Retrieval & update contract (authorization
  deferred to DEC-026; physical retrieval to P7) · Boundary notes.
- **G-5 Non-goals.** No physical storage/indexing/schema/AI-retrieval (P7); no
  domain-entity ownership beyond what this DEC resolves (P1); no surfaces/views/
  portals (P2); no sequences / Learn→Memory orchestration (P6); no capability
  definitions (P3); no authorization/policy rules (P1 Governance / DEC-026); no
  resolution of inherited Phase-1 questions; no implementation technology.
- **G-6 Client Brain ownership (this decision's core).** Q-001 resolved to Knowledge
  (above). **Q-004 (partitioning: per Client / per Brand / both) is carried** —
  entangled with Q-003 Brand placement, which has no resolving evidence in canon.
  Per the standing partition-agnostic rider, the eventual `memory.md` Client Brain
  entry is written valid under all three partitioning answers, so it does not
  silently resolve Q-004.
- **G-7 Insight → durable-knowledge threshold (`domains.md:1917`).** Carried, not
  resolved. The Phase-5 Learnings entry references the threshold as Phase-1
  Intelligence truth, pending — defines nothing, names no mechanism shape (R-027).

Landing (two phase-separated landings, per the DEC-026 precedent):
- **(i) This DEC + the isolated `domains.md` ownership update + knock-on
  reconciliation.** The `domains.md` ownership truth is made concrete (Knowledge
  "What it owns" gains Client Brain; the Client Brain section's ownership block
  becomes resolved; the Draft-v2 "Primary Owner" and the Proposed-Model joint-
  ownership lines are corrected to Knowledge-owner + Client-Success-contributor; the
  Knowledge↔Client Success boundary line is settled; the DEC-026 slice resource list
  is refreshed; the in-file Open-Question echoes of Q-001 are marked resolved). Stale
  ownership-draft echoes are reconciled so `domains.md` does not self-contradict.
  Knock-on citations in `experience-architecture.md` (four sites) are refreshed to
  the new truth as its own called-out commit. Q-004, Q-003, the aggregate-status
  question, and all other Draft areas are left untouched.
- **(ii) The `memory.md` Knowledge & Memory architecture** that builds on (i) — a
  separate, later landing.

Holds:
- **Resolves only Q-001.** No other open question, Draft area, or Phase-1 domain
  truth is changed. Q-004 / Q-003 / aggregate status / the inherited Intelligence
  questions (`domains.md:1915-1920`) are untouched.
- **R-028 (reference altitude):** `experience-architecture.md` citations are
  refreshed as references, not reinterpretations; `memory.md` is not yet written.
- **R-027:** no inherited Phase-1 question is resolved (G-7 carried).
- **DEC-008:** the Client Brain ownership Draft area is resolved by *explicit
  decision* (the permitted path), not silently; Brand placement, Service Agreement
  ownership, and Aggregate boundaries remain Draft.
- **DEC-026 access-only line held:** authorizing access to Client Brain is
  Governance's; owning it is Knowledge's; the two do not collide.

Tracker (same commit as the `domains.md` landing):
- `open-questions.md`: Q-001 → Resolved/Closed; Q-004 stays open with the Q-003
  entanglement + partition-agnostic note.

Basis:
- Phase 5 question-gate, inline grill-me (G-1 → G-7); Ali's calls on G-6 (Option A)
  and G-7 (carry); capture in
  `brainstorms/2026-06-08-phase5-knowledge-memory-gate.md`.
- Citations re-verified against raw bytes prior to this record; the knock-on set was
  confirmed grep-complete by an independent verifier, which surfaced four
  ownership-assertion sites beyond the initial enumeration (including two joint-
  ownership statements) now reconciled.

Status:
- Active

---

### DEC-028
**Phase 6 Workflow Design — scope and question-gate closure.**

Phase: 6. Resolves: Q-015 (only). Supersedes: none.
Closes the Phase 6 question-gate G-1 → G-7.

**Context.** Phase 6 scoping via question-gate before any content is
produced for `Faraz-OS-Canon/workflows.md` (the target file, per the
canonical phase map `Faraz-OS-Canon.md:115`). This decision records the
structural frame, the four posture decisions, the sub-item classification,
and the single boundary resolution. It mirrors the DEC-025 (Phase 4) and
DEC-027 (Phase 5) scope pattern. It authors **no** `workflows.md` content;
the first write is a separate gated content batch after this decision lands.

**G-1 — Logical altitude.** `workflows.md` sits at logical orchestration
altitude: it names ordered flows, gates, hand-offs, and the sequencing
contract over Phase-3 capabilities. It defines no execution engine, runtime
technology, data paths, or AI architecture (Phase 7). Parallels DEC-025 /
DEC-027 altitude framing.

**G-2 — Closed boundary set.** A definition/altitude line plus seven
cross-phase boundaries (Phase 1 split into two facets, per the DEC-027
precedent `Faraz-OS-Canon/memory.md:198-202`):
- Definition/altitude: governed by the **selection-vs-sequence test**
  (`decisions.md:823-830`) and the **approve-verb vs approval-gate test**
  (`decisions.md:1015-1018`).
- ↔ Phase 1 domain truth — flows traverse domain entities; referenced,
  never re-owned.
- ↔ Phase 1 Governance — Phase 1 authorizes *who may approve*; Phase 6
  sequences *when the gate fires* (`decisions.md:1015-1018`; DEC-026).
- ↔ Phase 2 Experience — surfaces render/experience workflows; Phase 6 owns
  the *triggering events* Phase 2 references
  (`Faraz-OS-Canon/experience-architecture.md:844-846`); authors no surfaces
  (Phase 2 non-goal `:859`).
- ↔ Phase 3 Capability — capabilities are order-free abilities; Phase 6
  *invokes, does not define* them (`Faraz-OS-Canon/capabilities.md:85-88`;
  sequence-test `decisions.md:702-703`).
- ↔ Phase 4 Extensibility — selection/routing is order-free (Phase 4);
  ordered run / orchestration is Phase 6
  (`Faraz-OS-Canon/extensibility.md:378-385`).
- ↔ Phase 5 Knowledge & Memory — Learn → Memory Update target and update
  contract is Phase 5; the orchestration is Phase 6
  (`Faraz-OS-Canon/memory.md:210-211`).
- ↔ Phase 7 System Architecture — runtime technology, wiring, data paths,
  AI Architecture; the engine-that-executes principle
  (`Faraz-OS-Canon/extensibility.md:343-344, :390-391`).

**G-3 — Sub-item classification.** All thirteen phase-map sub-items
(`Faraz-OS-Canon.md:116-128`) are firm; zero deferred stubs. They take three
structural forms in `workflows.md`:
- (A) Firm workflow entries on the G-4 skeleton — seven: the six named flows
  (`:116-121`) plus Learn → Memory Update (`:125`).
- (B) Firm cross-cutting pattern definitions, referenced by field 5 — three:
  Escalation Loop, Revision Loop, Failure/Exception Path (`:122-124`) —
  defined once, not restated per flow.
- (C) Firm framing / construct sections (not per-flow skeleton) — three:
  Human Approval Gates (`:127`; G-6(a)), Agent Chains (`:126`; G-6(b)),
  Workflow Runtime (`:128`; G-6(c)).

**G-4 — Per-workflow six-field skeleton.** Each form-(A) entry carries:
1 Definition · 2 Trigger / entry condition · 3 Ordered steps & hand-offs
(capabilities invoked — Phase-3 reference, name-only) · 4 Gates &
human-involvement mode (G-6(a) vocabulary) · 5 Exception / loop behavior
(references the form-(B) patterns) · 6 Cross-phase boundary notes (R-028
altitude). Parallels the DEC-024 / DEC-027 skeletons. Structural sub-call:
the three loop/path items are defined once as form-(B) patterns and
referenced via field 5, not duplicated per flow.

**G-5 — Non-goals.** Phase 6 authors no: capabilities (Phase 3);
surfaces / views / portals / the Permission Matrix (Phase 2);
authorization / permission rules (Phase 1 Governance / DEC-026);
memory / knowledge structure (Phase 5); provider / channel / model
selection or routing (Phase 4); domain-entity ownership or meaning (Phase 1
domain truth); runtime technology, data paths, execution engine, deployment
runtime, or AI architecture (Phase 7). It resolves no inherited Phase-1
question (R-027).

**G-6 — Posture decisions.**

(a) *HITL default model — bounded adoption.* Field 4 uses the
human-in-the-loop philosophy #5 mode vocabulary
(`Faraz-OS-Canon/human-in-the-loop-philosophy.md:18-22`) as the referenced
owning definition, carrying "hybrid by design" verbatim, not redefined. The
client-facing-publishing default-on checkpoint (#7, `:31-32`) carries the
verbatim override phrase "configurable based on workflow policy"; the policy
mechanism is left to Phase 4 / Phase 7. Philosophy #6 (`:24-29`) is a cited
guiding principle a field-4 placement may name as motivation, never an
enumerated Phase-6 rule table. Boundary guard: gate placement and mode =
Phase 6; who may approve = Phase 1 / DEC-026.

(b) *Agent Chains — bounded orchestration construct.* Owns the orchestration
contract only (ordered agent-performed steps, hand-offs, gates, per-step
execution mode). **Role-vs-identity litmus, recorded verbatim:** *"Names
where an agent-performed step sits in a sequence and what it hands off →
Phase 6. Defines what the agent is (identity, surface, executing AI
architecture) → Phase 7. Defines how the agent is chosen among
interchangeable agents by policy → Phase 4."* Role placeholders are named at
capability altitude only (e.g. "content-drafting agent role"), never a
concrete agent / product / architecture; if a step cannot be written without
identity vocabulary, the litmus has fired — escalate, do not write around it.
Per-step execution mode references the Phase-3 capability execution-mode
attribute and the G-6(a) field-4 vocabulary (no redefinition). The registered
Phase-7 agent / subagent-identity flag
(`Faraz-OS-Canon/extensibility.md:345-347, :457-459`) stays registered and
untouched — cited as deferred, not partially resolved. Backed by ai-philosophy
#8 (`Faraz-OS-Canon/ai-philosophy.md:24-25`) and DEC-025
(`Faraz-OS-Canon/extensibility.md:378-385`).

(c) *Workflow Runtime — bounded framing section.* A framing section (modeled
on the Runtime vs Config-Time Extensions precedent,
`Faraz-OS-Canon/extensibility.md:396-400`), not a skeleton entry. It opens
with the three-way "runtime" disambiguation, citing all three canon
locations: the Phase-4 Runtime-vs-Config-Time binding attribute
(`Faraz-OS-Canon/extensibility.md:396-415`), the Phase-6 logical
workflow-runtime semantics, and the Phase-7 Runtime Architecture engine
(`Faraz-OS-Canon.md:138`). **P6↔P7 litmus, recorded verbatim:** *"Defines
what a workflow means while running — its logical lifecycle states, what
suspends/resumes at a gate, how a loop/exception behaves semantically →
Phase 6 Workflow Runtime. Defines the engine that executes workflows —
schedulers, queues, process model, state persistence, deployment runtime →
Phase 7 Runtime Architecture."* Explicit firewall list: no engine,
scheduler, queue, process model, state persistence, or deployment-runtime
vocabulary. Vocabulary test: every lifecycle state is defined in semantic
terms ("awaiting human decision at a gate"), never mechanism terms; if a
state cannot be written without engine vocabulary, the litmus has fired —
escalate, do not write around it. Field-5 entries reference this section,
they do not restate it. Standing policing note: any future edit re-applies
the litmus in review. This is the highest-R-028 surface in Phase 6.

(d) *Q-015 — resolved (see below).*

**Q-015 resolution (the only question this decision resolves).** Resolved in
three parts, each stated as a decision:
1. Atomic push ("push approved content to a channel") = Phase 3 Publishing
   capability (confirms the existing lean, `Faraz-OS-Canon/capabilities.md:90`).
2. Scheduled-publish *when-parameter* = firm Phase 3 — moved from "probably
   in-capability" to firm; it carries no cross-item ordering. Called out as a
   decision, not a restatement.
3. Cross-item queueing / sequencing = Phase 6 orchestration — it names an
   ordering across items (a sequence), so the selection-vs-sequence test
   (`decisions.md:823-830`) places it in Phase 6.
Venue-change note (recorded): Q-015's own text named the `capabilities.md`
write as its resolution venue; that pass deliberately chose flag-not-resolve —
the flag note, now refreshed at `Faraz-OS-Canon/capabilities.md:89-93`. The venue moves to this gate
because the deciding instrument — the ratified selection-vs-sequence test
(DEC-025) — now exists. This is a deliberate re-venue, applying the litmus as
a recorded decision, not a default — the opposite of the "silently fold
queueing into the capability" failure mode the flag warned against.

**G-7 — Carried / not-owned.**
- R-027 set carried unresolved: Q-003 (Brand placement), Q-004 (Client Brain
  partitioning), the insight→durable-knowledge threshold
  (`Faraz-OS-Canon/domains.md:1918`), and the inherited Intelligence-Draft-v1
  questions.
- Q-012 carried unchanged — Phase-6 completion is its downstream unblock
  trigger ("Deferred until Phase 6 is complete," `open-questions.md:268`).
  This decision does not resolve it.
- R-028 reference-altitude discipline held, with the two new verbatim litmus
  tests (b, c) as the active guards on the highest-risk surfaces.

Status:
- Active

---

### DEC-029
**Phase 6 Workflow Design — declared complete at DEC-028's scope; Q-012 trigger
fired.**

Phase: 6. Resolves: none (Q-012 is unblocked, not resolved). Supersedes: none.

**Context.** This decision makes the gated phase-status call that the Phase 6
first write (Snapshot-037) and consistency review (Snapshot-038) set up. It
changes phase status; it authors no architecture and no Phase-7 content.

**Decision.** **Phase 6 Workflow Design is complete at DEC-028's scope —
13/13 sub-items.** All thirteen phase-map sub-items (`Faraz-OS-Canon.md:116-128`),
declared firm with zero deferred stubs by DEC-028 (G-3), are written in
`workflows.md` at logical orchestration altitude (G-1): the seven flow entries on
the six-field skeleton, the three loop/exception patterns, and the three
framing/construct sections. The first write is complete and verified (Snapshot-037;
Batches A–C, commits `6eefd90` / `a7de5ef` / `a0fe15d`), and the consistency review
found it clean at the meaning level (Snapshot-038; 33 citations content-verified,
both litmuses verbatim, all G-6 conditions held). Completion is **scope-anchored to
DEC-028**, not open-ended: it asserts that DEC-028's defined scope is fully realized
at the scoped logical altitude, not that Phase 6 can never gain a further increment.

**Q-017 preserved (not a blocker).** Q-017 (system-administrator visual workflow
viewing + management) surfaced during Phase 6 as a **new, multi-phase** question
(candidate homes P2 / P4 / P6 / P7) and is **outside DEC-028's defined scope**;
`workflows.md` authors no visual workflow-management capability. Any **future
Q-017-driven Phase-6 increment** (e.g. workflow definitions as configurable
artifacts) is **marked-future** — it does **not** reopen this phase — following the
Phase-2 precedent, where deferred/parked sub-details (Navigation Model
landing-surface / notification-routing / deep-linking; Q-016) did not block the
Phase-2 7-of-7 completion.

**Cross-phase flags carried verbatim (not Phase 6's to resolve).** Agent / subagent
identity remains the registered **Phase-7** flag (`extensibility.md:345-347`,
`:457-459`). The R-027 inherited Phase-1 questions — Q-003 (Brand placement),
Q-004 (Client Brain partitioning), and the insight→durable-knowledge threshold
(`domains.md:1918`) — remain **Phase-1's** to resolve, referenced at altitude.

**Q-012 trigger fired.** Q-012's deferral condition — *"Deferred until Phase 6 is
complete"* — is met by this decision; `open-questions.md` is updated in the same
change (Q-012 deferred → active). **Q-012 (Phase 7 ↔ Phase 8 boundary) moves
deferred → active**, and the **Phase 7 ↔ Phase 8 boundary *scoping* becomes the next
open thread**. This fires
the *scoping* question only — it is **expressly NOT Phase-7 content**, which awaits
its own question-gate (no Phase-7 / Phase-8 content is authored before then).
Linear `KNI-11` re-opens (reconciled after the verified push).

**Honest note (recorded).** Phase-2 completion was declared via a **snapshot record**
(Snapshot-033), not a standalone DEC. Declaring Phase 6 complete via a **DEC** is a
deliberate **elevation** over that precedent, chosen because this call **fires a
cross-phase trigger** (Q-012) and therefore warrants a gated, decision-level record
rather than a record-only snapshot statement.

Status:
- Active

---

### DEC-030
**Phase 7 ↔ Phase 8 boundary — scope distinction (Q-012 resolution).**

Phase: 7/8 boundary. **Resolves: Q-012** (only). Supersedes: none.
Scoping only — authors **no** Phase-7 (`system-architecture-blueprint.md`) or
Phase-8 (`architecture.md`) content; each phase awaits its own question-gate.

**Context.** DEC-029 fired Q-012's trigger (`decisions.md:1436-1443`). Q-012
(`open-questions.md:259-262`) asks the intended boundary between Phase 7 System
Architecture Blueprint (`Faraz-OS-Canon.md:131`) and Phase 8 Puzzle Board
Architecture (`Faraz-OS-Canon.md:140`), since both "appear to cover system-level
concerns." This decision draws that one boundary only; it is **narrower** than full
Phase 7 scoping (a separate later question-gate). It mirrors no content write.

**Decision — the boundary.**
- **Phase 7 = the substantive cross-cutting *concern-views* (lenses).** Its seven
  sub-items (`Faraz-OS-Canon.md:132-138` — Logical, Application, Data, AI,
  Integration, Security, Runtime Architecture) each answer *how the system handles a
  cross-cutting concern*.
- **Phase 8 = the *layered assembly* (the board).** Its **seven** layers
  (`Faraz-OS-Canon.md:141-147` — Core, Domains, Capabilities, Plugins,
  Infrastructure, plus Experience and AI, the latter two `[ADDED]` at `:146-147`)
  organize the **concrete building blocks** into layers. Most are pieces already
  owned elsewhere; Phase 8 is an *assembly view*, not a place that re-designs them.
- **One-way dependency:** Phase 8 assembles to satisfy Phase 7; **Phase 7 is
  scoped/written first** (consistent with the canon phase ordering 7→8).

**Not a 1:1 mapping (pre-empts a false-symmetry error).** The seven P7 concern-views
and the seven P8 layers are **not** a one-to-one correspondence despite the matching
count. Phase 8 assembles blocks **owned across phases**: Domains Layer → Phase 1
domain truth; Capabilities Layer → Phase 3; Plugins Layer → Phase 4; Experience Layer
→ Phase 2; while Core, Infrastructure, and AI Layers are each assembled from multiple
sources. No P7 view "becomes" a P8 layer; P7 views are lenses, P8 layers are
assembled groupings.

**Boundary test (recorded verbatim for reuse):**
1. *"How does the system handle [data / execution / AI / integration / security /
   runtime] as a cross-cutting concern?"* → **Phase 7** (a concern-view / lens).
2. *"What concrete building blocks exist, and which layer do they sit in — Core /
   Domains / Capabilities / Plugins / Infrastructure / Experience / AI?"* →
   **Phase 8** (the assembled board).
3. *Re-defines what a domain / capability / plugin / experience-surface **is**, who
   owns it, or its sequence* → **neither**; that is Phases 1 / 2 / 3 / 4 / 6,
   **referenced**.

**Worked example — AI Architecture (P7) vs AI Layer (P8), the highest-collision
seam.** This is the exact pair the boundary test must disambiguate, and the seam
where Q-013 (AI / agent-surface home, `open-questions.md:292-293` — "Likely Phase 7
System Architecture Blueprint (AI Architecture)" / "Possibly relates to Phase 8 AI
Layer") and the registered
agent / subagent-identity flag (`Faraz-OS-Canon/extensibility.md:345-347, :457-459`)
both sit.
- *How the system runs AI* — the chain-modelling / routing engine, agent execution,
  model-per-part selection enforcement, human/hybrid paths as a cross-cutting
  concern → **Phase 7 AI Architecture** (`Faraz-OS-Canon.md:135`).
- *Where the assembled AI building blocks sit as a layer* in the board → **Phase 8
  AI Layer** (`Faraz-OS-Canon.md:147`).
- *What an agent/subagent **is** (identity), and the home of AI/agent-facing
  surfaces* → **neither is resolved here**: Q-013 and the agent-identity flag are
  **carried untouched** to their own later passes; this decision only names the seam,
  it does not resolve what lives on either side of it.

**Naming convention — disambiguation, not rename.** "Architecture" recurs across both
phase names, all seven P7 sub-items, and P8's title; and "AI" names both a P7 view and
a P8 layer. Per the proven three-way "runtime" disambiguation precedent
(`Faraz-OS-Canon/extensibility.md:396-400`; DEC-028 G-6(c) `decisions.md:1341-1360`),
the fix is **disambiguation, not a phase-map rename** (a rename is a
wide-blast-radius change). The eventual Phase-7 scope doc opens by distinguishing
**architecture-as-concern-view (Phase 7)** from **architecture-as-layered-assembly
(Phase 8)**, and **must specifically disambiguate AI Architecture (P7, the how-AI-runs
concern-view) from AI Layer (P8, the assembled AI grouping)** — not only the generic
word "architecture." Optional working nicknames: *"the Blueprint" (P7) / "the Board"
(P8)*. An actual rename is reserved only if a later gate finds a name conceptually
wrong, not merely colliding.

**Rejected alternative (recorded).** *"Phase 8 is the real architecture; Phase 7 is
conceptual preamble."* Rejected: it leaves Phase 7 thin and wastes its seven-view
structure; the seven views are classic architectural concern-views, the seven layers
are mostly already-defined pieces being assembled.

**Resolves.** Q-012 → resolved (the P7 ↔ P8 scope distinction). Linear **KNI-11 →
Done** after the verified push.

**Carried, NOT resolved here (verbatim).** This decision draws one boundary only. It
does **not** open Phase 7 scope (a later question-gate) and authors no Phase-7/8
content. Carried untouched: the **inversion guard** (the Phase-7 R-028 flip —
*architects how vs re-defines what*) is a later Phase-7-gate call, not here; the
**Feature-Modules / module-mounting** dependency (deferred Phase-4 sub-item) is a
later-gate call; **Q-017** (multi-phase; marked-future); **Q-013** (AI / agent-surface
home; deferred, repo-only); the registered **agent / subagent-identity Phase-7 flag**
(`Faraz-OS-Canon/extensibility.md:345-347, :457-459`); the **R-027 set** — Q-003
(Brand placement), Q-004 (Client Brain partitioning), the insight→durable-knowledge
threshold (`Faraz-OS-Canon/domains.md:1918`); **Q-016**; the **Service Agreement**
draft boundary; **R-028** reference-altitude discipline.

Status:
- Active

---

### DEC-031
**Phase 7 System Architecture Blueprint — scope and question-gate closure.**

Phase: 7. Resolves: Q-013 (AI / agent-surface architecture-home). Supersedes: none.
Closes the Phase 7 question-gate G-1 → G-7. Un-defers the agent / subagent-identity
flag into Phase 7 scope.

**Context.** Phase 7 scoping via question-gate before any content is produced for
`Faraz-OS-Canon/system-architecture-blueprint.md` (the target file, per the canonical
phase map `Faraz-OS-Canon.md:131`). Mirrors the DEC-024 (`decisions.md:679`), DEC-025
(`decisions.md:749`), DEC-027, and DEC-028 scope pattern. It authors **no** blueprint
content; the first write is a separate gated content batch after this decision lands.
The Phase 7 ↔ Phase 8 boundary is already drawn (DEC-030): Phase 7 = the cross-cutting
concern-views; Phase 8 = the layered assembly; referenced, not re-opened.

**G-1 — Altitude (the inversion guard).** `system-architecture-blueprint.md` sits at
system-architecture altitude: it architects **how** the system runs, stores, secures,
integrates, and executes AI as cross-cutting concerns, **referencing** — never
re-deciding — **what** things are and who owns them (Phases 1/2/3/6). This is the
**R-028 inversion** from earlier phases: through Phase 6 the risk was
engine/mechanism talk bleeding *into* logical phases; in Phase 7 it flips — the risk is
Phase 7 re-deciding domain / capability / workflow / experience truth instead of
referencing it. **Governing litmus, recorded verbatim:** *"Architects how the system
runs / stores / secures / integrates / executes X → Phase 7. Re-defines what X is, who
owns it, its sequence, or its surface → Phases 1 / 2 / 3 / 6, referenced."* If a view
cannot be written without re-defining owned truth, the litmus has fired — escalate, do
not write around it.

**G-2 — Closed boundary set.** A definition/altitude line plus six cross-phase
boundaries:
- Definition/altitude: governed by the G-1 inversion litmus.
- ↔ Phase 1 domain truth & Governance — Phase 7 architects how domain truth is
  persisted / secured / served; it never re-owns entity meaning or authorization
  (who-may-approve = Phase 1 / DEC-026, `decisions.md:972`).
- ↔ Phase 2 Experience — Phase 7 Security Architecture *enforces* the Permission
  Matrix and Application Architecture *runs* the portals; it authors no surfaces,
  views, or permission rules. Agent-facing **surface rendering** stays Phase 2; the
  AI/agent **architecture** is Phase 7 (the Q-013 split, G-6(b)).
- ↔ Phase 3 Capability — capabilities are the units the architecture executes; Phase 7
  invokes / runs, never defines them (`capabilities.md:85-88`).
- ↔ Phase 4 Extensibility — Phase 4 owns selection / routing policy and the
  Feature-Module **contract**; Phase 7 architects the **engine** that executes routing
  and the **mounting / running / composing** of modules (`extensibility.md:390-391`).
- ↔ Phase 6 Workflow — Phase 6 owns workflow-runtime *semantics*; Phase 7 Runtime
  Architecture owns the *engine*. **P6↔P7 litmus carried verbatim**
  (`Faraz-OS-Canon/workflows.md:167-171`; DEC-028 `decisions.md:1348-1353`): *"Defines
  what a workflow means while running — its logical lifecycle states, what
  suspends/resumes at a gate, how a loop/exception behaves semantically → Phase 6
  Workflow Runtime. Defines the engine that executes workflows — schedulers, queues,
  process model, state persistence, deployment runtime → Phase 7 Runtime
  Architecture."*
- ↔ Phase 8 Puzzle Board — the DEC-030 boundary: concern-views (P7) vs layered
  assembly (P8); Phase 7 authors no Phase-8 layer content.

**G-3 — Sub-item classification.** All seven phase-map sub-items
(`Faraz-OS-Canon.md:132-138`) are firm concern-views; zero deferred stubs — Logical,
Application, Data, AI, Integration, Security, Runtime Architecture. **AI Architecture
is the spine** (AI-native), but **never AI-only**: every view honors Core Principle #1
(`Faraz-OS-Canon/principles.md:3`, "AI-first, but not AI-only") and the HITL mode
vocabulary (`Faraz-OS-Canon/human-in-the-loop-philosophy.md:18-22`) — AI as default
executor with human / hybrid paths first-class.

**G-4 — Per-view skeleton.** Each concern-view carries a six-field skeleton (parallels
DEC-024 / 025 / 027 / 028): 1 Definition / concern · 2 What it architects (the *how*) ·
3 Referenced owned-truth (the *what*, by phase — an explicit reference list) · 4 Key
decisions / mechanisms at logical altitude (no named technology) · 5 Cross-phase
boundary notes (the G-1 litmus) · 6 Open / deferred items. The skeleton is firm at
scope; field content is the gated write.

**G-5 — Non-goals.** Phase 7 authors no: named technology / vendor / language / cloud
(deferred to the Claude Code handoff — preserves the generalizable-pattern value);
implementation code; re-decided Phase-1 domain truth or authorization, Phase-3
capability definitions, or Phase-6 workflow sequences / semantics; Phase-8 layered-
assembly content. **Single-tenant constraint (new, this decision):** Faraz OS is
single-tenant — **no multi-tenant isolation layer is architected.** Recorded as a
Phase-7 scoping constraint / non-goal, sourced to the strategic framing (Ali's
direction), not pre-existing canon.

**G-6 — Posture decisions.**

(a) *Agent / subagent identity — un-deferred into Phase 7 scope.* The registered
agent / subagent-identity flag (`Faraz-OS-Canon/extensibility.md:345-347, :457-459`) is
**un-deferred**: **Phase 7 AI Architecture owns agent / subagent identity.** It is
**defined in the content write**, not in this gate. On landing, the Phase-4 flag and
the philosophy-#7 routing annotation (`Faraz-OS-Canon/extensibility.md:388-391`) get a
reference-altitude refresh ("scoped to Phase 7 per DEC-031"); the Phase-4 selection /
routing scope itself is unchanged.

(b) *Q-013 resolved — architecture-home split.* Q-013 (`open-questions.md:297`,
`:301-302`) is **resolved**: the **architecture / engine home of AI & agent-facing
capability is Phase 7 AI Architecture**; **surface rendering** of agent-facing surfaces
stays **Phase 2 Experience** (which already owns surfaces). Only a genuinely pure
surface-rendering nuance, should one surface, is a Phase-2 item; no new Phase-2 work is
implied by this resolution.

(c) *Feature Modules — boundary + required sequencing.* The boundary is crisp:
**Phase 4 owns the Feature-Module contract** (`Faraz-OS-Canon/extensibility.md:433-434`,
currently a deferred stub); **Phase 7 architects the mounting / running / composing**;
**Phase 8 is the assembled Plugins Layer.** Phase 7 **references, never defines** what a
module is. **Required sequencing prerequisite (recorded):** Phase-4 "Feature Modules"
must be **un-deferred as its own gated Phase-4 decision BEFORE the Phase 7 Application /
Logical Architecture content write.** This prerequisite does **not** block this scope
DEC or the other five view writes; it blocks only those two specific view writes until
the Phase-4 contract exists.

**G-7 — Carried / not-owned.**
- R-027 set carried unresolved: Q-003 (Brand placement), Q-004 (Client Brain
  partitioning), the insight→durable-knowledge threshold
  (`Faraz-OS-Canon/domains.md:1918`).
- Q-016 (Phase-2 view-membership nuance) carried; Q-017 (system-administrator visual
  workflow management, multi-phase) carried — a candidate Phase-7 home is noted, but its
  placement is its own gated decision, not resolved here.
- Service Agreement draft boundary carried (Phase-1 owned).
- R-028 discipline held as the active G-1 inversion guard.

Status:
- Active

---

### DEC-032
**Phase 4 Feature Modules — un-defer; scope / posture decision (the DEC-031 prerequisite).**

Phase: 4. Resolves: none (un-defers a DEC-025-deferred sub-item). Supersedes: none.
This is the un-defer **DEC-025 anticipated** — DEC-025 recorded the deferred sub-items as
"flagged, not dropped" (`decisions.md:772-773`), so un-deferring Feature Modules is the
foreseen path, not a correction; DEC-025 itself is not retro-touched (its other three
deferrals stand).

**Context.** DEC-031 G-6(c) (`decisions.md:1651-1660`) recorded that Phase-4 "Feature
Modules" must be **un-deferred as its own gated Phase-4 decision before the Phase 7
Application / Logical Architecture view writes.** DEC-025 deferred Feature Modules as a
forward-looking concern presupposing the core contract model
(`decisions.md:768-772`; Philosophy #12, `extensibility-philosophy.md:43-45`); that
core contract model now exists (the `extensibility.md` first write, Snapshot-030). This
decision **un-defers** Feature Modules and fixes the scope / posture for its
`extensibility.md` entry. It authors **no** entry content; the stub→firm write is a
separate gated content batch.

**Decision — un-defer + Option A (first-class).** Feature Modules
(`Faraz-OS-Canon.md:103`) moves deferred → in-scope. A **Feature Module is
first-class:** a **mountable unit of product functionality** that mounts on the base
and **may aggregate plugins**, declared through the existing **Extension Contracts**
surface (`Faraz-OS-Canon/extensibility.md:196-203`). It **composes** Extension Contracts
+ Plugin Model; it does **not** re-define plugins.

**Definition / altitude of the Feature-Module CONTRACT (logical altitude — recorded
verbatim for the write to apply):**
- *What a Feature Module is:* a first-class, mountable unit of product functionality — a
  cohesive, base-mountable slice of the product — that declares itself to the core
  through the Extension Contracts surface and may aggregate one or more plugins,
  providers, or channels.
- *Its boundary:* the entry defines the module **contract** — what a module is, how it
  declares / registers itself, its interface to the core — at logical altitude; it names
  no mounting / runtime mechanism and no concrete module inventory.
- *Module-vs-plugin altitude line (verbatim):* **"A plugin attaches a single extension
  — a channel, provider, or integration — to the core through the contract surface
  (`Faraz-OS-Canon/extensibility.md:273-284`). A Feature Module is a coarser-grained,
  mountable unit of product functionality that may aggregate plugins; it composes the
  Plugin Model and Extension Contracts, and never re-defines either."**

**Boundary held verbatim (from DEC-031 G-6(c), `decisions.md:1651-1660`):** **Phase 4
owns what a module is / its contract; Phase 7 references — never defines —
(mounting / running / composing); Phase 8 is the assembled Plugins Layer**
(`Faraz-OS-Canon.md:144`). The Feature-Module entry authors no mounting / runtime /
composition mechanism and no assembled-layer content.

**Promotion-path stance (Philosophy #12, `extensibility-philosophy.md:43-45`).** Phase 4
defines the **promotion CONTRACT HOOK only** — the contract-level seam by which a
widely-used, strategically-central module *could* be promoted into the configurable core.
The actual **promotion-to-core decision** is referenced as a **product / governance
call**, not Phase 4's per-module business decision; the entry names the hook and
references the decision — it authors no promotion rule and makes no promotion.

**Entry skeleton (the existing DEC-025 six-field shape, `decisions.md:856-863`).** The
stub→firm write uses: Definition · Contract surface (incl. versioned interfaces) ·
Provider-agnostic note (what the module composes / aggregates) · Governance touchpoints
(the #8 categories, referenced, never authored) · Runtime vs Config-Time (the attribute)
· Boundary notes / inherited flags (the DEC-031 P4 / P7 / P8 boundary; any inherited
Phase-1 question preserved). Stub (`Faraz-OS-Canon/extensibility.md:436-437`) → firm
entry; the "deferred per DEC-025" stub line flips to the firm entry in that content
batch, not here.

**Non-goals.** The Feature-Module entry authors no: mounting / runtime / composition
engine (Phase 7); assembled-layer content (Phase 8 Plugins Layer); named technology /
vendor / language / cloud; re-decided Plugin Model or Extension Contracts (composed, not
re-defined); promotion-to-core rule or any actual promotion (product / governance).

**Carried / not-owned.** The other three deferred Phase-4 sub-items —
**Versioning & Compatibility, External Integrations, Future Domains** — stay deferred per
DEC-025, untouched. The **R-027** set (Q-003 Brand placement, Q-004 Client Brain
partitioning, the insight→durable-knowledge threshold `Faraz-OS-Canon/domains.md:1918`)
is referenced, carried, unresolved.

**Prerequisite satisfied (recorded).** This un-defer **satisfies the DEC-031 G-6(c)
prerequisite** for the Phase 7 Application / Logical Architecture view writes — those two
writes unblock once the Feature-Module entry (the stub→firm content batch) lands. The
other five Phase-7 concern-views were never blocked by it.

Status:
- Active

---

## Supersession Rule
If a current decision is replaced:
- keep the same decision id if only wording is refined
- create a new decision id if meaning materially changes
- mark the older one as Superseded if needed

---

## Review Rule
Review this file regularly.

If a decision:
- is still shaping current work, keep it here
- has been replaced, mark it clearly
- is only historical, move the detail to snapshots
