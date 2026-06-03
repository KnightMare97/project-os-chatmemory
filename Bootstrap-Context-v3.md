# Bootstrap Context v3

## Project Name
Faraz OS

## Repository Role
This repository is the working architecture memory,
canon,
and handoff layer for Faraz OS.

It supports:
- architecture discovery
- snapshot-based continuity
- controlled AI collaboration
- later execution handoff to Claude Code

---

## Current State
Faraz OS is currently in structured architecture design.

The current architecture work is organized by phases.

The canon currently defines:

- Phase 0: Vision & Principles
- Phase 1: Domain Discovery
- Phase 2: Extensibility Model
- Phase 3: Knowledge & Memory Architecture
- Phase 4: Capability Map
- Phase 5: Workflow Design
- Phase 6: Puzzle Board Architecture
- Phase 7: Infrastructure Design
- Phase 8: Build Roadmap
- Phase 9: Claude Code Operating System

---

## Current Working Position
The most active current architecture work is in Phase 1 Domain Discovery.

Phase 1 has progressed far enough
that the next major step is a dedicated normalization pass
for `domains.md`,
not broad new discovery.

This does not mean every boundary is finalized.

It means the current model is stable enough
that cleanup,
deduplication,
canonicalization,
and wording alignment
should now be the primary focus.

---

## Source of Truth
Interpret repository truth in this priority order:

1. latest relevant snapshot
2. `Faraz-OS-Canon.md`
3. current phase files in `Faraz-OS-Canon/`
4. explicit planning or definition files referenced by newer snapshots

Historical drafts,
archive files,
and older bootstrap files
should not be treated as current truth
unless a newer snapshot explicitly points back to them.

---

## Current High-Importance Files
At this stage,
the most important working files include:

- `Faraz-OS-Canon.md`
- `Faraz-OS-Canon/Definition of Done - Phase 1 Domain Discovery.md`
- `Faraz-OS-Canon/Normalization Pass v1 Plan for domains.md`
- latest relevant files in `snapshots/`

---

## Current Architectural Direction
Faraz OS should remain:

- AI-first but human-governed
- risk-tiered in human checkpoints
- multi-model and provider-agnostic
- routing-capable and orchestration-ready
- domain-driven
- capability-based in reuse
- plugin-ready
- event-driven in coordination
- memory-centric
- security and governance by default

---

## Current Modeling Discipline
Preserve explicit distinction between:

- Domain
- Subdomain
- Bounded Context
- Entity
- Candidate Aggregate
- Capability
- Workflow
- Plugin
- Provider
- Memory Object
- Shared Service / Shared Service Artifact
- Business Artifact
- Domain Artifact

Do not collapse these concepts into each other.

---

## Current Phase 1 Direction
For Phase 1,
`domains.md` is the active source of truth for the domain model.

The current discovery work has already established:
- core domain coverage
- canonical classification rules
- explicit treatment of sensitive cross-domain concepts
- visible draft ambiguity through Assumption, Open Question, and Risk

The next major expected step is normalization,
not broad architectural expansion.

---

## Current Normalization Direction
Normalization of `domains.md` should:

- remove duplicated definitions
- keep one canonical definition for important concepts
- align wording across domain sections
- improve heading and structural consistency
- reduce repeated cross-domain explanations

Normalization must not:
- invent new architecture
- silently finalize unresolved boundaries
- collapse meaningful distinctions
- remove important draft ambiguity markers

Normalization is expected to be handled later
through Claude Code
with explicit constraints
and human review.

---

## Important Draft Boundaries
The following are still meaningful draft areas
and should not be silently finalized:

- final Client Brain ownership
- final Brand placement
- final Service Agreement ownership
- final Aggregate boundaries
- some cross-domain operational ownership details

---

## Working Style
When contributing to this project:

- prefer updating existing files over creating parallel files
- prefer minimal diffs
- make change intent explicit
- keep snapshots meaningful
- avoid speculative redesign
- preserve visible open questions and risks

---

## Usage Note for Claude
If repository files conflict,
prefer the newest relevant snapshot
and current canon files.

If a root summary file appears stale,
treat it as secondary
until refreshed or confirmed by newer material.

If a task requires large-scale cleanup,
prefer a controlled plan first
before proposing broad edits.
