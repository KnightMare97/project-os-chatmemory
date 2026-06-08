# Open Questions

## Purpose
This file tracks the current important unresolved questions
for Faraz OS.

It is not a historical archive of every question ever raised.

It should contain only active,
still-relevant,
cross-file questions that matter to current work.

Historical or already-resolved questions
should be moved into snapshots,
decision records,
or archive material as appropriate.

---

## Usage Rules
- Keep questions current.
- Remove or relocate resolved questions.
- Prefer one canonical entry per unresolved issue.
- Link question wording to the latest relevant canon and snapshots.
- If a question becomes a decision, move it to `decisions.md`.
- If a question is only historical, keep it out of this file.

---

## Current High-Priority Questions

### Q-001
What is the final ownership model for Client Brain?

Current direction:
- Client Brain is currently treated as a Memory Object
  and Shared Service Artifact direction.
- Knowledge appears to be the strongest long-term ownership direction.
- Client Success contributes important relationship memory.
- Final ownership remains draft.

Why it matters:
- This affects memory ownership,
  retrieval design,
  update authority,
  and cross-domain boundaries.

Resolved (DEC-027):
- Client Brain is owned by Knowledge as a Memory Object / Shared Service Artifact.
- Client Success contributes relationship-relevant content but does not own it;
  CRM references it but does not own it.
- Made concrete in `domains.md` (Knowledge "What it owns"; Client Brain section)
  in the same landing.
- Partitioning (per Client / per Brand / both) remains open — that is Q-004, not Q-001.
- Closed.

---

### Q-002
What is the final ownership model for Service Agreement?

Current direction:
- Service Agreement is currently treated as a Business Artifact.
- It is distinct from CRM Client Account,
  Client Brain,
  and Engagement Scope.
- Final ownership remains draft.

Why it matters:
- This affects agreement truth,
  scope control,
  service coordination,
  and future aggregate or bounded context design.

---

### Q-003
What is the final placement of Brand?

Current direction:
- Brand should not be treated casually
  as just a field inside Client Brain.
- It may require its own Entity treatment
  or more explicit scoped modeling.
- Final placement remains draft.

Why it matters:
- This affects client structure,
  memory design,
  account structure,
  and scope modeling.

---

### Q-004
Should Client Brain exist per Client,
per Brand,
or support both levels?

Current direction:
- This remains explicitly open.
- Current material suggests Brand may need stronger modeling.
- No final structural rule is locked yet.

Why it matters:
- This affects memory partitioning,
  retrieval,
  ownership,
  and scaling of client context.

Note (DEC-027):
- Q-001 (Client Brain ownership) is resolved to Knowledge; Q-004 (partitioning)
  stays open, entangled with Q-003 (Brand placement).
- The Phase-5 Client Brain entry is written partition-agnostic — valid under
  per-Client, per-Brand, or both — so it does not silently resolve Q-004.

---

### Q-005
What is the final ownership boundary between CRM Client Account
and Client Success Relationship?

Current direction:
- CRM should own account baseline and commercial continuity.
- Client Success should own active post-conversion relationship handling.
- The distinction is draft but directionally clear.

Why it matters:
- This affects domain boundaries,
  relationship lifecycle modeling,
  and later aggregate clarity.

---

### Q-006
What is the final lifecycle relationship
between Service Agreement and Engagement Scope?

Current direction:
- Engagement Scope should be derived from,
  constrained by,
  or validated against Service Agreement.
- The exact lifecycle link is still draft.

Why it matters:
- This affects scope governance,
  execution correctness,
  and later service-delivery modeling.

---

### Q-007
Should assigned human operator references
inside Engagement Scope remain simple references,
or evolve into a stronger assignment artifact?

Current direction:
- Workforce remains the source of truth
  for Human Operator identity,
  availability,
  capacity,
  and eligibility.
- Engagement Scope may reference assignment-related information.
- Final structure remains draft.

Why it matters:
- This affects the Workforce / Service Delivery boundary
  and later aggregate design.

---

### Q-008
RESOLVED — see DEC-011.

Normalization of `domains.md` produces a proposed normalized draft
plus a review summary before any canonical file replacement.
Direct update to the canonical file is not the accepted operating model.
This question is closed.

---

### Q-009
Should normalization produce only a cleaned `domains.md`,
or also a short change log summarizing what changed and why?

Current direction:
- This remains open.
- A review-oriented summary may improve trust and traceability.

Why it matters:
- This affects handoff clarity,
  review quality,
  and future maintenance.

Partial direction established:
The review summary component of DEC-011 should serve the change log purpose.
It should cover what was consolidated, what was left unchanged,
and any newly surfaced Open Questions or Risks.
Whether the review summary should also be persisted
as a standalone file after acceptance remains open.

Further partial direction established:
The review summary requirements section of the Execution Checklist v1
now specifies the required format and content of the review summary,
including Changes Made, Items Left Unchanged,
Duplicate Definitions Consolidated,
Draft Boundaries Confirmed Preserved,
Follow-up Discovery Items,
and Residual Ambiguity.
Whether the review summary should persist as a standalone file
after acceptance remains open.
Full resolution of Q-009 is deferred until after
the first normalization pass is complete.

---

### Q-010
RESOLVED — see Execution Checklist v1 appended to
`Faraz-OS-Canon/Normalization Pass v1 Plan for domains.md`.

A dedicated normalization checklist has been produced
and appended to the Normalization Pass v1 Plan.
Claude Code must read and follow it in full
before beginning the normalization pass.
This question is closed.

Priority raised following DEC-011:
Claude Code must operate under explicit constraints
even when producing only a proposed draft.
A normalization checklist reduces the risk of constraint drift
during the pass and should be prepared before Claude Code begins.

---

### Q-011
RESOLVED — see DEC-019 in
`snapshots/Snapshot-013 - Phase 2 Experience Architecture Scope Defined.md`.

The Phase 2 ↔ Phase 3 boundary
and the Permission Matrix question
are resolved.

Direction:
- Operator-facing surfaces are in Phase 2 scope.
- Phase 2 owns where / to whom / how humans interact.
- Phase 2 does not own human identity (Workforce / Phase 1),
  capabilities (Phase 3),
  or authorization rules (Governance / Phase 1).
- The Phase 2 Permission Matrix is a read-only projection
  of Governance rules onto the experience layer
  (rows = personas; columns = surfaces / portals / views;
  not capabilities).
- Phase 2 authors no rules.

This question is closed.

---

### Q-012
What is the intended boundary between
Phase 7 System Architecture Blueprint
and Phase 8 Puzzle Board Architecture?

Current direction:
- Both appear to cover system-level concerns
  and need an explicit scope distinction
  before working content is produced for either.
- Deferred until Phase 6 is complete.
- Not tracked as active work.
- Lives in this file as the system of record;
  tracked in Linear as `KNI-11`, Canceled with a
  re-open-after-Phase-6 note (deferral pattern,
  not a separate status).

Why it matters:
- This affects how Phase 7
  (System Architecture Blueprint)
  and Phase 8 (Puzzle Board Architecture,
  including the Experience Layer and AI Layer)
  are scoped and what each owns.
- It prevents premature finalization of either phase's
  responsibility before Phase 6 reveals concrete needs.

---

### Q-013
What is the exact home of AI / agent-facing surfaces?

Current direction:
- Likely Phase 7 System Architecture Blueprint (AI Architecture).
- Possibly relates to Phase 8 AI Layer.
- Deferred to a later Phase 7 / 8 scoping pass.
- Not blocking Phase 2.
- Repo-only; not tracked as an active Linear issue
  (see Snapshot-013).

Why it matters:
- This affects where agent-driven and AI-driven surfaces
  belong in canon.
- It prevents Phase 2 from silently absorbing
  AI / agent-facing surfaces.

---

### Q-014
What concrete Phase 1 Governance rules are required
to populate the Phase 2 Permission Matrix,
and when do they become available?

Current direction:
- The Phase 2 Permission Matrix is structurally defined
  (rows = personas; columns = surfaces / portals / views;
  a read-only projection of Governance rules),
  but it cannot be populated until Phase 1 Governance
  authorization and permission rules in `domains.md`
  are concrete.
- This is a cross-phase dependency:
  Permission Matrix population is blocked on Phase 1 Governance.
- Trigger: reopening Phase 1 Governance
  (making its permission / authorization rules concrete)
  is what unblocks Permission Matrix population.
- Deferred; not active work.
- The Permission Matrix population work itself remains
  in `KNI-14` (In Progress, blocked).
- This dependency lives in this file as the system of record;
  tracked in Linear as a separate issue,
  Canceled with a reopen-when-Phase-1-Governance-rules-concrete
  note (deferral pattern, not a separate status).

Why it matters:
- It prevents Phase 2 from authoring permission rules
  (which belong to Phase 1 Governance)
  merely to populate the matrix.
- It makes the Phase 2 -> Phase 1 dependency explicit,
  so the Permission Matrix is populated
  only when Governance truth exists.

Resolved (DEC-026 / Snapshot-033):
- Phase-1 half — the Governance authorization slice is concrete in `domains.md`
  ("Authorization (accepted slice — DEC-026)"); DEC-026.
- Phase-2 half — the Permission Matrix is populated as a read-only projection of
  those rules through the surface↔resource mapping (`experience-architecture.md`;
  Snapshot-033), reproducing the ratified DEC-020 exposure with zero divergence.
  Phase 2 is now 7-of-7; KNI-14 → Done.
- Closed.

---

### Q-015
At what altitude does Publishing scheduling/queueing sit —
within the Publishing capability (Phase 3),
or orchestration (Phase 6)?

Resolved (DEC-028) — split three ways:
- Atomic "push approved content to a channel" = Phase 3
  Publishing capability.
- A scheduled-publish *when-parameter* = **firm Phase 3** (moved
  from "probably in-capability"); it carries no cross-item ordering.
- Cross-item **queueing / sequencing** = **Phase 6 orchestration**:
  it names an ordering across items (a sequence), so the
  selection-vs-sequence test (`decisions.md:823-830`) places it
  in Phase 6.

Venue-change note (recorded in DEC-028):
- Q-015's own text named the `capabilities.md` write as its
  resolution venue; that pass deliberately chose flag-not-resolve —
  the flag note, now refreshed at `Faraz-OS-Canon/capabilities.md:89-93`.
  The venue moved to the
  Phase 6 question-gate because the deciding instrument — the
  ratified selection-vs-sequence test (DEC-025) — now exists.
  A deliberate re-venue, applying the litmus as a recorded decision,
  not a default.

Knock-on (reference altitude, isolated commit):
- The `capabilities.md` Publishing entry flag note (`:89-93`) is
  refreshed to "resolved by DEC-028"; the capability itself stays
  atomic, order-free, unchanged.

Linear: KNI-21 → Done (after the resolving push is raw-verified on
origin/main).

Why it mattered:
- It kept the Phase 3 ↔ Phase 6 boundary clean: a capability is a
  single, order-free, gate-free ability, while ordered cross-item
  sequencing belongs to Phase 6 Workflow Design. Defaulting
  Publishing toward "the queueing is part of the ability" would
  have silently imported workflow orchestration into a capability.

---

### Q-016
Does the Client persona have scoped exposure to the Performance & Analytics View?
View Inventory (:614) says scoped; Client portal table (:370) omits it.
Pre-existing inconsistency between two ratified Phase-2 sources, surfaced by the
matrix view projection (Snapshot-033). Resolution reopens DEC-022 view membership
— its own small decision.

Current direction:
- Flagged in the Permission Matrix view projection as `‡`; not resolved there
  (the matrix authors no decision; R-027/R-028).
- The Client's surface-level Reports & Analytics exposure (Scoped, own-engagement)
  is unaffected and reproduces the ratified surface table; this question is only
  the view-membership nuance.
- Deferred; its resolution is a small DEC reopening DEC-022 view membership.
- Lives in this file as the system of record; tracked in Linear if/when scheduled.

---

## Question Review Rule
Review this file regularly.

If a question is:
- resolved, move it to `decisions.md`
- obsolete, remove it
- historical, move it to snapshots or archive
- still active, keep it here

This file should stay short,
current,
and decision-relevant.
