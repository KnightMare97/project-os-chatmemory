# Snapshot-035 - Phase 5 Knowledge & Memory First Write Complete (memory.md; KNI-25)

## Current Phase
Phase 11 Claude Code Operating System — operational
Phase 5 Knowledge & Memory Architecture — **first write complete**; `memory.md`
written (landing (ii) of DEC-027)
Phase 1 Domain Discovery — Q-001 resolved (DEC-027 / Snapshot-034), unchanged
Phase 4 Extensibility Model — first write complete (Snapshot-030), unchanged
Phase 3 Capability Map — written (Snapshot-025), unchanged
Phase 2 Experience Architecture — complete (7-of-7, Snapshot-033), unchanged

## Current Topic
Landing (ii) of DEC-027: the first write of `Faraz-OS-Canon/memory.md` from the
approved Phase 5 scope. Six firm entries on the DEC-027 six-field skeleton, plus the
Asset Intelligence deferred stub. This snapshot records the close-out at reference
altitude.

## Status
`Faraz-OS-Canon/memory.md` is written and verified on origin/main (commit
`89f5034`, on top of `d958b70`); working tree clean. The file defines, for each
memory/knowledge structure, the Phase-5 logical contract: Definition · Owner
(Phase-1 reference) · Contents · Lifecycle/durability · Retrieval & update contract ·
Boundary notes.

**Six firm entries:** Client Brain, Agency Brain, Knowledge Base, Decision Logs,
Learnings, Context Retrieval. **Asset Intelligence** is a deferred-and-flagged stub
(no content authored). Every Owner field is a Phase-1 reference — Phase 5 architects,
never re-owns: Knowledge owns all six (`domains.md:1253-1263`; Client Brain via
DEC-027 `:1263`).

**Discipline holds confirmed by independent verifier (content checks PASS):**
- **Partition-agnostic** (Q-004): no Client Brain line implies per-Client, per-Brand,
  or both; partitioning flagged open.
- **R-027:** the Learnings entry references the insight→durable-knowledge threshold
  (`domains.md:1918`) at altitude and defines no threshold and no mechanism.
- **R-028:** other phases referenced, never re-owned; authorization defers to DEC-026,
  physical retrieval/storage to Phase 7.
- **No-invention:** every content category and lifecycle stage traces to cited canon.

**Citation correction (see FIND-032):** the first verifier pass false-passed several
`domains.md` citations that had shifted under the same-session DEC-027 edits. All
~25 citations were re-derived from post-landing ground truth and confirmed by a
deterministic stale-token sweep before landing. Adopted as a standing operating rule.

---

## Document Updates

### DOC-086
`Faraz-OS-Canon/memory.md` — **created** (commit `89f5034`): the Phase 5 Knowledge &
Memory canon file. Purpose, altitude, governing ownership; six firm entries on the
six-field skeleton; Asset Intelligence deferred stub; non-goals; the closed
seven-boundary set; open/inherited flags.

### DOC-087
`findings.md` — **FIND-032 backfilled** (same close-out): LLM verifier false-passing
shifted-range citations; corrective named (post-landing ground-truth re-derivation +
deterministic stale-token sweep).

### DOC-088
`Current-State.md` — Phase 5 updated from "scoped; first write pending" to **first
write complete**; Next Focus updated.

---

## Decisions
No new decision. This executes the already-committed DEC-027 (Active), landing (ii).
No DEC changed or superseded.

---

## Findings

### FIND-032 (new)
An LLM verification pass can false-pass line-number citations into a file edited
earlier in the same session (the DEC-027 same-session edits shifted `domains.md`
lines; the verifier passed `:1254-1257` / `:2746-2752` / `:1262`, all wrong).
Sibling to FIND-031 (grep-completeness for reconciliation sweeps); the distinct
lesson is that LLM citation-checking is unreliable across shifted ranges.
**Corrective (standing rule):** after any same-session canon landing, re-derive all
draft citations from post-landing ground truth and run a deterministic stale-token
sweep before the verifier pass. See `findings.md`.

---

## Open Questions
- **Q-004 — open (carried):** Client Brain partitioning (per Client / per Brand /
  both); entangled with Q-003 Brand placement; the `memory.md` Client Brain entry is
  written partition-agnostic.
- **Q-003 — open (untouched):** final Brand placement.
- Carried, untouched: Q-015 (KNI-21); Q-016 (Client × Performance & Analytics View);
  the inherited Intelligence-Draft-v1 Open Questions (`domains.md:1916-1921`, incl.
  the insight→durable-knowledge threshold — G-7 carried, R-027).

## In-canon open items surfaced by the write (not new questions; existing canon flags)
- Client Brain Aggregate vs Memory Object — draft (`domains.md:1322-1333`).
- Approval-before-durable and Decision Log / Learning Record aggregate granularity —
  open in canon (`domains.md:1448-1452`).

---

## Assumptions
- Assumption: every `memory.md` content category and lifecycle stage is traceable to
  cited canon (no invention); verifier-confirmed.
- Assumption: the six-field logical contract sits at Phase-5 altitude — no physical
  storage/indexing/schema authored (that is Phase 7), no authorization rule authored
  (that is DEC-026).
- Assumption: the citation set is byte-accurate against post-landing `domains.md`
  (deterministic sweep + ground-truth re-derivation).

---

## Risks

### R-027 (carried forward, active — held)
No inherited Phase-1 question resolved: the Learnings entry references the
insight→durable-knowledge threshold at altitude, pending; defines nothing.

### R-028 (carried forward, active — held)
Reference altitude: `memory.md` references P1 ownership, P2 surfaces, P3
capabilities, P4, P6, P7, and DEC-026 without reinterpreting or re-owning them.

### R-029 (carried forward, active)
Authorization-slice bleed (from DEC-026). Untouched by this write (access authorization
referenced, not authored). Keep active.

### R-025 / R-026 (carried forward, active)
R-025 close-out discipline applied (content read + independent verifier + deterministic
stale-token sweep before landing; same-commit tracker backfill). R-026 sync-protocol
tooling-name watch unchanged.

---

## Next Focus
1. **Phase 5 carry-forwards** (none blocking): Asset Intelligence un-defer (its own
   gated decision); Client Brain Aggregate-vs-Memory-Object and the approval-before-
   durable / aggregate-granularity canon flags resolve when their owning work is
   scheduled.
2. **Q-004** (Client Brain partitioning) — resolves with Q-003 Brand placement; its
   own gated decision. Not blocking.
3. Candidate next major threads (all fresh, gated): **Phase 6 Workflow Design** (will
   exercise the selection-vs-sequence test, the Learn → Memory Update sequence against
   this memory contract, and the approve-verb / approval-gate boundary); the four
   Phase-4 deferred sub-items (Versioning & Compatibility, External Integrations,
   Feature Modules, Future Domains); Phase 5 Asset Intelligence un-defer.
4. Normalization backlog: `CLAUDE.md` stale Client-Brain-ownership draft example
   (gated procedure edit); plus the standing items in the normalization-pass backlog.
5. Linear: **KNI-25 → Done** (memory.md written).
