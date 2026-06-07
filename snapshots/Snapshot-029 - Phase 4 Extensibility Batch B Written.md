# Snapshot-029 - Phase 4 Extensibility Batch B Written

## Current Phase
Phase 11 Claude Code Operating System — operational
Phase 4 Extensibility Model — Batch B of `extensibility.md` written this session
(five of eight in-scope entries now written); Batch C pending
Phase 3 Capability Map — written (Snapshot-025), unchanged
Phase 2 Experience Architecture — 5-of-7 populated (Snapshot-026), unchanged;
Channel Behaviors (KNI-18) remains unblockable

## Current Topic
Execution of Batch B of the DEC-025-approved batched-write plan for
`Faraz-OS-Canon/extensibility.md` (KNI-23): the Extension Contracts, Permission,
and Plugin Model entries, plus the Status-section update. This snapshot records
the write at reference altitude; it re-decides nothing — DEC-025 is the decision
of record.

## Status
Batch B is committed (commit `1b148d4`, on top of `80f47af`). Working tree clean.
`extensibility.md` now carries five of the eight in-scope entries: Provider Model,
Channel Model (Batch A) and Extension Contracts, Permission, Plugin Model
(Batch B).

Batch B content:
- **Extension Contracts** — formalizes the contract surface that the Batch A
  Provider/Channel entries referenced at altitude. Names the interaction modes
  (APIs, events, permissions, schemas, versioned interfaces — Philosophy #4) **at
  altitude**; does not specify concrete interfaces/schemas (contract-altitude rule
  held); contract evolution deferred to Versioning & Compatibility.
- **Permission** — states **only** Phase 4's grant altitude (extension / plugin /
  provider capability grants via contracts) and references DEC-019 / FIND-022 for
  the full three-altitude triad; it does not restate the triad, and the ↔ Phase 1
  Governance / ↔ Phase 2 boundary is drawn in the Boundary-notes field (the
  correct placement, confirmed at the content read). No concrete Governance policy
  enumerated (grant-altitude rule / R-028 held). Q-014 referenced, not resolved.
- **Plugin Model** — the packaging / attachment axis (Philosophy #5), distinct
  from Provider Model and Channel Model (what is attached). Selection-vs-sequence
  test applied in the ↔ Phase 6 boundary note (plugin makes capabilities/providers
  available, order-free; ordering is Phase 6).

Each entry is on the six-field skeleton; the six Philosophy-#8 governance
categories are named verbatim where touched; citations were checked for
wrap-around precision. One content-read trim was applied before landing: an
unsourced characterization ("the canonical config-time end of the attribute") was
removed from Plugin Model's Runtime-vs-Config-Time field. An independent verifier
passed the batch (six-field skeleton; the four operational rules; the hybrid grant
rule; citation accuracy; R-027/R-028; Batch-A consistency).

Batch B resolves no Phase 1 open question and writes no content beyond its scope.

---

## Document Updates

### DOC-065
`Faraz-OS-Canon/extensibility.md` — Batch B written (commit `1b148d4`): the
Extension Contracts, Permission, and Plugin Model entries inserted after Channel
Model, and the Status section updated to "Batches A and B landed; Batch C
pending."

### DOC-066
`Current-State.md` refreshed in this close-out: the Phase 4 block now records
Batches A and B written (five entries) with only Batch C remaining, and Next
Focus points at Batch C (AI Model Routing carrying the heaviest
selection-vs-sequence work). Additive/minimal edits.

---

## Decisions
No new decision. Batch B executes the already-committed DEC-025 (Active); it is
referenced here, not re-decided. No DEC changed or superseded.

---

## Findings
No new finding.

---

## Open Questions
No open question is resolved or newly opened. Carried, referenced not resolved:
- Registered Phase 4 open flags: agent/subagent identity (likely Phase 7);
  safety-controls vocabulary (`extensibility-philosophy.md:30` vs
  `domains.md:2189/2226/2262`); the optional philosophy-#7 annotation; the
  repo-wide inherited-question citation drift (FIND-028).
- Inherited Phase 1 questions: `domains.md:1915-1916`, `:1917`, `:1918-1919`, and
  Q-014 (Permission Matrix ↔ Governance) — the Permission entry references Q-014
  and does not resolve it.
- Q-001 / Q-004 (Client Brain) — open, untouched. Q-015 (KNI-21) — open.

---

## Assumptions
- Assumption: Batch B is faithful execution of DEC-025; no Phase 1 truth,
  ownership, or boundary is changed, and no open question is resolved.
- Assumption: the Extension Contracts entry stays at altitude (names the contract
  machinery, does not specify it), consistent with the Batch A forward-reference.
- Assumption: the Permission entry's hybrid-rule compliance and the
  Boundary-notes placement of ↔P1/↔P2 reflect the content read as accepted.

---

## Risks

### R-028 (carried forward, active — held)
Reference-altitude overcommitment. Batch B exercised this hardest at the
Permission entry: the triad is referenced (DEC-019/FIND-022), not restated; no
concrete Governance policy enumerated; Governance touchpoints name only the six
Philosophy-#8 categories at altitude. Held. Keep active for Batch C.

### R-027 (carried forward, active — held)
No inherited Phase 1 question was resolved or narrowed; Q-014 and the inherited
domains.md questions are referenced as open. Keep active for Batch C.

### R-023 (carried forward, active)
Phase 4 ↔ Phase 6 altitude drift (routing vs orchestration). Batch B applied the
selection-vs-sequence test in the Plugin Model boundary note; the sharpest
exercise is the Batch C AI Model Routing entry. Keep active.

### R-026 (carried forward, active)
`workflows/sync-protocol.md` references Linear MCP tools by logical name. Update
the Tooling section if tool names change.

### R-025 (carried forward, active)
Close-out applied by discipline under the standing reduced-check-in mode: Batch B
had one content read before landing; this record close-out follows an independent
verifier pass.

---

## Next Focus
1. **Batch C** — Model, AI Model Routing, and the Runtime-vs-Config-Time framing
   section. The **AI Model Routing** entry carries the heaviest
   selection-vs-sequence work; its boundary language should lean on the test
   verbatim (order-free selection = Phase 4; orchestration = Phase 6). The
   **Runtime-vs-Config-Time framing section** defines the cross-cutting attribute
   and does not enumerate extensions (OQ-K). Model and AI Model Routing stay two
   distinct entries (OQ-E).
2. **KNI-18 readiness** unchanged: the Channel Model exists and meets its
   acceptance test; reopening KNI-18 is a gated structural Linear change.
3. Carry the registered open flags and inherited Phase 1 questions forward
   unresolved through Batch C.
4. KNI-23 stays In Progress until Batch C lands; on completion, the Phase 4 first
   write (eight in-scope sub-items) is done and KNI-23 can move to Done (a gated
   structural Linear change).
