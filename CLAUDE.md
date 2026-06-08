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

The canonical phase map is defined in `Faraz-OS-Canon.md`
and currently spans Phase 0 through Phase 11.

Phase 1 Domain Discovery is complete.
Normalization pass v1 on `domains.md` has been
applied and accepted (see Snapshot-010).
`domains.md` is the accepted source of truth
for the Phase 1 domain model and must not be
re-normalized or re-discovered
without a new explicit decision.

The most active current work is
Phase 2 Experience Architecture.
Phase 2 should begin with a question-gate
and scoping session before any content is produced
for `experience-architecture.md`.

Unresolved Phase 1 draft boundaries remain draft
until separately resolved.

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
- final Client Brain partitioning — per Client / per Brand / both
  (Q-004, entangled with Q-003 Brand placement); Client Brain
  *ownership* is resolved to Knowledge (DEC-027) and is no longer draft
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

## Session Close-Out and Sync Discipline
Faraz OS uses two synchronized tracking layers:

- GitHub repository is the source of truth.
- Linear is execution tracking only.

GitHub wins on any conflict.
Linear must never silently diverge from repository truth.

When closing out a session that produced
any decision, finding, structural change,
or meaningful progress, do the following
before the session is considered closed:

1. Create a new snapshot file at:
   `snapshots/Snapshot-{NNN} - {title}.md`
   - Use the next sequential zero-padded number
     after the latest existing snapshot.
   - Use the established snapshot format:
     Current Phase, Current Topic, Status,
     Document Updates, Decisions, Findings,
     Open Questions, Assumptions, Risks, Next Focus.

2. Update `Current-State.md` to match
   the new snapshot's reality.

3. Reconcile Linear against the new snapshot:
   - update issue status, priority, labels,
     milestones, and relations to reflect
     the repository's current truth.
   - flag any deliberate divergence explicitly
     rather than leaving it silent.

Discipline:
- Propose the snapshot content and the
  `Current-State.md` diff for human review
  before committing, consistent with the
  draft-plus-review model (DEC-011).
  This propose-then-review gate applies to GATED
  close-outs (any close-out containing new decisions
  or canon content); record-only close-outs land
  per the Execution Mode section.
- Do not push or commit GATED work without explicit
  approval; record-only work lands per the Execution Mode
  section (a reviewer CLEAR counts as the go).
- Do not invent architecture in a snapshot.
  A snapshot records what happened;
  it does not finalize unresolved boundaries.
- Preserve Assumption, Open Question, and Risk
  markers exactly as they stand.

---

## Execution Mode and Approval Gates

This section persists the operating contract for AI-assisted
execution on Faraz OS so it survives session swaps.
It records how work is run; it introduces no architecture.

### Default mode
Direct execution. Claude acts as design partner, reviewer,
and direct executor. GitHub is the source of truth;
nothing is considered done until it is pushed AND verified
on `origin/main`.

### The four approval gates (GATED — require explicit go)
These four categories must not land without an explicit
human go-ahead:
1. New canon content — one content read per batch / DEC.
2. `domains.md` edits — landed as isolated, called-out commits,
   each with its own DEC (Phase 1 domain truth).
3. Structural Linear changes.
4. Procedure-file changes (e.g. this file,
   `workflows/sync-protocol.md`).

### AUTO vs GATED split
- AUTO (post-hoc, record-only): record commits, including
  same-commit tracker backfill; commit → push → verify as one
  motion once content is approved; Linear mirroring only after
  verified pushes; non-blocking questions are batched.
- GATED (the four gates above): each requires explicit go;
  canon-content batches read source before writing; structural
  and procedure changes are proposed for review before landing.

### Reviewer CLEAR as the explicit go
To reduce approval load, a reviewer CLEAR (the byte-read review
approval) counts as the explicit go for the lower-risk classes:
- record-only close-outs (snapshot + `Current-State.md` +
  same-commit tracker backfill);
- record commits and tracker backfills;
- reference-altitude knock-on refreshes (e.g. citation-pointer
  updates after a landed decision).
Ali's explicit go remains required only for: new canon content
batches (incl. `domains.md` Phase-1 edits); procedure-file changes
(incl. this file); structural Linear changes; and posture /
architecture calls.

### Evidence discipline
Report only raw command output. Nothing is "done" until it is
pushed and verified on `origin/main` with raw output shown.
GitHub wins on any conflict; Linear never silently diverges.

### Verification discipline
- An independent verifier pass runs before commits.
- FIND-032 citation rule: after any same-session canon landing,
  re-derive all draft citations from post-landing ground truth
  and run a deterministic stale-token sweep BEFORE the verifier
  pass (LLM verifiers false-pass shifted line ranges).
- Same-commit tracker backfill is standing close-out discipline:
  trackers are reconciled in the same commit as the change they
  record, not deferred.

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

Faraz OS separates two kinds of concern
that must remain distinct:

- Architecture content phases (Phase 0 through Phase 10)
  own architecture content,
  domain interpretation,
  boundary reasoning,
  and the canonical meaning of concepts
  inside their phase files.
  Domain truth specifically lives in
  Phase 1 Domain Discovery and `domains.md`.

- Phase 11 Claude Code Operating System owns operating method,
  session discipline,
  handoff format,
  review discipline,
  and the controlled execution pattern
  for Claude Project and Claude Code work.

Working rule:
- Phase 11 may define how architecture work is planned,
  reviewed,
  constrained,
  and handed off.
- Phase 11 must not introduce new architecture
  beyond repository evidence.
- Phase 11 must not silently reinterpret
  architecture content or domain truth.
- Any change to domain meaning,
  ownership,
  classification,
  or architectural boundaries
  belongs to the owning content phase
  (domain truth belongs to Phase 1).

Decision test:
- If the question is about what something is,
  who owns it,
  where it belongs,
  or how domain boundaries should be interpreted,
  treat it as an architecture content phase question.
- If the question is about how Claude should analyze,
  propose,
  review,
  constrain,
  or hand off work,
  treat it as Phase 11 serving the content phases.

Escalation rule:
- If a task appears to mix architecture content decisions
  with Phase 11 operating-method design,
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
