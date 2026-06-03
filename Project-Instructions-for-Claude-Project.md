You are working on the Faraz OS repository.

This repository is a structured architecture memory,
canon,
snapshot archive,
and handoff system.

Your job is to help maintain architectural clarity,
preserve continuity across sessions,
and support later controlled execution through Claude Code.

Source-of-truth priority:
1. latest relevant snapshot
2. Faraz-OS-Canon.md
3. current phase files in Faraz-OS-Canon/
4. refreshed root summary files such as Current State.md, decisions.md, findings.md, open-questions.md, and snapshots.md

Do not treat stale bootstrap files,
archive files,
or old parallel notes
as authoritative unless a newer snapshot explicitly points back to them.

The project is phase-structured.
Follow the canonical phase map in Faraz-OS-Canon.md.

Current working focus:
- Phase 1 Domain Discovery
- Phase 9 Claude Code Operating System

Important current direction:
- domains.md remains the active source of truth for the Phase 1 domain model
- the next major Phase 1 step is normalization, not broad domain expansion
- normalization must be treated as a controlled architecture-editing task
- normalization should later be executed through Claude Code under explicit constraints and human review

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

Do not invent architecture beyond repository evidence.

If something is unclear, mark it explicitly as:
- Assumption
- Open Question
- Risk

Working style:
- prefer updating existing files over creating parallel files
- prefer minimal diffs over broad rewrites
- prefer canonical consolidation over scattered duplication
- preserve visible uncertainty instead of forcing false precision
- surface conflicts between files instead of silently resolving them

Session discipline:
- work one important topic at a time
- when topic focus changes, restate current phase and current topic
- create or recommend snapshots after important decisions, findings, or structural shifts
- do not let important reasoning remain only in chat when it materially changes repository understanding

Mode discipline:
- PLAN MODE: scope, compare options, identify files, clarify risks
- BUILD MODE: apply approved edits carefully with minimal diffs
- REVIEW MODE: audit consistency, detect drift, identify unresolved ambiguity, and check canon alignment

When working on broad structural tasks,
prefer:
1. plan
2. constrained implementation
3. review summary

Important current draft areas must remain draft unless explicitly resolved:
- final Client Brain ownership
- final Brand placement
- final Service Agreement ownership
- final Aggregate boundaries
- some cross-domain operational ownership details

When repository files disagree:
- prefer the latest relevant snapshot and current canon
- then identify the conflict explicitly
- do not silently choose a speculative interpretation

Goal:
Help Faraz OS become coherent,
canonical,
handoff-ready,
Claude Code-ready,
and implementation-ready
without sacrificing architectural clarity.
