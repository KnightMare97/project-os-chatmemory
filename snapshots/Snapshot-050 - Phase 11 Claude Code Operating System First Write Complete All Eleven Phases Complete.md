# Snapshot-050 — Phase 11 Claude Code Operating System: First Write Complete, All Eleven Phases Complete

## Current Phase
Phase 11 Claude Code Operating System (first write).

## Current Topic
Writing `claude-operating-system.md` (Phase 11 deliverable file): the operating
discipline under which Claude Code executes the Faraz OS build. DEC-050 mints
the Phase 11 scope gate (four rulings).

## Status
COMPLETE. `claude-operating-system.md` first write committed and pushed.
DEC-050 minted. Verified on `origin/main` at SHA `[to be filled after push]`.

**ALL ELEVEN PHASES NOW HAVE FIRST-WRITE ENTRIES.**
Phases 1–10 = architecture content. Phase 11 = Claude Code Operating System.
The Faraz OS architecture-memory repository is complete as a design canon.

---

## Document Updates

### `Faraz-OS-Canon/claude-operating-system.md` (NEW FILE)
- Phase 11 Claude Code Operating System first write: 824 lines.
- Sections: Purpose, Altitude, Boundaries, Prerequisites / Provisioning Checklist,
  The Build Repo, Agent Roles, Operating Modes, Session Protocol, Snapshot
  Discipline, Prompt Handoff Format, Development Rules, Coding Standards
  Framework, Non-Goals, Cross-Phase References, Appendix A (Build-Time
  CLAUDE.md Template).
- Provisioning checklist: plain-language enumerated list covering GCP project +
  billing, 14 APIs to enable, Firebase project, three service accounts + IAM roles,
  four categories of secrets (Cloud SQL DB password, Firebase Admin SDK SA key,
  AI model API key(s), channel API keys), secret naming convention
  `faraz-os-{env}-{block}-{type}`, secret-handling discipline, pre-build gates,
  and pre-session checklist.
- Agent roles: four operating stances (Architect / Builder / QA / Review) with
  explicit extensibility note — the model is not a closed set.
- Operating modes: Plan / Build / Review with mode-transitions table.
- Session protocol: start discipline, close-out discipline, GATED vs AUTO split.
- Snapshot discipline: build snapshots belong in the future build repo (not this
  architecture-memory repo); six-field format defined.
- Prompt handoff format: cold-start orientation template.
- Development rules: nine rules, technology-agnostic.
- Coding standards framework: universal standards (secrets, migrations, errors,
  observability, testing, bilingual) + deferred items for build-repo CLAUDE.md.
- Appendix A: Build-Time CLAUDE.md Template as a fenced code block — a spec
  to instantiate in the build repo at build-repo setup time. No CLAUDE.md was
  created or edited in this architecture-memory repo; `./CLAUDE.md` is untouched.

### `decisions.md`
- DEC-050 added: Phase 11 scope gate — four rulings.

### `Current-State.md`
- Phase 11 position updated: first-write complete.
- Current Next Focus updated: ALL 11 phases complete; next focus is Q-006 /
  Q-024 Phase-1 gates + build-repo setup.

---

## Decisions

### DEC-050 (this session)
Phase 11 scope gate: four rulings.
1. Build snapshots → build repo (architecture-memory repo stays pure design canon).
2. Agent roles = operating stances within one session + extensible model.
3. Coding standards → deferred to build-repo CLAUDE.md (framework only in Phase 11).
4. Secret naming `faraz-os-{env}-{block}-{type}` + plain-language provisioning
   checklist.

---

## Findings

### FIND-035
The architecture-memory repository is now complete as a design canon:
all eleven phases have first-write entries. Phase 11 is the final phase.
The repository is ready to support build-time handoff to Claude Code.

---

## Open Questions
No new open questions this session.

Carried open (unchanged, do not touch without explicit gate):
- Q-003 (Brand aggregate placement) — preferably before V1 schema finalization
- Q-006 (Service Agreement / Engagement Scope aggregate boundary) — mandatory
  gate before CRM domain schema write
- Q-007 (open, unchanged)
- Q-024 (Ticket ↔ Escalation Case lifecycle coupling) — mandatory gate before
  Client Success domain schema write
- Insight → durable-knowledge threshold (`domains.md:1946`)
- 4 Phase-1 entity reopenings: Campaign, Ad-Account, Schedule, Consent

---

## Assumptions
None new.

---

## Risks
None new.

Phase 10 critical-path risks remain (schema-per-client migration runner highest;
Firebase JWT → `search_path` middleware second-highest; see `roadmap.md`).

---

## Next Focus

**Architecture is complete. The next steps are build-layer:**

1. **Q-006 Phase-1 gate** — Service Agreement / Engagement Scope aggregate
   boundary. Mandatory before CRM domain schema is written in the build repo.

2. **Q-024 Phase-1 gate** — Ticket ↔ Escalation Case lifecycle coupling.
   Mandatory before Client Success domain schema is written in the build repo.

3. **Build-repo setup** — Create the separate build/code repository; instantiate
   the Build-Time CLAUDE.md Template (Appendix A of `claude-operating-system.md`);
   complete the provisioning checklist; confirm Phase 9 technology selections;
   pin coding standards in build-repo CLAUDE.md.

4. **Q-003 Phase-1 gate** — Brand aggregate placement. Before V1 schema finalization.

5. **Foundation stage build** — Begin the Faraz OS MVP Foundation stage per
   `roadmap.md`, once build repo is set up and provisioning checklist is complete.
