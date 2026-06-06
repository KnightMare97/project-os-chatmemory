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

---

### Q-015
At what altitude does Publishing scheduling/queueing sit —
within the Publishing capability (Phase 3),
or orchestration (Phase 6)?

Current direction:
- Atomic "push approved content to a channel" is clearly the
  Publishing capability (Phase 3).
- A scheduled-publish *when-parameter* is probably still within
  the capability.
- Cross-item **queueing** may be orchestration (Phase 6),
  not a capability, and needs a deliberate decision.
- Deferred to the Publishing entry-writing pass; resolve
  deliberately — flag, do not default. Not resolve-now.
- This question lives in this file as the system of record;
  tracked in Linear as a `boundary` + `Phase 3` issue (KNI-21),
  related to the write-`capabilities.md` issue (KNI-20).
- Resolution is a recorded `DEC-0NN` during the write of
  `capabilities.md`.

Why it matters:
- It keeps the Phase 3 ↔ Phase 6 boundary clean: a capability
  is a single, order-free, gate-free ability, while ordered
  cross-item sequencing belongs to Phase 6 Workflow Design.
- Defaulting Publishing toward "the queueing is part of the
  ability" would silently import workflow orchestration into a
  capability.

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
