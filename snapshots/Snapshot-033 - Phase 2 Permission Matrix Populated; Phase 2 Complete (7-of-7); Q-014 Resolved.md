# Snapshot-033 - Phase 2 Permission Matrix Populated; Phase 2 Complete (7-of-7); Q-014 Resolved

## Current Phase
Phase 11 Claude Code Operating System — operational
Phase 2 Experience Architecture — **complete (7-of-7)**; the Permission Matrix is
populated (landing (ii))
Phase 1 Domain Discovery — Governance authorization slice accepted (DEC-026 /
Snapshot-032); the rest of Governance Draft v1 stays draft
Phase 4 Extensibility Model — first write complete (Snapshot-030), unchanged
Phase 3 Capability Map — written (Snapshot-025), unchanged

## Current Topic
Landing (ii) of the Q-014 thread: populating the Phase 2 Permission Matrix as the
read-only projection of the landed DEC-026 authorization rules through the
surface↔resource mapping. This completes Phase 2 (7-of-7) and fully resolves Q-014.
This snapshot records the close-out at reference altitude.

## Status
The Permission Matrix is populated in `experience-architecture.md` (commit
`baf5314`, on top of `2f1bed1`), verified on origin/main; working tree clean. The
`## Permission Matrix` section's "Scope of definition" subsection was replaced by:
the surface↔resource mapping, the surface×persona matrix, the portal projection,
the seven-view projection, and the multi-role resolution (G-5). The matrix is a
read-only projection and **authors no rules** (DEC-019 / FIND-022); cells are
{Full / Scoped / —} (G-6); columns are surfaces / portals / views, never
capabilities.

**Acceptance criterion (DEC-026 G-3) — decisive use, PASSED.** An independent
verifier ran the **full** cell-by-cell derivation: all 80 surface×persona cells
derived from the DEC-026 rules + the mapping reproduce the ratified DEC-020 reuse
table with **zero divergence** (recorded as FIND-030). The five primary-persona
subject-bound cells (Client surfaces 9–12; Contractor surface 13) derive to
"Full (primary persona)" under the G-3 precision note, with `own-engagement` held
at the rule level.

**Q-014 fully resolved:** Phase-1 half by DEC-026 (the Governance authorization
rules are concrete); Phase-2 half by this matrix population. The open-questions.md
Q-014 entry is marked resolved and closed.

**Q-016 registered (new):** the one flagged Phase-2 view-membership nuance — the
Client × Performance & Analytics View, where the View Inventory and the Client
portal table disagree — surfaced by the matrix view projection, flagged `‡`, not
resolved (its resolution reopens DEC-022 view membership). It does not affect the
7-of-7 surface projection.

---

## Document Updates

### DOC-075
`Faraz-OS-Canon/experience-architecture.md` — Permission Matrix populated (commit
`baf5314`): the "Scope of definition" subsection replaced by the surface↔resource
mapping, the populated surface×persona matrix, portal projection, view projection,
multi-role resolution, and the status note. Additive in effect (the only deletion
is the superseded "does not populate … later refinement" subsection).

### DOC-076
`Current-State.md` — Phase 2 sub-item status updated to **Populated (7)** /
**7-of-7 complete** (Permission Matrix added); Next Focus item 2 updated to
record Phase 2 complete and Q-014 resolved; the Snapshot-026 audit note's count
scoped to 7-of-7.

### DOC-077
`open-questions.md` — **Q-014 marked Resolved/Closed** (DEC-026 + matrix
population); **Q-016 registered** (the Client × Performance & Analytics View
nuance).

### DOC-078
`findings.md` — **FIND-030 backfilled** (same-commit) recording the zero-divergence
acceptance-criterion result.

---

## Decisions
No new decision. This executes the already-committed DEC-026 (Active) and honors
DEC-019 / FIND-022 (Phase 2 authors no rules). No DEC changed or superseded.

---

## Findings

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

---

## Open Questions
- **Q-014 — RESOLVED** (DEC-026 + this matrix population); closed in
  open-questions.md.
- **Q-016 — new, open:** Client × Performance & Analytics View membership (View
  Inventory vs Client portal table disagree); resolution reopens DEC-022 view
  membership; tracked in open-questions.md, flagged `‡` in the matrix.
- Carried, untouched: Q-001 / Q-004 (Client Brain ownership); Q-015 (KNI-21);
  the inherited Intelligence-Draft-v1 Open Questions (`domains.md:1915-1919`).

---

## Assumptions
- Assumption: the matrix is a faithful read-only projection; it authors no rule,
  condition, or verb (only DEC-026's are used).
- Assumption: the zero-divergence derivation (FIND-030) reflects the committed
  rules + mapping as read this session; the acceptance criterion is satisfied.
- Assumption: Q-016 is a Phase-2 view-membership nuance only; the surface-level
  Reports & Analytics exposure is unaffected and reproduces DEC-020.

---

## Risks

### R-029 (carried forward, active)
Authorization-slice bleed (from DEC-026). Not exercised by this read-only
projection (which added no rule), but remains the watch for any later Governance
work. Keep active.

### R-028 / R-027 (carried forward, active — held)
Reference-altitude overcommitment / no inherited Phase 1 question resolved. Held:
the matrix references DEC-026 rules and Phase-2 structures at altitude; Q-016 is
registered, not resolved; Client Brain access-only (ownership Q-001/Q-004
untouched).

### R-026 (carried forward, active)
`workflows/sync-protocol.md` references Linear MCP tools by logical name; update
the Tooling section if names change.

### R-025 (carried forward, active)
Close-out applied by discipline under the standing reduced-check-in mode: the
matrix had a content read + a full-derivation independent verifier pass before
landing; this record close-out follows, with same-commit tracker backfill
(open-questions Q-014/Q-016; findings FIND-030).

---

## Next Focus
1. **Phase 2 Experience Architecture is complete (7-of-7).** No unblocked Phase 2
   content remains. Marked-future / parked carry-forwards: Navigation Model
   sub-detail (landing-surface, notification routing, deep-linking); the three
   Operating-Surface flags (Client Profile, System Configuration / Settings,
   Onboarding); the Future Personas placeholder.
2. **Q-016** (Client × Performance & Analytics View membership) — a small DEC
   reopening DEC-022 view membership when scheduled. Not blocking.
3. The rest of `Governance Draft v1` remains draft; concretizing any further
   Governance area is its own future gated decision (R-029 watch).
4. Candidate next major threads (all fresh, gated): the four Phase 4 deferred
   sub-items (Versioning & Compatibility, External Integrations, Feature Modules,
   Future Domains); Phase 5 Knowledge & Memory; Phase 6 Workflow Design (which
   will cross-check the selection-vs-sequence test and the approve-verb /
   approval-gate boundary).
5. Linear: **KNI-14 → Done** (matrix populated); KNI-16 already Done (Snapshot-032).
