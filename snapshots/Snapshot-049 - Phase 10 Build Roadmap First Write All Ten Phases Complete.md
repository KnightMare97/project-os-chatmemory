# Snapshot-049 — Phase 10 Build Roadmap: First Write Complete, All Ten Phases Have First-Write Entries

## Current Phase
Phase 10 Build Roadmap (first write).

## Current Topic
Writing `roadmap.md` (Phase 10 deliverable file): dependency-ordered Build
Roadmap from Foundation through Future, on the six-field skeleton. DEC-049
mints the Phase 10 scope gate (six rulings).

## Status
COMPLETE. `roadmap.md` first write committed and pushed. DEC-049 minted.
Verified on `origin/main` at SHA `193790e`.

---

## Document Updates

### `Faraz-OS-Canon/roadmap.md` (NEW FILE — commit `193790e`)
- Phase 10 Build Roadmap first write: 589 lines.
- Top-level structure: MVP / V1 / V2 / Future (matching `Faraz-OS-Canon.md:162-165`).
- MVP nested sub-stages: Foundation, Core Layer, T1 Launch.
- All Phase-9 Build-layer flags from `infrastructure.md` assigned to their
  Foundation stage build-layer decisions table.
- Q-006 and Q-024 as named explicit pre-build gates before CRM / Client
  Success domain schema writes (Gate A and Gate B).
- Bilingual / IR-sensitivity (Farsi/English bilingual + Dual-Path / Manual
  Fallback, DEC-037) as first-class T1 build constraints — five explicit
  constraints enumerated; Phase 11 must validate before writing Content or
  Publishing schema.
- Q-003 sequenced as V1 finalization gate (not T1 Launch blocker).
- T3 entities (Campaign / Ad-Account / Schedule / Consent) → V2
  gated-but-intended; each its own Phase-1 gate before schema write.
- V2 late deferred features: Agent Supervision (AI Layer deferred slot 2),
  visual workflow editing (DEC-048).
- Open and Deferred Items section carries Q-003 / Q-006 / Q-007 / Q-024,
  insight threshold, T3 entity reopenings — none resolved.
- Critical-path risks called out: schema-per-client migration runner
  (highest risk), Firebase JWT → `search_path` middleware (second-highest).
- Status: first-write-complete milestone (not phase-complete declaration;
  consistent with Phase-2 / 6 / 7 / 8 / 9 precedent).

### `decisions.md` (commit `193790e`)
- DEC-049 added: Phase 10 scope gate — six rulings.

---

## Decisions

### DEC-049 (COMMIT `193790e`)
Phase 10 Build Roadmap scope gate — six rulings: (1) MVP = all 7 workflows +
T1 domains; V1 = same system production-ready; MVP→V1 as contiguous showcase
target. (2) T3 entities → V2 gated. (3) Q-006 / Q-024 as explicit pre-build
gates. (4) Bilingual / IR-sensitivity (Farsi/English + Dual-Path) as
first-class T1 build constraints. (5) Q-003 → V1 finalization gate, not T1
blocker. (6) Phase 10 deliverable file is `Faraz-OS-Canon/roadmap.md`.

---

## Findings

### FIND-040 (COMMIT `193790e` context)
All 25 line-number cites introduced in `roadmap.md` mechanically verified
with `sed`/`grep` raw bytes in the same session before commit (PART A).
No same-session line-shift risk: `roadmap.md` is a new file; no existing
living-doc cites were shifted by this write. PART B semantic red-team
passed: altitude correct, no carried-open item resolved, wording matches
all five Ali rulings, R-028 held.

---

## Open Questions (remaining)

The following are explicitly carried and must not be touched without a
separate gated decision:
- **Q-003** (Brand aggregate placement) — Phase-1 gate; should resolve before
  V1 schema finalization. Distinct from Brand entity placement (DEC-036, resolved).
- **Q-006** (Service Agreement / Engagement Scope aggregate boundary) — Phase-1
  gate; must resolve before CRM and Service Delivery schema writes (Gate A in
  `roadmap.md`).
- **Q-007** (Engagement Scope assignment artifact) — intentionally deferred.
- **Q-024** (Ticket ↔ Escalation Case lifecycle coupling) — Phase-1 gate; must
  resolve before Client Success bounded-context schema write (Gate B in
  `roadmap.md`); cross-references `domains.md:1720`.
- Insight → durable-knowledge threshold (`domains.md:1946`, R-027 set) —
  Phase-1 truth pending.
- T3 Phase-1 entity reopenings: Campaign, Ad-Account, Schedule, Consent —
  V2 slots; each its own Phase-1 gate before domain schema write.

---

## Assumptions
None new. Pre-existing assumptions in canon files carried forward unchanged.

---

## Risks
- R-028 (reference-altitude discipline) — held throughout. `roadmap.md`
  authors no new architecture, resolves no Phase-1 questions, and makes no
  domain truth claims.

---

## Next Focus

**All ten architecture content phases (Phases 1–10) now have first-write
entries.**

The architecture canon is complete as a first-write body. Recommended next
steps when Ali is ready:

1. **Q-006 Phase-1 gate** — Service Agreement / Engagement Scope aggregate
   boundary; mandatory before CRM domain schema can be written in Phase 11.
2. **Q-024 Phase-1 gate** — Ticket ↔ Escalation Case lifecycle coupling;
   mandatory before Client Success domain schema can be written in Phase 11.
3. **Phase 11 Claude Code Operating System** — `claude-operating-system.md`,
   the final phase file, governing how Claude Code execution operates against
   this canon.
4. **Q-003 Phase-1 gate** — Brand aggregate placement; preferably before V1
   schema finalization.

Each of items 1–4 is a separate gated session. Items 1 and 2 are the
closest to the build path and should be sequenced before Phase 11 content
is written.
