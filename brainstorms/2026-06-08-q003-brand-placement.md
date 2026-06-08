# Brainstorm — Q-003: Brand placement (2026-06-08)

**Status:** Working reasoning behind DEC-036. Immutable once landed; cites resolve against
the landing commit. Not canon.

## Why this surfaced
Q-003 (final placement of Brand) is the 4th of the ~10 Phase-1 reopenings the gap analysis
surfaced, and the highest-leverage of the remainder because resolving it **unblocks Q-004**
(Client Brain partitioning per-Client / per-Brand / both), which DEC-027 had carried as
"entangled with Q-003 … no resolving evidence in canon" (`decisions.md:1178-1179`).

## The three-lens trio (PM + Workflow + System)
Strong convergence; one reconciled divergence.

**G-2 owner → CRM (extend), NOT a new domain (unanimous).**
- **System (decisive):** the orphan test (DEC-033) FAILS — Brand isn't orphaned; CRM is SoT
  for Client identity and the Brand Decision section already leans "Client = Entity in CRM;
  Brand = Entity candidate." The extend test (DEC-034) controls: Brand is the market-facing
  identity *under* a Client — an identity concept inside CRM's commercial-relationship
  responsibility. A new "Brand domain" would fragment a bounded responsibility (the DEC-034
  anti-pattern). The **DEC-034 mirror is exact.**
- **PM:** Brand has no agency-side workflow/pipeline of its own; it's always reached through a
  Client. A domain buys nothing at single-tenant scale and slows v1.
- **Workflow:** indifferent to top-level-vs-child; only requires Brand be *addressable* so
  Engagement Scope can hold a Brand reference for multi-brand execution.

**Reconciled divergence — G-3 classification (child-entity vs standalone Entity+FK).**
PM leaned "client-scoped child Entity"; System warned that modeling Brand as a child under a
Client aggregate **pre-draws an aggregate boundary** — the exact move DEC-034 refused for
Service Agreement ("not absorbed into Client Account; aggregate-pending"). Reconciled to the
System framing, which **absorbs PM's intent**: Brand is a **first-class Entity carrying a
mandatory Client reference (FK), 1 Client : N Brand, aggregate placement draft/pending** —
every Brand has a Client parent (PM's requirement) without committing the aggregate boundary.

**G-4 identity-vs-memory seam (unanimous, load-bearing):** Brand *identity* = the CRM Entity
(holds voice/style *references*); brand *voice/tone/style content* = Client Brain, owned by
**Knowledge (DEC-027, untouched)**. Same raw-vs-derived seam as DEC-033 (asset vs asset
intelligence) and DEC-035 (raw engagement vs Intelligence finding). The Entity is the key;
Client Brain is the content keyed by it. Flagged (not edited): the Client Brain Identity
`brand_name` field becomes denormalized — a Q-004 / Phase-5 memory-pass concern.

**G-6 Q-004 → unblocked, carried.** Q-003 supplies the addressable Brand object per-Brand
partitioning needs, so Q-004 is no longer blocked — but the partitioning decision itself
(per-Client / per-Brand / both) is a Phase-5 / Knowledge call and stays open; the Phase-5
Client Brain entry stays partition-agnostic. Q-004's note updated (unblocked-by-Q-003), not
resolved.

## Scope discipline
DEC-036 resolves **Brand ownership + classification ONLY** (the DEC-033/034/035 pattern).
Separate later gates: Brand Kit → Media & Assets (DEC-033); brand-style enforcement → Phase 3
/ Governance; Brand aggregate placement → later; the `brand_name` denormalization → Q-004 /
Phase-5. DEC-027 (Client Brain → Knowledge) untouched; Q-004 carried (unblocked); the R-027
threshold, Q-006, Q-016/Q-017, and the other ~6 reopenings untouched.

## Landing shape (DEC-033 / DEC-034 / DEC-035 precedent)
One isolated called-out commit: DEC-036 + isolated `domains.md` Brand-section promotion +
`:689` narrow + Q-003 → Resolved + Q-004 note update + Current-State + this brainstorm. The
domains.md Brand-section edit shifted Media & Assets down, so the blueprint's living-doc cite
to it was re-derived in the same commit (`domains.md:3740`→`:3775`).
