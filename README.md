# project-os-chatmemory

This repository contains the working architecture canon,
snapshots,
and project memory for Faraz OS.

It is used as the structured design and handoff layer
for ongoing architecture work
and for later execution with Claude Code.

---

## Project Name
Faraz OS

## Current Status
Architecture discovery is active,
with Phase 1 Domain Discovery now mature enough
to prepare for a dedicated normalization pass.

## Primary Source of Truth
Source-of-truth priority should be interpreted as:

1. latest relevant snapshot
2. `Faraz-OS-Canon.md`
3. current phase files inside `Faraz-OS-Canon/`

Historical drafts and archive files
should not be treated as the current source of truth
unless explicitly referenced by a newer snapshot or decision.

---

## Repository Purpose
This repository is intended to:

- preserve architecture context across sessions
- keep important decisions visible
- store snapshots of evolving understanding
- support structured handoff into Claude Projects
- support later execution through Claude Code

---

## Current Repository Areas

### Root Files
Root files contain project-level memory,
working summaries,
and handoff support documents.

These may include:
- bootstrap context
- decisions
- findings
- open questions
- rules
- snapshot summaries

Some root files may become outdated over time
and should be treated carefully
until explicitly refreshed.

### `Faraz-OS-Canon/`
This folder contains phase-aligned canonical architecture files.

### `snapshots/`
This folder contains chronological snapshots
that record important changes,
decisions,
findings,
and handoff state.

---

## Working Rules
- Prefer updating existing files over creating parallel files.
- Prefer minimal diffs and explicit change proposals.
- Do not invent architecture beyond the current canon and snapshots.
- Preserve distinction between Domain, Bounded Context, Entity, Candidate Aggregate, Capability, Workflow, Plugin, Provider, Memory Object, Shared Service, Business Artifact, and Domain Artifact.
- Keep unresolved items visible as Assumption, Open Question, or Risk.

---

## Current Direction
The repository is being prepared
for more reliable AI-assisted collaboration inside Claude.

This means:
- stale bootstrap files should be refreshed
- source-of-truth hierarchy should stay explicit
- canonical files should be favored over old parallel notes
- normalization and later build handoff should follow controlled operating rules

---

## Next Expected Cleanup
The next recommended cleanup steps are:
- refresh bootstrap context
- audit root memory files
- keep one canonical summary path
- prepare Claude Code operating instructions
