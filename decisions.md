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
