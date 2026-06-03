# CLAUDE.md

## Purpose
This file defines the operating rules
for AI-assisted collaboration on Faraz OS.

It is intended for use in Claude Projects
and later Claude Code execution.

These rules govern how Claude should interpret the repository,
how it should propose changes,
and how it should avoid damaging architecture quality.

---

## Source of Truth
Use this source-of-truth priority:

1. latest relevant snapshot
2. `Faraz-OS-Canon.md`
3. current phase files in `Faraz-OS-Canon/`
4. current planning and definition files referenced by newer snapshots

Do not treat old bootstrap files,
archive files,
or stale root summaries
as authoritative
unless a newer snapshot explicitly confirms them.

---

## Repository Role
This repository is a structured architecture memory
and handoff repository for Faraz OS.

It is not just a note dump.

It exists to support:
- architecture discovery
- continuity across sessions
- explicit decisions and findings
- controlled normalization
- later implementation handoff to Claude Code

---

## Core Architectural Discipline
Always preserve distinction between:

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

Do not collapse these terms into each other.

Do not invent architecture beyond current repository evidence.

If something is unclear,
mark it explicitly as:
- Assumption
- Open Question
- Risk

---

## Working Style
Prefer:
- updating existing files over creating parallel files
- minimal diffs over broad rewrites
- explicit change proposals over silent restructuring
- canonical wording over repeated local redefinition
- preserving uncertainty over false precision

Avoid:
- speculative redesign
- hidden ownership changes
- premature finalization of draft concepts
- spreading the same definition across many files
- creating competing source-of-truth documents

---

## Current Project Direction
The current architecture work remains phase-based.

The most active current work is Phase 1 Domain Discovery.

`domains.md` remains the active source of truth
for the Phase 1 domain model.

Phase 1 has progressed to the point
where normalization is the next major expected step,
not broad new discovery.

Normalization must improve clarity and consistency
without inventing new architecture.

---

## Normalization Rules
When working on normalization tasks:

- remove duplicated definitions
- keep one canonical definition for major concepts
- align wording across sections
- improve heading consistency
- improve section ordering consistency
- reduce repeated cross-domain explanations

Do not:
- finalize unresolved ownership silently
- erase Assumption, Open Question, or Risk markers
- convert draft ideas into final truth without explicit decision
- merge distinct concepts just because they sound similar

Examples of draft areas that must remain explicit unless separately resolved:
- final Client Brain ownership
- final Brand placement
- final Service Agreement ownership
- final Aggregate boundaries

---

## Session Discipline
Work one important topic at a time.

When topic focus changes,
restate:
- current phase
- current topic

Create or update a snapshot after:
- an important decision
- an important finding
- a major structural change
- completion of a meaningful domain milestone
- a long session that materially changes repository understanding

Do not let important reasoning remain only inside chat.

Important reasoning should be captured
in the appropriate repository file or snapshot.

---

## Mode Discipline
Use this default collaboration pattern:

### PLAN MODE
Use for:
- scoping
- comparing options
- identifying source files
- defining intended edits
- clarifying risks before changes

Do not make broad edits in Plan Mode.

### BUILD MODE
Use for:
- applying approved file changes
- executing constrained edits
- consolidating wording
- updating repository files deliberately

Prefer minimal-diff edits.

### REVIEW MODE
Use for:
- auditing a draft
- checking consistency against canon
- checking source-of-truth alignment
- identifying drift,
  duplication,
  ambiguity,
  or overreach

Do not confuse review comments with approved architecture decisions.

---

## File Behavior Rules
When editing or proposing edits:

- prefer one canonical place for each major definition
- prefer latest snapshot interpretation over older repeated notes
- preserve historical files when useful,
  but do not let them override active canon
- if a root file looks stale,
  treat it as secondary until refreshed
- if a file is incomplete,
  say so explicitly rather than pretending it is complete

---

## Claude Code Handoff Rules
When preparing work for Claude Code:

- separate plan from execution
- define the exact files in scope
- define what must not change
- preserve draft boundaries
- preserve architecture distinctions
- require a short review summary after major edits

If a task is structurally broad,
prefer:
- proposed edit plan first
- implementation second
- review summary third

---

## Phase Boundary Rule

Faraz OS currently has two active concerns
that must remain distinct:

- Phase 1 Domain Discovery owns architecture content,
  domain interpretation,
  boundary reasoning,
  and the canonical meaning of concepts inside `domains.md`.

- Phase 9 Claude Code Operating System owns operating method,
  session discipline,
  handoff format,
  review discipline,
  and the controlled execution pattern
  for Claude Project and Claude Code work.

Working rule:
- Phase 9 may define how architecture work is planned,
  reviewed,
  constrained,
  and handed off.
- Phase 9 must not introduce new architecture
  beyond repository evidence.
- Phase 9 must not silently reinterpret
  Phase 1 domain truth.
- Any change to domain meaning,
  ownership,
  classification,
  or architectural boundaries
  belongs to Phase 1.

Decision test:
- If the question is about what something is,
  who owns it,
  where it belongs,
  or how domain boundaries should be interpreted,
  treat it as Phase 1.
- If the question is about how Claude should analyze,
  propose,
  review,
  constrain,
  or hand off work,
  treat it as Phase 9 serving Phase 1.

Escalation rule:
- If a task appears to mix Phase 1 content decisions
  with Phase 9 operating-method design,
  separate the content question
  from the execution-method question
  before proceeding.

---

## Response Behavior
When assisting on this repository:

- be precise
- be conservative with interpretation
- explain architectural tradeoffs clearly
- avoid fake certainty
- do not over-compress important distinctions
- surface conflicts between files when they exist

If repository evidence is weak,
say so clearly.

If multiple files disagree,
prefer the latest relevant snapshot and current canon,
then explicitly call out the conflict.

---

## Default Goal
Help Faraz OS become:
- coherent
- canonical
- handoff-ready
- Claude Code-ready
- implementation-ready
without sacrificing architectural clarity.
