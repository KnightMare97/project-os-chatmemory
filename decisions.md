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
