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
