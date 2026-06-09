# Snapshot-048 — Reconciliation Sweep Complete: DEC-042–DEC-048, G-01–G-05

## Current Phase
Multi-phase reconciliation sweep (Phase 1 Q-resolution + Phase 2, 4, 5, 6, 7, 8 content fixes).

## Current Topic
Architecture reconciliation sweep initiated by the Phase 9 close-out review: landing all
seven deferred decisions (Q-009, Q-005, Q-022, Q-004, Q-020, Q-016, Q-017) and five gated
content fixes (G-01–G-05). All seven DECs (042–048) minted; all five content fixes landed.
Phase 10 is now unblocked.

## Status
COMPLETE. All 6 commits pushed and verified on origin/main.

---

## Document Updates

### `decisions.md`
- DEC-042 added: Q-009 resolved by completion
- DEC-043 added: Q-005 CRM / Client Success domain boundary
- DEC-044 added: Q-022 Knowledge owns PromptTemplate
- DEC-045 added: Q-004 per-Brand Client Brain partitioning with per-Client aggregation view
- DEC-046 added: Q-020 Phase 4 Channel Model operational attribute (access-status/connection-health)
- DEC-047 added: Q-016 Client sees Performance & Analytics View scoped to own-engagement
- DEC-048 added: Q-017 workflows fixed-flow at T1; visual editing deferred to v2

### `open-questions.md`
- Q-009: Resolved (DEC-042)
- Q-005: Resolved (DEC-043)
- Q-022: Resolved (DEC-044)
- Q-004: Resolved (DEC-045)
- Q-020: Resolved (DEC-046)
- Q-016: Resolved (DEC-047)
- Q-017: Resolved (DEC-048)

### `Faraz-OS-Canon/domains.md` (ISOLATED commits 2, 3, 4)
- CRM section (~766): CRM ↔ Client Success boundary note (DEC-043)
- Client Success section (~1519): CS ↔ CRM boundary note (DEC-043)
- Brand Assumptions (~3740): "Final Brand placement" → "Brand aggregate placement" (G-05)
- Knowledge "What it owns" (~1265): PromptTemplate entry added (DEC-044)
- Knowledge Candidate Entities (~1294): PromptTemplate added (DEC-044)
- Organizational Knowledge BC (~1346): templates note updated (DEC-044)
- AI Operations "not responsible for" and Domain Notes: Q-022 → DEC-044 (DEC-044)
- Client Brain Open Question (~660): resolved (DEC-045), per-Brand partitioning
- Knowledge entries (~1265, ~1278, ~1450, ~3010): Q-004 → DEC-045 throughout
- Client Brain Aggregate relationships (~2473, ~2795): Q-004 → DEC-045
- Brand Open Questions (~3748) and Ownership section (~3792): Q-004 → resolved (DEC-045)

### `Faraz-OS-Canon/memory.md`
- Client Brain partition description updated (Q-004 open → per Brand, DEC-045)
- Boundary notes updated (Q-004 → DEC-045)
- Comprehensive FIND-032 cite sweep (51+ corrections): all Knowledge section line-number
  cites updated to post-domains.md-edit ground truth

### `Faraz-OS-Canon/extensibility.md`
- Channel Model: 3 → 4 channel-level properties (access-status/connection-health; DEC-046)
- Lines ~148, ~155-159, ~163-164, ~169, ~191-193, ~201-204 updated for DEC-046
- Q-020 resolved reference added to boundary notes and acceptance test prose

### `Faraz-OS-Canon/experience-architecture.md`
- Lines 20-21, 44 (G-01): Permission Matrix status corrected to populated (DEC-026/Snapshot-033)
- Lines ~893-899 (G-01): Deferred section updated to completed
- Line 712 (G-02): Client Brain View row updated to DEC-045 per-Brand + CRM (Brand entity)
- Line 239 (G-03): Manager portal — Full (not "Full or Scoped")
- Line 338 (G-03): Agent & Workflow Monitor — Full (not "Full or Scoped")
- Line 617 (DEC-047): Performance & Analytics View Client column → Scoped (own-engagement)
- Lines 625-633 (DEC-047): `‡` footnote replaced with Q-016 resolved note
- Line 370 (DEC-047): Client portal table updated with Performance & Analytics View
- Line 712 (DEC-047): View Inventory Client column updated

### `Faraz-OS-Canon/architecture.md`
- Lines 407/~408 (G-04): Cross-Domain Views block updated to all 7 views including DEC-047 note
- Line ~467 (DEC-048): AI Layer deferred slot 1 → resolved (Q-017/DEC-048, fixed-flow at T1)
- Lines ~509-512 (DEC-048): Carried/deferred section updated
- Lines ~528-529 (DEC-048): Status section updated for Q-017 resolution
- Lines 91-92: Carried-open list — resolved questions removed, remaining (Q-006, Q-024, R-027 set) noted

### `Faraz-OS-Canon/workflows.md`
- Lines 269-270 (DEC-048): Q-017 registered-open flag → resolved (DEC-048; visual editing deferred to v2)
- Lines 432-440 (DEC-048): Q-017 boundary block replaced with resolved note (fixed-flow at T1)

### `Faraz-OS-Canon/system-architecture-blueprint.md`
- Lines 291-293 (DEC-048): AI Architecture open/deferred items — Q-017 → resolved (DEC-048)
- Lines 472-475: R-027 set updated — Q-004 removed (resolved DEC-045), Q-016/Q-017 marked resolved
- Line ~473: domains.md:1941 cite corrected to :1946 (insight→durable threshold)

### `Faraz-OS-Canon/infrastructure.md`
- Lines 92-93: Carried-open list — resolved questions removed, remaining noted

---

## Decisions

### DEC-042 (COMMIT 1 — ee27f92)
Q-009 (Phase 9 coherence — Channel Model continuity from Phase 4 to Phase 7/9) resolved
by completion: Snapshot-047 (infrastructure.md first write) + DEC-046 (Q-020 Channel
Model attribute) together close the coherence concern. No architectural gap.

### DEC-043 (COMMIT 2 — 14e2bb2; ISOLATED domains.md)
Q-005 — CRM owns commercial account identity (Client Account, Brand, Service Agreement,
Contact); Client Success owns the active post-conversion relationship lifecycle. Boundary:
CRM does not own relationship health; Client Success does not own commercial identity.
G-05 simultaneously: "Final Brand placement" language corrected to "Brand aggregate placement"
(Brand is already placed — DEC-036; only aggregate placement remains draft).

### DEC-044 (COMMIT 3 — f6f9f78; ISOLATED domains.md)
Q-022 — Knowledge domain owns PromptTemplate: a reusable structured AI prompt artifact
with version history. Extend test passes against Knowledge Artifact / Knowledge Version shape.
AI Operations does not own prompt versioning.

### DEC-045 (COMMIT 4 — 64c34e7; ISOLATED domains.md)
Q-004 — Client Brain partitioned **per Brand** (primary unit) with a **per-Client
aggregation view** for cross-brand context. Ownership remains Knowledge (DEC-027). The
per-Client aggregation view is a derived / read-only projection — not a separate partition.

### DEC-046 (COMMIT 5 — 22a94d6)
Q-020 — Access-status / connection-health is a **Phase 4 Channel Model operational attribute**
(4th channel-level property). Distinct from Phase 1 Governance policy-enabled/disabled.
Read by Dual-Path / Manual-Fallback routing (DEC-037; Phase 6) per-channel-binding,
per-client-context.

### DEC-047 (COMMIT 6 — d45eb1a)
Q-016 — Client persona sees the **Performance & Analytics View**, scoped to own-engagement
data only. View Inventory `‡` resolved to `Scoped (own-engagement)`. DEC-022 view
membership extended. Agency-level aggregated analytics remain outside Client scope.

### DEC-048 (COMMIT 6 — d45eb1a)
Q-017 — Workflows are **fixed-flow at T1**. Phase 6 canon flows authoritative as-written.
System Administrator views execution state via Phase 2 Agent & Workflow Monitor (Full; no new
surface). Visual workflow editing deferred to **v2** as multi-phase gated feature
(Phase 2 / 4 / 6 / 7 — own gate then).

---

## Findings

### FIND-038 (COMMIT 4 context)
FIND-032 shift-sweep after DEC-043/044/045 domains.md edits: net line shifts (+4 at ~766,
+4 at ~1519, +1 at ~1265, +1 at ~1294, -1 at ~660) produced 51+ stale cites in memory.md.
Corrected via Python reverse-lexicographic replacement script + targeted manual fixes for
collision edge cases.

### FIND-039 (COMMIT 6 context)
Stale-token sweep for Q-016/Q-017 across living docs surfaced 4 additional locations:
architecture.md carried-open list, infrastructure.md carried-open list,
system-architecture-blueprint.md Open/deferred block, blueprint.md Carried/not-owned block.
All 4 updated, including domains.md:1941 → :1946 cite correction in blueprint.md.

---

## Open Questions (remaining)

The following are explicitly carried and must not be touched:
- **Q-003** (Brand aggregate placement) — distinct from Brand entity placement (DEC-036).
  Brand entity is placed; only aggregate placement remains open.
- **Q-006** (Service Agreement aggregate boundary / Ticket aggregate boundary) — its own
  gated Phase-1 decision.
- **Q-007** (deferred — intentionally carried).
- **Q-024** (Ticket ↔ Escalation Case lifecycle coupling — two-entity vs single-lifecycle).
  Cross-references `domains.md:1720`.
- Insight→durable-knowledge threshold (R-027 set; `domains.md:1946`).
- Phase-1 entity reopenings still pending: Campaign, Ad-Account, Schedule, Consent — each
  its own gated decision.

---

## Assumptions
None new. Pre-existing assumptions in canon files carried forward unchanged.

---

## Risks
- R-028 (reference-altitude discipline) — held throughout. No new Phase 8 or Phase 9
  architecture was authored in content-fix commits. No domain truth authored in experience
  or architecture files.
- FIND-032 shift-sweep is inherently manual and complex. cite-correction Python script
  + PART A verifier used; all key cites byte-verified with sed/grep.

---

## Next Focus

**Phase 10 — Claude Code Architecture is now unblocked.**

The reconciliation sweep has cleared all 7 pending open questions. The architecture canon
is now at GREEN coherence — G-01–G-05 content fixes landed, DEC-042–DEC-048 minted,
open-questions.md reflects the resolved state.

Remaining open items (Q-003/Q-006/Q-007/Q-024, 4 Phase-1 reopenings, 3 Phase-4 deferred
sub-items, insight threshold, Agent Supervision/Observability deferred slot) are all
explicitly flagged and do not block Phase 10.

Phase 10 question-gate is the recommended next step: scope Claude Code Architecture and
define the Phase 10 sub-items before any content is written.
