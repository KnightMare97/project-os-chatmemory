# Brainstorm — Q-018: Client Asset domain ownership (2026-06-08)

**Status:** Working reasoning behind DEC-033. Immutable history once landed; cites
resolve against the landing commit. Not canon.

## Why this surfaced
Ali's asset/media/upload questions (client file storage per-client + client upload;
OS composes IG stories from raw/AI/uploaded media; video footage uploaded to the
client portal → notify the editor) hit a wall in the read-only recon: **canon owns no
Client Asset entity.** It carries only:
- asset *references* — `relevant_assets_refs` under Engagement Scope → Operational
  References (`domains.md:517`);
- asset *production* — Content / Video Creation "produce a … asset"
  (`capabilities.md:121-125`, `:172-176`), both serving Service Delivery.

The three-lens gap analysis (`grounding/Gap-Analysis-and-Roadmap.md`, non-canon) ranked
this the #1 first gated decision: it both blocks the Phase-7 Data Architecture view
(which can't architect asset storage / scoping / ingest / retention without an owning
domain to reference — inversion guard, DEC-031 G-1) and is the first instance of the
~10 Phase-1 entity reopenings the register implies.

## Candidate owners considered
- **Service Delivery** (`domains.md:3253`) — owns execution of agreed client work; the
  producing capabilities serve it. Strong for *produced deliverables*, but assets also
  include raw uploads, client-uploaded content, and AI-generated media that aren't
  "execution state."
- **Knowledge** (`domains.md:1225`) — owns reusable structured memory, explicitly "not
  merely a document file" (`:1378-1380`). Weak for the raw media artifact; it owns
  knowledge *about* assets (= Asset Intelligence, P5), not the asset itself.
- **CRM / Client Success** — client relationship/context; weak for produced
  deliverables.
- **A new Assets/Media domain** — if the asset (with rights / provenance / retention /
  lifecycle across all media states) warrants first-class ownership of its own.

## The fault line
Asset *entity* (storage-bearing artifact + rights/retention/provenance — Phase-1 domain
truth) vs asset *intelligence* (derived knowledge — Phase-5 Asset Intelligence). The
register pushes on both; Q-018 separates them.

## Ruling (reviewer; Ali delegated)
- **G-2 owner = (B) a new domain, *Media & Assets*.** Assets span raw / uploaded /
  AI-generated / produced and carry rights / provenance / retention as first-class
  domain truth — heavier than "deliverable execution state" (Service Delivery) and
  distinct from "structured knowledge" (Knowledge). A dedicated domain keeps the
  five-seam boundary clean and avoids overloading Service Delivery.
- **G-3 = (B) Asset Intelligence stays deferred.** Resolve the Phase-1 owner first
  (that's what unblocks the Phase-7 Data view); un-defer Asset Intelligence separately
  when its memory structure is actually needed (mirrors the Feature-Modules un-defer
  discipline — minimal change now).
- **Structural gates confirmed:** one entity across all media states; references
  unchanged; the five-seam boundary; scoping / retention / dual-path
  referenced-not-decided; carried set untouched.

## Scope discipline
DEC-033 resolves **Client Asset only.** The other ~9 reopenings (Engagement/Community,
Service Agreement → firm [Q-002], Brand [Q-003], Campaign, Cost-ledger/Prompt, Ticket,
Ad-Account, Schedule, Consent) are each their own future gated decision. R-027 set and
Q-002 / Q-016 / Q-017 carried, untouched.

## Landing shape (DEC-026 / DEC-027 precedent)
- Landing (i) — this package: the isolated `domains.md` ownership edit + DEC-033 +
  Q-018 registration/resolution + Current-State + this brainstorm, in one called-out
  commit.
- Landing (ii) — later, separate: the Phase-7 Data Architecture view consumes the now-
  owned Media & Assets entity.
