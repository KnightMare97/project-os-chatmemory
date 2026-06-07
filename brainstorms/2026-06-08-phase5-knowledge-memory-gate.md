# Phase 5 Knowledge & Memory — Question-Gate Capture (2026-06-08)

Inline grill-me question-gate for Phase 5 Knowledge & Memory (`memory.md`),
closed in DEC-027. This file captures the gate reasoning; `decisions.md` DEC-027
is the canonical record.

## Gate frame (G-1 → G-5, autonomous-structural)

- **G-1 Definition & altitude.** `memory.md` defines the logical architecture of
  memory/knowledge: per sub-item — what it is, owner (Phase-1 ref), contents
  (category level), lifecycle/durability, retrieval + update contract. Vocabulary
  reuses Memory Object / Shared Service Artifact / Knowledge Artifact / Retrieval
  Context. Logical contract only; physical storage/indexing/schema/AI-retrieval =
  Phase 7.
- **G-2 Closed seven-boundary set.** ↔ P1 domain truth (Knowledge owns Agency
  Brain / KB / Decision Logs / learnings / retrieval — Phase 5 architects, doesn't
  re-own; `domains.md:1253-1261`); ↔ P1 Governance (DEC-026 owns access; authors
  none); ↔ P2 (surfaces render, name-only); ↔ P3 (capabilities produce "may become
  durable knowledge"; `capabilities.md:61,104,148,164`); ↔ P4 (consumer of memory
  contracts; `extensibility.md:446`); ↔ P6 (Learn → Memory Update sequence;
  `Faraz-OS-Canon.md:125`); ↔ P7 (storage/wiring — OUT).
- **G-3 In-scope.** Six firm (Client Brain, Agency Brain, Knowledge Base, Decision
  Logs, Learnings, Context Retrieval); Asset Intelligence `[ADDED]` = deferred-
  flagged stub.
- **G-4 Six-field skeleton.** Definition · Owner (P1 ref) · Contents · Lifecycle/
  durability · Retrieval & update contract (authz → DEC-026; physical → P7) ·
  Boundary notes.
- **G-5 Non-goals.** No P7 storage/wiring; no P1 ownership beyond DEC-027; no P2
  surfaces; no P6 sequences; no P3 capability defs; no P1-Governance authz rules;
  no resolution of inherited P1 questions; no implementation tech.

## G-6 Client Brain ownership (stopped for Ali → Option A)

- **Q-001 resolved → Knowledge** owns Client Brain (Memory Object / Shared Service
  Artifact); Client Success contributes but does not own; CRM references but does
  not own. Evidence: `domains.md:1253-1261` (Knowledge "What it owns"),
  `:2761-2766` ("Knowledge remains the strongest long-term ownership direction"),
  Q-001 direction in `open-questions.md`.
- **Q-004 carried** (partitioning per Client / per Brand / both) — entangled with
  Q-003 Brand placement; no resolving evidence. Rider 1: `memory.md` Client Brain
  entry written partition-agnostic.
- Rider 2 (two-landing ceremony): (i) DEC + isolated `domains.md` ownership update
  + knock-on reconciliation; (ii) `memory.md` architecture later.

## G-7 Insight → durable-knowledge threshold (stopped for Ali → carry)

- `domains.md:1917` ("When does an insight become durable knowledge?") is Phase-1
  Intelligence-domain truth; carried, not resolved. Learnings entry references it
  at altitude (R-027). Consistent with `extensibility.md:470` carrying the same.

## Knock-on reconciliation (grep-complete, verifier-confirmed)

Initial enumeration named 2 primary `domains.md` sites + the slice list + 4
`experience-architecture.md` sites. The independent verifier's full grep surfaced
four more ownership-assertion sites in `domains.md` — including two **joint-
ownership** statements (`:374-376` Draft-v2 Primary Owner; `:690` Proposed Model)
that directly contradicted the resolution — plus `:1388-1389` ("ownership may
still be shared") and `:978-981` (CRM open-question sub-bullet). All folded into
the landing-(i) edit set. `extensibility.md` / `capabilities.md`: zero Client
Brain ownership citations.

## Calls

- Ali: G-6 = Option A (resolve Q-001, carry Q-004); G-7 = carry; include optional
  consistency edits; `:2457` keep unchanged; landing (i) split into two commits
  ([1] DEC + domains.md + trackers + this capture; [2] experience-architecture.md
  knock-on).
