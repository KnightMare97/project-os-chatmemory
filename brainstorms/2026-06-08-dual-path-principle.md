# Brainstorm — Dual-Path / Manual-Fallback principle (2026-06-08)

**Status:** Working reasoning behind DEC-037. Immutable once landed; cites resolve against the
landing commit. Not canon.

## Why this surfaced
The roadmap (#5; `grounding/Gap-Analysis-and-Roadmap.md`) flagged Dual-Path / Manual-Fallback
as the Iran-driven unifying insight — every external action needs a manual path with fallback
when the automated one is unavailable (platforms get blocked/throttled). The Phase-7 blueprint
already referenced it as a posture across Integration / Data / Runtime / Security and explicitly
flagged it as "a candidate Phase-6 fourth loop/exception pattern, not Phase-7"
(`system-architecture-blueprint.md:458-460`). The gate question: principle, 4th P6 pattern, or
property of an existing pattern?

## The three-lens trio (PM + Workflow + System) — unanimous (c)+(a)
- **System (decisive — the four-altitude argument):** dual-path has a *distinct, non-redundant
  expression at four altitudes* — P3 execution-mode (the can-run-in enabler), P4 availability
  (already a routing dimension, `extensibility.md:354/:381`), P6 (semantic routing), P7
  (detect+switch engine + idempotency `:420`). A concern that needs a real expression at four
  phases is a **higher-altitude principle each phase implements**, not a single-phase pattern.
  Recording it as *only* a P6 pattern would invert altitude (P3/P4/P7 forced to cite a P6
  pattern for behaviour genuinely theirs).
- **Workflow (the trigger distinction):** it's a **genuine 4th loop/exception pattern**, not a
  case of Failure/Exception — its trigger is **pre-dispatch availability-routing** ("the
  automated channel is unavailable → route to the manual path"), categorically different from
  Failure's **post-attempt non-completion**. Dual-path **falls through to** Failure/Exception
  when both paths are exhausted — proving they are distinct (one precedes the other). Fits the
  What/When/Semantic shape, field-5-referenceable, semantic-not-mechanism. Reject (b): folding
  it into Failure overloads one trigger with two conditions (term-collapse).
- **PM:** (c) is load-bearing — the founding Iran constraint must be a **default the
  architecture inherits**, not a per-feature checklist; (a) is the enforcement (field-5
  reference). (b) conflates availability-fallback with failure (operators paged constantly).

**Resolution:** **(c) cross-phase PRINCIPLE in a DEC + (a) a Phase-6 4th pattern as its
Phase-6 expression.** The DEC is the anchor (the what/why + the seam each phase cites); the P6
pattern is how workflows consume it. Avoids a competing source-of-truth and keeps P6 from
inventing the principle (R-028).

## Three orthogonal axes (no-collapse)
- **Oversight (HITL)** — who *judges/approves* (`human-in-the-loop-philosophy.md:18-32`).
- **Execution-capacity (P3 execution-mode)** — which modes a capability *can run in*
  (`capabilities.md:56-57`), design-time.
- **Availability-fallback (dual-path)** — which path *executes* when the automated one is down,
  runtime. The dual-path human **executes** (vs HITL human **judges**); dual-path is **not** a
  4th execution mode.

## The four-altitude seam
P1 Governance = WHEN fallback is permitted / what the manual path may do; P6 = semantic routing
(the 4th pattern, mechanism-free per the `workflows.md:183-190` firewall); P7 = detect+switch
engine + degraded-mode + **idempotency** (the safety pre-req — auto+manual must never
double-execute, `:420`); P4 = the **access-status / connection-health** signal (Channel Model
candidate, `extensibility.md:120`); P3 = the hybrid-capable enabler.

## Split landing (Ali's call)
- Step 1 (this package): **DEC-037** records the principle + seam; **Q-020** registers the P4
  access-status owner (open); Current-State + brainstorm. One isolated commit. No canon entity,
  no P6/P7 mechanism content.
- Step 2 (separate later gate): the **Phase-6 4th-pattern write** in `workflows.md` (the
  highest-R-028 surface — must stay mechanism-free).
- Step 3 (separate later gate): **Q-020** — the Phase-4 access-status owner.

## Tier
T1 (founding constraint). v1 floor = manual-toggle on explicit access-status for
publish/upload/payment-confirm/OAuth-re-auth + idempotency; auto-detection→auto-fallback and
whole-system degraded-mode = T2.
