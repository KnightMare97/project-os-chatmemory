# Brainstorm — Q-019: Community (post-publish audience engagement) domain (2026-06-08)

**Status:** Working reasoning behind DEC-035. Immutable once landed; cites resolve against
the landing commit. Not canon.

## Why this surfaced
The non-canon gap analysis (`grounding/Gap-Analysis-and-Roadmap.md`) ranked post-publish
audience engagement the biggest **coverage** gap: the canon workflow chain stops at
Publishing → Reporting (`workflows.md:343`); no domain owns comments / DMs / conversations;
`capabilities.md` has no community / reply capability. The entire post-publish stage
(community management, inbound lead capture, sentiment / crisis) was unmodeled. No
pre-existing open-question number — registered as Q-019 and resolved by DEC-035 in one
package.

## The three-lens trio (PM + Workflow + System)
Unanimous on the core call; reconciled on two nuances.

**G-2 owner → NEW domain (unanimous).**
- **System (the decisive frame):** the **orphan test (DEC-033)** controls; the **extend test
  (DEC-034)** fails on every candidate. CRM and Client Success are **B2B** (commercial
  pipeline / private agency↔client coordination); audience engagement is **B2C**
  (client's-audience ↔ brand, public, 1:many) — a responsibility *no existing domain has
  declared*. Intelligence owns *derived findings, not raw* interactions
  (`domains.md:1741-1742`), so it can't own the raw Comment/DM either.
- **PM:** public 1:many anonymous audience fits neither CRM's pipeline nor Client Success's
  private client channel; folding it in would distort those domains.
- **Workflow:** a dedicated owner turns the inbound-lead→CRM and crisis→incident hand-offs
  into clean domain-to-domain seams and gives the new entity cluster an unambiguous home.

**Reconciled nuance 1 — the NAME.** System lens proposed "Engagement"; PM caught that
**"Engagement Scope" already exists** as a Service-Delivery scope-of-work concept
(`domains.md:125, :172, :354`) — so "Engagement" would collide. **Reconciled: name the domain
"Community"** (collision-free; alt "Audience Engagement"). This is the kind of
classification-collapse the CLAUDE.md normalization rules forbid; the name dodges it.

**Reconciled nuance 2 — SENTIMENT ownership.** System lens flagged it **contested**: a raw
sentiment *tag* could sit on a Community interaction, but the **derived / analytical sentiment
+ crisis finding is Intelligence** (Anomaly / Trend Signal; Intelligence disowns raw
source-of-truth). **Reconciled: leave Sentiment-Signal final ownership DRAFT** — do not
silently hand Community the analytical layer.

**G-3 classification (consensus):** owns **Comment, Direct Message, Conversation/Thread
(aggregate-root candidate), Engagement Reply** as **Entities**; aggregate boundaries draft;
the reply **reuses the Publishing capability** (a reply is an outbound push,
`capabilities.md:73`) rather than implying a new dispatch capability.

**B2C ≠ B2B axis (the highest collapse-risk seam):** Community = client's-audience ↔ brand;
CRM / Client Success = agency ↔ client/prospect. Kept distinct in the boundary set.

## Scope discipline
DEC-035 resolves the **Community domain + entity set + classification ONLY** (the
DEC-033/DEC-034 pattern). Each cross-phase follow-on is its own later gate: a Phase-3
classify / engagement-reply capability; a Phase-4 inbound-channel category (all current
channels are outbound — the novel *inbound* direction); a Phase-6 8th workflow (the
post-publish engagement flow, attaching after Publishing → Reporting; dual-path load-bearing
twice — inbound capture + reply send); and Sentiment-Signal final ownership. R-027 set, Q-006,
Q-016/Q-017, and the other ~7 reopenings carried untouched.

## Landing shape (DEC-033 / DEC-034 precedent)
- Landing (i) — this package: register Q-019 + DEC-035 + isolated `domains.md` Community
  domain section + Q-019 → Resolved + Current-State + this brainstorm, one called-out commit.
- Landing (ii) — later, separate gates: the P3 capability, P4 inbound-channel, P6 8th
  workflow, and Sentiment ownership.
