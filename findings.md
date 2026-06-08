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

---

### FIND-027
`experience-architecture.md` asserted Phase-5 placement for the Client Brain
concept in three places (file lines 194, 259, 612) while Client Brain ownership
is an open, protected draft (Q-001, Q-004; DEC-008; `domains.md` direction =
Memory Object / Shared Service Artifact, unresolved). This was a
reference-altitude overcommitment: naming a phase owner for a concept whose
placement is undecided.

Meaning:
- The three phrases were corrected to reference altitude
  ("ownership draft, Q-001/Q-004") in commit edd4e55.
- The other Client Brain mentions are name-only Phase 2 objects
  (Client Brain Surface, Client Brain View) and were left unchanged.

Impact:
- No architecture decision; no open question resolved. Client Brain ownership
  stays draft. Generalized as risk R-028 (reference-altitude overcommitment).

Source:
- Backfilled from Snapshot-026; not created here.

---

### FIND-028
Repo-wide citation drift on the inherited Phase 1 open-question line refs. The
`domains.md` `### Open Questions` block (header at `:1914`) holds the three
inherited questions at byte-accurate ranges `:1915-1916` (Intelligence vs
Analytics / Reporting), `:1917` (when an insight becomes durable knowledge), and
`:1918-1919` (lead-scoring home). Prior canon files cite these off by one —
`capabilities.md:116/211` use `:1914-1915` and `:220/238` use `:1917-1918`; the
same off-by-one appears in Snapshot-025/026 and `Current-State.md`.

Meaning:
- DEC-025 uses the byte-accurate ranges and registers the drift as a minor
  normalization flag.

Impact:
- Alignment is deferred to a later normalization pass. It resolves no question
  and changes no domain truth.

Source:
- Backfilled from Snapshot-027; not created here.

---

### FIND-029
The DEC-025 Channel Model acceptance test held under its first real load. Writing
the Phase 2 Channel Behaviors for the one taxonomy channel type needed only the
Channel Model's taxonomy and its three experience attributes
(format/media constraints · preview affordance · notification capability) — the
three Phase 2 dimensions key 1:1 to the three attributes — with no further Phase 4
content required. This validates the OQ-C unblock-altitude decision (write the
Channel Model only to the altitude that unblocks Phase 2) and the broader pattern
of recording a verbatim cross-phase acceptance test as the contract between a
producing phase and a consuming phase. Citable precedent for future unblock-
altitude scoping.

Source:
- Backfilled from Snapshot-031; not created here.

---

### FIND-030
The DEC-026 G-3 acceptance criterion held on its decisive use: the Phase 2
Permission Matrix derived from the landed Governance authorization rules
(`domains.md`, "Authorization (accepted slice — DEC-026)") plus the Phase-2
surface↔resource mapping reproduces the ratified DEC-020 reuse table across all 80
surface×persona cells with **zero divergence** (full cell-by-cell derivation, not
spot-checks). This confirms the round-trip of the two-altitude design — Phase 1
authorizes (subject × verb × resource × condition), Phase 2 projects (persona ×
surface exposure) — and is the second hold of the cross-phase
acceptance-test-as-contract pattern (cf. FIND-029, the DEC-025 Channel-Model test).
Citable precedent for future producer→consumer phase projections.

Source:
- Backfilled from Snapshot-033; not created here.

---

### FIND-031
Resolving a long-standing draft that is echoed across a canon file requires a
grep-complete reconciliation sweep, not the initially-named edit sites. For DEC-027
(Client Brain ownership → Knowledge), the first knock-on enumeration named two
primary `domains.md` ownership statements plus the DEC-026 slice list; an
independent verifier's full grep then surfaced four more ownership-assertion sites —
including two that asserted **joint** Client Success + Knowledge ownership
(`domains.md` Draft-v2 "Primary Owner"; the Proposed-Model line) — which, left
stale, would have made `domains.md` self-contradict the resolution. This is the
FIND-027 stale-citation failure mode one level deeper: not a citation drifting, but
the source-of-truth file asserting the opposite of the decision. The independent
verification pass caught the incomplete enumeration before commit.

Meaning:
- When a DEC resolves a draft area, enumerate every surviving assertion of that
  draft's openness by independent grep, classify each as resolve vs
  legitimately-carry, and treat the verifier's grep-completeness check as a landing
  gate, not a formality.

Impact:
- No architecture changed by this finding. DEC-027's edit set was expanded to the
  grep-complete set (13 `domains.md` sites) and verified contradiction-free before
  landing.

Source:
- Snapshot-034 close-out; this session.

---

### FIND-032
An LLM verification pass can **false-pass** line-number citations that point into a
file edited earlier in the same session. During the DEC-027 landing (ii)
(`memory.md` write), the independent verifier reported several `domains.md`
citations "correct" (`:1254-1257`, `:2746-2752`, `:1262`) that were in fact off:
the lines had shifted under the same-session DEC-027 edits (D4 −1 at `:145`, D8 +2
at `:373`, D2a +1 at `:1263`, D1b −1 at `:2762`), and the draft had carried some
citations from pre-landing reads. This is a sibling to FIND-031 (which named the
grep-completeness lesson for reconciliation sweeps); the distinct lesson here is
that **LLM citation-checking is unreliable across shifted ranges** and must not be
the sole line-number guard.

Meaning / corrective (adopted as a standing operating rule):
- After any same-session canon landing, re-derive all draft citations from
  **post-landing ground truth** (content-anchor grep for current line numbers),
  never from pre-landing reads.
- Run a **deterministic stale-token sweep** on the draft (grep the old line numbers)
  before the verifier pass; do not rely on the LLM verifier alone for line-number
  accuracy.

Impact:
- No architecture changed. The `memory.md` draft's ~25 citations were re-derived
  from ground truth and confirmed byte-accurate by the sweep before landing. The
  corrective is persisted as a standing operating rule.

Source:
- Snapshot-035 close-out; this session.

### FIND-033
Citation verification must validate **anchor content**, not only token freshness.
During the DEC-028 landing (Phase 6 scope), a draft citation `memory.md:196-199`
was **mis-anchored**: line 196 is unrelated trailing text and the range stopped
before the second Phase-1 facet the citation claimed (the two-facet boundary-set
precedent). The content actually sat at `:198-202`. Two distinct failure modes
surfaced:
- A **stale-token sweep does not catch a mis-anchor** — no token shifted; the
  citation was simply wrong at authoring time. Only re-deriving from ground truth
  and byte-reading the cited range's *content* caught it.
- The **independent LLM verifier false-passed** the mis-anchored citation — the
  same unreliability FIND-032 named for shifted ranges also applies to
  authored-wrong ranges.
- Separately, the deterministic `89-94` sweep surfaced a **third** stale
  occurrence beyond the human reviewer's two-item enumeration, confirming the
  sweep must be run rather than trusting any manual list.

This is a sibling to FIND-032 (same-session shift) and FIND-031
(grep-completeness for reconciliation sweeps); the distinct lesson is that
**citation-checking must verify content at the anchor, not just token freshness.**

Meaning / corrective (adopted as a standing operating rule; extends FIND-032):
- The pre-commit verifier must **byte-read each cited range and confirm it
  contains the claimed content** (anchor-content check), not only sweep for stale
  tokens.
- Always run the **deterministic sweep** rather than trusting a manual
  enumeration of fixes — both, not either.

Impact:
- No architecture changed. The DEC-028 trio's citations were re-derived from
  post-landing ground truth, the mis-anchor corrected to `:198-202`, all three
  `89-94` occurrences corrected to `:89-93`, and all anchors content-verified
  before landing.

Source:
- Snapshot-036 close-out; this session.

### FIND-034
**Living-doc `domains.md` citation drift, re-derived from ground truth.** A
normalization pass over the living canon docs found that their `domains.md`
line-number citations had drifted — sometimes by one line, sometimes several, and
in some cases pointing at the wrong content entirely — because the cites were
authored against **historical `domains.md` states** and verified, pre-FIND-033, by
token presence rather than anchor content. `domains.md` grew and shifted over the
project (e.g. the gated DEC-027 ownership update), so the cites silently fell out of
alignment. **FIND-028** (the inherited Phase-1 question refs being "off by one") was
the **surfacing subset** of this broader drift; the full re-derivation also caught a
content-error (`:1904` Intelligence/**Knowledge** overlap cited where the
Intelligence/**Reporting** overlap `:1906-1907` was meant) and a separate
Service-Delivery Revision cluster (`:3217/:3250/:3287` → `:3336/:3369/:3406`).

Ground-truth map (Intelligence Draft v1 Open Questions, current `domains.md`):
Q1 Intelligence vs Analytics/Reporting `:1916-1917`; Q2 insight→durable-knowledge
threshold `:1918`; Q3 lead-scoring placement `:1919-1920`.

Meaning / corrective (adopted as a standing operating rule):
- **Living docs** (current canon + trackers: `capabilities.md`, `extensibility.md`,
  `Current-State.md`, etc.) track **current** `domains.md`; their cites are
  re-derived from ground truth and content-verified (FIND-033), not token-matched.
- **Immutable history** — snapshots, `brainstorms/`, and `decisions.md` (DEC entries
  are point-in-time records) are **never retro-edited** for citation drift; their
  cites **resolve against their landing commits**, which is the durable direction of
  reference.
- When a living-doc fix makes an open-flag stale (e.g. a "citation drift deferred"
  flag), the flag is refreshed in the **same** fix commit.

Impact:
- No architecture changed. The three living docs were re-derived from ground truth
  and content-verified, each as its own called-out commit: `capabilities.md`
  (`79ec993`, 11 sites incl. the `:1904` content-fix and the Revision cluster),
  `extensibility.md` (`b7b2b55`, incl. the stale FIND-028 flag), `Current-State.md`
  (`35391bb`, incl. the stale-flag refresh and a Q-015 open/resolved consistency
  fix). FIND-028 is hereby closed by this re-derivation; the immutability rule is
  persisted. `domains.md` was read-only throughout.

Source:
- Normalization-backlog thread (item 3 / FIND-028); this session.
