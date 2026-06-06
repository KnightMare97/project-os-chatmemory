# Findings

## Purpose
This file tracks the current important findings
that shape interpretation of Faraz OS.

It is not a complete historical log.

It should contain active,
still-relevant findings
that influence current architecture work,
current repository understanding,
or current execution planning.

Historical detail may remain in snapshots.

---

## Usage Rules
- Keep findings current.
- Prefer one canonical entry per important finding.
- If a finding becomes outdated, remove it or move it to snapshots.
- If a finding turns into an explicit decision, capture the decision in `decisions.md`.
- Do not duplicate full snapshot history here.

---

## Current Active Findings

### FIND-001
The repository is phase-structured,
not topic-chaotic.

Meaning:
- Faraz OS is organized through explicit phases.
- `Faraz-OS-Canon.md` is the canonical phase map.
- Phase interpretation should remain aligned to the canon.

Impact:
- Work should be placed into the correct phase context
  instead of being handled as unstructured notes.

---

### FIND-002
Repository truth is hierarchical,
not flat.

Meaning:
- Newer snapshots and canon material carry more weight
  than stale root notes or old bootstrap files.
- Not every markdown file should be treated as equally current.

Impact:
- Claude collaboration must respect source-of-truth priority.

---

### FIND-003
Phase 1 Domain Discovery now has enough structure
to shift primary effort toward normalization.

Meaning:
- The main missing work is increasingly document stabilization work
  rather than broad new domain discovery.

Impact:
- The next valuable step is controlled normalization,
  not broad expansion.

---

### FIND-004
Phase 1 already has a stronger readiness basis
than earlier drafts.

Meaning:
- There is now a canonical classification layer.
- Core domains are explicitly treated.
- Sensitive cross-domain concepts have explicit draft handling.
- Assumption, Open Question, and Risk are actively used.

Impact:
- The project is more stable for interpretation
  and safer for controlled cleanup.

---

### FIND-005
Normalization is a structurally sensitive task,
not simple document cleanup.

Meaning:
- It affects terminology,
  repeated definitions,
  section consistency,
  and cross-domain interpretation.
- Poor cleanup could create concept drift.

Impact:
- Normalization needs explicit constraints
  and careful review.

---

### FIND-006
AI-assisted normalization is safer than broad manual editing
for the current repository state.

Meaning:
- The work is cross-cutting,
  repetitive,
  and easy to damage through inconsistent manual edits.
- Claude Code is the preferred later execution path
  if guided by clear rules and human review.

Impact:
- Normalization should be prepared as a controlled handoff,
  not casual cleanup.

---

### FIND-007
The repository currently contains mixed freshness levels
in root summary files.

Meaning:
- Some root files are current enough to keep.
- Some are stale or incomplete.
- Root summaries should not automatically override canon or snapshots.

Impact:
- Root files need selective refresh
  before full trust inside Claude Project.

---

### FIND-008
Snapshot discipline is essential
for preserving continuity across sessions.

Meaning:
- Important decisions,
  findings,
  and shifts in interpretation
  should not remain only in chat.
- Snapshots provide the chronology layer for repository memory.

Impact:
- Chat-only reasoning must be promoted into repository files
  when it materially changes project understanding.

---

### FIND-009
Phase ownership and operating ownership are distinct concerns.

Meaning:
- Architecture content belongs to its corresponding phase.
- Claude collaboration method belongs to Phase 9
  and repository-level operating rules.

Impact:
- This reduces confusion between
  architecture truth
  and AI operating procedure.

---

### FIND-010
Current unresolved boundaries are visible enough
to continue productively without pretending they are solved.

Meaning:
- Some important areas remain draft,
  such as Client Brain ownership,
  Brand placement,
  Service Agreement ownership,
  and some aggregate boundaries.
- Visible ambiguity is currently healthier than false certainty.

Impact:
- Progress can continue
  without forced premature finalization.

---

### FIND-011
Canonical consolidation is now more valuable
than adding more parallel notes.

Meaning:
- The repository benefits more from aligning,
  cleaning,
  and stabilizing current material
  than from creating new overlapping summaries.

Impact:
- Prefer updating existing canonical files
  over adding new parallel documents.

---

### FIND-012
Claude Project migration should be curated,
not raw.

Meaning:
- Uploading stale root files too early
  can distort Claude’s understanding of current truth.
- Canon files and snapshots are safer first imports.

Impact:
- Migration should happen in stages,
  beginning with canonical and snapshot material,
  then refreshed root memory files.

---

### FIND-013
The risk asymmetry between direct canonical file update
and proposed draft plus review summary
strongly favors the proposed draft operating model
for broad normalization of `domains.md`.

Meaning:
- In a direct update model, a bad normalization edit corrupts
  the canonical file before human review can catch it.
- In a proposed draft model, a bad edit is visible and rejectable
  before the canonical file is touched.
- This asymmetry is especially significant for `domains.md`
  because it is the active Phase 1 source of truth.

Impact:
- Broad AI-assisted normalization of `domains.md`
  should follow the proposed draft plus review summary pattern,
  not direct mutation.
- This may also be a strong default pattern
  for future broad structural editing of canonical files,
  but that has not yet been separately decided.

---

### FIND-014
Follow-up Discovery Items found during normalization
should be recorded in the review summary by default.

Meaning:
- If preserving architectural meaning in the proposed draft
  requires an explicit marker,
  the item may also appear in the proposed draft
  using Draft, Open Question, Risk,
  or Follow-up Discovery labeling.
- Silent redesign is not permitted in either case.

Impact:
- Normalization passes must surface follow-up items
  rather than absorb them silently
  into the canonical file.

---

### FIND-015
Phase 1 Domain Discovery is complete through normalization.

Meaning:
- `domains.md` contains:
  - canonical classification rules
  - all eight core domain sections
  - boundary decisions
  - service agreement and brand decision sections
  - explicit draft markers on all unresolved boundaries

Impact:
- Phase 1 is the stable reference layer
  for downstream phase work.

---

### FIND-016
`Faraz-OS-Canon.md` is aligned with the intended
Phase 0–11 structure.

Meaning:
- Two new phases are present:
  - Phase 2 Experience Architecture
    → `experience-architecture.md`
  - Phase 7 System Architecture Blueprint
    → `system-architecture-blueprint.md`
- Canon alignment is confirmed complete.

Impact:
- The canon map is the authoritative phase scaffold
  for all subsequent work.

---

### FIND-017
The normalization operating model established through
DEC-011 and Execution Checklist v1 proved effective.

Meaning:
- The proposed draft plus review summary pattern
  kept the canonical file safe throughout the pass.

Impact:
- This pattern is a strong default for future broad
  structural editing of canonical files.

---

### FIND-018
Phase 2 Experience Architecture is the first phase
after the completed Phase 1.

Meaning:
- Phase 2 has a canon entry, a filename,
  and defined sub-items in `Faraz-OS-Canon.md`:
  Personas, Operating Surfaces, Portals,
  Navigation Model, Permission Matrix,
  Cross-Domain Views, Channel Behaviors.

Impact:
- Phase 2 is the natural next focus after Phase 1.
- The framework canon write now lives in
  `Faraz-OS-Canon/experience-architecture.md`
  (see DEC-019 and Snapshot-014).

---

### FIND-022
Governance (Phase 1, `domains.md`) owns permission,
authorization, and policy rules as the source of truth
and is explicitly modeled as not a UI permission table
(`domains.md` lines ~2170-2173).

Meaning:
- The three-altitude permission separation
  (Phase 1 Governance rules,
  Phase 4 extension grants,
  Phase 2 experience projection)
  has a Phase 1 evidentiary basis.
- The apparent Phase 2 / Phase 4 permission overlap
  raised in Q-011 is removed by this finding.

Impact:
- The Phase 2 Permission Matrix is a read-only projection
  of Governance rules.
- Phase 2 authors no permission or authorization rules.
- Supports DEC-019.

---

### FIND-024
System Administrator surface count is growing relative
to other personas in the Phase 2 Operating Surfaces
inventory (DEC-020): 3 firm surfaces plus 1 flagged,
on top of full reuse of *Agent & Workflow Monitor*.

Meaning:
- Admin work is genuinely multi-headed (knowledge,
  workflow authoring, integration management,
  system configuration).
- The current shape is defensible, but the surface count
  is disproportionate to other personas.

Impact:
- Flagged as a potential later refactor candidate
  (for example, merging some admin surfaces, or splitting
  System Administrator into sub-personas if the count
  keeps growing).
- Informational only; no action this session.
- Supports the deferred *System Configuration / Settings*
  flag in DEC-020.

---

### FIND-025
Phase 2 Experience Architecture is 4-of-7 canon sub-items
populated, not near-complete. Prior trackers had read
"KNI-14 content sub-items complete" as near-complete Phase 2.

Meaning:
- Populated (4): Personas, Operating Surfaces, Portals,
  Cross-Domain Views.
- Framework only: Navigation Model (unblocked-but-unstarted)
  and Channel Behaviors (soft-blocked for per-channel
  population on the Phase 4 Channel Model; channel-agnostic
  patterns may be writable before then).
- Structure-defined but blocked: Permission Matrix
  (blocked on concrete Phase 1 Governance rules; Q-014).

Impact:
- The remaining Phase 2 work is now visible:
  Navigation Model is actionable; Channel Behaviors waits on
  Phase 4; Permission Matrix waits on Phase 1 Governance.
- Recording / hygiene correction only; no canon content was
  written and no flag was resolved (Client Profile, System
  Configuration / Settings, Onboarding stay flagged).

---

### FIND-026
Video Creation appears in the Phase 3 map (`Faraz-OS-Canon.md:82-90`) but is
absent from the `domains.md:184-191` Capability examples list. That examples
list is illustrative, not exhaustive (the phase map is authoritative); the
entry-writing pass should add Video Creation to it. Examples-touch-up altitude
only — this is NOT a Phase 1 domain-truth change and must not reinterpret
Phase 1.

Source:
- Backfilled from Snapshot-024; not created here.
