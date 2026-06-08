# Brainstorm — Q-021: AI Operations / AI usage-cost ledger (2026-06-08)

**Status:** Working reasoning behind DEC-038. Immutable once landed; cites resolve against the
landing commit. Not canon.

## Why this surfaced
Gap analysis §3 (the AI P&L — token/model cost per job + per client, margin view, budget caps
wired into routing, an AI usage/cost ledger). No domain owns an AI usage/cost record today.
The 5th of the ~10 Phase-1 reopenings.

## The three-lens trio (PM + Workflow + System)
Convergent; the owner was the one real posture call.

**G-2 owner → NEW thin Phase-1 domain "AI Operations" (orphan); Finance-sub-ledger fallback.**
- **System (decisive):** orphan test passes. Finance = outward-facing commercial money
  (invoices/payments), not internal per-job AI cost; Intelligence owns derived findings and
  disowns raw SoT + financial-ledger (`domains.md:1742/:1746`); Governance disowns raw execution
  telemetry (`:2245`); Phase 7 meters but can't own (inversion guard). The per-job record is
  orphaned → new domain. Finance-sub-ledger = carried fallback (DEC-034) if too thin.
- **Workflow:** the ledger is **P7-realized telemetry — the cost twin of the Audit Record**
  ("a system property realized in Phase 7; Phase 6 only marks the gate," `workflows.md:113-117`).
  Cost-recording is NOT a workflow step. The *what* is a domain's; the *how* (meter/persist) is P7.
- **PM:** operational telemetry vs commercial money — the record is the gated call; the
  per-client view is derived; budget cap is the T1.5 defensive lever.

**G-3 entity (unanimous):** per-job **UsageRecord** = Entity (raw SoT, per-job grain);
**per-client cost = DERIVED → Intelligence, not a 2nd entity**; aggregate-pending.

**G-4 four-way seam (unanimous):** AI Operations owns the UsageRecord (P1); P7 meters
(references-not-owns); Intelligence derives margin/per-client/ratio; Governance authors the
budget-cap policy (the existing **Routing Governance Aggregate**, `domains.md:2329-2337`) and
**P4 AI Model Routing enforces** it (cost is already a routing dimension, `extensibility.md:353/:381`).
Raw-vs-derived-vs-mechanism-vs-policy kept distinct.

**Workflow conclusion (no new P6 pattern):** the budget-cap gate = **(b) P4 routing-refusal**
(cap-as-routing-constraint, reuses the Routing Governance Aggregate) **default + (a) P6
Escalation gate** exception (over-budget = policy-violation intensify-when, reuses the existing
Escalation Loop, `workflows.md:206`). **Do NOT re-scope the Dual-Path pattern** (DEC-037) — its
trigger stays availability, not cost/policy; the manual path is just one human option under
Escalation. The seven flows get at most optional field-4/5 reference text.

**G-5 Prompt-as-asset → split (Q-022, open):** prompt/template versioning is a versioned
artifact (DEC-033-like); candidate home Media & Assets or Knowledge; its link to cost is only a
referential `cost-per-prompt-version` join. Its own later gate — un-bundled from the cost ledger.

## Scope discipline
DEC-038 resolves the **AI Operations domain + UsageRecord + the seam ONLY**. Separate later
gates: P7 metering mechanism; Intelligence margin/ratio views; Governance budget-cap-policy
authoring + P4 enforcement content; prompt-versioning (Q-022). DEC-026/027/034/037 + Governance
cost-constraint ownership + P4 cost-dimension referenced, not touched; R-027 set (Q-004 unblocked,
threshold), Q-006/Q-016/Q-017/Q-020 + the other ~5 reopenings untouched.

## Tier
Meter + hard budget cap = T1.5 (defensive); per-client margin view = T2; AI-vs-human-cost ratio
+ prompt-versioning = T3.

## Landing shape (DEC-033/035 precedent)
One isolated called-out commit: DEC-038 + isolated `domains.md` AI Operations section + Q-021
registered+resolved + Q-022 open + Current-State + this brainstorm.
