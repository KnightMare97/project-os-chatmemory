# Normalization Pass v1 Plan

## Purpose
This file defines the scope of Normalization Pass v1
for Phase 1 Domain Discovery.

The goal is to stabilize `domains.md`
without reopening broad discovery
and without inventing new architecture.

---

## In Scope
Normalization Pass v1 may do the following:

- remove duplicated definitions
- keep one canonical definition for major architectural terms
- align wording across Domain sections
- normalize repeated section naming patterns
- consolidate repeated cross-domain concept explanations
- reduce structural inconsistency
- improve readability and reference flow
- preserve explicit Assumption, Open Question, and Risk labels

---

## Out of Scope
Normalization Pass v1 must not do the following:

- invent new Domains
- invent new Bounded Contexts without existing evidence
- finalize unresolved ownership questions prematurely
- force final Aggregate boundaries
- resolve Brand placement beyond current evidence
- resolve final Client Brain ownership beyond current evidence
- resolve final Service Agreement ownership beyond current evidence
- introduce Phase 2+ architecture into Phase 1 cleanup

---

## Concepts Requiring Canonical Treatment
These concepts should have one primary canonical explanation
and should not be redefined in conflicting ways across `domains.md`:

- Domain
- Subdomain
- Bounded Context
- Entity
- Candidate Aggregate
- Memory Object
- Shared Service / Shared Service Artifact
- Business Artifact
- Domain Artifact
- Capability
- Workflow
- Plugin
- Provider
- Client
- Client Account
- Client Relationship
- Client Brain
- Engagement Scope
- Service Agreement
- Brand
- Human Operator

---

## Structural Goals
Normalization Pass v1 should improve:

- heading consistency
- section ordering consistency
- terminology consistency
- cross-reference consistency
- distinction between identity, memory, execution, and governance concepts

---

## Discovery Preservation Rule
If normalization reveals a true missing Domain
or a truly missing critical boundary,
mark it explicitly as:

- Assumption
- Open Question
- Risk
- Follow-up Discovery Item

Do not silently redesign the file during normalization.

---

## Desired Outcome
After Normalization Pass v1:

- `domains.md` remains the source of truth
- duplicated definitions are reduced
- the canonical classification layer becomes the main reference point
- cross-domain concepts are easier to interpret consistently
- remaining unresolved issues stay visible without destabilizing the model

---

# Execution Checklist v1 for Claude Code

## Purpose
This section defines the constraints, preservation rules,
out-of-scope rules, and acceptance gate
that Claude Code must follow
when performing the normalization pass on `domains.md`.

It must be read and followed in full
before any normalization work begins.

This checklist is a Phase 9 operating artifact
serving a Phase 1 content task.

---

## Operating Model
Normalization must not update `domains.md` directly.

The required operating sequence is:
1. produce a proposed normalized draft as a separate file
2. produce a review summary alongside it
3. await human review and explicit approval
4. only replace `domains.md` after explicit acceptance

The proposed draft file should be named:
- `domains-normalized-draft.md`

The review summary file should be named:
- `domains-normalization-review-summary.md`

Both files should be placed in the working directory
until explicitly accepted.

Neither file replaces `domains.md` until the human confirms acceptance.

---

## Pre-Pass Requirements
Before beginning normalization, Claude Code must confirm:

- [ ] `domains.md` is the current active source of truth for Phase 1
- [ ] the latest relevant snapshot has been read
- [ ] `Faraz-OS-Canon.md` has been read
- [ ] this checklist has been read in full
- [ ] the canonical classification rules inside `domains.md` are understood
- [ ] the following unresolved draft boundaries are noted
      and will remain draft throughout the pass:
  - final Client Brain ownership
  - final Brand placement
  - final Service Agreement ownership
  - final Aggregate boundaries
  - some cross-domain operational ownership details

---

## Preservation Rules

### Canonical Distinctions
The following concepts must remain clearly distinct
and must not be collapsed, merged, or redefined:

- Domain
- Subdomain
- Bounded Context
- Entity
- Candidate Aggregate
- Memory Object
- Shared Service / Shared Service Artifact
- Business Artifact
- Domain Artifact
- Capability
- Workflow
- Plugin
- Provider

If a section uses these terms inconsistently,
align it to the canonical classification rules
already present in `domains.md`.
Do not redefine the canonical rules themselves.

### Draft Markers
All existing instances of the following markers must be preserved:

- Assumption
- Open Question
- Risk
- Draft
- Candidate

If normalization finds an implicit assumption or unresolved question
that is not yet marked,
add the appropriate marker
rather than treat the item as resolved.

### Architectural Intent
Normalization must not change the intended meaning
of any section, boundary decision, or classification direction.

If wording is simplified,
the simplified version must carry the same architectural meaning
as the original.

---

## Out-of-Scope Rules
Claude Code must not do any of the following
during the normalization pass:

- invent new Domains
- invent new Bounded Contexts without existing evidence
- invent new Entities or Aggregates
- finalize Client Brain ownership
- finalize Brand placement
- finalize Service Agreement ownership
- finalize any Aggregate boundary currently marked as candidate or draft
- resolve any Open Question silently
- remove any Risk or Assumption without replacing it
  with an explicit explanation in the review summary
- introduce Phase 2 or later architecture into Phase 1 content
- change the meaning of a boundary decision
  even if the current wording is imprecise
- restructure the ordering of major sections
  unless section ordering inconsistency was an explicit normalization target

---

## Minimal-Diff Expectations

Prefer:
- removing a duplicated definition over rewriting both instances
- aligning wording to the canonical classification rules
  already present in `domains.md`
- consolidating a repeated cross-domain explanation
  into one reference location
- fixing heading inconsistency without changing heading meaning

Avoid:
- rewriting a section from scratch when targeted edits would suffice
- changing wording that is already consistent and clear
- adding new explanatory content that was not present before
- removing content that is imprecise but not harmful

If a section cannot be normalized without a broad rewrite,
leave it unchanged and flag it in the review summary
as requiring a separate targeted decision.

---

## Handling Open Questions, Risks, Assumptions,
## and Follow-up Discovery Items

### Existing Open Questions
Preserve exactly as written.
Do not reword, consolidate, or remove existing Open Questions
unless two are exact duplicates.
If consolidating duplicates, keep one and note the consolidation
in the review summary.

### Existing Risks
Preserve exactly as written.
Do not remove a Risk even if it appears to have been mitigated.
If a Risk appears resolved,
flag it in the review summary for human decision.

### Existing Assumptions
Preserve exactly as written.

### Follow-up Discovery Items
If normalization reveals a true missing boundary,
a genuinely missing concept,
or a meaningful inconsistency that cannot be resolved
through wording alignment alone:

Default handling:
Record these items in the review summary.
If preserving architectural meaning in the proposed draft
requires an explicit marker,
the item may also be surfaced in the proposed draft
using clear Draft, Open Question, Risk,
or Follow-up Discovery labeling.
Do not silently redesign the file.
Do not treat the item as resolved.

---

## Review Summary Requirements
The review summary file (`domains-normalization-review-summary.md`)
must cover the following sections:

### Changes Made
For each change:
- what was changed
- where it was changed
- why it was changed
- what canonical rule it aligns to

### Items Left Unchanged
For each item considered but not changed:
- what was considered
- why it was left unchanged

### Duplicate Definitions Consolidated
For each consolidation:
- what was duplicated
- which instance was kept
- which instance was removed or redirected

### Draft Boundaries Confirmed Preserved
Explicit confirmation that the following remain draft and unchanged:
- Client Brain ownership
- Brand placement
- Service Agreement ownership
- Aggregate boundaries

### Follow-up Discovery Items
Any items found during normalization that reveal a missing boundary,
inconsistency, or architectural question
requiring a separate decision.

### Residual Ambiguity
Any remaining ambiguity that normalization did not resolve
and that a human should be aware of before accepting the draft.

---

## Acceptance Gate
The proposed normalized draft must not replace `domains.md`
until all of the following are true:

- [ ] human has read the review summary
- [ ] human has confirmed that draft boundaries remain intact
- [ ] human has confirmed that no Open Questions were silently resolved
- [ ] human has confirmed that no canonical distinctions were collapsed
- [ ] human has reviewed any Follow-up Discovery Items
- [ ] human has explicitly stated acceptance

---

## Failure Modes to Watch For
Claude Code should self-check for these during the pass:

- treating "Candidate Aggregate" and "Aggregate" as interchangeable
- treating "Memory Object" as equivalent to "Entity" or "Aggregate"
- treating "Domain Artifact" as equivalent to "Domain"
- treating "Business Artifact" as a resolved classification
- removing "Draft" or "Candidate" labels to improve wording cleanliness
- consolidating two genuinely distinct concepts
  because their names sound similar
- silently choosing one interpretation of an ambiguous boundary
  instead of preserving the ambiguity and flagging it
- treating the absence of a Risk marker
  as evidence that a risk has been resolved

---

## Checklist Completion Confirmation
Before submitting the proposed draft and review summary,
Claude Code must confirm:

- [ ] all preservation rules were followed
- [ ] all out-of-scope rules were respected
- [ ] all Open Questions, Risks, and Assumptions are present
      in the proposed draft
- [ ] the review summary covers all required sections
- [ ] no unresolved boundary was silently finalized
- [ ] the proposed draft file is named `domains-normalized-draft.md`
- [ ] the review summary file is named
      `domains-normalization-review-summary.md`
- [ ] neither file has replaced `domains.md`
- [ ] this checklist was followed in full
