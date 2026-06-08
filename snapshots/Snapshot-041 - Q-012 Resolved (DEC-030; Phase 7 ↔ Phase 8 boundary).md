# Snapshot-041 - Q-012 Resolved (DEC-030; Phase 7 ↔ Phase 8 boundary)

## Current Phase
Phase 11 Claude Code Operating System — operational
Phase 6 Workflow Design — complete at DEC-028's scope (DEC-029 / Snapshot-040), unchanged
Phase 5 Knowledge & Memory — first write complete (Snapshot-035), unchanged
Phase 4 Extensibility Model — first write complete (Snapshot-030), unchanged
Phase 3 Capability Map — written (Snapshot-025), unchanged
Phase 2 Experience Architecture — complete (7-of-7, Snapshot-033), unchanged
Phase 1 Domain Discovery — Q-001 resolved (DEC-027), unchanged
**Open thread (new): the Step-2 full Phase 7 question-gate (G-1…G-7) — scoping only,
no Phase-7 content before its scope DEC lands.**

## Current Topic
The DEC-030 close-out: recording the **Q-012 resolution** (the Phase 7 ↔ Phase 8
boundary) and flipping the living docs to match. DEC-030 itself landed in a prior,
isolated commit (`fdbe0fe`); this snapshot **records** the resolution at reference
altitude and closes the same-commit living-doc group (open-questions.md +
Current-State.md + this snapshot). It authors no architecture and no Phase-7/8 content.

## Status
DEC-030 is written and verified on origin/main (commit `fdbe0fe`). This close-out
groups three living-doc updates in one commit per standing same-commit discipline:
`open-questions.md` (Q-012 → Resolved), `Current-State.md` (Q-012 resolved; Next Focus
leads with the Step-2 Phase 7 gate), and this snapshot. Working tree otherwise carries
only the untracked `Phase-7-Grounding-Brief.md` (working aid, intentionally not canon).

**The resolution (DEC-030):**
- **Phase 7 = the substantive cross-cutting concern-views** (seven lenses,
  `Faraz-OS-Canon.md:132-138`); **Phase 8 = the layered assembly** (seven layers,
  `Faraz-OS-Canon.md:141-147`, incl. Experience + AI `[ADDED]` at `:146-147`).
- **One-way dependency:** Phase 8 assembles to satisfy Phase 7; Phase 7 is
  scoped/written first.
- **Not 1:1:** the seven P7 views and seven P8 layers do not map one-to-one; P8
  assembles blocks owned across phases (Domains → P1, Capabilities → P3, Plugins →
  P4, Experience → P2; Core / Infrastructure / AI assembled from multiple).
- **Boundary test + disambiguation-not-rename convention** recorded verbatim, with the
  **AI Architecture (P7) vs AI Layer (P8)** worked example as the highest-collision
  seam — the seam where Q-013 and the agent/subagent-identity flag sit, both carried.
- **Scope guard:** DEC-030 draws one boundary only; it authors no Phase-7/8 content and
  does not open Phase 7 scope (that is the Step-2 gate).

**Anchor-fix discipline note (FIND-033/034 class, no new finding):** two citation
anchors were corrected during the byte-read before landing — (i) the Experience + AI
`[ADDED]` layers are at `Faraz-OS-Canon.md:146-147` (the reviewer's earlier `:145-146`
was off by one; `:145` is Infrastructure Layer); (ii) the Q-013 quote was re-anchored
from `open-questions.md:288` (the `### Q-013` header) to `:292-293` (the quoted lines).
Both were content-verified at their anchors and a deterministic stale-token sweep was
re-run clean after the fix. This is the existing discipline applied, not a new finding.

---

## Document Updates

### DOC-114
`decisions.md` — **DEC-030 added** (commit `fdbe0fe`): Phase 7 ↔ Phase 8 boundary scope
distinction; resolves Q-012 (only); boundary test + disambiguation convention + AI/AI
worked example; carried set verbatim; authors no Phase-7/8 content.

### DOC-115
`open-questions.md` — **Q-012 → Resolved** (this close-out commit): mirrors the Q-015
closure pattern (Resolved block citing DEC-030; "Why it mattered" in past tense);
carried set recorded; KNI-11 → Done.

### DOC-116
`Current-State.md` — Q-012 marked resolved in the Architecture Position narrative and
the trailing open-questions list; Current Next Focus rewritten to lead with the Step-2
full Phase 7 question-gate (this close-out commit).

### DOC-117
`Current-State.md` / `snapshots/` — Snapshot-041 recorded as the Q-012 resolution
record (this close-out).

---

## Decisions
No new decision. **DEC-030 is recorded, not re-decided** — it landed in commit
`fdbe0fe` and is referenced here at reference altitude. (DEC-029 and DEC-028 untouched —
immutable.)

---

## Findings
No new finding. The two anchor corrections (`:146-147`, `:288` → `:292-293`) were
handled under the existing FIND-033/034 citation discipline (content-verify at anchor
+ deterministic stale-token sweep before the verifier pass). Nothing new to record.

---

## Open Questions
- **Q-012 — RESOLVED (DEC-030).** Phase 7 ↔ Phase 8 boundary drawn; KNI-11 → Done.
- **Carried, unchanged (not resolved by DEC-030):** Q-013 (AI / agent-surface home),
  the agent/subagent-identity Phase-7 flag, the inversion guard, and Feature-Modules /
  module-mounting — all deferred to the Step-2 Phase 7 question-gate or their owning
  passes; Q-017 (system-administrator visual workflow management, multi-phase); Q-003,
  Q-004, the inherited threshold (`domains.md:1918`) — R-027 set; Q-016. Q-001, Q-011,
  Q-014, Q-015 remain resolved.

---

## Assumptions
- Assumption: DEC-030 resolves the boundary only; no Phase-7/8 content is authored by
  the decision or this close-out.
- Assumption: the Step-2 Phase 7 question-gate is a separate proposal, opened on the
  next explicit go — not automatically by this resolution.

---

## Risks

### R-024 (carried forward — narrowed)
The Phase 7 ↔ Phase 8 boundary risk is addressed at the **boundary-scoping** level by
DEC-030; the residual (premature finalization of either phase's internal scope) is now
carried by the Step-2 Phase 7 gate, not by any Phase-7/8 content.

### R-027 (carried forward, active — held)
DEC-030 resolves no inherited Phase-1 question; the R-027 set is referenced, carried.

### R-028 (carried forward, active — held)
Reference altitude preserved; the resolution, the worked example, and the
disambiguation convention are reference-altitude, no architecture authored. The R-028
**inversion guard** (the Phase-7 flip: architects *how* vs re-defines *what*) is carried
to the Step-2 gate.

### R-029 / R-025 / R-026 (carried forward, active)
Unchanged. R-025 close-out discipline applied (anchor-content + deterministic sweep;
two anchors corrected before landing).

---

## Next Focus
1. **Step-2 full Phase 7 question-gate (G-1…G-7)** — the open thread. A full scope gate
   (as in DEC-024/025/027/028), fed by the Phase-7 Grounding Brief, opened as its own
   proposal on the next explicit go. It must address: the inversion guard (R-028 flip),
   the Feature-Modules / module-mounting dependency (reference vs un-defer is a gate
   call), the agent/subagent-identity flag + Q-013 (the AI Architecture seam), and the
   candidate non-goals. **No Phase-7 content before that scope DEC lands.**
2. **Q-017** — system-administrator visual workflow viewing + management: its own gated,
   multi-phase decision; any Phase-6 increment is marked-future.
3. Other fresh, gated threads: the four Phase-4 deferred sub-items; Phase 5 Asset
   Intelligence un-defer.
4. `Phase-7-Grounding-Brief.md` stays untracked (working aid, not canon); decide
   deletion/archive once the Phase 7 scope DEC lands.
