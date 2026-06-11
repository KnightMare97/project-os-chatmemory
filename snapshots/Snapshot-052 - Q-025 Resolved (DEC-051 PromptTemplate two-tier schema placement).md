# Snapshot-052 — Q-025 Resolved (DEC-051; PromptTemplate two-tier schema placement)

## Current Phase
All eleven phases complete (Phase 0 through Phase 11 first-write entries exist).
No active content phase in progress. This snapshot records the resolution of a
single carried-open question (Q-025), the highest-priority item in the Snapshot-051
pre-V1 gate batch.

## Current Topic
Resolving Q-025 — PromptTemplate schema tier (platform/shared vs. per-client). The
only true V1 schema blocker in the pre-V1 batch. Ali approved the F-8
critique-verification recommendation: a two-tier model, both tiers Knowledge-owned.

## Status
RESOLVED. DEC-051 minted. Q-025 closed. One isolated, called-out `domains.md`
concept-altitude edit landed (net-zero line count). No other open question touched.
The T1 Knowledge / Content schema work in the build repo is now unblocked.

---

## Document Updates

### `decisions.md`
- Added **DEC-051** — Q-025 resolution: PromptTemplate is a two-tier entity, both
  tiers Knowledge-owned (DEC-044 unchanged): **SystemPromptTemplate** (platform/shared
  tier, `public` schema — `infrastructure.md:430`) and **ClientPromptTemplate**
  (per-client tier, `client_{uuid}` schema — `infrastructure.md:436`, partitioned
  per-Brand per DEC-045). Records the tier-selection litmus and the canon-altitude
  boundary (no build DDL).

### `open-questions.md`
- Q-025 Status changed UNRESOLVED / TRACKED → **RESOLVED — see DEC-051**.
- Pre-V1 batch header annotated with a dated update line: Q-025 resolved; Q-026–Q-033
  remain open.
- No other Q entries modified.

### `Faraz-OS-Canon/domains.md` (ISOLATED, called-out — Phase-1 domain truth, DEC-051)
- Knowledge "What it owns": PromptTemplate line annotated with the two-tier
  distinction at concept altitude (platform-shared SystemPromptTemplate / per-client,
  per-Brand ClientPromptTemplate).
- Knowledge "Candidate Entities": PromptTemplate annotated with the two named tiers.
- **Net-zero line count** (numstat 2/2): no downstream `domains.md` line citation was
  shifted; no cascade cite-sweep required (contrast DEC-045's FIND-032 sweep).
- Concept altitude only — no schema names, columns, or DDL written into `domains.md`
  (physical `public`/`client_{uuid}` placement lives in DEC-051, citing Phase 9).

### `findings.md`
- Added **FIND-042**: the net-zero-line technique for keeping an isolated `domains.md`
  concept-altitude edit from triggering the FIND-032/033/034 downstream cite-shift
  cascade.

### `Current-State.md`
- Current Next Focus + pre-V1 batch section updated: Q-025 marked resolved (DEC-051);
  remaining open list narrowed to Q-026–Q-033; T1 Knowledge/Content schema noted as
  unblocked.

### No other files changed.
- All other phase files in `Faraz-OS-Canon/` — NOT touched.

---

## Decisions
**DEC-051** (new) — Q-025 resolved. PromptTemplate is a two-tier entity, both tiers
Knowledge-owned (DEC-044 unchanged):
1. **SystemPromptTemplate** — platform / shared tier; system-default templates shared
   across all clients; lives in the `public` schema tier (`infrastructure.md:430`).
2. **ClientPromptTemplate** — per-client tier; brand-specific / client-customized
   templates; lives in each client's `client_{uuid}` schema tier
   (`infrastructure.md:436`), partitioned per-Brand (DEC-045).

Tier-selection litmus: system-default/shared → System tier; brand/client-specific →
Client tier. Canon altitude (ownership + platform-vs-per-client placement); concrete
DDL is build-layer (DEC-049 / DEC-050).

---

## Findings
**FIND-042** (new): An isolated `domains.md` concept-altitude edit can be authored
**net-zero-line** (replace N lines with N lines), which keeps every downstream
`domains.md` line citation in living docs from shifting — avoiding the
FIND-032/033/034 cascade cite-sweep and preserving true commit isolation. Used for
the DEC-051 `domains.md` edit (numstat 2/2; `:1720`, `:1944-1945`, `:1946` re-derived
intact post-edit).

---

## Open Questions
Q-025 is **resolved** (DEC-051). The remaining pre-V1 batch items stay open:
- Q-026 (Domain Event Registry), Q-027 (Operational Risk Stubs — deferred past V1),
  Q-028 (Phase-11 FAST tier — GATED), Q-029 (day-in-the-life validation gate),
  Q-030 (Intelligence vs Analytics/Reporting boundary — hard pre-schema gate),
  Q-031 (PublishedItem entity), Q-032 (Campaign + Schedule status), Q-033 (Client
  Onboarding Phase-6 workflow gap).

Previously-active open items remain as-is:
- Q-003 (Brand aggregate placement), Q-006, Q-007, Q-024, insight→durable-knowledge
  threshold (`domains.md:1946`), 4 Phase-1 entity reopenings (Campaign, Ad-Account,
  Schedule, Consent), Agent Supervision slot.

---

## Assumptions
None introduced.

---

## Risks
- DEC-051 sets the schema *tier* placement at canon altitude. The build repo must not
  invent a third tier or collapse the two tiers when writing the actual DDL; the
  tier-selection litmus is the guard.

---

## Self-Review (Two-Part)

### PART A — Mechanical Citation Verifier

Citations introduced by this change:
- `infrastructure.md:430` and `infrastructure.md:436` (DEC-051 + open-questions.md
  Q-025 Status line).

Verification (raw bytes, shell-confirmed):
```
$ sed -n '430p;436p' Faraz-OS-Canon/infrastructure.md
public schema
client_{uuid} schema  [one per client account]
```
`:430` is the `public schema` (platform-level shared tables) heading in the Schema
Layout block; `:436` is the `client_{uuid} schema [one per client account]` heading.
Both byte-accurate and content-verified.

Stale-token / same-session shift sweep:
- The `domains.md` edit is **net-zero line count** (`git diff --numstat` = `2 2`).
  A net-zero change at lines 1264 / 1293 shifts no line below it.
- Re-derived downstream living-doc-cited regions post-edit — all intact:
```
$ sed -n '1720p' Faraz-OS-Canon/domains.md
  → Cross-referenced to Q-024 (Ticket ↔ Escalation Case lifecycle coupling, open).
$ sed -n '1944,1945p' Faraz-OS-Canon/domains.md
- What belongs in Intelligence
  versus Analytics / Reporting capability?
$ sed -n '1946p' Faraz-OS-Canon/domains.md
- When does an insight become durable knowledge?
```
- No living-doc `domains.md:` citation required updating.
- Immutable history (snapshots/, brainstorms/, `decisions.md` prior entries) not
  retro-edited. DEC-051 is a new entry, not an edit to landed history.

### PART B — Semantic Red-Team

1. **Resolution matches the approved recommendation?** Yes. Two tiers
   (SystemPromptTemplate / ClientPromptTemplate), both Knowledge-owned (DEC-044
   unchanged), platform/`public` vs. per-client/`client_{uuid}`, Client tier per-Brand
   (DEC-045) — verbatim the F-8 recommendation Ali approved.

2. **Litmus recorded verbatim?** Yes — DEC-051 and the Q-025 Status line both carry:
   system-default/shared → System tier; brand/client-specific → Client tier.

3. **Altitude correct (no build DDL)?** Yes. DEC-051 fixes *where the tiers live*
   (ownership + placement principle); `domains.md` records only the concept-altitude
   two-tier distinction. No columns, types, indexes, or version-table structure
   written. Build DDL explicitly deferred to the build repo (DEC-049 / DEC-050).

4. **No other open question touched?** Confirmed. Q-006, Q-024, Q-026–Q-033, Q-003,
   Q-007, the insight→durable-knowledge threshold, and the 4 entity reopenings are all
   untouched and still open. Only Q-025 changed status.

5. **DEC-044 / DEC-045 honored, not overridden?** Yes. DEC-044 (Knowledge owns
   PromptTemplate) is explicitly unchanged; DEC-045 (per-Brand partitioning) is reused
   for the Client tier. No supersession.

6. **No architecture invented beyond evidence / no boundary crossed (R-028)?** The
   two named tiers are the approved resolution; the schema-tier model they map onto
   already exists in Phase 9 `infrastructure.md`. No new domain, ownership, or boundary
   invented.

PART B: PASSED.

---

## Next Focus
Q-025 resolved removes the top blocker from the pre-V1 sequence. Recommended next:

1. **Q-030** — Intelligence vs Analytics/Reporting boundary (hard pre-schema gate;
   `domains.md:1944-1945`).
2. **Q-006, Q-024** — Service Agreement aggregate boundary; Ticket ↔ Escalation Case
   lifecycle coupling.
3. **Q-031, Q-033** — PublishedItem entity; Client Onboarding Phase-6 workflow.
4. **Q-032** — Campaign + Schedule promote-vs-field posture check.
5. **Build-repo setup** — per `claude-operating-system.md` Appendix A; the T1
   Knowledge / Content schema can now reference the DEC-051 two-tier PromptTemplate
   model.

Q-027 (infrastructure stubs) and Q-028 (FAST tier proposal) remain deferred / gated.
