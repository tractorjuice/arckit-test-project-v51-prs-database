# Project Requirements: PRS Database

> **Template Origin**: Official | **ArcKit Version**: 5.4.0 | **Command**: `/arckit:requirements`

## Document Control

| Field | Value |
|-------|-------|
| Document ID | ARC-001-REQ-v1.0 |
| Document Type | Business and Technical Requirements |
| Project | PRS Database (Project 001) |
| Classification | OFFICIAL |
| Status | DRAFT |
| Version | 1.0 |
| Created Date | 2026-05-28 |
| Last Modified | 2026-05-28 |
| Review Date | 2026-06-27 |
| Owner | Service Owner, PRS Register Service, MHCLG Digital |
| Reviewed By | [PENDING] |
| Approved By | [PENDING] |
| Distribution | PRS Register Programme Board, MHCLG Digital, MHCLG Policy (PRS Division), CDDO assurance team, LGA liaison |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-05-28 | ArcKit AI | Initial creation from `/arckit:requirements` command, traced to ARC-001-STKE-v1.0 and ARC-000-PRIN-v1.0 | [PENDING] | [PENDING] |

## Document Purpose

This document specifies the business, functional, non-functional, integration, and data requirements for the national Private Rented Sector (PRS) Database delivered under the Renters' Rights Act 2025 (UKPGA 2025/26, Part 2). It is the authoritative requirements baseline for downstream artefacts: SOBC, DPIA, ADRs, HLD/DLD, SOW, vendor evaluation, GDS service assessment, and the eventual traceability matrix. Every requirement carries a unique ID, MoSCoW priority, rationale, acceptance criteria, and traceability to stakeholder drivers (SD-/G-/O- in `ARC-001-STKE-v1.0`) and to architecture principles (P-1…P-23 in `ARC-000-PRIN-v1.0`).

---

## Executive Summary

### Business Context

The Renters' Rights Act 2025 introduces a mandatory national register of landlords and rental properties in England, owned by MHCLG. Registration becomes a precondition for serving a valid possession notice, with civil penalties from £5,000 up to £40,000 for non-compliance. The register is delivered to ~2.3M landlords, ~5.5M tenant households, ~317 local housing authorities (LHAs), and letting agents.

Delivery is phased: landlord/property registration first (rolling out area-by-area from late 2026), public tenant lookup second (within 12 months of national registration commencement). The register integrates with GOV.UK One Login (individual identity), Companies House (corporate identity), HM Land Registry (UPRN/title verification), GOV.UK Pay (fees), GOV.UK Notify (communications), HMCTS (possession notice validation), and the PRS Ombudsman.

The programme is statutory, time-pressured, regulator-scrutinised, and operates against an aggressive Ministerial commitment. The compliance surface (UK GDPR Article 35 DPIA, NCSC Secure by Design, GDS Service Standard, Technology Code of Practice, Accessibility Regulations 2018, GovS 005/007, AI Playbook + ATRS if any automated risk-scoring is added) is unusually broad.

### Objectives

- Stand up a national, statutorily compliant register that materially changes enforcement outcomes in the rental sector.
- Deliver phase 1 landlord registration in the first designated area by end of 2026; deliver public tenant lookup within 12 months of national registration commencement.
- Achieve LHA enforcement adoption ≥ 90% within 12 months of national rollout, supporting a 60% reduction in unregistered-let possession notices reaching county courts by end of Year 2.
- Operate a self-funding service from FY 2027–28 on landlord fees, with zero ICO enforcement actions in the first 24 months.
- Reuse common GOV.UK platforms (One Login, Pay, Notify, Design System) by default.

### Expected Outcomes (from `ARC-001-STKE-v1.0`)

- **O-1**: Statutory commencement dates met without slippage > 30 days.
- **O-2**: Zero ICO enforcement actions / formal reprimands in first 24 operating months.
- **O-3**: 60% reduction in unregistered-let possession notices reaching county courts by end of Year 2.
- **O-4**: 100% cost recovery from FY 2027–28.
- **O-5**: ≥ 90% LHA active monthly adoption at 12 months post national rollout.
- **O-6**: ≥ 75% landlord proportionality CSAT and ≥ 80% tenant lookup ease-of-use.

### Project Scope

**In Scope**:

- Landlord registration (individual and corporate) with identity assurance via One Login / Companies House federation.
- Property registration keyed on UPRN (or address-resolution fallback where UPRN absent), with property attributes per RRA 2025 Part 2.
- Annual fee collection via GOV.UK Pay.
- Three data views: (a) registrant self-service, (b) LHA enforcement view (full restricted scope), (c) minimum-necessary public tenant lookup.
- LHA enforcement workflow including search, watchlists, evidence assembly, and write-back of enforcement outcomes.
- Bulk registration for letting agents and portfolio landlords (API and CSV).
- HMCTS integration for registration verification on possession notices.
- PRS Ombudsman data sharing for case linkage.
- Communications and renewal reminders via GOV.UK Notify.
- Subject access, rectification, erasure, and portability handling.
- Service operations (telemetry, security monitoring, incident response).

**Out of Scope (v1)**:

- Automated risk scoring or fraud detection over personal data (governed via P-21; reserved for future controlled scope under ATRS).
- Tenant identity records or tenant accounts (lookup is unauthenticated).
- Rent regulation enforcement (separate policy stream).
- Selective licensing scheme replacement (the register supplements, not replaces, LHA selective licensing).
- Devolved nations (Wales, Scotland, Northern Ireland — register operates for England only under RRA 2025).
- AI/ML features of any kind in v1.

---

## Stakeholders

| Stakeholder | Role | Organization | Involvement Level |
|-------------|------|--------------|-------------------|
| Housing Minister | Ministerial Sponsor | MHCLG | Decision maker on statutory commencement |
| SRO, PRS Register Programme | Senior Responsible Owner | MHCLG | Accountable for delivery |
| Service Owner | Product owner, GDS assessment lead | MHCLG Digital | Day-to-day requirements authority |
| Director, PRS Policy | Policy / SI drafting lead | MHCLG Policy | Policy intent translator |
| MHCLG SIRO | Information risk owner | MHCLG | DPIA approval, residual risk acceptance |
| MHCLG DPO | Data protection lead | MHCLG | UK GDPR compliance, ICO interface |
| MHCLG CDIO | Departmental digital strategy | MHCLG | Technology assurance |
| MHCLG Cyber Lead | Security architect | MHCLG | Secure by Design, CAF, ITHC |
| LGA representative | LHA voice | Local Government Association | Enforcement workflow co-design |
| ICO | Independent regulator | ICO | DPIA scrutiny, enforcement risk |
| CDDO | Cross-government assurance | Cabinet Office | Service Standard + spend control |
| NRLA | Landlord representative body | NRLA | Sector input on scope and fees |
| Generation Rent | Tenant advocacy | Generation Rent | Public-facing scope input |
| HMT Spending Team | Spending control | HM Treasury | Cost recovery model approval |
| HMCTS | Justice integration partner | HMCTS | Possession notice integration |
| PRS Ombudsman | Redress scheme | PRS Ombudsman | Downstream consumer of register |

Full driver-to-goal traceability is in `ARC-001-STKE-v1.0` §Stakeholder Drivers Analysis.

---

## Business Requirements

### BR-001: Deliver statutory registration in first area by end of 2026

**Description**: The PRS register MUST be live and accepting landlord registrations in the first designated rollout area on or before 31 December 2026.

**Rationale**: Ministerial commitment under RRA 2025 Part 2 commencement order; central to political and statutory credibility.

**Success Criteria**:

- First-area commencement date achieved without slippage > 30 days.
- 90% of in-area landlords registered within 6 months of first-area commencement.
- GDS beta service assessment passed prior to launch.

**Priority**: MUST_HAVE

**Stakeholder**: Housing Minister, SRO. Traces to SD-1 → G-1 → O-1.

---

### BR-002: Deliver public tenant lookup within 12 months of national registration commencement

**Description**: A public, accessible, rate-limited tenant lookup service MUST be live within 12 months of national landlord registration commencement.

**Rationale**: The public lookup is the demonstrable benefit to tenants — the constituency the Act protects.

**Success Criteria**:

- Public lookup live by month-12 milestone.
- ≥ 80% tenant ease-of-use score on GOV.UK feedback widget.
- WCAG 2.2 AA conformance audit passed.

**Priority**: MUST_HAVE

**Stakeholder**: Tenants / Generation Rent. Traces to SD-12 → G-2 → O-1, O-6.

---

### BR-003: Achieve ≥ 90% LHA enforcement adoption within 12 months

**Description**: At least 90% of the 317 LHAs in England MUST be actively using the enforcement view (UI or API) within 12 months of national rollout completion.

**Rationale**: The register's enforcement value is realised only through LHA use; without adoption, the Minister has a database, not a deterrent.

**Success Criteria**:

- Active-monthly-usage rate ≥ 90% at month-12.
- API integration completed by ≥ 5 of the top 8 LHA case management system vendors.
- LHA CSAT ≥ 70%.

**Priority**: MUST_HAVE

**Stakeholder**: LHAs / LGA. Traces to SD-6 → G-3 → O-5.

---

### BR-004: Operate as a self-funding service from FY 2027–28

**Description**: From FY 2027–28 onwards, the register MUST recover 100% of operating cost (excluding initial build) from landlord registration and renewal fees, with sensitivity-tested forecast variance within ±15%.

**Rationale**: HMT spend-control condition; sustainable funding model independent of departmental settlement.

**Success Criteria**:

- Cost recovery ratio = 100% at FY end, FY 2027–28.
- Per-landlord fee published with itemised cost rationale.
- Volume forecast variance ≤ ±15%.

**Priority**: MUST_HAVE

**Stakeholder**: HMT, MHCLG Finance. Traces to SD-7 → G-5 → O-4.

---

### BR-005: Sustain zero ICO enforcement actions and a clean DPIA record across the first 24 months

**Description**: The service MUST operate without triggering ICO enforcement, formal reprimands, or NCSC-reported major incidents over the first 24 months of live operation. Article 35 DPIA MUST be approved and current at every release.

**Rationale**: A regulator enforcement action against MHCLG on this programme would destroy public/political trust in the register and is the highest-impact non-political risk.

**Success Criteria**:

- Count of ICO enforcement actions / formal reprimands = 0 across first 24 months.
- DPIA approved before each major release.
- SAR statutory turnaround ≥ 99%.

**Priority**: MUST_HAVE

**Stakeholder**: ICO, SIRO, DPO. Traces to SD-8 → G-4 → O-2.

---

### BR-006: Demonstrably reduce unregistered-let possession notices reaching county court

**Description**: By end of Year 2 of national operation, unregistered-let possession notices reaching county courts MUST fall by ≥ 60% relative to the post-launch baseline established in months 1–6.

**Rationale**: This is the policy outcome — the way Ministers prove the register has shifted sector behaviour.

**Success Criteria**:

- HMCTS data sharing operational with month-by-month tracking.
- 60% reduction achieved by month-24 of national rollout.

**Priority**: MUST_HAVE

**Stakeholder**: Director PRS Policy, Minister. Traces to SD-1 / SD-4 → G-8 → O-3.

---

### BR-007: Pass all GDS service assessments and demonstrate Technology Code of Practice compliance

**Description**: The service MUST pass cross-government GDS service assessments at alpha, beta, and live phases, and MUST satisfy all 14 points of the GDS Service Standard and the Technology Code of Practice without any Red ratings at spend control submissions.

**Rationale**: These are formal quality gates protecting Permanent Secretary defensibility, CDDO portfolio confidence, and HMT spend approval.

**Success Criteria**:

- First-time pass at each of three assessments (alpha, beta, live).
- Zero Red TCoP items at any review.
- CDDO spend control submissions approved at each gate.

**Priority**: MUST_HAVE

**Stakeholder**: Service Owner, CDDO, Permanent Secretary. Traces to SD-5 / SD-9 / SD-2 → G-6 → O-1.

---

### BR-008: Provide a proportionate, low-friction registration experience for landlords

**Description**: The registration journey MUST be perceived as proportionate by ≥ 75% of landlords surveyed in independent user research, with a median single-property registration time ≤ 30 minutes for an individual landlord and bulk-registration support for portfolio landlords and letting agents.

**Rationale**: Disproportionate friction collapses compliance, raises political opposition, and breaches user-centred design obligations under the GDS Service Standard.

**Success Criteria**:

- ≥ 75% landlord "proportionate / straightforward" CSAT.
- Median single-property registration completion time ≤ 30 minutes.
- Drop-off rate on the registration journey ≤ 15% at beta.

**Priority**: MUST_HAVE

**Stakeholder**: Landlords / NRLA, Service Owner. Traces to SD-11 → G-1 → O-6.

---

## Functional Requirements

### User Personas

#### Persona 1: Individual landlord (small portfolio)

- **Role**: Buy-to-let owner with 1–4 properties; salaried day job; digital literacy mixed.
- **Goals**: Register quickly, understand fees, avoid penalty.
- **Pain Points**: Anxiety about exposing personal address; confused by overlap with selective licensing; resentful of compliance burden.
- **Technical Proficiency**: Low–Medium.

#### Persona 2: Corporate landlord / portfolio landlord

- **Role**: Limited company or housing association with 5–thousands of properties.
- **Goals**: Bulk register, integrate with property management system, manage renewals at portfolio level.
- **Pain Points**: Manual rekeying, lack of API.
- **Technical Proficiency**: High.

#### Persona 3: Letting agent

- **Role**: Operates as authorised agent for multiple landlord clients.
- **Goals**: Register on behalf of clients, manage renewals, evidence regulatory compliance to clients.
- **Pain Points**: Authority delegation, attribution of fees, multi-tenancy in workflows.
- **Technical Proficiency**: Medium.

#### Persona 4: Tenant / prospective tenant

- **Role**: Renter searching, signing, or living in a tenancy.
- **Goals**: Verify a landlord/property before signing; report concerns; understand rights.
- **Pain Points**: Information asymmetry; fear of reprisal; accessibility needs.
- **Technical Proficiency**: Variable (must serve the lowest tier).

#### Persona 5: Local Housing Authority enforcement officer

- **Role**: Council environmental health / housing enforcement officer.
- **Goals**: Identify unregistered lets, build cases against bad actors, prioritise effort.
- **Pain Points**: Heterogeneous case management systems, capacity constraint, data quality.
- **Technical Proficiency**: Medium.

#### Persona 6: PRS Ombudsman case handler

- **Role**: Adjudicates landlord/tenant disputes referred through the Ombudsman scheme.
- **Goals**: Confirm landlord identity and registration status for case validity.
- **Pain Points**: Spurious or partial identity claims.
- **Technical Proficiency**: Medium.

#### Persona 7: HMCTS court clerk

- **Role**: Processes possession notices in county court.
- **Goals**: Validate that the landlord serving the notice is registered.
- **Pain Points**: Court process redesign, training, integration with HMCTS systems.
- **Technical Proficiency**: Medium.

#### Persona 8: MHCLG operations / programme staff

- **Role**: Service support, finance, policy admin.
- **Goals**: Service health, fee reconciliation, statistical publication.
- **Pain Points**: Operational tooling.
- **Technical Proficiency**: High.

---

### Use Cases

#### UC-1: Individual landlord registers a single property

**Actor**: Persona 1.

**Preconditions**: Landlord has a property in a designated rollout area; identity not yet verified; not previously registered.

**Main Flow**:

1. Landlord arrives on the GOV.UK landing page and starts the registration journey.
2. System authenticates the landlord via GOV.UK One Login (creates One Login account if absent).
3. System asks the landlord whether they are an individual or a company; routes appropriately.
4. System collects landlord personal data (name, contact, correspondence address) and validates against One Login identity claims.
5. System collects property details: address (UPRN-resolved), bed count, occupancy, furnishing, gas/electrical/EPC certificates, banning order disclosure.
6. System pre-fills available evidence (e.g., EPC from EPC register) where the landlord confirms consent to pull it.
7. System calculates and displays fee with itemised rationale and links to fee policy.
8. System collects payment via GOV.UK Pay.
9. System issues a registration confirmation (certificate / unique landlord registration number) via GOV.UK Notify.

**Postconditions**: Landlord record created, property record linked to landlord via UPRN, registration status active, fee receipted.

**Alternative Flows**:

- **Alt 5a**: UPRN unresolved — fall back to manual address entry; flag record for moderation.
- **Alt 8a**: Payment fails — registration retained as "pending payment" for 14 days, then expires.

**Exception Flows**:

- **Ex 1**: One Login identity check fails — registration cannot proceed; user signposted to One Login support.

**Business Rules**:

- A landlord cannot register a property without identity assurance.
- Property is keyed on UPRN; manual addresses require moderation.

**Priority**: CRITICAL

---

#### UC-2: Letting agent bulk-registers properties for client landlords

**Actor**: Persona 3.

**Preconditions**: Agent has an authorised principal-agent relationship with each landlord; agent has API credentials or CSV upload access.

**Main Flow**:

1. Agent authenticates (Persona 3 identity verified separately to landlord identity).
2. Agent uploads CSV (or POSTs to bulk API) listing landlords and properties.
3. System validates each row: UPRN resolution, landlord identity reference, required fields.
4. System creates a draft batch and returns row-level validation results.
5. Agent reviews validation, corrects errors, confirms the batch.
6. System invoices the fee total to the agent via GOV.UK Pay (single transaction or per-landlord).
7. System issues per-landlord registration certificates to landlord email of record.

**Postconditions**: Each accepted row results in a linked landlord + property + active registration.

**Business Rules**:

- Each landlord on the batch must have already established One Login or have explicit consent for the agent to act on their behalf.
- Agent attribution is recorded for every registration.

**Priority**: HIGH

---

#### UC-3: Tenant looks up a landlord/property via the public service

**Actor**: Persona 4.

**Preconditions**: Public lookup is live for the area in question; user is unauthenticated.

**Main Flow**:

1. Tenant enters a property address or postcode; or searches by landlord name (within rate limit).
2. System resolves the search to a UPRN where possible.
3. System returns minimum-necessary fields: registration status (active/expired/suspended), basic property compliance flags (gas certificate present yes/no, EPC band, banning order present yes/no), and signposting to LHA and PRS Ombudsman.
4. Tenant may follow a "report a concern" link to a structured report routed to the LHA.

**Postconditions**: Tenant has a record of the lookup time (in their browser only — not stored centrally for unauthenticated lookups beyond aggregate telemetry).

**Business Rules**:

- Public view scope is the minimum agreed via DPIA.
- No personal landlord contact details, NI numbers, or unredacted dates of birth are exposed in the public view.
- Rate limit enforced per IP / per session to prevent bulk scraping.

**Priority**: CRITICAL

---

#### UC-4: LHA enforcement officer searches for unregistered lets and assembles a case

**Actor**: Persona 5.

**Preconditions**: LHA officer authenticated via LHA federated identity; LHA jurisdiction recorded.

**Main Flow**:

1. Officer authenticates and lands in the LHA enforcement workspace (UI or API consumer).
2. Officer queries by area (postcode, ward), landlord name, address, or unregistered-status indicator.
3. System returns the full restricted record set scoped to the officer's LHA area, including evidence fields the officer's role permits.
4. Officer opens a case file, attaches evidence, raises an enforcement action, and writes it back to the register.
5. System emits an event to the LHA's case management system via the LHA API.

**Postconditions**: Enforcement action is recorded against the landlord/property, visible to other LHAs at the appropriate scope.

**Business Rules**:

- Cross-area access requires elevated role and is logged.
- Write-back actions are recorded with officer identity and timestamp.

**Priority**: CRITICAL

---

#### UC-5: HMCTS court clerk validates landlord registration during possession notice processing

**Actor**: Persona 7.

**Preconditions**: HMCTS integration live; possession notice contains a landlord identifier or property reference.

**Main Flow**:

1. HMCTS system queries register API with the landlord identifier and property reference at the time the notice is filed.
2. Register returns registration status, validity window, and any relevant flags.
3. HMCTS uses the result in its standard court process.

**Postconditions**: Court has authoritative registration evidence at point of decision.

**Priority**: CRITICAL (for BR-006 outcome)

---

#### UC-6: Landlord renews annual registration

**Actor**: Persona 1 / Persona 2.

**Preconditions**: Active registration nearing expiry; renewal reminder issued via GOV.UK Notify.

**Main Flow**:

1. Landlord receives renewal reminder.
2. Landlord authenticates and reviews their current record.
3. Landlord updates any changed fields (certificates, occupancy) and confirms.
4. Landlord pays renewal fee via GOV.UK Pay.
5. System extends the registration validity window and issues an updated certificate.

**Postconditions**: Registration validity extended by the renewal period.

**Priority**: CRITICAL

---

#### UC-7: Landlord exercises a UK GDPR subject right (SAR, rectification, erasure consideration)

**Actor**: Persona 1 / Persona 2.

**Preconditions**: Authenticated identity.

**Main Flow**:

1. Landlord submits an SAR, rectification request, or erasure request via the service.
2. System acknowledges within 24 hours; assigns to DPO queue.
3. DPO reviews; for SAR, returns data within statutory deadline.
4. For erasure, assesses against the lawful basis (statutory obligation generally precludes full erasure of register data while the obligation persists; partial erasure of contact preferences and similar is honoured).

**Postconditions**: SAR / rectification fulfilled; erasure decision recorded with rationale.

**Priority**: HIGH

---

### Functional Requirements Detail

#### FR-001: Landlord identity assurance via GOV.UK One Login

**Description**: The service MUST verify the identity of individual landlords via GOV.UK One Login at a verification level appropriate to the act of registration. Stepped-up assurance MAY be required for downstream actions (e.g., serving a possession notice).

**Relates To**: BR-001, BR-005, BR-008, UC-1, UC-6, INT-001, P-4, P-18.

**Acceptance Criteria**:

- [ ] Given an unverified landlord, when they begin registration, then the service redirects to One Login.
- [ ] Given One Login verifies the landlord, when the verification level meets the agreed minimum, then registration proceeds.
- [ ] Given One Login returns lower-than-required assurance, when the landlord attempts a privileged action, then they are stepped up before completing it.
- [ ] Edge case: One Login outage — registration journey shows a clear error, no half-state records created.

**Data Requirements**:

- **Inputs**: One Login identity claims (verified name, date of birth, address history).
- **Outputs**: Landlord record linked to One Login subject ID.
- **Validations**: Claim freshness ≤ defined window; no claim accepted from a revoked One Login session.

**Priority**: MUST_HAVE

**Complexity**: HIGH

**Dependencies**: INT-001 (One Login).

**Assumptions**: One Login can provide the assurance level required by the time of first-area commencement.

---

#### FR-002: Corporate landlord identity federation via Companies House

**Description**: The service MUST verify corporate landlord identity by federating against Companies House (company number lookup, status check, officer verification for the company representative).

**Relates To**: BR-001, BR-008, UC-1, INT-002, P-8 (single source of truth), P-18.

**Acceptance Criteria**:

- [ ] Given a company number, the service retrieves company status and registered office from Companies House.
- [ ] Given an officer claims to act for the company, their One Login identity is matched against named officers in Companies House.
- [ ] If Companies House is unavailable, registration is queued — not silently failed.

**Priority**: MUST_HAVE

**Complexity**: HIGH

**Dependencies**: INT-002 (Companies House), FR-001.

---

#### FR-003: Property identity resolution via UPRN

**Description**: Properties MUST be canonically identified by Unique Property Reference Number (UPRN), with fallback to moderated manual address entry only where UPRN cannot be resolved.

**Relates To**: BR-001, UC-1, UC-3, UC-4, INT-003, P-8 (single source of truth).

**Acceptance Criteria**:

- [ ] Given a typed address, the service offers UPRN-resolved candidates.
- [ ] Given a confirmed UPRN, the property record uses UPRN as primary key.
- [ ] Given no UPRN match, the manual record is flagged for moderation and excluded from public lookup until verified.

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

**Dependencies**: INT-003 (Land Registry / OS Open UPRN).

---

#### FR-004: Property attributes capture per RRA 2025 Part 2

**Description**: The service MUST capture all statutorily required property attributes for each registered property: address (UPRN), bed count, occupancy, furnishing status, gas safety certificate evidence, electrical safety certificate evidence, EPC reference, banning order history, rent enforcement history.

**Relates To**: BR-001, BR-006, UC-1, P-7 (data minimisation — limited to RRA 2025 scope).

**Acceptance Criteria**:

- [ ] Given a complete property registration, every statutorily required field is populated.
- [ ] Given an EPC reference, the service can pull the corresponding EPC record (consent permitting).
- [ ] Given a banning order applies, the record reflects it and disables the landlord's ability to serve a valid possession notice.

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

---

#### FR-005: Annual fee collection via GOV.UK Pay

**Description**: The service MUST accept registration and renewal payment via GOV.UK Pay (card and direct debit at minimum), with itemised receipts and reconciliation against MHCLG Finance management accounts.

**Relates To**: BR-004, UC-1, UC-6, INT-004, P-18.

**Acceptance Criteria**:

- [ ] Given a registration ready for payment, the service hands off to GOV.UK Pay.
- [ ] On payment success, the registration becomes active and the fee is recorded against the landlord/portfolio.
- [ ] On payment failure, the registration remains pending for the configurable grace period.

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

---

#### FR-006: Tiered fee structure with itemised cost rationale

**Description**: The fee schedule MUST support a tiered structure (per-property base fee with a portfolio cap for landlords with ≥ N properties, configurable parameters) with published itemised cost rationale and a defined review cadence.

**Relates To**: BR-004, BR-008, NFR-C-005, Conflict C-3 (HMT cost recovery vs. small landlord burden).

**Acceptance Criteria**:

- [ ] Fee schedule parameters are configurable without code change.
- [ ] Itemised fee rationale is published with each fee change.
- [ ] Fee structure passes HMT and Ministerial sign-off prior to a fee change going live.

**Priority**: MUST_HAVE

**Complexity**: LOW

---

#### FR-007: Three-tier data view model (registrant / LHA / public)

**Description**: The service MUST expose three distinct data projections — registrant self-service view, LHA enforcement view (restricted full scope), public tenant lookup view (minimum-necessary) — implemented as separate projections rather than filtered queries.

**Relates To**: BR-002, BR-005, NFR-SEC-002, P-7 (data minimisation), P-21 (no algorithmic risk scoring).

**Acceptance Criteria**:

- [ ] The public view exposes only the fields explicitly listed in the DPIA-approved scope.
- [ ] No public-view endpoint can return restricted fields under any query, including pathological inputs.
- [ ] LHA view enforces jurisdiction scope unless an elevated cross-area role is exercised.

**Priority**: MUST_HAVE

**Complexity**: HIGH

**Dependencies**: DPIA scope decision.

---

#### FR-008: Public lookup search and rate-limited query

**Description**: The public lookup MUST support search by full property address, postcode, and (within rate limits) landlord name, returning only the minimum-necessary fields and with bot mitigation and rate limiting active.

**Relates To**: BR-002, NFR-SEC-006, NFR-P-001, UC-3.

**Acceptance Criteria**:

- [ ] Single-property lookup returns within p95 < 1 second.
- [ ] Bulk patterns trigger rate limit before extracting > N records / minute.
- [ ] Automated scraping detection blocks repeat offenders.

**Priority**: MUST_HAVE

**Complexity**: HIGH

---

#### FR-009: LHA enforcement workspace and watchlist

**Description**: LHA officers MUST be able to search, save watchlists, open case files, attach evidence, raise enforcement actions, and write outcomes back to the register.

**Relates To**: BR-003, BR-006, UC-4, NFR-SEC-002.

**Acceptance Criteria**:

- [ ] Officer can query the register restricted view scoped to their LHA.
- [ ] Officer can persist a watchlist and receive alerts on watched landlords/properties.
- [ ] Officer can record an enforcement action with evidence, captured immutably with timestamp and identity.

**Priority**: MUST_HAVE

**Complexity**: HIGH

---

#### FR-010: LHA API for case management system integration

**Description**: The service MUST expose a versioned REST API that LHA case management vendors can consume to read register data and post enforcement outcomes back. API contract MUST be published openly.

**Relates To**: BR-003, NFR-I-001, NFR-I-002, P-3, P-10.

**Acceptance Criteria**:

- [ ] OpenAPI specification published and version-controlled.
- [ ] Contract tests available to integrating vendors.
- [ ] At least 5 of the top 8 LHA CMS vendors integrated by end of national rollout.

**Priority**: MUST_HAVE

**Complexity**: HIGH

---

#### FR-011: HMCTS integration for possession notice validation

**Description**: The service MUST expose an authenticated API that HMCTS systems can query at possession-notice filing time to validate landlord registration status.

**Relates To**: BR-006, UC-5, INT-006.

**Acceptance Criteria**:

- [ ] HMCTS query returns within p95 < 500 ms.
- [ ] Validation result includes registration status and supporting evidence reference for audit.
- [ ] HMCTS query traffic is signed with mutual TLS or equivalent.

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

---

#### FR-012: PRS Ombudsman data sharing

**Description**: The service MUST share landlord identity and registration status with the PRS Ombudsman scheme for case validity confirmation, under an MoU and data-sharing agreement.

**Relates To**: BR-005, INT-007.

**Acceptance Criteria**:

- [ ] Ombudsman queries the register through a defined API or signed file transfer.
- [ ] Data shared is the minimum necessary for case validity.

**Priority**: SHOULD_HAVE

**Complexity**: MEDIUM

---

#### FR-013: Renewal lifecycle and reminders

**Description**: The service MUST manage the renewal lifecycle: notification N days before expiry, grace period after expiry, status transition to expired, signposting for re-registration.

**Relates To**: BR-001, UC-6, INT-005.

**Acceptance Criteria**:

- [ ] Renewal reminder issued at configurable lead time.
- [ ] Registration auto-expires at end-of-period unless renewed.
- [ ] Expired registrations do not appear as valid in the HMCTS or LHA views.

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

---

#### FR-014: Subject access request and other UK GDPR rights handling

**Description**: The service MUST support landlord-initiated subject access, rectification, erasure-consideration, restriction, and portability requests, with statutory turnaround.

**Relates To**: BR-005, UC-7, NFR-C-001.

**Acceptance Criteria**:

- [ ] SAR queue with statutory turnaround monitored ≥ 99%.
- [ ] Erasure decisions logged with lawful-basis rationale (statutory obligation generally precludes full erasure while obligation persists).
- [ ] Portability returns structured machine-readable export.

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

---

#### FR-015: Operational dashboards and statistical publication

**Description**: The service MUST provide operational dashboards for MHCLG programme staff and produce quarterly statistical publications suitable for transparency and ministerial reporting.

**Relates To**: BR-006, BR-007, NFR-M-001, P-5 (observability), P-22 (user-centred / iterative).

**Acceptance Criteria**:

- [ ] Real-time service health dashboard available to operations.
- [ ] Quarterly statistical release published to GOV.UK in machine-readable form.

**Priority**: SHOULD_HAVE

**Complexity**: MEDIUM

---

#### FR-016: "Report a concern" channel from public lookup into LHA

**Description**: Tenants using the public lookup MUST be able to lodge a structured concern that is routed to the appropriate LHA.

**Relates To**: BR-002, BR-003, UC-3, UC-4.

**Acceptance Criteria**:

- [ ] Report form available from any public-view record.
- [ ] Report routed to LHA queue by jurisdiction.
- [ ] Report state visible to reporter via reference number (no account required).

**Priority**: SHOULD_HAVE

**Complexity**: MEDIUM

---

#### FR-017: Bulk CSV upload and bulk API for portfolio landlords and letting agents

**Description**: Portfolio landlords and authorised agents MUST be able to register, update, and renew multiple properties in bulk via either CSV upload or REST API.

**Relates To**: BR-008, UC-2, NFR-I-002.

**Acceptance Criteria**:

- [ ] Bulk submission accepted with row-level validation and rollback on critical errors.
- [ ] Audit log records each row's outcome.

**Priority**: MUST_HAVE

**Complexity**: HIGH

---

#### FR-018: Authorised-agent delegation model

**Description**: A landlord MUST be able to authorise a letting agent (or other party) to register and manage their entries on their behalf, with the authority revocable at any time and clearly audited.

**Relates To**: UC-2, NFR-SEC-002.

**Acceptance Criteria**:

- [ ] Landlord can grant, view, and revoke delegated authority through their account.
- [ ] Every agent action is attributed to both the agent identity and the landlord they act for.

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

---

#### FR-019: Banning order enforcement and possession notice block

**Description**: A landlord under an active banning order MUST be flagged in the register such that they cannot register new properties, and HMCTS validation MUST flag any attempted possession notice from a banned landlord.

**Relates To**: BR-006, UC-4, UC-5.

**Acceptance Criteria**:

- [ ] Banning order flag is settable through LHA enforcement workflow.
- [ ] HMCTS query for a banned landlord returns a clear "not valid to serve" response.

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

---

#### FR-020: V1 explicitly excludes automated risk scoring

**Description**: V1 of the service MUST NOT include automated risk scoring, fraud detection, or AI/ML inference against landlord or tenant personal data. Any subsequent introduction MUST trigger a refreshed DPIA, ATRS publication, and AI Playbook review.

**Relates To**: BR-005, NFR-C-004, P-21, Conflict C-5.

**Acceptance Criteria**:

- [ ] No automated decisioning over personal data in v1; architecture decision recorded in ADR.
- [ ] Change control gate explicitly references P-21, ATRS, and Article 22 GDPR.

**Priority**: MUST_HAVE

**Complexity**: LOW (control gate, not feature)

---

## Non-Functional Requirements (NFRs)

### Performance Requirements

#### NFR-P-001: Response time for user-facing journeys

**Requirement**:

- Public lookup query: p95 < 1 second; p99 < 3 seconds
- Registration form page load: p95 < 2 seconds
- LHA enforcement search: p95 < 2 seconds
- HMCTS validation API: p95 < 500 ms; p99 < 1 second

**Measurement Method**: Continuous synthetic monitoring + real-user telemetry; SLO dashboards.

**Load Conditions**:

- Peak public lookup: 200 queries/second sustained, 1,000 queries/second 5-minute burst
- Peak registration: 10 concurrent journeys/second during area rollout
- LHA traffic: aggregated across 317 LHAs, peak 50 queries/second

**Priority**: CRITICAL. Traces to BR-002, BR-008, P-12.

---

#### NFR-P-002: Throughput at registration rollout peak

**Requirement**: The registration pathway MUST sustain 10 concurrent end-to-end registrations per second during an area rollout opening week.

**Scalability**: Must scale horizontally to 3× peak without code changes.

**Priority**: HIGH. Traces to BR-001, P-1.

---

### Availability and Resilience Requirements

#### NFR-A-001: Service uptime SLA

**Requirement**:

- Public lookup: 99.9% uptime once live
- Registration journey: 99.5% uptime
- LHA enforcement workspace: 99.5% uptime
- HMCTS validation API: 99.95% uptime (court process dependency)

**Maintenance Windows**: Planned out-of-hours; communicated ≥ 5 working days in advance.

**Priority**: CRITICAL. Traces to BR-003, BR-006, P-13.

---

#### NFR-A-002: Disaster recovery RPO and RTO

**Requirement**:

- RPO ≤ 15 minutes for landlord and property records
- RTO ≤ 4 hours for full service restoration

**Backup**: Continuous transactional replication; daily verified restore exercise. Backups encrypted at rest. UK-resident backups only.

**Failover**: Automated failover to secondary UK region; failover time < 30 minutes.

**Priority**: CRITICAL. Traces to BR-005, P-2, P-13.

---

#### NFR-A-003: Graceful degradation on partner outage

**Requirement**: When a downstream partner (One Login, Companies House, Land Registry, Pay, Notify, HMCTS) is unavailable, the service MUST degrade gracefully — explicit user messaging, no silent failure, no half-state records.

**Resilience Patterns Required**:

- [ ] Circuit breaker for every external dependency
- [ ] Bounded timeouts with explicit fallback
- [ ] Retry with exponential backoff (idempotent calls only)
- [ ] Queue-and-resume for non-real-time integrations (e.g., Companies House lookup)
- [ ] Visible service status page

**Priority**: CRITICAL. Traces to P-2.

---

### Scalability Requirements

#### NFR-S-001: Horizontal scaling

**Requirement**: All components MUST scale horizontally to meet demand without code change.

**Growth Projections**:

- End Year 1 (national rollout in progress): 0.5M registered landlords; 50 lookup queries/sec average
- End Year 2 (full national operation): 2.3M registered landlords; 200 lookup queries/sec average, 1,000/sec peak
- Year 3+: stable population scale, peaks driven by enforcement campaigns and media

**Priority**: HIGH. Traces to P-1.

---

#### NFR-S-002: Data volume scaling

**Requirement**: The system MUST handle approximately:

- 2.3M landlord records
- 4–5M property records (each landlord averages 2 properties)
- Multi-million certificate documents over time
- 100M+ audit log entries / year

**Data Archival**: Audit logs and superseded certificate evidence moved to cold storage after retention threshold (default 7 years for audit, 5 years for certificates).

**Priority**: HIGH. Traces to BR-005, P-6.

---

### Security Requirements

#### NFR-SEC-001: Identity-based authentication and MFA

**Requirement**:

- Landlord and tenant lookup users: identity model per persona (One Login for landlords, unauthenticated for tenant lookup)
- LHA officers: federated identity via LHA SSO, with MFA mandatory
- MHCLG operations and admin: One Login + MFA, with hardware-backed factor for privileged operations
- Service-to-service: mutual TLS or signed bearer tokens with short expiry

**Priority**: CRITICAL. Traces to P-4.

---

#### NFR-SEC-002: Least-privilege authorisation and role separation

**Requirement**: Role-based access control with least privilege. Roles include: landlord (self only), agent (clients only, with delegation evidence), LHA officer (LHA area only), LHA supervisor (cross-LHA read), MHCLG operations (full read for service ops, no write to registrant records), MHCLG admin (with break-glass logging).

**Privilege Elevation**: Documented break-glass process with logging and review.

**Priority**: CRITICAL. Traces to P-4.

---

#### NFR-SEC-003: Encryption in transit and at rest

**Requirement**:

- Transport: TLS 1.3 or current NCSC-recommended minimum on every network hop, including internal service-to-service.
- At rest: encryption on all data stores, including replicas and backups, using NCSC-aligned key management.
- Field-level encryption for highly sensitive PII (e.g., where required by DPIA).

**Priority**: CRITICAL. Traces to P-4, P-6.

---

#### NFR-SEC-004: Secrets management

**Requirement**: No secrets in source, configuration, environment dumps, or container images. All secrets held in a managed secret store with automated rotation.

**Priority**: CRITICAL. Traces to P-4.

---

#### NFR-SEC-005: Vulnerability management and penetration testing

**Requirement**:

- Automated dependency, container, and SAST scanning on every build.
- DAST against the running service in non-production.
- Independent ITHC before each major release.
- Annual red team exercise.
- CAF / GovAssure self-assessment refreshed annually.

**Remediation SLA**:

- Critical: 48 hours to mitigate
- High: 7 days
- Medium: 30 days

**Priority**: CRITICAL. Traces to P-4.

---

#### NFR-SEC-006: Bot mitigation and rate limiting on public surfaces

**Requirement**: The public lookup MUST be protected against systematic scraping by rate limiting (per IP, per session) and bot mitigation. Anomalous patterns MUST be detected and blocked.

**Priority**: CRITICAL. Traces to BR-005, P-4.

---

#### NFR-SEC-007: Audit trail and tamper-evident logging

**Requirement**: All registration, fee, enforcement, banning-order, SAR, and admin actions MUST produce a tamper-evident audit record (who, what, when, where, why, result).

**Log Retention**: 7 years for audit logs; tamper-evident storage.

**Priority**: CRITICAL. Traces to P-5.

---

#### NFR-SEC-008: Incident response readiness

**Requirement**: The programme MUST maintain a tested incident response playbook covering data breach, scraping incident, abuse of public lookup, identity-fraud incident, integration partner outage. Tabletop exercise once per 12 months minimum. ICO 72-hour reporting capability proven.

**Priority**: CRITICAL. Traces to BR-005, P-4.

---

### Compliance and Regulatory Requirements

#### NFR-C-001: UK GDPR Article 35 DPIA and Article 36 readiness

**Requirement**: An Article 35 DPIA MUST be completed and approved before each major release. If residual risk is HIGH, Article 36 prior consultation with the ICO MUST be undertaken.

**Compliance Requirements**:

- [ ] DPIA scope covers full processing lifecycle including telemetry
- [ ] Lawful basis recorded per processing activity (Article 6(1)(c) statutory obligation + Article 6(1)(e) public task as applicable)
- [ ] Subject rights handling operational (FR-014)
- [ ] Breach notification ≤ 72 hours
- [ ] Annual transparency report published

**Data Residency**: UK only by default. Cross-border processing requires documented transfer mechanism + transfer impact assessment.

**Priority**: CRITICAL. Traces to BR-005, P-6, P-7.

---

#### NFR-C-002: NCSC Secure by Design

**Requirement**: Programme MUST evidence NCSC Secure by Design principles throughout discovery, alpha, beta, and live. Documented Secure by Design assessment maintained.

**Priority**: CRITICAL. Traces to P-4.

---

#### NFR-C-003: Technology Code of Practice (TCoP) — no Red ratings

**Requirement**: All 11 TCoP points MUST be assessed at each spend control submission with no Red ratings; Amber items MUST have remediation plans.

**Priority**: CRITICAL. Traces to BR-007, P-18, P-23.

---

#### NFR-C-004: ATRS / Algorithmic Accountability gate

**Requirement**: Any introduction of automated decisioning, risk scoring, or AI/ML against personal data MUST trigger ATRS publication, AI Playbook compliance review, and Article 22 GDPR assessment. V1 explicitly contains no such functionality.

**Priority**: CRITICAL. Traces to P-21, FR-020.

---

#### NFR-C-005: Renters' Rights Act 2025 Part 2 alignment

**Requirement**: The data captured, the legal basis, the enforcement workflows, the fee model, and the public/restricted scope MUST align with RRA 2025 Part 2 and the commencement Statutory Instruments. Any scope change requires Director PRS Policy + DPO sign-off.

**Priority**: CRITICAL. Traces to BR-001.

---

#### NFR-C-006: Statistical publication and parliamentary transparency

**Requirement**: Quarterly statistical releases published on GOV.UK covering registration volumes, fee collection, enforcement outcomes, and SAR / breach metrics, with annual transparency report.

**Priority**: HIGH. Traces to SD-14, P-20.

---

### Usability Requirements

#### NFR-U-001: Accessibility — WCAG 2.2 AA

**Requirement**: All public and operational user interfaces MUST meet WCAG 2.2 Level AA. Accessibility statement published per the Accessibility Regulations 2018.

**Accessibility Features**:

- [ ] Keyboard navigation for all functions
- [ ] Screen reader compatibility (NVDA, JAWS, VoiceOver tested)
- [ ] Adjustable font sizes and high contrast mode
- [ ] Plain English content (Hemingway grade 9 or lower)
- [ ] Alt text and captions where applicable

**Testing**: Automated accessibility CI checks + independent manual audit before live release.

**Priority**: CRITICAL. Traces to BR-002, P-19.

---

#### NFR-U-002: GOV.UK Design System alignment

**Requirement**: All citizen-facing UI MUST adopt the GOV.UK Design System patterns and components, unless a documented exception is approved.

**Priority**: HIGH. Traces to P-18.

---

#### NFR-U-003: Multi-channel content (English only at v1)

**Requirement**: Service is English-only at v1. Welsh and accessible-format alternatives (large print, easy-read) MUST be available via accessible request path.

**Priority**: SHOULD_HAVE.

---

### Maintainability and Supportability Requirements

#### NFR-M-001: Observability

**Requirement**: Structured logging, RED metrics (rate, errors, duration), distributed tracing, SLO-based alerting with named runbooks for every alert. Telemetry MUST NOT contain unredacted personal data.

**Priority**: CRITICAL. Traces to P-5.

---

#### NFR-M-002: Documentation currency

**Requirement**: Architecture documentation (HLD, DLD, C4 diagrams), API documentation (published OpenAPI), runbooks, and ADRs MUST be updated within 10 working days of the change they describe.

**Priority**: HIGH. Traces to P-14.

---

#### NFR-M-003: Operational runbooks

**Requirement**: Runbooks MUST exist for: deployment, rollback, backup and restore, DR failover, incident response (per playbook), SAR processing, breach notification, fee reconciliation, integration partner outage.

**Priority**: CRITICAL.

---

### Portability and Interoperability Requirements

#### NFR-I-001: Open API standards

**Requirement**: All published APIs MUST use OpenAPI 3.x specifications with semantic versioning and a documented deprecation policy. AsyncAPI used for event interfaces.

**Priority**: CRITICAL. Traces to P-3.

---

#### NFR-I-002: Contract testing and consumer support

**Requirement**: Public APIs MUST be supported by contract tests; integrating consumers (LHA CMS vendors, HMCTS, Ombudsman) MUST have access to a non-production sandbox.

**Priority**: HIGH. Traces to BR-003, FR-010.

---

#### NFR-I-003: Data portability and open data publication

**Requirement**: Where appropriate (e.g., aggregated statistics), data is published openly on data.gov.uk under the Open Government Licence. Landlords MUST be able to export their own record in a structured machine-readable format.

**Priority**: SHOULD_HAVE. Traces to P-20, FR-014.

---

## Integration Requirements

### External System Integrations

#### INT-001: GOV.UK One Login

**Purpose**: Individual landlord identity assurance.

**Integration Type**: Real-time OAuth 2.0 / OpenID Connect.

**Data Exchanged**: PRS → One Login: identity assurance request. One Login → PRS: verified claims (name, DOB, address history).

**Authentication**: OAuth 2.0 with PKCE; service registration with One Login team.

**SLA**: One Login published availability; PRS implements graceful degradation when unavailable.

**Owner**: GDS One Login team.

**Priority**: CRITICAL. Traces to FR-001.

---

#### INT-002: Companies House

**Purpose**: Corporate landlord identity federation.

**Integration Type**: Real-time REST API (Companies House public API + authenticated endpoints where available).

**Data Exchanged**: Company number lookup, status, officers.

**Authentication**: Companies House API key + IP allow-listing where supported.

**Owner**: Companies House.

**Priority**: CRITICAL. Traces to FR-002.

---

#### INT-003: HM Land Registry / OS Open UPRN

**Purpose**: Property identity resolution via UPRN.

**Integration Type**: Reference data lookup; cached locally with periodic refresh.

**Data Exchanged**: Address → UPRN resolution; UPRN → canonical address.

**Authentication**: API key.

**Owner**: HM Land Registry / Ordnance Survey.

**Priority**: CRITICAL. Traces to FR-003.

---

#### INT-004: GOV.UK Pay

**Purpose**: Fee collection (card, direct debit).

**Integration Type**: Real-time hosted payment journey.

**Data Exchanged**: PRS → Pay: payment intent. Pay → PRS: payment completion event (webhook).

**Authentication**: Pay API key.

**Owner**: GDS GOV.UK Pay team.

**Priority**: CRITICAL. Traces to FR-005.

---

#### INT-005: GOV.UK Notify

**Purpose**: User notifications (registration confirmation, renewal reminders, SAR acknowledgements).

**Integration Type**: Asynchronous REST API.

**Authentication**: Notify API key.

**Owner**: GDS GOV.UK Notify team.

**Priority**: HIGH. Traces to FR-013.

---

#### INT-006: HMCTS

**Purpose**: Possession notice validation.

**Integration Type**: Real-time authenticated REST API.

**Data Exchanged**: Landlord identifier + property → registration status.

**Authentication**: Mutual TLS.

**Owner**: HMCTS digital team.

**Priority**: CRITICAL. Traces to FR-011.

---

#### INT-007: PRS Ombudsman

**Purpose**: Case validity verification.

**Integration Type**: Authenticated REST API or signed file exchange.

**Data Exchanged**: Minimum-necessary registration confirmation per case.

**Authentication**: Mutual TLS or equivalent.

**Owner**: PRS Ombudsman scheme.

**Priority**: HIGH. Traces to FR-012.

---

#### INT-008: LHA case management systems

**Purpose**: LHA enforcement workflow integration.

**Integration Type**: Open published REST API consumed by LHA vendors (Civica, Capita, NEC, in-house).

**Authentication**: OAuth 2.0 client credentials per LHA.

**Owner**: PRS Register service + each LHA vendor.

**Priority**: CRITICAL. Traces to FR-010, BR-003.

---

## Data Requirements

### Data Entities

#### DR-001: Landlord

**Description**: A natural or legal person required to register under RRA 2025 Part 2.

**Attributes**:

| Attribute | Type | Required | Description | Constraints |
|-----------|------|----------|-------------|-------------|
| landlord_id | UUID | Yes | Unique register identifier | Primary key |
| type | Enum | Yes | individual / corporate | |
| one_login_subject_id | String | Conditional | Required for individual | Foreign key to One Login subject |
| company_number | String(8) | Conditional | Required for corporate | Companies House key |
| display_name | String(255) | Yes | Trading name | |
| correspondence_address | Address | Yes | Service of process | |
| email | String | Yes | Notify channel | UK GDPR personal data |
| phone | String | No | | UK GDPR personal data |
| created_at | Timestamp | Yes | | |
| updated_at | Timestamp | Yes | | |
| status | Enum | Yes | active / suspended / banned | |
| banning_order_active | Boolean | Yes | | |

**Relationships**: One-to-many with Property (DR-002); one-to-many with Registration (DR-003).

**Data Volume**: 2.3M records steady state.

**Data Classification**: OFFICIAL (with PII).

**Data Retention**: Retained for the lifetime of the statutory obligation + 7 years for audit purposes.

---

#### DR-002: Property

**Description**: A let or to-be-let property in scope of RRA 2025.

**Attributes**:

| Attribute | Type | Required | Description | Constraints |
|-----------|------|----------|-------------|-------------|
| property_id | UUID | Yes | Internal key | Primary key |
| uprn | String | Conditional | UPRN | Indexed; unique where set |
| canonical_address | Address | Yes | Resolved address | |
| beds | Integer | Yes | Bed count | ≥ 0 |
| occupancy | Enum | Yes | single / shared / HMO | |
| furnishing | Enum | Yes | furnished / unfurnished / part | |
| gas_cert_ref | String | Conditional | Required if applicable | |
| electrical_cert_ref | String | Yes | | |
| epc_ref | String | Yes | EPC register reference | |
| created_at | Timestamp | Yes | | |
| updated_at | Timestamp | Yes | | |

**Relationships**: Many-to-one with Landlord (DR-001) via Registration (DR-003).

**Data Volume**: 4–5M records steady state.

**Data Classification**: OFFICIAL.

**Data Retention**: Lifetime of register + 7 years.

---

#### DR-003: Registration

**Description**: The active legal relationship binding a Landlord to a Property within a validity window.

**Attributes**:

| Attribute | Type | Required | Description | Constraints |
|-----------|------|----------|-------------|-------------|
| registration_id | UUID | Yes | | Primary key |
| landlord_id | UUID | Yes | | Foreign key |
| property_id | UUID | Yes | | Foreign key |
| status | Enum | Yes | active / expired / suspended | |
| valid_from | Date | Yes | | |
| valid_to | Date | Yes | | |
| fee_paid_amount | Money | Yes | | |
| fee_paid_reference | String | Yes | GOV.UK Pay reference | |
| agent_id | UUID | Conditional | If agent acted | |

**Data Volume**: ~5M active registrations.

**Data Classification**: OFFICIAL.

---

#### DR-004: Enforcement Action

**Description**: An action raised by an LHA officer against a landlord/property using register evidence.

**Attributes**: action_id, lha_id, officer_id, landlord_id, property_id, action_type (civil penalty / banning order / improvement notice / other), evidence_refs, opened_at, status, outcome, closed_at.

**Data Volume**: Indeterminate; growing.

**Data Classification**: OFFICIAL-SENSITIVE.

**Data Retention**: 7 years post-closure.

---

#### DR-005: Banning Order

**Description**: A formal banning order under existing legislation, recorded against a Landlord.

**Attributes**: banning_id, landlord_id, issued_by_lha, issued_at, expires_at, evidence_ref, scope.

**Data Classification**: OFFICIAL-SENSITIVE.

---

#### DR-006: Fee Transaction

**Description**: Each financial transaction in or out of GOV.UK Pay.

**Attributes**: transaction_id, gateway_reference, landlord_id, registration_id, amount, status, settled_at.

**Data Classification**: OFFICIAL.

**Data Retention**: 7 years (financial audit).

---

#### DR-007: Audit Log Record

**Description**: A tamper-evident record of every action of consequence in the service.

**Attributes**: audit_id, actor_identity, actor_role, action_type, target_entity, target_id, request_id, timestamp, result, ip_address (where appropriate).

**Data Classification**: OFFICIAL.

**Data Retention**: 7 years; immutable storage.

---

#### DR-008: Public Lookup Projection

**Description**: The minimum-necessary projection exposed to the unauthenticated public lookup. This is a derived projection, not a query over the master.

**Attributes**: A subset of (registration status, address with UPRN, property compliance flags, LHA jurisdiction, signposting). Excludes contact details, full landlord identity, certificate evidence beyond yes/no flags.

**Data Classification**: PUBLIC.

---

#### DR-009: LHA Restricted View Projection

**Description**: The restricted projection exposed to LHA officers, scoped to their area unless cross-area role exercised.

**Data Classification**: OFFICIAL-SENSITIVE.

---

#### DR-010: SAR / Subject Right Request Record

**Description**: A record of each SAR, rectification, erasure, restriction, or portability request and its handling.

**Attributes**: request_id, requester_landlord_id, request_type, received_at, due_at, fulfilled_at, decision_rationale.

**Data Classification**: OFFICIAL-SENSITIVE.

---

### Data Quality Requirements

- **Accuracy**: Identity claims from One Login / Companies House are authoritative — local edits cannot override them.
- **Completeness**: All statutorily required fields are required-on-submit; partial records do not constitute registration.
- **Consistency**: UPRN is the single source of truth for property identity (P-8). Companies House is the single source of truth for company identity.
- **Timeliness**: Reference data refresh cadence documented per integration; freshness shown to LHA users.
- **Lineage**: All ingested data records its source and timestamp.

### Data Migration Requirements

**Migration Scope**: No mass migration from existing LHA selective licensing data at v1 (data shape and provenance differ). Optional later phase to ingest LHA selective licensing data with provenance preserved.

**Strategy**: Phased — empty register at first-area commencement; landlords register fresh.

**Rollback Plan**: Per-record rollback for erroneous data ingestion; no full-service rollback envisaged after live.

---

## Constraints and Assumptions

### Technical Constraints

**TC-1**: Common GOV.UK platforms (One Login, Pay, Notify) MUST be used unless an ADR justifies an alternative (P-18).

**TC-2**: Personal data MUST reside in the UK by default (P-6).

**TC-3**: Property identifier MUST be UPRN where one exists (P-8).

**TC-4**: No automated risk scoring in v1 (P-21, FR-020).

**TC-5**: WCAG 2.2 AA conformance is mandatory (P-19, NFR-U-001).

### Business Constraints

**BC-1**: First-area commencement date is set in the SI commencement order; slippage > 30 days is a Ministerial-level event.

**BC-2**: Fees published with itemised rationale and reviewed periodically; fee schedule is politically sensitive.

**BC-3**: New burdens funding to LHAs must flow before LHA adoption is expected.

**BC-4**: Programme operates under HMT spend controls and CDDO assurance.

### Assumptions

**A-1**: GOV.UK One Login is available at the assurance level needed by first-area commencement.

**A-2**: HM Land Registry / OS UPRN reference data remains available under the existing data-sharing arrangement.

**A-3**: HMCTS digital team is resourced to deliver INT-006 within the required timeframe.

**A-4**: LHA capacity exists to onboard once funding flows.

**Validation Plan**: Discovery / alpha contacts with each partner team validate against the dates underpinning these assumptions. Confirmed assumptions become commitments in the integration MoUs.

---

## Success Criteria and KPIs

### Business Success Metrics

| Metric | Baseline | Target | Timeline | Measurement Method |
|--------|----------|--------|----------|-------------------|
| First-area registrations | 0 | 90% of in-area landlords | 6 months post-first-area commencement | Register telemetry |
| LHA active monthly usage | 0 | ≥ 90% of 317 LHAs | 12 months post national rollout | Telemetry + CSAT |
| Unregistered-let possession notices at county court | Baseline established in months 1–6 | −60% | End of Year 2 of national operation | HMCTS data sharing |
| Cost recovery ratio | 0% | 100% | FY 2027–28 | MHCLG Finance accounts |
| Landlord proportionality CSAT | Unknown | ≥ 75% | 6 months post-launch per area | Independent user research |
| Tenant lookup ease-of-use | Unknown | ≥ 80% | 3 months post public-lookup launch | GOV.UK feedback widget |

### Technical Success Metrics

| Metric | Target | Measurement Method |
|--------|--------|-------------------|
| Public lookup p95 latency | < 1 s | APM telemetry |
| HMCTS validation p95 latency | < 500 ms | APM telemetry |
| Public lookup uptime | 99.9% | Uptime monitoring |
| ICO enforcement actions | 0 | ICO correspondence log |
| ITHC critical/high findings open at release | 0 | Release gate checklist |
| WCAG 2.2 AA conformance | 100% AA | Independent audit |

### User Adoption Metrics

| Metric | Target | Timeline | Measurement Method |
|--------|--------|----------|-------------------|
| In-area landlord registration completion | 90% | 6 months post area-commencement | Telemetry vs. tax records baseline |
| LHA officers active per month | ≥ 90% of LHAs | 12 months post national rollout | Telemetry |
| Public lookup unique queries | Volume target TBC at beta | Continuous | Telemetry |

---

## Dependencies and Risks

### Dependencies

| Dependency | Description | Owner | Target Date | Status | Impact if Delayed |
|------------|-------------|-------|-------------|--------|-------------------|
| RRA 2025 commencement order | Statutory Instrument setting first-area date | Director PRS Policy | Q3–Q4 2026 | On Track | HIGH — sets the legal go-live |
| One Login integration | Assurance level + onboarding | GDS One Login | Q3 2026 | At Risk (parallel programme) | HIGH — landlord identity blocked |
| Companies House federation | API access at scale | Companies House | Q3 2026 | On Track | HIGH — corporate identity blocked |
| Land Registry / OS UPRN data | Reference data licence + technical access | HM Land Registry | Q2 2026 | On Track | MEDIUM — property identity fallback exists |
| HMCTS integration | API + court process change | HMCTS | Q4 2026 | At Risk | HIGH — enforcement outcome blocked |
| New burdens funding to LHAs | HMT / MHCLG agreement | MHCLG Finance | Q3 2026 | At Risk | HIGH — LHA adoption blocked |
| GDS service assessments | Alpha / beta / live | CDDO | Per phase | On Track | HIGH — release blocker |

### Risks (cross-reference `ARC-001-STKE-v1.0` §Risk Register)

| Risk ID | Description | Probability | Impact | Mitigation | Owner |
|---------|-------------|-------------|--------|------------|-------|
| R-1 | Ministerial pressure forces release before service is ready | HIGH | HIGH | Pre-agreed descope playbook; phased rollout; visible CDDO gating | SRO |
| R-2 | ICO requires DPIA rework or prior consultation, delaying beta | MEDIUM | HIGH | Engage ICO from discovery; iterate DPIA; narrow public scope at launch | DPO, SIRO |
| R-3 | LHA adoption stalls — funding or vendor lock-in | MEDIUM–HIGH | MEDIUM | Early HMT agreement on new burdens funding; published open API; reference UI fallback | Service Owner |
| R-4 | Major data breach or scraping incident in first 12 months | MEDIUM | VERY HIGH | Minimum-necessary public scope; rate limiting; ITHC; CAF; SOC integration; incident playbook | Cyber Lead |
| R-5 | NRLA mobilises opposition to fee or scope | MEDIUM | MEDIUM | Early consultation; itemised cost rationale; fee review cycle | Director PRS Policy |
| R-6 | Function creep introduces algorithmic risk scoring without ATRS | MEDIUM (multi-year) | HIGH | ADR explicitly excluding from v1; change control requiring ATRS + DPIA refresh | SIRO |
| R-7 | SRO / Service Owner departure during delivery | MEDIUM | MEDIUM–HIGH | Documented succession; deputy/shadow appointments | Permanent Secretary |

---

## Requirement Conflicts & Resolutions

These conflicts are lifted from `ARC-001-STKE-v1.0` §Conflict Analysis and resolved in concrete requirement language. They are the *known* conflict surface — implementation will surface more.

### Conflict C-1: Ministerial speed vs. quality gates

**Conflicting Requirements**:

- BR-001 (statutory date) vs. BR-007 (GDS Service Standard pass + TCoP no-Red).

**Stakeholders Involved**:

- Housing Minister (SD-1): visible delivery on date.
- Service Owner / CDDO / Permanent Secretary (SD-5 / SD-9 / SD-2): clean assessment.

**Nature of Conflict**: An aggressive Ministerial date plus an unconditional assessment requirement leaves no slack if discovery uncovers complexity.

**Trade-off Analysis**:

| Option | Pros | Cons | Impact |
|--------|------|------|--------|
| Push date | Honours commitment | Risks failed assessment | Minister happy short-term, Permanent Secretary exposed long-term |
| Slip date | Clean assessment | Misses commitment | Permanent Secretary defensible, Minister exposed |
| Phased rollout (chosen) | Visible "first-area live" milestone + scope contained | First area is a small share of total | Both broadly satisfied |

**Resolution Strategy**: PHASE.

**Decision**: Honour the Ministerial commitment as "first-area live by end of 2026," NOT "national live by end of 2026." Service Owner empowered to descope features within the first area to protect the assessment. National rollout follows on a multi-area schedule.

**Impact on Requirements**:

- BR-001 scoped to first-area commencement.
- Pre-agreed descope list maintained outside this document by the Service Owner.

**Decision Authority**: SRO with Ministerial sign-off; CDDO assessment gate respected.

---

### Conflict C-2: Public data scope (tenants vs. landlords vs. ICO)

**Conflicting Requirements**:

- BR-002 + FR-008 + DR-008 (public lookup utility) vs. NFR-C-001 + P-7 (data minimisation, ICO proportionality).

**Stakeholders Involved**:

- Tenants / Generation Rent (SD-12): broad visibility.
- Landlords / NRLA (SD-11 / SD-13): minimum scope.
- ICO (SD-8): proportionality test.

**Resolution Strategy**: PRIORITIZE with INNOVATE (three-projection model).

**Decision**: Implement three distinct data projections (DR-008 / DR-009 / master). Public projection is minimum-necessary per DPIA scope; iterative review with ICO post-launch to expand if evidenced.

**Impact on Requirements**: FR-007 (three-tier views), DR-008 (public projection), NFR-C-001 (DPIA-driven scope), NFR-SEC-006 (rate limiting and bot mitigation).

---

### Conflict C-3: Cost recovery vs. small landlord burden

**Conflicting Requirements**:

- BR-004 (100% cost recovery from fees) vs. BR-008 (proportionate / low burden).

**Resolution Strategy**: COMPROMISE — tiered fee structure with portfolio cap.

**Decision**: FR-006 — tiered fees with portfolio cap, itemised cost rationale, periodic review tied to actual cost.

**Decision Authority**: HMT + Minister + MHCLG Finance.

---

### Conflict C-4: LHA central-tool vs. local autonomy

**Conflicting Requirements**:

- BR-003 (90% LHA adoption) + FR-009 (UI workspace) vs. LHA preference for integration with existing case management systems.

**Resolution Strategy**: INNOVATE — API-first with reference UI.

**Decision**: FR-010 — open API for LHA CMS vendor integration; reference UI provided for LHAs whose vendor isn't yet integrated.

---

### Conflict C-5: Function creep — algorithmic risk scoring

**Conflicting Requirements**:

- Policy interest in identifying high-risk landlords vs. NFR-C-004 + P-21 (ATRS / Article 22).

**Resolution Strategy**: PRIORITIZE — explicit V1 exclusion.

**Decision**: FR-020 — v1 explicitly excludes automated risk scoring; introduction requires DPIA refresh + ATRS publication + AI Playbook review.

---

### Conflict C-6: Identity assurance — rigour vs. friction

**Conflicting Requirements**:

- NFR-SEC-001 (strong identity) vs. BR-008 (low friction).

**Resolution Strategy**: INNOVATE — stepped-up assurance.

**Decision**: FR-001 — minimum verification at registration; stepped-up assurance for high-consequence downstream actions (e.g., serving a possession notice). Decision recorded in a forthcoming ADR.

---

## Timeline and Milestones

| Milestone | Description | Target Date | Dependencies |
|-----------|-------------|-------------|--------------|
| Requirements approval | Stakeholder sign-off on this document | Q2 2026 | This document |
| DPIA v1.0 | First DPIA draft completed | Q2 2026 | This document |
| Alpha service assessment | GDS alpha | Q3 2026 | Requirements, alpha build |
| Beta service assessment | GDS beta | Q4 2026 | Alpha findings closed |
| First-area commencement | SI signed; service live in first area | 31 December 2026 | All MUST-HAVE requirements |
| Live service assessment | GDS live | Q1 2027 | Beta operation |
| Public lookup live | DR-008 projection live | Within 12 months of national registration commencement | DPIA + ICO scope agreed |
| FY 2027–28 cost recovery | 100% recovery | 31 March 2028 | National rollout completed |

---

## Budget

> Budget figures are placeholders pending the SOBC (next step). Quantification owned by MHCLG Finance and validated by HMT.

### Cost Estimate (indicative)

| Category | Estimated Cost | Notes |
|----------|----------------|-------|
| Discovery / Alpha / Beta | TBC at SOBC | Multi-disciplinary team for ~12–18 months |
| Build | TBC at SOBC | Common-platform reuse expected |
| Infrastructure | TBC at SOBC | UK-resident, scalable |
| Independent assurance (ITHC, accessibility, DPIA review) | TBC at SOBC | Multiple rounds |
| LHA new burdens funding | TBC at SOBC | Settled with HMT |
| Communications / engagement | TBC at SOBC | NRLA, LGA, Generation Rent, comms campaign |
| **Total** | **TBC at SOBC** | |

### Ongoing Operational Costs

| Category | Annual Cost | Notes |
|----------|-------------|-------|
| Service operation | TBC | Includes SRE / on-call |
| Common platforms | TBC | One Login, Pay, Notify usage |
| Independent assurance ongoing | TBC | Annual ITHC, CAF refresh |
| **Total** | **TBC** | Cost recovery target = 100% from FY 2027–28 |

---

## Approval

### Requirements Review

| Reviewer | Role | Status | Date | Comments |
|----------|------|--------|------|----------|
| SRO, PRS Programme | Business Sponsor | [ ] PENDING | PENDING | |
| Service Owner | Product Owner | [ ] PENDING | PENDING | |
| MHCLG CDIO delegate | Enterprise Architect | [ ] PENDING | PENDING | |
| MHCLG Cyber Lead | Security | [ ] PENDING | PENDING | |
| MHCLG DPO | Compliance | [ ] PENDING | PENDING | |
| LGA representative | LHA voice | [ ] PENDING | PENDING | |
| ICO (informal review) | Regulator | [ ] PENDING | PENDING | |

### Sign-Off

| Stakeholder | Signature | Date |
|-------------|-----------|------|
| SRO, PRS Programme | PENDING | PENDING |
| Service Owner | PENDING | PENDING |
| Director, PRS Policy | PENDING | PENDING |

---

## Requirements Traceability Matrix (summary)

| Requirement | Traces To Stakeholder Driver / Goal | Traces To Architecture Principle |
|-------------|--------------------------------------|----------------------------------|
| BR-001 | SD-1 / G-1 / O-1 | P-22 |
| BR-002 | SD-12 / G-2 / O-1, O-6 | P-19, P-22 |
| BR-003 | SD-6 / G-3 / O-5 | P-3, P-10 |
| BR-004 | SD-7 / G-5 / O-4 | P-23 |
| BR-005 | SD-8 / G-4 / O-2 | P-4, P-6, P-7 |
| BR-006 | SD-1 / G-8 / O-3 | — |
| BR-007 | SD-5 / SD-9 / G-6 | P-18, P-22, P-23 |
| BR-008 | SD-11 / G-1 / O-6 | P-19, P-22 |
| FR-001 | BR-001, BR-005 | P-4, P-18 |
| FR-002 | BR-001 | P-8, P-18 |
| FR-003 | BR-001 | P-8 |
| FR-007 | BR-005 | P-7, P-21 |
| FR-008 | BR-002 | P-1, P-4 |
| FR-010 | BR-003 | P-3, P-10, P-20 |
| FR-011 | BR-006 | P-3 |
| FR-020 | BR-005 | P-21 |
| NFR-SEC-* | BR-005 | P-4 |
| NFR-C-001 | BR-005 | P-6, P-7 |
| NFR-U-001 | BR-002, BR-008 | P-19 |
| NFR-I-* | BR-003 | P-3, P-23 |

A full machine-readable traceability matrix will be produced via `/arckit:traceability` once design artefacts exist.

---

## Appendices

### Appendix A: Glossary

- **PRS** — Private Rented Sector
- **RRA 2025** — Renters' Rights Act 2025 (UKPGA 2025/26)
- **LHA** — Local Housing Authority
- **MHCLG** — Ministry for Housing, Communities and Local Government
- **UPRN** — Unique Property Reference Number
- **SI** — Statutory Instrument
- **DPIA** — Data Protection Impact Assessment (Article 35 UK GDPR)
- **TCoP** — Technology Code of Practice
- **CAF** — Cyber Assessment Framework (NCSC)
- **ITHC** — IT Health Check
- **ATRS** — Algorithmic Transparency Recording Standard
- **HMCTS** — His Majesty's Courts and Tribunals Service
- **SAR** — Subject Access Request
- **NRLA** — National Residential Landlords Association

### Appendix B: Reference Documents

- `projects/000-global/ARC-000-PRIN-v1.0.md` — Architecture Principles
- `projects/001-prs-database/ARC-001-STKE-v1.0.md` — Stakeholder Analysis
- Renters' Rights Act 2025 (UKPGA 2025/26)
- Technology Code of Practice (gov.uk)
- GDS Service Standard (gov.uk)
- NCSC Secure by Design
- UK GDPR + Data Protection Act 2018
- Accessibility Regulations 2018 (WCAG 2.2 AA)
- ATRS (gov.uk)
- AI Playbook for the UK Government

---

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| *None at v1.0* | — | — | — | Drafted from CLAUDE.md, ARC-001-STKE-v1.0, and ARC-000-PRIN-v1.0. External documents (RRA 2025 explanatory notes, MHCLG org chart, LGA briefings) to be placed in `projects/001-prs-database/external/` before v1.1. |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| — | — | — | — | — |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| — | — | — |

---

**Generated by**: ArcKit `/arckit:requirements` command
**Generated on**: 2026-05-28 GMT
**ArcKit Version**: 5.4.0
**Project**: PRS Database (Project 001)
**AI Model**: Claude Opus 4.7 (1M context) — `claude-opus-4-7[1m]`
**Generation Context**: Synthesised from `ARC-001-STKE-v1.0` (stakeholder drivers, goals, outcomes, conflict analysis, risk register), `ARC-000-PRIN-v1.0` (23 architecture principles), CLAUDE.md project context (statutory basis, integration points, compliance surface). No external documents loaded — `projects/001-prs-database/external/` empty at time of drafting.
