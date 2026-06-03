# Snapshots

## Purpose
This file explains how snapshots should be interpreted
in this repository.

It is not the full snapshot archive.

The full chronological record lives in the `snapshots/` folder.

This file exists to define:
- the role of snapshots
- how to use them
- how they relate to canon files
- how to interpret current versus historical snapshot material

---

## Snapshot Role
Snapshots are the chronological memory layer of the repository.

They capture:
- important decisions
- important findings
- topic shifts
- handoff state
- structural changes in understanding
- preparation for later controlled execution

Snapshots preserve continuity across sessions.

They should prevent important reasoning
from existing only inside chat.

---

## Relationship to Other Files
Snapshots do not replace canonical architecture files.

Use them together with:

1. latest relevant snapshot
2. `Faraz-OS-Canon.md`
3. current phase files in `Faraz-OS-Canon/`
4. current root summary files, if refreshed and still valid

Snapshots may clarify,
interpret,
or record progress,
but they should not be treated as permission
to silently override active canon without explicit reasoning.

---

## Current Folder Role
The `snapshots/` folder is the actual chronological archive.

Each snapshot should represent a meaningful state change,
not routine note dumping.

Snapshots may include:
- current phase
- current topic
- status
- decisions
- findings
- assumptions
- risks
- open questions
- next focus

---

## Current Usage Rules
- Create a snapshot after an important decision.
- Create a snapshot after an important finding.
- Create a snapshot after a meaningful topic shift.
- Create a snapshot after a significant structural update.
- Create a snapshot when a session produces material repository impact.

Do not create snapshots for trivial chatter.

Do not leave important reasoning only in conversation
when it materially changes the repository understanding.

---

## Current Interpretation Rules
When reading snapshots:

- prefer the latest relevant snapshot
- do not assume the newest snapshot overrides everything globally
- interpret each snapshot in relation to its topic and phase
- keep canon files as the stable structural layer
- treat snapshots as the change-history and handoff layer

If two snapshots appear to conflict,
prefer the one that is:
- newer
- more directly relevant to the active topic
- better aligned with current canon

If conflict remains unclear,
mark it explicitly rather than guessing.

---

## Current Snapshot Status
The repository currently maintains
a dedicated `snapshots/` folder
containing chronological snapshot files.

Recent snapshots are especially important
for understanding the current architecture direction
and Claude Code handoff preparation.

In particular,
recent snapshot work reflects:
- stabilization of Phase 1 domain work
- readiness for normalization direction
- stronger operating-model separation between architecture content and Claude execution method

---

## Maintenance Rule
This file should stay short.

Do not turn this file into a duplicate
of the full snapshot archive.

If snapshot indexing is needed later,
create a separate snapshot index file
or enhance this file carefully
without replacing the actual archive folder.

---

## Default Guidance
When in doubt:
- use snapshots for chronology
- use canon files for structure
- use active root files for current curated summaries
- use `CLAUDE.md` for operating behavior
