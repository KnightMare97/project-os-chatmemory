# Snapshot-007 - Claude Code Operating System Ownership for Normalization Work

## Current Phase
Phase 9 Claude Code Operating System

## Current Topic
Where normalization handoff and controlled AI document editing should live

## Status
Clarified

The current working conclusion is that normalization execution guidance
should not remain only as an implicit note inside Phase 1 discovery materials.

It should also be treated as a Phase 9 concern,
because controlled AI-assisted editing,
session discipline,
snapshot usage,
prompt handoff,
and review flow belong to the Claude Code Operating System layer.

---

## Purpose
This snapshot clarifies where the operational rules
for AI-assisted normalization work should live.

It does not move ownership of `domains.md`
out of Phase 1 Domain Discovery.

It clarifies that the execution method
for how Claude Code should later perform normalization
belongs to Phase 9.

---

## Decisions

### DEC-024 Draft
Phase 1 Domain Discovery owns the content being normalized.

This includes:
- `domains.md`
- domain boundaries
- candidate Entities
- candidate Aggregates
- candidate Bounded Contexts
- cross-domain concept treatment
- readiness for normalization

### DEC-025 Draft
Phase 9 Claude Code Operating System should own
the operating method for how AI-assisted normalization is executed.

This includes:
- snapshot-aware editing discipline
- session protocol
- prompt handoff format
- Plan Mode
- Build Mode
- Review Mode
- controlled edit behavior
- review-oriented AI collaboration rules

### DEC-026 Draft
Normalization planning may be referenced from Phase 1,
but the reusable operating pattern for performing that normalization with Claude Code
should ultimately be defined in `claude-operating-system.md`.

This avoids scattering AI operating procedure
across architecture content files.

---

## Findings

### FIND-049
A useful distinction is:

- Phase 1 owns **what** is being modeled and normalized
- Phase 9 owns **how** Claude Code should perform the work

### FIND-050
This separation reduces confusion between:
- architecture content
- architecture editing procedure
- AI collaboration protocol

### FIND-051
If normalization procedure stays only inside Phase 1 artifacts,
the operating pattern may become duplicated later
when the same AI-assisted editing model is needed for other files.

### FIND-052
Placing the reusable execution method inside Phase 9
is more consistent with the Canon structure,
which already reserves Phase 9 for:
- Snapshot
- Session Protocol
- Plan Mode vs Build Mode vs Review Mode
- Prompt Handoff Format
- Rules

---

## Assumptions

- Assumption: `domains.md` remains a Phase 1 source-of-truth artifact.
- Assumption: normalization of `domains.md` is still a Phase 1 content task.
- Assumption: Claude Code execution procedure belongs to Phase 9.
- Assumption: future AI-assisted document normalization for other files may reuse the same operating pattern.

---

## Risks

### R-016
If Phase 1 and Phase 9 responsibilities are mixed,
content ownership and execution ownership may blur.

### R-017
If Claude Code normalization rules are documented only inside Phase 1 snapshots,
the same procedure may need to be redefined again later.

### R-018
If Phase 9 does not absorb this operating pattern,
Claude Code usage may remain session-specific
instead of becoming a reusable system practice.

---

## Open Questions

### Q-024
Should `claude-operating-system.md`
contain a dedicated section for AI-assisted document normalization tasks?

### Q-025
Should normalization prompts for major canon files
be standardized under one reusable handoff structure?

### Q-026
Should the first implementation example inside Phase 9
use `domains.md` normalization as the reference case?

---

## Next Focus
The next recommended focus is:

- keep Phase 1 as the owner of `domains.md` content
- move reusable Claude Code normalization procedure into Phase 9
- later define the normalization operating pattern inside `claude-operating-system.md`
- keep future AI-assisted editing rules reusable rather than file-specific
