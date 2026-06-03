## CRM (Draft v2)

### Domain Position
CRM is a Domain responsible for managing relationship-facing
commercial records and pipeline visibility across the client lifecycle.

At this stage, CRM should be modeled as having two major parts:
- Lead Acquisition & Conversion
- Current Client Management

The current implementation strongly supports
Lead Acquisition & Conversion.

Current Client Management is valid as part of the CRM Domain,
but remains less mature and more draft in the current system.

---

### Responsibilities
CRM is responsible for managing the relationship and commercial-facing layer
between Faraz and prospects, leads, current clients, and client accounts.

It is responsible for:
- lead intake
- lead qualification flow
- sales pipeline stage tracking
- follow-up scheduling
- manager assignment for lead handling
- interaction and call summary tracking
- dead lead archiving and recheck flow
- commercial relationship visibility
- current client account visibility
- client status visibility
- service history visibility at CRM level
- client-facing stakeholder/contact visibility
- sales and CRM dashboard reporting

CRM is not responsible for:
- service delivery execution
- persistent strategic memory ownership
- Engagement Scope ownership
- workforce identity ownership
- financial ledger ownership
- channel credential ownership
- raw analytics warehouse ownership

---

### What it owns
CRM owns the source of truth for:
- lead records
- lead pipeline state
- lead follow-up state
- lead interaction history
- dead lead archive entries
- manager-to-lead handling visibility
- current client account records
- client contact records
- account lifecycle status
- high-level service relationship visibility
- CRM dashboard and reporting views

CRM may reference but should not own:
- Client Brain
- Engagement Scope
- workforce operator profiles
- financial contracts or ledger records
- publishing state
- knowledge artifacts
- secrets and credentials

---

### Bounded Contexts

#### Lead Acquisition & Conversion
This Bounded Context is responsible for:
- lead capture
- channel/source tracking
- qualification flow
- sales stage progression
- follow-up management
- signal-based prioritization
- manager work queue visibility
- conversion to signed client or dead lead

This is the strongest and most grounded part
of the current CRM implementation.

#### Current Client Management
This Bounded Context is responsible for:
- active client account visibility
- current client contact and stakeholder visibility
- client status tracking
- client service relationship visibility
- relationship notes at CRM level
- commercial continuity and retention visibility

This part is valid as a CRM concern,
but is still more draft and less explicit
in the current implementation.

#### Dead Lead Recovery
This Bounded Context is responsible for:
- dead lead archive management
- dead reason tracking
- recheck scheduling
- lead reactivation back into pipeline

#### CRM Reporting & Dashboarding
This Bounded Context is responsible for:
- sales summary visibility
- manager performance visibility
- service demand visibility
- active pipeline reporting
- conversion-facing dashboard views

---

### Candidate Entities

#### Lead Acquisition & Conversion
- Lead
- Lead Source
- Lead Stage
- Follow-up Schedule
- Signal
- Interaction Note
- Manager Assignment
- Dead Lead Archive Entry

#### Current Client Management
- Client Account
- Client Contact
- Stakeholder
- Client Status
- Service Relationship Record
- Account Note

#### Shared or Cross-Context Candidates
- Manager
- Service Selection
- Relationship Timeline Entry

---

### Candidate Aggregates

#### Lead Aggregate
Possible contents:
- Lead
- source
- stage
- follow-up state
- signal
- interaction summary
- assigned manager
- requested services
- notes

#### Dead Lead Aggregate
Possible contents:
- Dead Lead Archive Entry
- dead reason
- dead date
- recheck date
- previous manager ref
- reactivation state

#### Client Account Aggregate
Possible contents:
- Client Account
- contact refs
- stakeholder refs
- client status
- service relationship summary
- account notes

#### Manager Queue Projection
This is likely not an Aggregate.

It is better treated as a read model or operational projection
generated from pipeline data.

#### CRM Dashboard Projection
This is likely not an Aggregate.

It is better treated as a reporting projection
generated from CRM records.

---

### Notes on Key Terms

#### Domain
CRM is a Domain.

It should not be reduced to only a spreadsheet implementation,
even if the current operational system is built on Google Sheets
and Apps Script.

#### Bounded Context
Lead Acquisition & Conversion
and Current Client Management
should be treated as separate Bounded Contexts
inside the CRM Domain.

#### Entity
Lead is a strong candidate Entity
in the current implementation.

Client Account is also a valid candidate Entity,
but currently less evidenced in the implementation.

#### Aggregate
Lead Aggregate is the strongest candidate Aggregate
in the current CRM system.

Client Account Aggregate is a valid candidate,
but remains more draft.

#### Memory Object
Client Brain is not a CRM Entity or CRM Aggregate.

It is a separate Memory Object
that may reference CRM records
but should not replace CRM ownership.

#### Shared Service
CRM Dashboarding behaves more like a reporting view
or projection than a Shared Service.

It should not be mistaken for the CRM Domain itself.

---

### Inbound events
Candidate inbound events to CRM:
- lead captured
- lead manually created
- lead updated
- source recorded
- signal updated
- follow-up scheduled
- follow-up completed
- stage advanced
- stage reverted
- lead marked dead
- dead lead recheck triggered
- dead lead reactivated
- manager assigned
- manager changed
- client converted from lead
- current client updated
- client contact updated
- stakeholder updated
- service relationship updated

---

### Outbound events
Candidate outbound events from CRM:
- lead created
- lead qualified
- lead became overdue
- lead requires follow-up today
- lead converted to client
- lead moved to dead archive
- dead lead scheduled for recheck
- dead lead reactivated
- manager queue changed
- client account created
- client status changed
- client relationship updated
- CRM dashboard updated

---

### Risks
- If CRM is modeled only around the current implementation,
  Current Client Management may be underrepresented.
- If CRM is modeled too broadly,
  it may incorrectly absorb Client Brain responsibilities.
- Lead pipeline logic is strongly evidenced,
  but client account modeling is still structurally lighter.
- Manager queue views and dashboard views
  may be mistaken for source-of-truth aggregates
  when they are better treated as projections.

---

### Open Questions
- When a lead becomes a signed client,
  does Lead evolve into Client Account,
  or does a new Client Account Entity get created?
- How much of current client management
  should remain inside CRM
  versus move into Client Success?
- Should Service Relationship Record stay inside CRM
  as a commercial/account view,
  while Engagement Scope remains in Service Delivery?
- What is the exact boundary between:
  - CRM Client Account
  - Client Success account handling
  - Client Brain memory ownership

---

### Implementation Grounding Notes
The current operational backend strongly supports:
- pipeline stages
- follow-up dates
- manager assignment
- signal scoring
- dead lead archive
- recheck cycle
- manager tabs
- CRM dashboard reporting

The current operational backend provides weaker evidence for:
- rich client account structure
- standalone brand modeling
- explicit service agreement artifacts
- mature current-client account management structures

Therefore:
- Lead Acquisition & Conversion is implementation-grounded
- Current Client Management is architecturally valid,
  but still draft and extensible
