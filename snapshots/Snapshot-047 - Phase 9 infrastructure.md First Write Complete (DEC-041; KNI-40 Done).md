# Snapshot-047 - Phase 9 infrastructure.md First Write Complete (DEC-041; KNI-40 Done)

## Current Phase
Phase 11 Claude Code Operating System — operational (two-part self-review in force).
**Phase 9 Infrastructure Design — first write COMPLETE (this snapshot; DEC-041).**
Phase 8 Puzzle Board Architecture — first write complete (Snapshot-046), unchanged.
Phase 7 System Architecture Blueprint — first write complete (Snapshot-044), unchanged.
Phase-1 reopening program — **7 of ~11 done** (~4 remain: Campaign, Ad-Account,
Schedule, Consent), unchanged.
Open: Q-020 (Phase-4 access-status / connection-health owner, KNI-32), Q-022 (prompt /
template versioning), Q-024 (Ticket ↔ Escalation Case lifecycle coupling), Q-017 (visual
workflow management), Q-004, Q-006, Q-016.

## Current Topic
Record-only close-out of the Phase 9 `infrastructure.md` first write (DEC-041;
approved 2026-06-09). This snapshot **records** at reference altitude; it authors no
architecture and resolves no open question.

## Status
`Faraz-OS-Canon/infrastructure.md` is written as the Phase 9 Infrastructure Design
first write, under DEC-041 scope, with full two-part self-review before commit:

- **PART A** — all citations verified with raw sed/grep bytes: `architecture.md:184-190`
  (7 abstract block definitions), `:117-119` (Core enforcement blocks), `:134-136`
  (Core↔Infrastructure governing table), `:197-199` (P8↔P9 cut verbatim), `:246`
  (Media & Assets domain), `:403` (Operating Surfaces / Agent & Workflow Monitor),
  `:461-465` (AI Layer blocks table); `Faraz-OS-Canon.md:149` (Phase 9 entry);
  `experience-architecture.md:239` (Agent & Workflow Monitor surface row);
  `domains.md:3801` (Media & Assets domain header); `extensibility.md:426` (Feature
  Modules definition). One citation fix applied: an over-claiming reference to
  `architecture.md:334-347` corrected to `extensibility.md:426`. No same-session shift:
  `infrastructure.md` is a new file; `architecture.md` was read-only this session.
  Immutable-history cites unchanged. PART A CLEAN.

- **PART B** — altitude correct (technology assignment only; no redefinition of abstract
  blocks); P8↔P9 boundary not crossed; no carried-open question resolved (Q-004, Q-006,
  Q-016, Q-017, Q-020, Q-022, Q-024, R-027 set all referenced, not resolved); no Phase 10
  build specifics locked in (all flagged illustrative-not-locked or as Build-layer flags);
  no Phase 1 domain truth authored; no architecture invented beyond repository evidence;
  R-028 reference-altitude discipline held. PART B CLEAN.

Final file: `Faraz-OS-Canon/infrastructure.md`, 706 lines, all 7 abstract
Infrastructure Layer blocks assigned physical GCP technology. KNI-40 → **Done**.

---

## Document Updates

### DOC-138
`Faraz-OS-Canon/infrastructure.md` — **Phase 9 Infrastructure Design first write
complete** (commit this session; 706 lines; DEC-041). All 7 abstract Infrastructure
Layer blocks assigned: Cloud SQL (Persistent Store) · pg-boss (Job Queue / Event Bus)
· Cloud Run (Worker / Job Runtime) · Firebase Authentication (Auth Backing Service)
· GCP Secret Manager (Secret Store) · Cloud Logging + Cloud Monitoring + Grafana Cloud
(Observability Infrastructure) · Schema-per-client + RLS (Per-Client Data Scoping
Scheme). Frontend Serving (Firebase Hosting / Cloudflare Pages) and Object Storage
(GCP Cloud Storage) as supplementary entries.

### DOC-139
`decisions.md` — DEC-041 appended: Phase 9 scope approved; all-GCP ruling; three-option
comparison (A self-hosted Supabase on GCE, B managed Cloud SQL + Firebase Auth, C
Supabase Cloud Pro); Option B ruling; schema-per-client data separation; routing chain;
RLS belt-and-suspenders; service-role security invariant; pg-boss job queue selection.

### DOC-140
`Current-State.md` — Phase 9 first-write-complete recorded; DEC-041 noted; KNI-40 Done;
`infrastructure.md` all-GCP stack with schema-per-client noted (this close-out commit).

### DOC-141
`snapshots/` — Snapshot-047 recorded as the Phase-9 / infrastructure.md first-write-
complete close-out.

---

## Decisions

### DEC-041 (recorded this session)
Phase 9 Infrastructure Design — scope approved; all-GCP stack ruling (Cloud SQL +
Firebase Auth + Cloud Run + GCS + Secret Manager + Cloud Logging; pg-boss job queue;
SSE-on-Cloud-Run realtime; schema-per-client + RLS data separation). Three-option
comparison run; Option B (managed all-GCP) won on cost ($29–57/month), ops burden
(zero), no SPOF, and schema-per-client viability via Cloud SQL session-mode Auth Proxy.
See `decisions.md` for full ruling.

---

## Findings

No new finding. PART A + PART B self-review confirmed clean:
- 12 cites verified (architecture.md × 7 cite ranges + Faraz-OS-Canon.md:149 +
  experience-architecture.md:239 + domains.md:3801 + extensibility.md:426; plus
  architecture.md:117-119 and :134-136).
- One citation fix: `architecture.md:334-347` overclaim corrected to
  `extensibility.md:426` (Feature Modules definition).
- No same-session line-shift cascade required (infrastructure.md is new;
  architecture.md read-only).

---

## Open Questions

- **Q-017 — open** (system-administrator visual workflow management; multi-phase; own
  gated decision). Referenced in infrastructure.md Status; if resolved to AI Layer,
  Block 3 topology may gain a dedicated Cloud Run service. Carried unchanged.
- **Q-020 — open** (Phase-4 access-status / connection-health owner; KNI-32). Referenced
  in infrastructure.md Status; affects how Dual-Path routing signal is surfaced in
  infrastructure layer. Carried unchanged.
- **Q-022 — open** (prompt / template versioning; registered DEC-038). Referenced in
  infrastructure.md Status; may add a versioned prompt store to Block 1 or Block 9.
  Carried unchanged.
- **Q-024 — open** (Ticket ↔ Escalation Case lifecycle coupling; registered DEC-039).
  Carried, not touched by Phase 9.
- **Carried, unchanged:** Q-004 (Client Brain partitioning), Q-006 (SA ↔ Engagement-Scope
  consistency), Q-016. R-027 set. Q-012 / Q-013 / Q-014 / Q-015 / Q-018 / Q-019 / Q-021
  / Q-002 / Q-003 / Q-023 remain resolved.

---

## Assumptions

- Assumption: Phase 9 first write is a milestone, not a phase-complete declaration. A
  Phase-9-complete call is a separate later gated decision (Phase-2/6/7/8 precedent).
- Assumption: infrastructure.md Build-layer flags (exact SKUs, autoscaling thresholds,
  migration scripts, CI/CD config) are Phase 10 decisions; none are locked in Phase 9.
- Assumption: the four remaining Phase-1 entity reopenings (Campaign, Ad-Account,
  Schedule, Consent) each add tables to `client_{uuid}` schemas; no infrastructure
  re-architecture required — the schema migration runner accommodates new tables
  automatically.

---

## Risks

### R-028 (carried forward, active — held throughout)
Reference-altitude discipline held. infrastructure.md assigns technology; it does not
re-define abstract blocks (Phase 8), author domain truth (Phase 1), or specify build
procedures (Phase 10). R-028 standing guard applies to future Phase 9 updates and the
Phase 10 downstream.

### R-027 (carried forward, active — held)
No inherited Phase-1 question resolved; the R-027 set is referenced, carried.

### R-025 / R-026 / R-029 (carried forward, active)
Unchanged.

---

## Next Focus

1. **Phase-1 entity reopening program (~4 remaining: Campaign, Ad-Account, Schedule,
   Consent)** — each its own gated decision; PAUSED pending Ali's relay of direction.
2. **Open Qs carried:** Q-004, Q-006, Q-016, Q-017, Q-020, Q-022, Q-024 — each its own
   gated resolution, not authored in Phase 9.
3. **Phase 10 Build Roadmap** (`roadmap.md`) — translates the all-GCP assigned
   technologies from infrastructure.md into build steps, MVP scope, and implementation
   sequence. Downstream of Phase 9. Requires its own scoping gate.
4. **T1 build** — the single-tenant showcase; the module-mountable AI-native BASE is the
   real product. Phase 10 downstream.
