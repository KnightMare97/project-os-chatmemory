# Claude Project Workflows

## Purpose
This file defines reusable workflows
for working with Faraz OS inside Claude Project
and for handing approved work to Claude Code.

It exists to make repository collaboration:
- consistent
- low-risk
- reviewable
- handoff-ready

It should be used together with:
- `CLAUDE.md`
- `Current State.md`
- `Faraz-OS-Canon.md`
- current canon files
- latest relevant snapshots

---

## Source-of-Truth Reminder
Always interpret repository truth in this order:

1. latest relevant snapshot
2. `Faraz-OS-Canon.md`
3. current phase files in `Faraz-OS-Canon/`
4. refreshed root summary files

Do not let stale bootstrap files,
archive files,
or older parallel summaries
override newer canon or snapshots.

---

## Default Working Pattern
Use this default workflow for important tasks:

1. understand current context
2. identify exact file scope
3. propose a plan
4. apply only constrained changes
5. review for drift,
   ambiguity,
   and canon conflict
6. decide whether a new snapshot is needed

---

## Workflow 1: Update Repository Memory Files

### When to Use
Use this workflow after a meaningful discussion
that may have changed:
- findings
- decisions
- open questions
- current status
- snapshot-worthiness

### Prompt
```text
We are updating the repository memory files for Faraz OS.

Use these rules:
- Follow source-of-truth priority:
  1. latest relevant snapshot
  2. Faraz-OS-Canon.md
  3. current phase files in Faraz-OS-Canon/
  4. refreshed root summary files
- Preserve the distinction between Domain, Subdomain, Bounded Context, Entity, Candidate Aggregate, Capability, Workflow, Plugin, Provider, Memory Object, Shared Service / Shared Service Artifact, Business Artifact, and Domain Artifact.
- Do not invent architecture beyond repository evidence.
- Do not silently finalize unresolved boundaries.
- Prefer minimal diffs over broad rewrites.
- Keep open questions visible if they are still unresolved.
- If something is weakly supported, mark it as Assumption, Open Question, or Risk.

Task:
Review the recent conversation and repository context,
then identify:
- new findings
- new decisions
- resolved open questions
- newly created open questions
- whether a new snapshot is warranted

Output format:
1. PLAN MODE
   - What changed
   - Which files should be updated
   - Why each update is justified
2. PROPOSED FILE UPDATES
   - For `findings.md`
   - For `decisions.md`
   - For `open-questions.md`
   - For `snapshots.md` only if needed
3. SNAPSHOT RECOMMENDATION
   - yes or no
   - if yes, provide a proposed snapshot title and a draft structure
4. REVIEW MODE
   - identify any ambiguity
   - identify any conflict with canon or recent snapshots
   - identify anything that should not yet be turned into a decision

Important:
Do not rewrite whole files unless necessary.
Prefer append, refine, mark obsolete, or move items.
Preserve existing IDs where meaning has not materially changed.
```

---

## Workflow 2: Update Findings

### When to Use
Use this workflow when the session produced
new interpretation,
new repository understanding,
or new architecture-relevant observations.

### Prompt
```text
Update `findings.md` based on the recent session.

Rules:
- Only include current, still-relevant findings.
- Do not duplicate snapshot history.
- Prefer minimal diffs.
- Do not convert a finding into a decision unless it is explicitly resolved.
- If a previous finding is now stale, mark it for removal or relocation.

Output:
1. PLAN MODE
2. Proposed minimal-diff update for `findings.md`
3. REVIEW MODE with any ambiguity or weak evidence
```

---

## Workflow 3: Update Decisions

### When to Use
Use this workflow only when something
has actually become decided.

Do not use it for mere direction,
preference,
or early interpretation.

### Prompt
```text
Update `decisions.md` based on the recent session.

Rules:
- Only add items that are genuinely decided.
- Do not treat directional preference as a final decision unless explicitly established.
- Preserve existing decision IDs where wording is refined but meaning stays the same.
- If meaning materially changes, propose a new decision ID.
- Prefer minimal diffs.

Output:
1. PLAN MODE
2. Proposed minimal-diff update for `decisions.md`
3. REVIEW MODE
   - identify anything that looks like a finding rather than a decision
   - identify anything that remains open
```

---

## Workflow 4: Update Open Questions

### When to Use
Use this workflow when unresolved questions
have appeared,
changed,
been resolved,
or become obsolete.

### Prompt
```text
Update `open-questions.md` based on the recent session.

Rules:
- Keep only active, still-relevant unresolved questions.
- Move resolved items out of open questions.
- Do not keep historical or obsolete questions here.
- Prefer one canonical entry per unresolved issue.
- Prefer minimal diffs.

Output:
1. PLAN MODE
2. Proposed minimal-diff update for `open-questions.md`
3. REVIEW MODE
   - identify which questions are newly opened
   - identify which questions may now be resolved
   - identify any question that belongs in snapshots instead
```

---

## Workflow 5: Decide Whether to Create a Snapshot

### When to Use
Use this workflow when the session may have produced:
- an important decision
- an important finding
- a meaningful topic shift
- a major structural clarification
- a significant handoff-state change

### Prompt
```text
Determine whether the recent session warrants a new snapshot.

Rules:
- Recommend a snapshot if the session produced:
  - an important decision
  - an important finding
  - a meaningful topic shift
  - a major structural clarification
  - a material handoff state change
- Do not recommend a snapshot for trivial discussion.
- Align with repository snapshot discipline.

If a snapshot is warranted, output:
1. Proposed snapshot title
2. Current phase
3. Current topic
4. Status
5. Draft sections:
   - Document Updates
   - Decisions
   - Findings
   - Assumptions
   - Risks
   - Open Questions
   - Next Focus

If not warranted, explain why not.
```

---

## Workflow 6: Prepare Claude Code Handoff

### When to Use
Use this workflow when proposed repository changes
have already been clarified
and are ready for implementation.

### Prompt
```text
Prepare a Claude Code handoff for the approved repository updates.

Scope:
- [list exact files]

Constraints:
- preserve source-of-truth hierarchy
- preserve canonical distinctions
- preserve unresolved draft boundaries
- prefer minimal diffs
- do not invent architecture
- do not silently remove Assumption, Open Question, or Risk markers unless explicitly instructed

Required output:
1. PLAN MODE
   - exact edit scope
   - intended changes
   - non-goals
2. BUILD MODE
   - apply only approved changes
3. REVIEW MODE
   - summarize what changed
   - identify any residual ambiguity
   - identify anything that still needs human review
```

---

## Workflow 7: Review a Broad Change Before Approval

### When to Use
Use this workflow before accepting
any broad structural edit,
normalization pass,
or multi-file cleanup.

### Prompt
```text
Review the proposed repository changes before approval.

Check for:
- conflict with latest relevant snapshot
- conflict with `Faraz-OS-Canon.md`
- drift from current phase boundaries
- collapse of important architectural distinctions
- hidden resolution of open questions
- unnecessary broad rewriting
- duplication instead of consolidation

Output:
1. REVIEW SUMMARY
2. RISKS
3. REQUIRED FIXES BEFORE APPROVAL
4. SAFE TO IMPLEMENT? yes or no, with reason
```

---

## Normalization Safety Reminder
For normalization-related work,
always remember:

- normalization is not discovery
- normalization should improve clarity and consistency
- normalization must not invent architecture
- normalization must not silently finalize draft boundaries
- normalization should be reviewable and human-governed

---

## Recommended Usage Pattern
For most important repository tasks:

1. run PLAN MODE in Claude Project
2. inspect proposed minimal-diff updates
3. revise if needed
4. hand approved work to Claude Code if actual file edits are needed
5. run REVIEW MODE before accepting broad changes
6. create a snapshot when the session materially changed repository understanding

---

## Maintenance Rule
Keep this file practical.

Add workflows only when they are reusable.

Do not turn this file
into a duplicate of `CLAUDE.md`
or a duplicate of snapshot history.
