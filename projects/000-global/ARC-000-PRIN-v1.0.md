# MHCLG PRS Programme — Enterprise Architecture Principles

> **Template Origin**: Official | **ArcKit Version**: 5.4.0 | **Command**: `/arckit:principles`

## Document Control

| Field | Value |
|-------|-------|
| Document ID | ARC-000-PRIN-v1.0 |
| Document Type | Enterprise Architecture Principles |
| Project | 000 — Global (cross-project, all PRS-domain initiatives) |
| Classification | OFFICIAL |
| Status | DRAFT |
| Version | 1.0 |
| Created Date | 2026-05-28 |
| Last Modified | 2026-05-28 |
| Review Cycle | Annual (or on material change to UK Government digital standards) |
| Next Review Date | 2027-05-28 |
| Owner | MHCLG Chief Digital and Information Officer (CDIO) |
| Reviewed By | MHCLG Architecture Review Board |
| Approved By | PENDING |
| Distribution | All MHCLG digital programmes, integration partner architects (One Login, Companies House, Land Registry, HMCTS), CDDO portfolio team |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-05-28 | ArcKit AI | Initial creation from `/arckit:principles` command | PENDING | PENDING |

---

## Executive Summary

This document establishes the immutable architectural principles governing all technology decisions taken by MHCLG digital programmes operating in the Private Rented Sector (PRS) policy domain — most immediately the national PRS Database under the Renters' Rights Act 2025 (UKPGA 2025/26), and subsequently any related services (PRS Ombudsman integration, possession-notice validation, sector intelligence).

**Scope**: All technology projects, systems, and procurements delivered by or on behalf of MHCLG within the PRS policy domain.

**Authority**: MHCLG Architecture Review Board, accountable to the CDIO and ultimately the Permanent Secretary as Accounting Officer.

**Compliance**: Mandatory unless a time-bound exception is approved through the process in Section VI.

**Philosophy**: Principles describe **what qualities** the architecture must have and **what outcomes** it must produce. They do not name specific vendors, products, programming languages, or cloud providers. Concrete technology choices happen during `/arckit:research` and ADR phases, *guided by* these principles. Principles are intended to outlast the technology that implements them.

**UK Government context**: These principles incorporate and extend — but do not replace — the [Technology Code of Practice (TCoP)](https://www.gov.uk/guidance/the-technology-code-of-practice), [GDS Service Standard](https://www.gov.uk/service-manual/service-standard), [NCSC Secure by Design](https://www.ncsc.gov.uk/collection/cyber-security-design-principles), the Public Sector Bodies (Websites and Mobile Applications) (No. 2) Accessibility Regulations 2018 (targeting WCAG 2.2 AA), UK GDPR, and Government Functional Standards GovS 005 (Digital) and GovS 007 (Security). Where these are referenced in individual principles, the referenced source is authoritative and these principles read consistently with it.

---

## I. Strategic Principles

### 1. Scalability and Elasticity

**Principle Statement**: All systems MUST be designed to scale horizontally to meet demand. Capacity MUST adapt automatically to load without manual reconfiguration or architectural change.

**Rationale**: PRS-domain services serve a population-scale user base (~2.3M landlords, ~5.5M tenant households, ~317 local authorities). Demand is not uniform — registration deadlines, enforcement-driven access spikes, and media-driven public lookup traffic all produce load profiles that cannot be safely pre-provisioned for the worst case.

**Implications**:

- Design stateless components that can be replicated behind a load balancer.
- No hard-coded capacity ceilings or single-machine assumptions.
- Persistent state held in horizontally scalable stores, not in compute instance memory.
- Autoscaling driven by demand signals (queue depth, request rate, latency).
- Cost model assumes variable capacity.

**Validation Gates**:

- [ ] System scales horizontally without code change
- [ ] No component is a singleton in the critical path
- [ ] Load testing demonstrates linear or sub-linear scaling under added capacity
- [ ] Autoscaling triggers and bounds documented
- [ ] Cost is modelled at peak, average, and trough

---

### 2. Resilience and Fault Tolerance

**Principle Statement**: All systems MUST degrade gracefully when dependencies fail and recover automatically without unrecoverable data loss or sustained manual intervention.

**Rationale**: PRS services depend on multiple external systems (GOV.UK One Login, GOV.UK Pay, Companies House, HM Land Registry, HMCTS). Each is operated by an independent team with its own incident profile. The user-facing service cannot become unavailable every time a dependency hiccups.

**Implications**:

- Circuit breakers on every external dependency.
- Bounded timeouts on every network call; no unbounded waits.
- Retries with exponential backoff and jitter, but only on idempotent calls.
- Defined degraded mode: which user journeys still work if Companies House is down? if One Login is down? Documented and exercised.
- Documented Recovery Time Objective (RTO) and Recovery Point Objective (RPO) per service.
- Bulkhead isolation so one dependency failure does not consume all worker threads.

**Validation Gates**:

- [ ] Per-dependency failure modes documented in a service threat-and-failure register
- [ ] Chaos / fault-injection exercise completed before live release
- [ ] RTO and RPO defined per service and per data domain
- [ ] Automated failover proven through a controlled exercise within the last 12 months
- [ ] Degraded-mode behaviour documented and visible to users (status page or in-product banner)

---

### 3. Interoperability and Integration via Open Standards

**Principle Statement**: All systems MUST expose functionality through well-defined, versioned, machine-readable interfaces using open, industry-standard protocols. Direct database access across system boundaries is prohibited.

**Rationale**: Open standards make integrations cheap to build and replaceable over time. Closed/proprietary integration locks future programmes into today's vendor or today's design. Direct database access across boundaries couples systems to internal data structures and makes deprecation impossible.

**Implications**:

- Interfaces use open protocols (HTTP with structured payloads, asynchronous messaging, event streaming) — not vendor-proprietary protocols.
- Every interface has a published, version-controlled specification.
- Backward compatibility maintained for at least one supported version; deprecation announced with sufficient lead time.
- Consumers MUST NOT bypass interfaces by reading another service's database.
- Reference implementations or contract tests offered to integrating partners (LHA case management vendors, agent platforms).

**Validation Gates**:

- [ ] Interface specification published in an open format (e.g., OpenAPI, AsyncAPI, GraphQL SDL)
- [ ] Versioning strategy documented (including deprecation policy)
- [ ] Authentication and authorisation model documented per interface
- [ ] Error model and retry semantics documented
- [ ] No database connection strings or table-level coupling cross system boundaries

---

### 4. Security by Design (NON-NEGOTIABLE)

**Principle Statement**: All architectures MUST implement defence-in-depth with zero-trust assumptions. Security is foundational, not an add-on, and is assessed and evidenced from discovery through live operation. Compliance with [NCSC Secure by Design](https://www.ncsc.gov.uk/collection/cyber-security-design-principles) is mandatory.

**Rationale**: A statutory register of identities, contact details, and property addresses is a top-tier target for fraud, doxxing, scraping, and state-aligned threat actors. A material breach destroys trust in the service, triggers ICO and NCSC consequences, and exposes individuals to real-world harm (landlords personally; tenants whose addresses appear in lookup data).

**Zero Trust Pillars**:

1. **Identity-based access** — every request authenticated; network position is not a trust signal.
2. **Least privilege** — narrowest permission, time-bound where possible, separation of duties.
3. **Encryption everywhere** — data encrypted in transit and at rest, including backups.
4. **Continuous verification** — monitor, log, and analyse access; assume breach and design for detection.

**Mandatory Controls**:

- [ ] Multi-factor authentication for every human administrative access path
- [ ] Service-to-service authentication using strong cryptographic credentials (mutual TLS or signed bearer tokens with short expiry)
- [ ] Secrets held in a managed secret store, never in source, configuration, or environment dumps
- [ ] Network segmentation with explicit allow-lists between zones
- [ ] Encryption at rest for all stores containing OFFICIAL or higher data, including replicas and backups
- [ ] Encrypted transport for every network hop, internal as well as external
- [ ] Structured authentication, authorisation, and admin-action logging
- [ ] Independent penetration testing (ITHC) before each major release and on a defined recurring cadence
- [ ] CAF / GovAssure self-assessment maintained and refreshed annually
- [ ] Bot mitigation and rate limiting on all public lookup interfaces
- [ ] Defined incident response playbook with named owners and tested escalation

**Compliance Frameworks**:

- UK GDPR + Data Protection Act 2018
- NCSC Secure by Design
- NCSC Cyber Assessment Framework (CAF) / GovAssure
- GovS 007 — Government Functional Standard for Security
- ISO 27001 alignment where reasonable

**Exceptions**: None. The control inventory may be satisfied through equivalent compensating controls, but the underlying security outcomes are non-negotiable.

**Validation Gates**:

- [ ] Threat model (STRIDE or equivalent) completed and reviewed
- [ ] Privacy threat model (LINDDUN or equivalent) completed for any service handling personal data at scale
- [ ] Security architecture review documented in ADR
- [ ] Pen test scheduled; findings tracked to closure
- [ ] Incident response runbook tested in tabletop exercise

---

### 5. Observability and Operational Excellence

**Principle Statement**: All systems MUST emit structured telemetry — logs, metrics, and distributed traces — sufficient to operate the service, support users, and evidence compliance, without that telemetry itself becoming a privacy or security risk.

**Rationale**: A service we cannot observe is a service we cannot operate, debug, defend, or evidence to regulators. Conversely, telemetry that captures more personal data than is necessary becomes itself a target.

**Telemetry Requirements**:

- **Logging**: structured, correlation-ID-tagged, free of unredacted personal data unless strictly necessary
- **Metrics**: request volume, latency percentiles (p50, p95, p99), error rate, dependency health, business KPIs
- **Tracing**: distributed traces across service boundaries, including external dependencies
- **Alerting**: Service Level Objective (SLO)-based, with actionable runbooks

**Required Instrumentation**:

- Request volume, latency, error rate, saturation (the four golden signals)
- Resource utilisation (CPU, memory, I/O, network)
- Business metrics (registrations completed, lookup queries, enforcement actions originated)
- Security events (authentication failures, anomalous query patterns, rate-limit breaches)

**Log Retention** (default, override only with documented rationale):

- Security and audit logs: 7 years (aligned to evidence requirements for enforcement and ICO)
- Application logs: 90 days
- Metrics: 2 years (aggregated for longer-term trends)
- Distributed traces: 30 days for full traces, longer for aggregates

**Privacy Constraints on Telemetry**:

- No raw personal data (names, addresses, NI numbers) in logs unless strictly necessary and risk-assessed.
- Tokenise or pseudonymise where the field is needed for joining but not for human reading.
- Access to production telemetry is itself privileged and logged.

**Validation Gates**:

- [ ] Logging, metrics, tracing instrumented at every service boundary
- [ ] Dashboards and SLO-based alerts configured
- [ ] Runbooks exist for every alert
- [ ] Telemetry privacy review completed and signed off by DPO
- [ ] Capacity planning informed by telemetry, refreshed quarterly

---

## II. Data Principles

### 6. Data Sovereignty, UK GDPR Compliance, and Residency

**Principle Statement**: All personal data processing MUST comply with UK GDPR and the Data Protection Act 2018, with documented lawful basis, data minimisation, residency, retention, and access controls. Population-scale processing requires a Data Protection Impact Assessment (DPIA) under Article 35.

**Data Classification Tiers**:

1. **OFFICIAL** — default for most operational data, including landlord and property records.
2. **OFFICIAL-SENSITIVE** — datasets whose disclosure would harm individuals or the public interest (e.g., enforcement intelligence, threat-actor analyses, joined datasets that re-identify individuals).
3. **PUBLIC** — derived, minimum-necessary public lookup view, scoped through DPIA.
4. **SECRET / TOP SECRET** — not applicable to this domain.

**Residency**:

- Personal data of UK residents stored in the United Kingdom by default.
- Any processing or storage outside the UK requires a documented international transfer mechanism (adequacy, Standard Contractual Clauses, BCRs) and a transfer impact assessment.
- Backups and replicas inherit the same residency constraints.

**Retention**:

- Retention schedule documented per data domain, signed by DPO and SIRO.
- Automated deletion where the lawful basis no longer applies.
- Litigation hold process documented; backups subject to retention schedule.

**Validation Gates**:

- [ ] DPIA completed and refreshed at every major scope change
- [ ] Lawful basis documented per processing activity (Article 6, and Article 9 for any special-category data)
- [ ] Residency map produced and matches procurement contracts
- [ ] Retention schedule operational with automated deletion
- [ ] Subject access, rectification, erasure, and portability paths designed and tested

---

### 7. Data Minimisation and Purpose Limitation

**Principle Statement**: Services MUST collect, store, expose, and share only the minimum personal data necessary for each defined purpose. Function creep across purpose boundaries MUST be prevented by design and by governance.

**Rationale**: The political and regulatory cost of over-collection is asymmetric — a single ICO action or doxxing incident wipes out years of trust-building. Holding less data is the most reliable security control.

**Implications**:

- Each data field has a documented purpose, lawful basis, and retention.
- Public and restricted views are designed as distinct projections, not as filtered views over a single all-fields query.
- New purposes for existing data require a refreshed DPIA before implementation.
- Risk scoring, fraud detection, or other downstream uses of personal data triggers fresh ICO consultation and ATRS publication where automated.

**Validation Gates**:

- [ ] Data inventory mapping each field to purpose, lawful basis, retention
- [ ] Public view scope reviewed by DPO and signed off against DPIA
- [ ] Function-creep change control documented (any new purpose requires re-assessment)

---

### 8. Single Source of Truth and Authoritative Reference Data

**Principle Statement**: Every data domain MUST have a single authoritative system of record. Derived copies are read-only, clearly labelled, and synchronised through documented pipelines. Authoritative reference data MUST come from the recognised UK Government source where one exists.

**Rationale**: Multiple authoritative sources produce reconciliation problems, conflicting answers to users, and audit failures. For UK Government data, the recognised central source (Companies House for company information, HM Land Registry for property title, the Unique Property Reference Number (UPRN) for property identity, GOV.UK One Login for individual identity assurance) should be the canonical reference rather than a re-keyed local copy.

**Implications**:

- For each data domain, name the system of record in an ADR.
- Use UPRN as the canonical property identifier wherever possible.
- Federate identity from One Login (individuals) and Companies House (corporates) rather than re-collecting it.
- Derived copies are read-only and clearly time-stamped at point of replication.
- Bidirectional sync is avoided; if unavoidable, conflict resolution is explicit.

**Validation Gates**:

- [ ] System of record named per data entity in ADR
- [ ] Reference-data sources identified and integrated, not duplicated
- [ ] Derived copies labelled with source and freshness
- [ ] No silent bidirectional synchronisation

---

### 9. Data Quality and Lineage

**Principle Statement**: Data pipelines MUST maintain documented data quality standards and provide end-to-end lineage suitable for audit, regulatory enquiry, and operational troubleshooting.

**Quality Standards**:

- **Completeness**: required fields populated; null patterns monitored.
- **Consistency**: cross-system reconciliation routinely executed.
- **Accuracy**: validation at source; rejection of obviously bad input rather than silent correction.
- **Timeliness**: freshness SLAs defined per data domain.

**Lineage Requirements**:

- Source-to-target mapping for every data flow.
- Transformation logic version-controlled and reviewable.
- Quality metrics tracked per pipeline.
- Schema-change impact analysis prior to deployment.

**Validation Gates**:

- [ ] Data quality rules expressed as automated checks
- [ ] Lineage metadata captured and queryable
- [ ] Producer/consumer data contracts in place
- [ ] Schema evolution policy documented (additive change, deprecation window, migration plan)

---

## III. Integration Principles

### 10. Loose Coupling

**Principle Statement**: Systems MUST be loosely coupled through published interfaces. Shared databases, shared file systems, and tight runtime dependencies across system boundaries are prohibited.

**Rationale**: PRS-domain integration spans Departmental teams, common GOV.UK platforms, and external vendor systems. Tight coupling at any boundary turns every integration partner into a release-coordination dependency. Loose coupling lets teams deploy independently and lets components be replaced without rewriting their consumers.

**Implications**:

- Systems communicate through APIs or events, not by reading each other's databases.
- Each system owns its data lifecycle.
- Shared libraries are minimised; duplication is sometimes preferable to coupling.
- Distributed transactions across systems are avoided; sagas or eventual consistency used instead.

**Validation Gates**:

- [ ] No cross-system database access
- [ ] Each system has an independent data store and deployment pipeline
- [ ] Deploying one system does not force deploying another
- [ ] Interface changes are versioned and backward-compatible across at least one supported version

---

### 11. Asynchronous Communication for Non-Real-Time Work

**Principle Statement**: Systems SHOULD use asynchronous, message-driven communication for non-real-time interactions and for any interaction with a slower or less-reliable external system.

**Rationale**: Asynchronous patterns reduce temporal coupling, improve resilience under partner outages, and enable better throughput.

**When async is appropriate**:

- Non-real-time business processes (overnight reconciliation, batch enforcement reports, renewal reminders).
- Event notification (registration completed, enforcement action raised).
- Long-running workflows that do not need to block the user.
- Integration with slower or less reliable external systems.

**When synchronous is acceptable**:

- Real-time user interactions needing immediate feedback (registration submission, public lookup query).
- Read-only, idempotent query operations.
- Operations that must be transactionally consistent.

**Validation Gates**:

- [ ] Async patterns used where appropriate
- [ ] Message durability and delivery guarantees explicit (at-least-once vs exactly-once)
- [ ] Event schemas versioned and published
- [ ] Dead-letter queues and poison-message handling configured

---

## IV. Quality Attributes

### 12. Performance and Efficiency

**Principle Statement**: All systems MUST meet defined, measurable performance targets under expected load. Resource use MUST be efficient enough to justify on a cost-per-transaction basis under the cost-recovery model.

**Performance Targets** (defined per service):

- **Response time**: p50, p95, p99 latency targets, expressed in milliseconds
- **Throughput**: requests per second sustainable, transactions per minute at peak
- **Concurrency**: simultaneous user capacity at peak
- **Resource efficiency**: cost-per-transaction tracked

**Implications**:

- Performance targets defined in NFRs *before* implementation, not retro-fitted.
- Load testing at and beyond expected peak before each release.
- Continuous performance monitoring, not point-in-time checks.
- Caching strategy for expensive read-heavy operations such as public lookup.

**Validation Gates**:

- [ ] Performance NFRs documented with measurable targets
- [ ] Load test results retained from latest release
- [ ] Performance dashboards monitored in production
- [ ] Cost-per-transaction tracked against cost-recovery model

---

### 13. Availability and Reliability

**Principle Statement**: All systems MUST meet defined availability targets with automated recovery and bounded data loss. Maintenance windows MUST be planned, communicated, and minimised.

**Availability Targets** (defined per service in NFRs):

- **Uptime SLA**: declared per service; recommended baseline ≥ 99.5% for registration, ≥ 99.9% for public lookup once live
- **RTO**: maximum acceptable downtime documented
- **RPO**: maximum acceptable data loss documented

**High-Availability Patterns**:

- Redundancy across availability zones / data centres
- Automated health checks and failover
- Backup, restore, and disaster-recovery procedures tested at least annually
- Status page available to users when degraded

**Validation Gates**:

- [ ] Availability SLA declared
- [ ] RTO and RPO documented
- [ ] Redundancy implemented and proven through failover exercise
- [ ] Backup and restore tested within the last 12 months
- [ ] Status page or user-visible degraded-mode signalling in place

---

### 14. Maintainability and Evolvability

**Principle Statement**: All systems MUST be designed for change, with clear module boundaries, separation of concerns, automated tests sufficient to enable safe refactoring, and current architectural documentation including ADRs for material decisions.

**Rationale**: PRS-domain services will outlive their first delivery team and at least one supplier contract. The cheap, replaceable system five years from now is the one that was designed today for someone else to read, change, and replace.

**Implications**:

- Modular architecture with explicit responsibility boundaries.
- Separation of concerns between business logic, data access, and presentation.
- Code is self-documenting via meaningful naming; comments explain non-obvious *why*, not *what*.
- ADRs for every material architectural choice, retained in the project repository.
- Automated tests provide enough coverage to refactor with confidence.

**Validation Gates**:

- [ ] Up-to-date architecture documentation (HLD, DLD, C4 diagrams)
- [ ] Module boundaries explicit and reflected in code organisation
- [ ] ADRs present for major decisions
- [ ] Automated test coverage sufficient to refactor with confidence (target informed by service criticality)

---

## V. Development and Operations Practices

### 15. Infrastructure as Code

**Principle Statement**: All infrastructure MUST be defined declaratively as version-controlled code and provisioned through automated pipelines. Manual changes to production infrastructure are prohibited.

**Rationale**: Manually configured infrastructure produces drift, hidden state, and irreproducibility. IaC makes environments reproducible, auditable, and recoverable.

**Implications**:

- Infrastructure defined in declarative code, version-controlled alongside application code where appropriate.
- Infrastructure changes go through the same code review and CI pipeline as application changes.
- Environments are reproducible from code; no "snowflake" production servers.
- Break-glass manual interventions are logged, audited, and re-codified within a defined window.

**Validation Gates**:

- [ ] Infrastructure defined as code
- [ ] Code held in version control with reviewable history
- [ ] Automated provisioning pipeline exists
- [ ] No untracked manual changes in production for more than the break-glass window

---

### 16. Automated Testing

**Principle Statement**: All code changes MUST be validated by automated tests before production deployment. Test coverage MUST be proportionate to risk.

**Test Pyramid** (indicative):

- Unit tests: fast, isolated, high volume
- Integration tests: cross-component, including contract tests against external partner APIs
- End-to-end tests: critical user journeys (landlord registration, public lookup, LHA enforcement workflow)

**Required Test Types**:

- Functional (does it do the right thing?)
- Performance (is it fast enough at expected load?)
- Security (does it resist known attack patterns?)
- Accessibility (does it meet WCAG 2.2 AA?)
- Resilience (does it survive dependency failure?)

**Validation Gates**:

- [ ] Automated tests run on every merge
- [ ] Coverage meets agreed thresholds for the service tier
- [ ] Critical paths covered by end-to-end tests
- [ ] Performance tests run on a defined cadence
- [ ] Accessibility tests run on every UI change

---

### 17. Continuous Integration and Deployment

**Principle Statement**: All code changes MUST flow through an automated build → test → security-scan → deploy pipeline with quality gates at each stage. Production releases MUST be reversible.

**Pipeline Stages**:

1. **Source control** — every change committed
2. **Build** — automated compilation and packaging
3. **Test** — automated test suites executed
4. **Security scan** — dependency, container, and static-analysis scans
5. **Deployment** — automated promotion through environments

**Quality Gates**:

- All required tests pass
- No critical or high security findings open without compensating control
- Code review by a different person to the author
- Production deployment gated on a documented production-readiness checklist
- Tested rollback or roll-forward path available

**Validation Gates**:

- [ ] CI/CD pipeline configured and required
- [ ] Security scanning integrated
- [ ] Deployment is automated, audited, and reproducible
- [ ] Rollback or roll-forward proven through exercise

---

## VI. UK Government Overlay Principles

These principles encode UK Government context that is mandatory for the PRS Database and any sibling PRS-domain services.

### 18. Reuse Common GOV.UK Platforms Before Building Bespoke

**Principle Statement**: Services MUST first evaluate and, where suitable, adopt the common GOV.UK platforms (identity, payments, notifications, design system, hosting) before building bespoke equivalents. Bespoke replacements require documented justification and Architecture Review Board sign-off.

**Rationale**: Reuse reduces cost, accelerates delivery, gains shared scrutiny on security, and aligns with the Technology Code of Practice ("make things open" and "use cloud first"). Common platforms have already passed scrutiny that a bespoke build would have to repeat.

**Implications**:

- Default identity assurance for individuals via GOV.UK One Login.
- Default payment collection via GOV.UK Pay.
- Default user notifications via GOV.UK Notify.
- Default visual/interaction design via the GOV.UK Design System.
- A documented ADR is required for any decision *not* to use a common platform, including a comparison of total cost, integration complexity, and risk.

**Validation Gates**:

- [ ] Common-platform assessment recorded in an ADR for each capability
- [ ] Justification documented for any bespoke build
- [ ] CDDO spend control submission references the assessment

---

### 19. Accessibility — WCAG 2.2 AA Minimum

**Principle Statement**: All public and operational user interfaces MUST meet WCAG 2.2 Level AA, as required by the Public Sector Bodies (Websites and Mobile Applications) (No. 2) Accessibility Regulations 2018. An accessibility statement MUST be published and kept current.

**Rationale**: Inaccessible services exclude users with disabilities, breach the Accessibility Regulations 2018, and fail GDS service assessment. Accessibility is a legal obligation, not a quality nice-to-have.

**Implications**:

- Accessibility built in from design through implementation; not bolted on at the end.
- Automated accessibility testing on every UI change.
- Independent manual accessibility audit before each major release.
- Accessibility statement published on each public service.
- Plain-English content reviewed by content designers.

**Validation Gates**:

- [ ] Automated accessibility tests integrated in CI
- [ ] Independent manual audit completed before live release
- [ ] Accessibility statement published and current
- [ ] User research includes participants with access needs

---

### 20. Open by Default, Open Source Where Sensible

**Principle Statement**: Non-sensitive source code, documentation, and data SHOULD be published openly under permissive open-source or open-government licences. Decisions to keep code or data closed MUST be justified and time-bound.

**Rationale**: Open code is more scrutinised, more reusable across government, and supports the Technology Code of Practice ("make things open"). Defaults favour openness; closure is the exception requiring justification.

**Implications**:

- Default code repository visibility: public, unless content makes it OFFICIAL-SENSITIVE or higher.
- Statistical and reference data published on data.gov.uk or equivalent where appropriate.
- Threat-model details, secrets, and operational runbooks remain restricted.
- Contribution guidelines and licences agreed at project inception.

**Validation Gates**:

- [ ] Repository visibility decision recorded with rationale
- [ ] Licences chosen and applied (e.g., MIT, Apache-2.0, OGL for content)
- [ ] Open data publication plan in place for non-sensitive statistical outputs

---

### 21. Transparency, Algorithmic Accountability, and ATRS Compliance

**Principle Statement**: Any use of automated decision-making, risk scoring, or AI/ML against personal data MUST be subject to UK GDPR Article 22 assessment, [Algorithmic Transparency Recording Standard (ATRS)](https://www.gov.uk/government/collections/algorithmic-transparency-recording-standard-hub) publication, and the [UK Government AI Playbook](https://www.gov.uk/government/publications/ai-playbook-for-the-uk-government). Adding such functionality MUST be a deliberate, governed decision, not an emergent feature.

**Rationale**: A statutory register that quietly grows into an algorithmic risk-scoring system would breach the ICO's expectations and create political and legal risk. Transparency is the regulator-visible alternative.

**Implications**:

- V1 of any PRS-domain service explicitly does NOT include algorithmic risk-scoring of individual landlords or tenants.
- Any later addition of automated decision-making requires: refreshed DPIA, Article 22 assessment, ATRS record published, ICO engagement, and AI Playbook compliance review.
- Human oversight is preserved in any decision with significant effect on individuals.
- Training data, model performance metrics, and known biases documented in the ATRS record.

**Validation Gates**:

- [ ] ADR explicitly records the absence (or scope) of automated decision-making
- [ ] ATRS record drafted and published before any algorithmic feature goes live
- [ ] Human-in-the-loop pathway documented
- [ ] AI Playbook assessment completed if applicable

---

### 22. User-Centred Design and Iterative Delivery

**Principle Statement**: Services MUST be designed with continuous user research from discovery onwards, iteratively delivered in line with the GDS Service Standard, and assessed at the appropriate gates (discovery, alpha, beta, live).

**Rationale**: Government has an unbroken track record of failed big-bang programmes that did not engage users early. Iterative delivery against the Service Standard reduces both the probability and severity of failure.

**Implications**:

- User research is funded and resourced from discovery; not a phase-gate that ends at alpha.
- Multi-disciplinary teams (product, design, research, engineering, content, policy).
- Service assessments planned and booked early.
- Permission to descope or defer rather than ship broken capability.
- Telemetry tied back to outcomes, not just outputs.

**Validation Gates**:

- [ ] User research conducted at each phase, with findings recorded
- [ ] Service assessments booked early; first-time pass targeted
- [ ] Multi-disciplinary team composition documented
- [ ] Outcome metrics defined and tracked, not only delivery metrics

---

### 23. Procurement Discipline and Avoidance of Vendor Lock-In

**Principle Statement**: Procurement MUST follow Crown Commercial Service routes (G-Cloud, Digital Outcomes and Specialists, sector-specific frameworks) where suitable. Architecture decisions MUST avoid hard vendor lock-in by preferring open standards, exit-ability, and substitutability.

**Rationale**: Vendor lock-in turns the supplier's commercial decisions into the Department's risk. Public-sector procurement frameworks are designed both for value-for-money and to maintain competitive supply.

**Implications**:

- Architecture decisions explicitly assess exit cost and substitutability.
- Long-running services prefer portable patterns (open APIs, standard data formats) over vendor-specific abstractions when the substitution cost is high.
- Procurement choices reference CCS frameworks where available, with documented rationale for any off-framework approach.
- Multi-supplier strategies considered for critical capability.

**Validation Gates**:

- [ ] Exit cost / substitution cost assessed in ADR for each major platform choice
- [ ] Procurement route documented and justified
- [ ] Contractual exit and transition obligations agreed up front
- [ ] No proprietary data formats without an open export path

---

## VII. Exception Process

### Requesting Architecture Exceptions

Principles are mandatory unless a time-bound, documented exception is approved by the MHCLG Architecture Review Board.

**Valid exception reasons**:

- A genuine technical constraint preventing compliance
- A regulatory or legal requirement that overrides
- A transitional state during migration with a defined end date
- A pilot or proof-of-concept with a defined end date and explicit exit path

**Exception request requirements**:

- [ ] Business and technical justification
- [ ] Alternative approach and compensating controls
- [ ] Risk assessment and mitigation plan
- [ ] Expiration date — exceptions are time-bound
- [ ] Remediation plan to reach compliance

**Approval process**:

1. Submit exception request to MHCLG Enterprise Architecture team
2. Architecture Review Board reviews and challenges
3. CDIO approves exceptions to non-security principles; SIRO approves any with security/data protection implications
4. Exception documented in the project's architecture documentation
5. Exceptions reviewed quarterly; expired exceptions automatically revoked
6. Security principles (Principle 4) and ATRS/transparency principles (Principle 21) cannot be excepted — only specific control implementations may differ, with compensating controls

---

## VIII. Governance and Compliance

### Architecture Review Gates

All PRS-domain projects must pass architecture reviews at GDS-aligned phase gates.

**Discovery**:

- [ ] Principles understood and shared with the team
- [ ] High-level approach aligns with these principles
- [ ] No obvious principle violations
- [ ] User research plan in place

**Alpha**:

- [ ] Candidate architecture documented
- [ ] DPIA in train
- [ ] Common-platform assessment recorded (Principle 18)
- [ ] Initial threat model

**Beta**:

- [ ] Detailed architecture documented
- [ ] Compliance with each principle validated
- [ ] Exceptions requested and approved
- [ ] Security, accessibility, and data-protection validated
- [ ] First service assessment passed

**Pre-Live**:

- [ ] Implementation matches approved architecture
- [ ] Validation gates passed
- [ ] Operational readiness verified (runbooks, on-call, incident response)
- [ ] Pen test findings closed or accepted
- [ ] Accessibility audit complete
- [ ] Live service assessment passed

**Post-Live**:

- [ ] Retrospective architecture review after 90 days of operation
- [ ] Annual compliance review with this principles document

### Enforcement

- Architecture reviews are mandatory for all PRS-domain projects.
- Principle violations must be remediated before live release, except where covered by an approved exception.
- Approved exceptions are time-bound and reviewed quarterly.
- Compliance reviews are performed on live services at least annually.

---

## IX. Appendix

### Principle Summary Checklist

| # | Principle | Category | Criticality | Validation focus |
|---|-----------|----------|-------------|------------------|
| 1 | Scalability and Elasticity | Strategic | HIGH | Load testing, autoscaling |
| 2 | Resilience and Fault Tolerance | Strategic | CRITICAL | Chaos testing, RTO/RPO |
| 3 | Interoperability via Open Standards | Strategic | HIGH | Versioned open specs |
| 4 | Security by Design | Strategic | CRITICAL | Threat model, pen test, CAF |
| 5 | Observability | Strategic | HIGH | Logs, metrics, traces, SLOs |
| 6 | Data Sovereignty & UK GDPR | Data | CRITICAL | DPIA, residency, retention |
| 7 | Data Minimisation | Data | CRITICAL | Field-purpose inventory |
| 8 | Single Source of Truth | Data | HIGH | System of record, UPRN, One Login |
| 9 | Data Quality & Lineage | Data | MEDIUM | Quality rules, lineage metadata |
| 10 | Loose Coupling | Integration | HIGH | No cross-system DB access |
| 11 | Asynchronous Communication | Integration | MEDIUM | Async patterns where appropriate |
| 12 | Performance | Quality | HIGH | Load testing, NFRs |
| 13 | Availability | Quality | CRITICAL | SLA, RTO, RPO, DR exercise |
| 14 | Maintainability | Quality | MEDIUM | Documentation, ADRs, tests |
| 15 | Infrastructure as Code | DevOps | HIGH | IaC coverage |
| 16 | Automated Testing | DevOps | HIGH | Functional, perf, security, a11y |
| 17 | CI/CD | DevOps | HIGH | Pipeline + rollback |
| 18 | Reuse GOV.UK Platforms | UK Gov | HIGH | One Login, Pay, Notify, GDS |
| 19 | Accessibility (WCAG 2.2 AA) | UK Gov | CRITICAL | Audit, statement |
| 20 | Open by Default | UK Gov | MEDIUM | Public repos, OGL/Apache |
| 21 | Algorithmic Accountability / ATRS | UK Gov | CRITICAL | ATRS record, AI Playbook |
| 22 | User-Centred Iterative Delivery | UK Gov | HIGH | Service assessments, research |
| 23 | Procurement Discipline / Exit-ability | UK Gov | HIGH | CCS routes, exit cost in ADR |

### Cross-Reference to Stakeholder Drivers (ARC-001-STKE-v1.0)

This principles set is consistent with — and partially derived from — the stakeholder drivers in `projects/001-prs-database/ARC-001-STKE-v1.0.md`:

- Principles 4, 6, 7, 19, 21 satisfy drivers SD-8 (ICO), SD-10 (NCSC/Cyber), SD-12 (Tenants)
- Principles 18, 22, 23 satisfy drivers SD-7 (HMT), SD-9 (CDDO), SD-2 (Permanent Secretary)
- Principles 3, 8, 10 satisfy driver SD-6 (LHAs) on integration with existing case management
- Principle 21 directly addresses conflict C-5 in the stakeholder document (function creep into algorithmic risk scoring)

---

## External References

> This section provides traceability from generated content back to source documents.

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| *None at v1.0* | — | — | — | No external policy documents lodged in `projects/000-global/policies/` at time of writing. Principles synthesised from CLAUDE.md project context, the linked UK Government standards (TCoP, Service Standard, NCSC Secure by Design, Accessibility Regulations 2018, UK GDPR, GovS 005, GovS 007, ATRS, AI Playbook), and the stakeholder analysis at `projects/001-prs-database/ARC-001-STKE-v1.0.md`. |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| — | — | — | — | — |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| — | — | — |

### Linked UK Government Standards

- [Technology Code of Practice](https://www.gov.uk/guidance/the-technology-code-of-practice)
- [GDS Service Standard](https://www.gov.uk/service-manual/service-standard)
- [NCSC Secure by Design](https://www.ncsc.gov.uk/collection/cyber-security-design-principles)
- [Public Sector Bodies (Websites and Mobile Applications) (No. 2) Accessibility Regulations 2018](https://www.legislation.gov.uk/uksi/2018/952/contents/made)
- [WCAG 2.2](https://www.w3.org/TR/WCAG22/)
- [GovS 005 — Digital](https://www.gov.uk/government/publications/government-functional-standard-govs-005-digital)
- [GovS 007 — Security](https://www.gov.uk/government/publications/government-functional-standard-govs-007-security)
- [Algorithmic Transparency Recording Standard (ATRS)](https://www.gov.uk/government/collections/algorithmic-transparency-recording-standard-hub)
- [UK Government AI Playbook](https://www.gov.uk/government/publications/ai-playbook-for-the-uk-government)
- [NCSC Cyber Assessment Framework (CAF)](https://www.ncsc.gov.uk/collection/caf)

---

**Generated by**: ArcKit `/arckit:principles` command
**Generated on**: 2026-05-28
**ArcKit Version**: 5.4.0
**Project**: MHCLG PRS Programme — Global Principles (Project 000)
**AI Model**: Claude Opus 4.7 (1M context) — `claude-opus-4-7[1m]`
