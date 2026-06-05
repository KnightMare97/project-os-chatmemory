# Snapshot-016 - Phase 2 Operating Surfaces Scope Defined

## Current Phase
Phase 11 Claude Code Operating System — operational
Phase 2 Experience Architecture — active, framework canon written (Snapshot-014); Operating Surfaces sub-item scoped this session

## Current Topic
Scoping session for the Operating Surfaces sub-item of Phase 2
(first sub-task of KNI-14). A structured grill-me interview
defined the inventory of Operating Surfaces, formalized the
granularity rule and the persona reuse vocabulary, decided the
naming convention, resolved the "Client" subject-vs-persona
ambiguity, and surfaced the lead-context gap. No canon content
was written to `experience-architecture.md` this session.

## Status
A structured scoping interview (grill-me) was completed and
captured in `brainstorms/2026-06-06-phase-2-operating-surfaces.md`.
Operating Surfaces inventory defined: **16 firm + 5 flagged = 21
entries**. Two canon-worthy rules were formalized
(granularity, persona reuse vocabulary). Two renames were
decided ("Client Context Surface" → "Client Brain Surface";
"Workflow Control Panel" → "Agent & Workflow Monitor").
The Permission Matrix sub-item remains explicitly deferred
(Phase 1 Governance rules are not yet concrete).
This snapshot records the decisions; the canon write to
`Faraz-OS-Canon/experience-architecture.md` is a separate
session. Repository is in a stable, confirmed state.

---

## Document Updates

### DOC-029
`brainstorms/2026-06-06-phase-2-operating-surfaces.md` created.
Full scoping capture for the Operating Surfaces sub-item:
the discovery method, the operator-anchored seed set, the
persona reuse map, the persona-distinct emerging surfaces, the
completeness backstop additions, the granularity rule, the
persona reuse vocabulary, the naming convention, the renames,
the carried flags, and the non-goals. It is a working capture,
not canon.

### DOC-030
`Faraz-OS-Canon/experience-architecture.md` was NOT modified.
Writing the Operating Surfaces canon content from the approved
scope is deferred to a separate session under plan → build → review.

### DOC-031
`decisions.md` updated. DEC-020 added (Operating Surfaces scope
defined and human-confirmed; canon-worthy rules), citing this
snapshot and the brainstorm.

### DOC-032
`findings.md` updated. FIND-024 added (System Administrator
surface count growing; potential later refactor candidate;
informational only).

### DOC-033
`Current-State.md` updated to reflect:
- The Operating Surfaces sub-item is scoped (this snapshot).
- The next deliverable is the canon write of the Operating
  Surfaces section of `experience-architecture.md`.
- Remaining KNI-14 sub-items (portal contents, Cross-Domain
  Views by name) stay queued; Permission Matrix population
  stays deferred until Phase 1 Governance rules are concrete.

---

## Decisions

### DEC-020
The Operating Surfaces inventory for Phase 2 is defined and
human-confirmed.

- **Discovery method.** Persona-driven, starting with
  Workforce/Operator. Reuse across other personas is then
  mapped; persona-distinct emerging surfaces become separate
  inventory entries, not specializations of a parent.
  Activity-driven and domain-driven discovery approaches were
  considered and rejected (activity-driven risks Phase 3 drift;
  domain-driven would explode into one surface per
  domain × persona).
- **Granularity rule (canon-worthy).** Operating Surfaces are
  sized at one surface per coherent work-mode, not one per
  task type.
- **Naming convention (canon-worthy).** Persona-facing surfaces
  are persona-prefixed (e.g. *Client Notifications*); subject-
  facing surfaces use distinct subject words rather than
  persona names (e.g. *Client Brain Surface*, not
  *Client Context Surface*).
- **Persona reuse vocabulary (canon-worthy).** Four modes —
  **Full** (same surface, same content),
  **Scoped** (same surface, restricted content),
  **Distinct surface** (a different surface serves the same
  intent for that persona, and is added to the inventory),
  **—** (no access).
- **Scoped marker placement.** Phase 2 records "Scoped" as a
  marker on the surface↔persona relationship. The rules that
  define what is scoped come from Phase 1 Governance and are
  projected via the Permission Matrix. Matrix population
  remains deferred (Governance rules are not yet concrete).
- **Renames.**
  *Client Context Surface* → **Client Brain Surface**
  (anchors on the Phase 5 Knowledge & Memory concept of
  Client Brain; eliminates the "Client" subject-vs-persona
  ambiguity; scope deliberately narrowed to current-client
  strategic memory; pre-engagement lead context lives in
  CRM and gets its own surface).
  *Workflow Control Panel* → **Agent & Workflow Monitor**
  (sharper separation from Phase 6 Workflow Design;
  observation + intervention are P2, the workflow logic itself
  is P6).
- **Firm inventory (16 surfaces):**
  Operator-anchored (8): *Operator Inbox*, *Production
  Workspace*, *Review Queue*, *Client Brain Surface*,
  *Knowledge Workspace*, *Agent & Workflow Monitor*,
  *Reports & Analytics Surface* (carries a classification
  flag — possibly a Cross-Domain View), *Lead Workspace*.
  Client persona (4): *Client Notifications*,
  *Client Approval Queue*, *Client Deliverable Library*,
  *Client Billing / Invoices Surface*.
  Contractor persona (1): *Contractor Assignments*.
  System Administrator (3): *Admin Knowledge*,
  *Workflow & Agent Configuration*,
  *Credentials & Integrations*.
- **Flagged (5, deferred):**
  *Client Profile* (tentative; needs later confirmation);
  *Team Performance / Oversight Surface*
  (possibly Cross-Domain View);
  *System Configuration / Settings*
  (depends on Phase 4 / Phase 9 maturity);
  *Operator-finance gap* (operator's view of engagement
  revenue, contractor payment status; currently absorbed by
  Client Brain Surface and Reports & Analytics Surface);
  *Onboarding / first-time-use surfaces* (none named for any
  persona).

This decision records scope only. It does not modify
`experience-architecture.md`, does not finalize any Phase 1
domain boundary, does not populate the Permission Matrix,
and does not enumerate Portals or Cross-Domain Views.

---

## Findings

### FIND-024
System Administrator surface count is growing relative to
other personas — 3 firm surfaces (*Admin Knowledge*,
*Workflow & Agent Configuration*, *Credentials & Integrations*)
plus 1 flagged (*System Configuration / Settings*), on top of
full reuse of *Agent & Workflow Monitor*. Defensible: admin
work is genuinely multi-headed (knowledge, workflow authoring,
integration management, system configuration). Flagged as a
potential later refactor candidate (e.g. merging some admin
surfaces, or splitting System Administrator into sub-personas
if the count keeps growing). Informational only; no action
this session.

---

## Open Questions
No new open questions this session.
- Q-011 resolved (unchanged; via DEC-019).
- Q-012 deferred (unchanged; Phase 7 ↔ Phase 8).
- Q-013 deferred (unchanged; AI / agent-surface home).

---

## Assumptions
- Assumption: the scope captured in DEC-020 reflects
  human-confirmed decisions made this session; the canon
  write to `Faraz-OS-Canon/experience-architecture.md` is
  pending and will be done under plan → build → review in
  a separate session.
- Assumption: no Phase 1 domain truth, ownership, or
  boundary was modified by this session. The Operating
  Surfaces inventory references Phase 1 concepts
  (Client Brain via Phase 5, CRM, Service Delivery, Finance,
  Knowledge, Governance) without reinterpreting them.
- Assumption: the locked persona set from DEC-019 remains
  the boundary; persona-distinct emerging surfaces in this
  session were assigned within the locked set.
- Assumption: the 16-firm inventory is stable for the canon
  write; the 5 flagged items remain explicitly flagged and
  must not be silently resolved.
- Assumption: Permission Matrix population remains deferred
  until Phase 1 Governance rules in `domains.md` are
  concrete; this session did not change that deferral.

---

## Risks

### R-023 (carried forward, active, partial mitigation this session)
Phase 2 may drift into Phase 3 Capability Map or Phase 6
Workflow Design territory as the framework matures into
populated detail. Mitigations applied this session:
the granularity rule, the naming convention, the persona
reuse vocabulary, and the rename of *Workflow Control Panel*
to *Agent & Workflow Monitor* all sharpen the altitude marker.
Keep active through Phase 2 refinement work.

### R-025 (carried forward, active)
Session close-out is applied by discipline, not enforced by
tooling. Mitigation: `workflows/sync-protocol.md` codifies
the procedure; consider extending it to formalize tracker
backfill at close-out (carried forward from Snapshot-015).

### R-026 (carried forward, active)
`workflows/sync-protocol.md` references Linear MCP tools by
logical name; if those tool names change, its Tooling section
must be updated.

---

## Next Focus
1. Write the Operating Surfaces section of
   `Faraz-OS-Canon/experience-architecture.md` from the
   approved DEC-020 scope, under plan → build → review,
   in a separate session. Replace the framework-only
   Operating Surfaces section with the populated
   16-firm-inventory framework, the granularity rule, the
   naming convention, and the persona reuse vocabulary.
   Carry the 5 flagged items forward in the
   Open / Deferred Items section.
2. After repo approval of this close-out, reconcile Linear
   per `workflows/sync-protocol.md`: set KNI-14 to
   `In Progress` with a comment noting the Operating Surfaces
   sub-task is scoped (this snapshot) and ready for content
   write.
3. Subsequent KNI-14 sub-items remain queued:
   portal contents per persona,
   then concrete Cross-Domain Views
   (which will resolve the *Reports & Analytics Surface*
   and *Team Performance / Oversight Surface* flags).
4. Permission Matrix population remains deferred until
   Phase 1 Governance rules in `domains.md` are concrete.
5. Carry the Future Personas placeholder and the deferred
   navigation sub-detail (notification routing, deep-linking)
   forward as marked future items.
6. Keep Claude Project input limited to high-signal current
   files; prepare later controlled handoff to Claude Code.
