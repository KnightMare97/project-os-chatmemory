# Snapshot-017 - Phase 2 Operating Surfaces Canon Written

## Current Phase
Phase 11 Claude Code Operating System — operational
Phase 2 Experience Architecture — active; Operating Surfaces
sub-item now written into canon (this session)

## Current Topic
Canon write of the Operating Surfaces section of
`Faraz-OS-Canon/experience-architecture.md` from the approved
DEC-020 scope (Snapshot-016). The framework-only section was
replaced with the populated sixteen-surface inventory and its
three canon-worthy rules. No new architecture was invented;
this session executed an already human-confirmed decision under
plan → build → review.

## Status
The Operating Surfaces section of
`Faraz-OS-Canon/experience-architecture.md` is now populated.
It carries the granularity rule, the naming convention, the
persona reuse vocabulary (Full / Scoped / Distinct surface / —),
the Scoped marker placement note, and the firm inventory of
**16 surfaces** with their primary persona and reuse pattern.
The **5 flagged surfaces** are carried forward in the file's
Open and Deferred Items section and remain explicitly flagged.
The Permission Matrix remains unpopulated; portal contents per
persona and concrete Cross-Domain Views remain deferred. No new
decisions, findings, or open questions were produced this
session — it was execution of DEC-020. Repository is in a
stable, confirmed state.

---

## Document Updates

### DOC-034
`Faraz-OS-Canon/experience-architecture.md` updated
(single-file, minimal-diff). Changes:
- `## Operating Surfaces` rewritten from framework-only to the
  populated section: Definition and "What Operating Surfaces are
  not" preserved; new subsections added for the Granularity Rule,
  Naming Convention, Persona Reuse Vocabulary (with the Scoped
  marker placement note), and the Surface Inventory (16-row
  table: Surface | Primary persona | Reuse pattern), followed by
  a boundary note (reuse mapping is a Phase 2 surface property,
  not the populated Permission Matrix) and reference-altitude
  cross-references. The "Scope of definition in this file"
  subsection was rewritten to state what the section now
  enumerates and what it still defers.
- `## Purpose` and `## Status` disclaimers nuanced: the file now
  enumerates concrete Operating Surfaces, but still does not
  populate the permission matrix, name portal contents, or
  enumerate concrete cross-domain views.
- `## Open and Deferred Items`: removed "concrete Operating
  Surfaces by name" from Deferred — Concrete enumeration (now
  done); added a "Flagged — Operating Surfaces carried forward"
  subsection listing the 5 flagged surfaces with reasons, plus an
  informational FIND-024 note (System Administrator surface count
  growing; potential later refactor candidate; no action).
- `## Risks Carried Forward`: R-023 annotated with the partial
  mitigation added by this population (granularity rule, naming
  convention, persona reuse vocabulary, Agent & Workflow Monitor
  rename). R-023 stays active.
- `## Provenance`: added DEC-020 / Snapshot-016 and
  `brainstorms/2026-06-06-phase-2-operating-surfaces.md`.

### DOC-035
`Current-State.md` updated to reflect that the Operating
Surfaces section is written (this snapshot), and to re-point
the next focus at the remaining KNI-14 sub-items (portal
contents per persona, then concrete Cross-Domain Views), with
Permission Matrix population still deferred.

---

## Decisions
No new decisions this session.
- DEC-020 (Operating Surfaces scope) was executed, not changed.
- The 5 flagged surfaces remain flagged; none was resolved.

---

## Findings
No new findings this session.
- FIND-024 (System Administrator surface count growing) is
  carried into `experience-architecture.md` as an informational
  note; it was recorded in Snapshot-016 and is unchanged.

---

## Open Questions
No new open questions this session.
- Q-011 resolved (unchanged; via DEC-019).
- Q-012 deferred (unchanged; Phase 7 ↔ Phase 8).
- Q-013 deferred (unchanged; AI / agent-surface home).

---

## Assumptions
- Assumption: the canon write faithfully reflects the
  human-confirmed DEC-020 scope; no surface, rule, rename, or
  flag was added, dropped, or altered beyond that decision.
- Assumption: no Phase 1 domain truth, ownership, or boundary
  was modified. The inventory references Phase 1 (CRM, Finance,
  Governance), Phase 4 (provider/channel/model), and Phase 5
  (Client Brain) at reference altitude only.
- Assumption: Permission Matrix population remains deferred
  until Phase 1 Governance rules in `domains.md` are concrete;
  this session did not change that deferral.
- Assumption: the persona reuse patterns recorded in the
  inventory are a Phase 2 surface property and do not constitute
  the populated Permission Matrix.

---

## Risks

### R-023 (carried forward, active, reduced)
Phase 2 may drift into Phase 3 Capability Map or Phase 6
Workflow Design territory as detail is populated. Mitigation
strengthened this session: the granularity rule, naming
convention, persona reuse vocabulary, and the Agent & Workflow
Monitor rename sharpen the altitude marker. Keep active through
Phase 2 refinement.

### R-025 (carried forward, active)
Session close-out is applied by discipline, not enforced by
tooling. Mitigation: `workflows/sync-protocol.md` codifies the
procedure; extending it to formalize tracker backfill at
close-out remains a candidate (carried from Snapshot-015/016).

### R-026 (carried forward, active)
`workflows/sync-protocol.md` references Linear MCP tools by
logical name; if those names change, its Tooling section must
be updated.

---

## Next Focus
1. Remaining KNI-14 sub-items, in order:
   portal contents per persona,
   then concrete Cross-Domain Views (which will resolve the
   *Reports & Analytics Surface* and *Team Performance /
   Oversight Surface* flags).
2. Permission Matrix population remains deferred until Phase 1
   Governance rules in `domains.md` are concrete.
3. Revisit the 5 flagged Operating Surfaces in their owning
   sessions; do not silently fold them into the firm inventory.
4. Carry the Future Personas placeholder and the deferred
   navigation sub-detail (notification routing, deep-linking)
   forward as marked future items.
5. Keep Claude Project input limited to high-signal current
   files; prepare later controlled handoff to Claude Code.
