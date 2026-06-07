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
