# Governance Authorization Slice (Q-014 Phase-1 half): Brainstorm / Gate Capture
Date: 2026-06-08 · Goal: Make concrete the minimal Phase 1 Governance authorization rules needed to unblock the Phase 2 Permission Matrix, resolving Q-014's Phase-1 half — then (separately) populate the matrix. Phase 1 owning-phase content work.

## Status
Question-gate complete; promoted to DEC-026 (Active) and landed with an isolated
`domains.md` authorization-slice edit (commit `10822d0`), recorded in Snapshot-032.
Repo is source of truth; this is the Phase-11 operating-method capture feeding the
Phase-1 decision. Per CLAUDE.md, this did not finalize any other Governance area,
resolve any other open question, or touch Q-001/Q-004 or other draft areas.

## Method
Inline grill-me gate, recon-first. Recon read the Governance Draft v1 domain
(`domains.md:2154-2413+`), the Permission Matrix / Portals / reuse structures in
`experience-architecture.md`, and Q-014. Autonomy split (Ali): G-2/G-4/G-5 brought
to Ali individually (security-posture decisions); G-1/G-3/G-6/G-7 decided on
recommendations with caveats. DEC content read + an enumerated-rules content read,
both with independent verifier passes (incl. derivation spot-checks), preceded
landing.

## Gate outcomes (G-1 → G-7)
- **G-1 (scope):** (A) authorization-only slice with a named boundary; rest of
  Governance Draft v1 stays draft, byte-untouched, markers preserved. Slice-bleed
  escalation rule accepted → risk R-029.
- **G-2 (rule shape):** Axis 1 = (c) data/action altitude by reference (Phase 2
  owns the surface↔resource mapping; matrix derives exposure). Axis 2 = (b) closed
  evidence-derived verb set view/edit/approve/configure. Riders: verbs closed +
  evidence-traced; approve-verb (Phase 1) vs approval-gate (Phase 6) boundary.
- **G-3 (baseline):** ratify the human-confirmed DEC-020 reuse/portal tables as the
  expected *derived projection* (not authoritative rules); the matrix population
  must reproduce them (acceptance criterion). Acceptance-criterion precision added
  (subject-binding on a primary persona's own surface still reads "Full").
- **G-4 (conditions):** closed set of 3 — own-engagement (defined at altitude),
  assigned-client, engagement-relevant; the two Reports & Analytics Scoped cells
  resolved to own-engagement (decided here); Manager · Agent & Workflow Monitor =
  Full-at-`view` (SysAdmin distinguished by `configure`); `managed-scope` left a
  future-evidence door (set stays at 3).
- **G-5 (overlap):** (c) union of allows with explicit-deny-override (existing
  allow/deny field; no new construct; union never widens a grant's condition; zero
  deny rules authored; permissive-by-default per the portal-union canon;
  intersection rejected — would reopen that canon).
- **G-6 (cell shape):** {Full / Scoped / —}; verb+condition detail in the rules.
- **G-7 (promotion):** two phase-separated landings — (i) Phase 1 DEC + isolated
  domains.md edit (this capture); (ii) Phase 2 matrix population, separate gated
  step. Never mixed. One commit for (i) so the post-edit line refs land atomically.

## Required fix at the enumerated-rules content read (decided-here refinement)
Subject-binding on external personas: five rules gained `own-engagement` — Client
deliverables / approval items / notifications / billing, and Contractor assignment
records — because those resources are inherently subject-bound; unconditioned rules
would authorize cross-client/cross-contractor access at the authoritative layer.
Internal personas' Full rules stand by design. Resource label corrected to
"(Service Delivery / Client Success)".

## Verification
Independent verifier passed twice. Derivation spot-checks reproduced the ratified
DEC-020 exposure from the landed rules + mapping (the acceptance criterion applied
early), including the five re-derivations of the subject-bound external-persona
cells to "Full (primary persona)" under the precision note. The `domains.md` edit
was additive only (118 insertions, 0 deletions).

## Not done (next, separate, gated)
Landing (ii): the Phase 2 Permission Matrix population (read-only projection;
authors no rules) → Phase 2 to 7-of-7 → close KNI-14. The rest of Governance
Draft v1 remains draft.
