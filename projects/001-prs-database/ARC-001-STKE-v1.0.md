# Stakeholder Drivers & Goals Analysis: PRS Database

> **Template Origin**: Official | **ArcKit Version**: 5.4.0 | **Command**: `/arckit:stakeholders`

## Document Control

| Field | Value |
|-------|-------|
| Document ID | ARC-001-STKE-v1.0 |
| Document Type | Stakeholder Drivers & Goals Analysis |
| Project | 001 — PRS Database |
| Classification | OFFICIAL |
| Status | DRAFT |
| Version | 1.0 |
| Created Date | 2026-05-28 |
| Last Modified | 2026-05-28 |
| Review Cycle | Quarterly (next review on legislative commencement or change of Minister) |
| Next Review Date | 2026-08-28 |
| Owner | Service Owner, PRS Register Service, MHCLG Digital |
| Reviewed By | Senior Responsible Owner (SRO), PRS Register Programme |
| Approved By | PENDING — Steering Board sign-off |
| Distribution | MHCLG Digital, PRS Register Programme Board, MHCLG Policy (Private Rented Sector Division), CDDO assurance team, Local Government Association liaison |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-05-28 | ArcKit AI | Initial creation from `/arckit:stakeholders` command | PENDING | PENDING |

---

## Executive Summary

### Purpose

This document identifies the stakeholders implicated in the delivery of the national Private Rented Sector (PRS) database under Part 2 of the Renters' Rights Act 2025, their underlying drivers (political, statutory, operational, financial, personal), how those drivers translate into measurable goals, and the outcomes that will demonstrate satisfaction. The PRS register is a high-visibility statutory programme delivered by MHCLG with consequences for ~2.3M landlords, ~5.5M tenant households in England, and 317 local housing authorities (LHAs); stakeholder misalignment is a primary delivery risk.

### Key Findings

The dominant tension is between **statutory pace** (the Secretary of State has commenced Part 2 and committed to a phased rollout from late 2026) and **service quality at scale** — landlord-facing onboarding, LHA enforcement workflows, and tenant-facing search must each meet GDS Service Standard, Technology Code of Practice, and Accessibility Regulations 2018 (WCAG 2.2 AA) thresholds before a public release. A second axis of conflict runs between **landlord representative bodies** (who want minimal friction, narrow data scope, and clear cost recovery) and **tenant advocacy groups** (who want broad disclosure, low fees, and rapid enforcement visibility). Synergy exists across MHCLG, the Information Commissioner's Office (ICO), and the National Cyber Security Centre (NCSC) — all want a Secure by Design, DPIA-evidenced, minimum-necessary-data service, which also serves landlord trust.

### Critical Success Factors

- **Statutory milestones met**: First-area registration go-live by end of 2026, public tenant lookup released no later than 12 months after registration commencement, with no missed Section 1 commencement order date.
- **Local authority adoption**: At least 90% of the 317 LHAs onboarded to the enforcement view within 12 months of national availability, evidenced by usage telemetry and signed information-sharing memoranda.
- **Identity assurance integrity**: Zero unresolved cases of duplicate landlord registrations attributable to identity failure within the first 12 months; corporate landlords resolved via Companies House federation with > 99% match accuracy.
- **Tenant trust**: Public lookup ranks "easy to use" on the GOV.UK service feedback at ≥ 80% satisfaction; zero ICO enforcement actions in the first 24 months.
- **Enforcement leverage**: Demonstrable reduction in unregistered-let possession notices reaching county court — measurable via HM Courts & Tribunals Service (HMCTS) data sharing, with target reduction of 60% by end of Year 2.

### Stakeholder Alignment Score

**Overall Alignment**: MEDIUM

Most departmental and assurance stakeholders are aligned on the outcome (a working, lawful, secure register). The risks of misalignment sit at the political/policy interface (Ministerial expectation of speed vs. CDDO and GDS service-assessment quality bars), the procurement interface (HM Treasury value-for-money vs. landlord-paid cost recovery model), and the public/representative-body interface (NRLA vs. Generation Rent on data scope and fees). These are tractable through phased rollout and structured engagement, but require active management — they are not self-resolving.

---

## Stakeholder Identification

### Internal Stakeholders

| Stakeholder | Role/Department | Influence | Interest | Engagement Strategy |
|-------------|----------------|-----------|----------|---------------------|
| Secretary of State for Housing, Communities and Local Government | Ministerial accountability | HIGH | HIGH | Monthly readouts, PQ support, gateway sign-off |
| Minister of State for Housing and Planning | Day-to-day Ministerial lead on PRS reform | HIGH | HIGH | Fortnightly programme updates, policy decision escalation |
| Permanent Secretary, MHCLG | Accounting Officer, NAO defensibility | HIGH | MEDIUM | Quarterly assurance reviews, escalation route for AO-level risk |
| Senior Responsible Owner (SRO), PRS Register Programme | Programme accountability for delivery and benefits | HIGH | HIGH | Weekly steering, decision authority on scope/cost/time |
| Service Owner, PRS Register Service | End-to-end service ownership, user outcomes | HIGH | HIGH | Daily delivery oversight, GDS assessment lead |
| Director, Private Rented Sector Division (Policy) | Policy intent and Statutory Instrument drafting | HIGH | HIGH | Policy/delivery alignment forum, fortnightly |
| MHCLG Chief Digital and Information Officer (CDIO) | Departmental digital strategy and tech assurance | HIGH | MEDIUM | Monthly portfolio review, tech standards sign-off |
| MHCLG Senior Information Risk Owner (SIRO) | Information risk acceptance, DPIA sign-off | HIGH | MEDIUM | DPIA gates, security risk acceptance forum |
| MHCLG Data Protection Officer (DPO) | UK GDPR compliance, ICO interface | MEDIUM | HIGH | DPIA co-authorship, data flow reviews |
| Delivery Manager / Product Manager (Digital) | Sprint delivery cadence, backlog | MEDIUM | HIGH | Daily standups, sprint reviews |
| Technical Architect / Tech Lead | Architecture decisions, integration design | MEDIUM | HIGH | ADR forum, architecture working group |
| MHCLG Security Architect / Cyber Lead | Secure by Design, GovAssure / CAF | MEDIUM | HIGH | Security architecture reviews, threat modelling |
| MHCLG Commercial / Finance (SCS) | Procurement, cost recovery model, business case | HIGH | MEDIUM | Business case gates, supplier contract governance |
| MHCLG Communications | Press handling, launch comms, landlord engagement campaign | MEDIUM | HIGH | Comms working group, sign-off on landlord-facing copy |

### External Stakeholders

| Stakeholder | Organization | Relationship | Influence | Interest |
|-------------|--------------|--------------|-----------|----------|
| HM Treasury (Spending Control) | HMT | Approves business case, fee schedule, spending re-baselines | HIGH | MEDIUM |
| Central Digital and Data Office (CDDO) | Cabinet Office | Spend controls, digital service standards, GDS assessment | HIGH | MEDIUM |
| Information Commissioner's Office (ICO) | Independent regulator | UK GDPR enforcement, DPIA scrutiny | HIGH | MEDIUM |
| National Cyber Security Centre (NCSC) | Cyber regulator/advisor | CAF / GovAssure assessment, threat advice | MEDIUM | MEDIUM |
| National Audit Office (NAO) | Independent audit | Post-implementation value-for-money review | HIGH | LOW |
| Local Housing Authorities (×317) | Delivery partners, enforcement users | Operational reliance, statutory enforcement role | HIGH | HIGH |
| Local Government Association (LGA) | LHA representative body | Coordinates LHA voice into central programme | MEDIUM | HIGH |
| Landlords — individual (~2.0M) | Service users (registrants) | Compliance burden, fee payers | LOW | HIGH |
| Landlords — corporate (~0.3M) | Service users (registrants) | Compliance burden, larger portfolios | MEDIUM | HIGH |
| National Residential Landlords Association (NRLA) | Landlord representative body | Lobbying, policy commentary, sector voice | MEDIUM | HIGH |
| Tenants in England (~5.5M households) | Service users (lookup) | Beneficiaries, trust constituency | LOW | HIGH |
| Generation Rent / Renters' Reform Coalition | Tenant advocacy | Lobbying, scrutiny of scope and pace | MEDIUM | HIGH |
| Letting Agents (~20k firms) | Service users (registrants/agents) | Operational counterpart to landlords | LOW | HIGH |
| Propertymark | Letting agent professional body | Agent voice, training pathways | LOW | MEDIUM |
| HM Land Registry | Government data integration partner | UPRN / title verification feed | MEDIUM | MEDIUM |
| Companies House | Government data integration partner | Corporate landlord identity federation | MEDIUM | MEDIUM |
| GOV.UK One Login (Government Digital Service) | Identity platform | Individual landlord identity assurance | HIGH | MEDIUM |
| GOV.UK Pay (GDS) | Payment platform | Annual fee collection | MEDIUM | LOW |
| GOV.UK Notify (GDS) | Notifications platform | Renewal reminders, compliance prompts | LOW | LOW |
| HM Courts and Tribunals Service (HMCTS) | Justice integration partner | Possession notice validation, county court interface | MEDIUM | MEDIUM |
| PRS Ombudsman | Downstream redress scheme | Dispute resolution, register cross-reference | MEDIUM | HIGH |
| Parliament — Housing, Communities & Local Government Select Committee | Parliamentary scrutiny | Hearings, written evidence, post-legislative scrutiny | HIGH | MEDIUM |
| Media / Housing press | External scrutiny | Inside Housing, Landlord Today, BBC | MEDIUM | MEDIUM |

### UK Government Digital Roles (GovS 005)

> The [Government Functional Standard for Digital (GovS 005)](https://www.gov.uk/government/publications/government-functional-standard-govs-005-digital) defines mandatory digital governance roles. The PRS Register Service sits firmly within UK Government scope, so these roles are populated below.

| Role | Responsibility | Typical Power/Interest | Engagement Strategy |
|------|---------------|----------------------|---------------------|
| Senior Responsible Owner (SRO) | Accountable for PRS Register outcomes, benefits, and spend controls | HIGH / HIGH | Manage Closely — weekly steering, owns escalations to Permanent Secretary |
| Service Owner | Owns the end-to-end registration + enforcement + lookup service across all user groups | HIGH / HIGH | Manage Closely — daily delivery oversight, GDS assessment lead |
| Product Manager | Prioritises features against landlord/LHA/tenant needs and Renters' Rights Act intent | MEDIUM / HIGH | Keep Informed — sprint reviews, backlog grooming |
| Delivery Manager | Manages delivery cadence, risks, and inter-team dependencies (identity, payments, Land Registry) | MEDIUM / HIGH | Keep Informed — daily standups, fortnightly risk reviews |
| CDDO (Central Digital & Data Office) | Spend controls, GDS service standards, cross-government assurance | HIGH / MEDIUM | Keep Satisfied — spend control submissions, service assessment gates (alpha, beta, live) |
| CDIO (MHCLG) | Departmental digital strategy and technology oversight | HIGH / MEDIUM | Keep Satisfied — quarterly strategy alignment, ADR sign-off for high-cost decisions |
| DDaT Profession Lead | Digital, Data & Technology capability and career framework within MHCLG | LOW / MEDIUM | Monitor — capability assessment for the programme team, recruitment support |

### UK Government Security Roles (GovS 007)

> The [Government Functional Standard for Security (GovS 007)](https://www.gov.uk/government/publications/government-functional-standard-govs-007-security) defines mandatory protective security roles. These apply because the register handles personal data at population scale and supports statutory enforcement.

| Role | Responsibility | Typical Power/Interest | Engagement Strategy |
|------|---------------|----------------------|---------------------|
| Senior Security Risk Owner (SSRO) | Owns protective security risk at MHCLG board level | HIGH / MEDIUM | Keep Satisfied — quarterly security risk review, escalation for residual-risk acceptance |
| Departmental Security Officer (DSO) | Day-to-day security coordination and policy implementation | HIGH / MEDIUM | Keep Satisfied — security compliance gates, incident playbook approval |
| Senior Information Risk Owner (SIRO) | Owns information and cyber security risk, signs off risk acceptance and DPIA | HIGH / MEDIUM | Keep Satisfied — DPIA sign-off, ICO consultation decisions, data-sharing agreement approval |
| Cyber Security Lead | Operational cyber security, CAF self-assessment, GovAssure liaison, NCSC interface | MEDIUM / HIGH | Keep Informed — architecture security reviews, threat modelling, pen test scheduling |

### Stakeholder Power-Interest Grid

```text
                                       INTEREST
                       Low                                  High
                ┌─────────────────────────────┬─────────────────────────────┐
                │                             │                             │
                │       KEEP SATISFIED        │        MANAGE CLOSELY       │
           High │                             │                             │
                │  • HM Treasury              │  • Secretary of State       │
                │  • NAO                      │  • Housing Minister         │
                │  • CDDO                     │  • SRO                      │
                │  • Permanent Secretary      │  • Service Owner            │
                │  • ICO                      │  • Director PRS (Policy)    │
                │  • CDIO / SIRO              │  • Local Housing Authorities│
                │  • Select Committee         │                             │
        POWER   │                             │                             │
                ├─────────────────────────────┼─────────────────────────────┤
                │                             │                             │
                │           MONITOR           │        KEEP INFORMED        │
           Low  │                             │                             │
                │  • GOV.UK Notify            │  • Tenants                  │
                │  • Propertymark             │  • Individual landlords     │
                │  • GOV.UK Pay               │  • Letting agents           │
                │  • DDaT Profession Lead     │  • NRLA                     │
                │                             │  • Generation Rent          │
                │                             │  • PRS Ombudsman            │
                │                             │  • Tech Lead / Architect    │
                │                             │  • Delivery Manager         │
                │                             │  • Cyber Lead               │
                │                             │  • Media / Housing press    │
                │                             │                             │
                └─────────────────────────────┴─────────────────────────────┘
```

| Stakeholder | Power | Interest | Quadrant | Engagement Strategy |
|-------------|-------|----------|----------|---------------------|
| Secretary of State (MHCLG) | HIGH | HIGH | Manage Closely | Monthly readout, PQ support |
| Housing Minister | HIGH | HIGH | Manage Closely | Fortnightly programme review |
| SRO (PRS Programme) | HIGH | HIGH | Manage Closely | Weekly steering board |
| Service Owner | HIGH | HIGH | Manage Closely | Daily delivery oversight |
| Director, PRS Policy | HIGH | HIGH | Manage Closely | Fortnightly policy/delivery forum |
| Local Housing Authorities | HIGH | HIGH | Manage Closely | LGA-mediated forum, enforcement design partners |
| HM Treasury (Spend Control) | HIGH | MEDIUM | Keep Satisfied | Business case gates, fee schedule sign-off |
| CDDO | HIGH | MEDIUM | Keep Satisfied | Spend control + service assessment submissions |
| ICO | HIGH | MEDIUM | Keep Satisfied | DPIA consultation, prior consultation if needed |
| Permanent Secretary | HIGH | MEDIUM | Keep Satisfied | Quarterly Accounting Officer assurance |
| NAO | HIGH | LOW | Keep Satisfied | Annual update, document trail for VfM audit |
| HCLG Select Committee | HIGH | MEDIUM | Keep Satisfied | Written evidence as requested, hearing prep |
| Tenants / Generation Rent | LOW | HIGH | Keep Informed | User research panel, public roadmap, blog posts |
| Landlords / NRLA | LOW | HIGH | Keep Informed | Landlord engagement events, NRLA forum, comms campaign |
| Letting Agents / Propertymark | LOW | HIGH | Keep Informed | Agent pilot, Propertymark webinars |
| PRS Ombudsman | LOW | HIGH | Keep Informed | Joint operating model design, data-sharing MoU |
| HMCTS / Land Registry / Companies House / One Login | LOW–MEDIUM | MEDIUM | Keep Informed | Integration working groups, MoUs |
| Media / Housing press | MEDIUM | MEDIUM | Keep Informed | Press briefings, statistical publication calendar |
| Tech Lead / Delivery Manager / Cyber Lead | LOW–MEDIUM | HIGH | Keep Informed | Programme team forums, ADR contribution |
| GOV.UK Notify / Pay | LOW | LOW | Monitor | Service availability tracking, change notifications |
| DDaT Profession Lead | LOW | MEDIUM | Monitor | Annual capability assessment |

**Quadrant Interpretation:**

- **Manage Closely** (High Power, High Interest): Ministerial and SRO/Service Owner tier — set direction, hold decision authority. LHAs sit here because the service is unusable in their geography without their adoption.
- **Keep Satisfied** (High Power, Low–Medium Interest): Regulators and assurance bodies — they must remain confident in the programme; their dissatisfaction can stop a release at a gate.
- **Keep Informed** (Low Power, High Interest): User and representative groups — they have no formal veto but shape public legitimacy and parliamentary noise.
- **Monitor** (Low Power, Low Interest): Platform-as-a-service partners and capability/profession functions.

---

## Stakeholder Drivers Analysis

### SD-1: Secretary of State / Housing Minister — Deliver the manifesto commitment on time and visibly

**Stakeholder**: Secretary of State for Housing, Communities and Local Government, and the Minister of State for Housing and Planning.

**Driver Category**: STRATEGIC (with strong PERSONAL/political overlay)

**Driver Statement**: The Renters' Rights Act 2025 was a high-profile Government commitment; Ministers need to demonstrate that the register is live, working, and producing visible enforcement impact in time for the next Parliamentary cycle and ahead of Opposition attacks on housing policy.

**Context & Background**: The Act commenced in 2025 with phased rollout from late 2026. The Minister will face Parliamentary Questions, Select Committee hearings, and media scrutiny on go-live dates. A slipped or low-quality launch is politically costly; an unsafe or non-compliant launch (data breach, ICO action) is *more* costly. The Minister has personally signalled the register as evidence of "delivery for renters."

**Driver Intensity**: CRITICAL

**Enablers**:
- Clear, dated commitments inside the Statutory Instrument commencement order
- A phased rollout that produces visible "first area live" milestones to point to
- Strong supportive narrative from tenant groups at launch
- Pre-prepared PQ answers and lines-to-take

**Blockers**:
- A failed GDS service assessment forcing a release delay
- ICO prior consultation triggering a redesign cycle
- A high-profile data breach in any comparable government register (Companies House, HMRC) shifting risk appetite

**Related Stakeholders**: SRO (SD-3), Director PRS Policy (SD-4), Generation Rent (SD-12)

---

### SD-2: Permanent Secretary — Maintain Accounting Officer defensibility

**Stakeholder**: Permanent Secretary, MHCLG (Accounting Officer)

**Driver Category**: RISK / COMPLIANCE

**Driver Statement**: The Permanent Secretary, as Accounting Officer, is personally accountable to Parliament for regularity, propriety, and value for money. They need every major decision on the PRS register to be evidence-backed, proportionate, and survivable under NAO scrutiny.

**Context & Background**: Historical IT programmes in central government (Universal Credit early years, Common Platform, GP IT Futures) have left a strong Permanent Secretary memory of NAO and Public Accounts Committee criticism. The PRS register is novel — there is no comparable mandatory national landlord register in England — so the audit trail must be defensible without recourse to "we've always done it this way."

**Driver Intensity**: HIGH

**Enablers**:
- Clean business case (Green Book five-case model) approved by HMT
- Documented ADRs for every major architecture choice
- Independent technical assurance (e.g., GDS, IPA gate reviews)
- Routine internal audit coverage

**Blockers**:
- Decisions taken on Ministerial urgency without analytical underpinning
- Sole-sourced or extended contracts without commercial scrutiny
- Cost recovery model that fails when landlord numbers under-shoot forecast

**Related Stakeholders**: HM Treasury (SD-7), NAO, SRO (SD-3), CDDO (SD-9)

---

### SD-3: SRO, PRS Register Programme — Deliver in scope, on time, on budget, and credibly

**Stakeholder**: Senior Responsible Owner, PRS Register Programme (SCS, MHCLG)

**Driver Category**: STRATEGIC + PERSONAL

**Driver Statement**: The SRO's professional reputation depends on this delivery. They need confident control over scope, schedule, and budget, with credible reporting up to the Permanent Secretary and Minister, and confidence that integrating partners (One Login, Land Registry, Companies House, HMCTS) will hold their commitments.

**Context & Background**: SROs on the Government Major Projects Portfolio carry personal accountability and are named in the IPA Annual Report. A "red-rated" delivery is a personal reputational hit and limits future SCS career options. SROs typically push for risk transparency *to themselves* and reluctance to surface risk *upwards* until it's actionable.

**Driver Intensity**: CRITICAL

**Enablers**:
- Strong delivery team with continuity
- Working integration commitments (cross-government MoUs with One Login, Land Registry, Companies House)
- Phased descope options that protect critical path

**Blockers**:
- Integration partner slippage outside the SRO's control
- Late changes to policy intent from the SI process
- Talent loss (named tech lead departs)

**Related Stakeholders**: All internal stakeholders; particularly partner-platform owners

---

### SD-4: Director, PRS Policy — Implement the Act faithfully

**Stakeholder**: Director, Private Rented Sector Division (Policy), MHCLG

**Driver Category**: COMPLIANCE / STRATEGIC

**Driver Statement**: Policy leads need the digital service to implement the *intent* of the Renters' Rights Act 2025 — not merely a literal reading. They need the data scope, fee mechanism, and enforcement workflows to support the policy outcomes Ministers promised: a deterrent to non-compliant landlords, useful intelligence for LHAs, and meaningful protection for tenants.

**Context & Background**: There is always tension between policy ambition and digital pragmatism. Policy will want fields that are hard to verify (e.g., "is this property currently let?"); delivery will push back on anything that can't be measured cleanly. Policy is also the channel for SI drafting and so controls the legal envelope of what the service can do.

**Driver Intensity**: HIGH

**Enablers**:
- Policy/delivery integrated team that drafts SI alongside service design
- Clear escalation route when delivery requests policy change

**Blockers**:
- Late or vague SI drafting
- Policy team isolated from user research

**Related Stakeholders**: SRO (SD-3), Service Owner (SD-5), Ministers (SD-1)

---

### SD-5: Service Owner — Pass GDS service assessments and produce a service that users actually use

**Stakeholder**: Service Owner, PRS Register Service (MHCLG Digital)

**Driver Category**: OPERATIONAL / PROFESSIONAL

**Driver Statement**: The Service Owner is graded on user outcomes and on the service's progress through GDS service assessments (alpha → beta → live). They need a service that survives independent assessment, scales with onboarding waves, and produces usable enforcement workflows for LHAs.

**Context & Background**: A failed GDS assessment is a credible release blocker. The Service Owner is the person who has to stand in front of the lead assessor and defend choices — including those imposed by Policy or HMT against their advice. They are also the de facto product authority for prioritisation.

**Driver Intensity**: CRITICAL

**Enablers**:
- Continuous user research with landlords, tenants, LHAs from discovery onwards
- Permission to descope or defer rather than ship broken capability

**Blockers**:
- Mandatory features that contradict user-research evidence
- Underinvestment in accessibility (WCAG 2.2 AA)
- Lack of operational telemetry to evidence outcomes

**Related Stakeholders**: CDDO (SD-9), SRO (SD-3), Delivery Manager

---

### SD-6: Local Housing Authorities (×317) — Get usable enforcement intelligence without a new burden

**Stakeholder**: Local Housing Authorities, represented collectively through the LGA and the Chartered Institute of Environmental Health (CIEH).

**Driver Category**: OPERATIONAL + RISK

**Driver Statement**: LHAs have statutory enforcement powers under the Housing Act 2004, Selective Licensing schemes, and now under the Renters' Rights Act 2025. They need the register to give them *better* intelligence than they have today (where they rely on tip-offs, council tax data, and HMO licensing records), without giving them new administrative work they aren't funded for.

**Context & Background**: LHAs operate under severe funding constraint; environmental health and housing enforcement teams are often single-figures of FTE. They have heterogeneous case management systems (Civica, Capita, NEC, in-house). A national register that requires manual rekeying or licence-fee swallowing of new costs will be adopted slowly and resentfully. Conversely, a register that surfaces previously hidden non-compliant landlords with banning order and rent enforcement history is a genuine operational uplift.

**Driver Intensity**: HIGH (with significant variation between authorities)

**Enablers**:
- API access into LHA case management systems
- Pre-existing selective licensing data ingested rather than re-collected
- New burdens funding from MHCLG to LHAs ringfenced for register access

**Blockers**:
- Register access requiring use of yet another central portal
- No mechanism to write back enforcement outcomes (one-way only)
- LHA data quality from selective licensing being incompatible with the central schema

**Related Stakeholders**: LGA, PRS Ombudsman, HMCTS, Director PRS Policy

---

### SD-7: HM Treasury (Spending Control) — Value for money and a credible cost recovery model

**Stakeholder**: HM Treasury Spending Team for MHCLG

**Driver Category**: FINANCIAL / COMPLIANCE

**Driver Statement**: HMT needs the register to deliver against a Green Book five-case business case, with cost recovery from landlord fees that holds up under sensitivity testing (what happens if 30% of small landlords exit the sector? what if registration take-up under-shoots forecast in Year 1?).

**Context & Background**: HMT has tightened spend controls; cross-government technology spend over thresholds requires CDDO and HMT approval. Cost recovery models for landlord-paid services are politically sensitive (the fee is effectively a sector-wide statutory levy). Fee levels too high will be politically attacked; too low and the programme runs at a Departmental loss against the Spending Review settlement.

**Driver Intensity**: HIGH

**Enablers**:
- Robust demand modelling with named-team owner
- Clean SOBC and FBC, with sensitivity analysis
- Phased approach allowing cost re-baseline at known points

**Blockers**:
- Scope creep without baseline change control
- Optimism bias in landlord-take-up forecast
- Inadequate cost-allocation between registration and enforcement

**Related Stakeholders**: Permanent Secretary (SD-2), SRO (SD-3), MHCLG Commercial/Finance

---

### SD-8: ICO — Personal data processed lawfully, fairly, and proportionately

**Stakeholder**: Information Commissioner's Office

**Driver Category**: COMPLIANCE / REGULATORY

**Driver Statement**: ICO will scrutinise the lawful basis for processing landlord and tenant personal data, the scope and proportionality of public disclosure, and the DPIA for population-scale, statutorily mandated processing. They want a clean, well-documented controller/processor model and explicit data minimisation.

**Context & Background**: This is a textbook Article 35 DPIA-mandatory programme: systematic processing on a large scale, statutory basis with strong impact on individuals (landlord registration is compelled, and unregistered landlords lose the right to serve a valid possession notice — a real-world legal consequence). ICO has been more active recently on public-sector enforcement (e.g., Capita/PSNI). Prior consultation under Article 36 may be required if residual risk is high.

**Driver Intensity**: HIGH

**Enablers**:
- DPIA started in discovery, iterated through alpha/beta
- Early engagement with ICO before consultation is mandatory
- Clear public-vs-restricted view rules with policy traceability

**Blockers**:
- Function creep (e.g., fraud detection using algorithmic risk scoring without ATRS)
- Tenant data captured beyond what's strictly necessary
- Unclear retention schedule

**Related Stakeholders**: MHCLG DPO, SIRO, Generation Rent, Director PRS Policy

---

### SD-9: CDDO — Service meets cross-government digital standards and spend is justified

**Stakeholder**: Central Digital and Data Office (Cabinet Office)

**Driver Category**: COMPLIANCE / STRATEGIC

**Driver Statement**: CDDO needs the PRS register to demonstrate Technology Code of Practice (TCoP) compliance, GDS Service Standard pass at the appropriate phase gates, reuse of GOV.UK platforms (One Login, Pay, Notify) where suitable, and proportionate spend.

**Context & Background**: CDDO holds spend controls and runs cross-government service assessments. They are not just a compliance hurdle — they are also a route to platform-of-platforms efficiency. Their interest is moderate (they have many programmes to track) but their power is high (they can block a release).

**Driver Intensity**: HIGH

**Enablers**:
- Early engagement with the cross-government service assessment lead
- Demonstrable use of common GOV.UK platforms
- Open-source publication of non-sensitive code

**Blockers**:
- Bespoke identity, payment, or notification builds without justification
- Late submission of spend control requests
- Insufficient evidence at service assessment

**Related Stakeholders**: GDS, Service Owner (SD-5), CDIO

---

### SD-10: NCSC / MHCLG Cyber Lead — A secure, resilient register that survives hostile attention

**Stakeholder**: NCSC (advice + GovAssure assessment) and MHCLG Cyber Security Lead

**Driver Category**: RISK / COMPLIANCE

**Driver Statement**: A public register containing landlord names, contact details, full property addresses, and safety certificate evidence is an attractive target for scrapers, doxxing campaigns, organised crime (rental fraud, identity theft), and politically motivated actors. The cyber community needs Secure by Design controls, CAF-aligned resilience, and a tested incident response.

**Context & Background**: Government registers attract automated scraping and credential-stuffing. Personal contact data for ~2.3M individuals would be a top-tier target. NCSC's GovAssure regime expects evidence-based CAF profile assessment. Cyber Lead carries personal accountability under the departmental security organisation.

**Driver Intensity**: HIGH

**Enablers**:
- Threat modelling from day one (STRIDE / LINDDUN)
- Independent ITHC and red team testing
- Rate limiting and bot mitigation on public lookup
- Minimum-necessary public data scope

**Blockers**:
- Pressure to expose more landlord detail publicly
- Inadequate observability for breach detection
- Reuse of weak legacy identity solutions

**Related Stakeholders**: SIRO, ICO (SD-8), NRLA (SD-13)

---

### SD-11: Landlords (individual and corporate, via NRLA) — Reasonable, proportionate, low-friction registration

**Stakeholder**: ~2.3M landlords, ~20k letting agents, represented in policy debate by NRLA and Propertymark.

**Driver Category**: OPERATIONAL / FINANCIAL

**Driver Statement**: Landlords want to comply with their statutory duty at low cost and with low time-burden, without exposing more personal data than necessary, and with a clear understanding of what the fee covers.

**Context & Background**: The sector ranges from a single buy-to-let on top of a salaried job to corporate landlords with thousands of units. NRLA's lobbying position is generally: register fine in principle, fees should be modest, data scope should be limited, agent-handled registration must be straightforward. Resistance is highest at the small-landlord end where digital literacy is mixed and resentment of sector reform is high.

**Driver Intensity**: HIGH (per individual, low influence; aggregated, significant political weight)

**Enablers**:
- Bulk registration for agents/portfolio landlords
- Clear privacy notice
- Reasonable fee with itemised cost recovery rationale

**Blockers**:
- Confusing duplication with selective licensing
- Mandatory re-collection of evidence already held by LHAs
- Aggressive enforcement narrative at launch

**Related Stakeholders**: NRLA, Propertymark, LHAs (SD-6), Letting Agents

---

### SD-12: Tenants / Generation Rent / Renters' Reform Coalition — Meaningful protection and visibility

**Stakeholder**: ~5.5M tenant households in England, with organised advocacy via Generation Rent and the Renters' Reform Coalition.

**Driver Category**: CUSTOMER / STRATEGIC

**Driver Statement**: Tenants want to be able to check before they sign a tenancy whether their prospective landlord is registered and compliant, to see safety certificate evidence, and to know that enforcement will follow when something is wrong.

**Context & Background**: Tenant groups have lobbied hard for the register; they expect a strong, usable, public-facing service. Their narrative will set the press tone at launch. They will be quick to call out a register that is "private to bureaucrats and useless to renters."

**Driver Intensity**: HIGH

**Enablers**:
- A public lookup service available no later than 12 months after registration commencement
- Plain-language information on what renters can do with the register
- Transparency on enforcement actions and outcomes

**Blockers**:
- Delayed public lookup
- Public data restricted to anonymised aggregates
- Fees making registration partial in low-cost local markets

**Related Stakeholders**: Generation Rent, Renters' Reform Coalition, Housing Minister (SD-1), Media

---

### SD-13: NRLA (National Residential Landlords Association) — Sector legitimacy and proportionate regulation

**Stakeholder**: NRLA, the dominant landlord representative body

**Driver Category**: STRATEGIC / OPERATIONAL

**Driver Statement**: NRLA wants the register to legitimise the responsible landlord (the regulated sector becomes the trusted sector) without becoming an instrument of disproportionate enforcement against small landlords. They want clear, written guidance and predictable fees.

**Context & Background**: NRLA's strategic interest is genuinely aligned with a working register because it raises the floor on bad actors and creates a defensible market for compliant members. Their tactical interest is to keep the data scope and fee tight and to push back against function creep.

**Driver Intensity**: MEDIUM (high externally, low formal authority)

**Enablers**:
- Co-design of guidance materials
- Engagement on fee-setting consultation
- Transparency on enforcement outcomes per area

**Blockers**:
- Surprise scope additions
- Fee increases without consultation
- Use of register for algorithmic risk scoring without ATRS publication

**Related Stakeholders**: Landlords (SD-11), Director PRS Policy, ICO (SD-8)

---

### SD-14: Parliamentary scrutiny — Demonstrable delivery, lawful operation, and value for money

**Stakeholder**: Housing, Communities and Local Government Select Committee; Public Accounts Committee (post-implementation)

**Driver Category**: COMPLIANCE / POLITICAL

**Driver Statement**: Committees need a credible witness story: dates met, money spent against budget, data protected, users served. They will return to the topic 12–24 months after launch.

**Context & Background**: PAC in particular has form on calling Permanent Secretaries to account on government IT. Select Committees publish reports that shape future Bills. Their interest is intermittent but consequential.

**Driver Intensity**: MEDIUM

**Enablers**:
- Regular published statistics
- Clean alignment between commitments and outcomes
- Open contracts register

**Blockers**:
- Quietly missed milestones
- Cost overruns absorbed into business-as-usual

**Related Stakeholders**: Permanent Secretary (SD-2), HMT (SD-7), NAO

---

## Driver-to-Goal Mapping

### Goal G-1: First-area landlord registration live by end of 2026

**Derived From Drivers**: SD-1 (Ministers), SD-3 (SRO), SD-4 (Policy), SD-14 (Parliament)

**Goal Owner**: SRO, PRS Register Programme

**Goal Statement**: Open landlord and property registration in the first designated rollout area (to be set by the commencement order) by 31 December 2026, with at least 90% of in-area landlords registered within 6 months of commencement.

**Why This Matters**: Ministers have a public-facing date; the Act has commenced; political and statutory pressure aligns. Hitting this date with a working service vindicates the legislative commitment and creates the credibility needed for national rollout.

**Success Metrics**:
- **Primary Metric**: First-area commencement date achieved without slip ≥ 30 days
- **Secondary Metrics**:
  - In-area landlord registration completion rate at 6 months post-launch
  - Service uptime in first 90 days (≥ 99.5%)
  - Service assessment outcome at beta and live (Pass)

**Baseline**: No service exists; 0% of landlords registered.

**Target**: First-area registration live by 31 December 2026; 90% in-area registration by 30 June 2027.

**Measurement Method**: Service telemetry, commencement order publication, GDS assessment record.

**Dependencies**:
- Statutory Instrument commencement order signed in time
- GOV.UK One Login integration complete for individual landlord identity
- Companies House integration complete for corporate landlord identity
- New burdens funding agreed with LGA for in-area LHA

**Risks to Achievement**:
- One Login or Companies House integration slippage
- ICO consultation requiring DPIA rework
- Procurement of supplier capability slipping past August 2026

---

### Goal G-2: Public tenant lookup live no later than 12 months after national registration commencement

**Derived From Drivers**: SD-1, SD-4, SD-12 (Tenants), SD-14

**Goal Owner**: Service Owner

**Goal Statement**: Release a public, accessible (WCAG 2.2 AA), rate-limited tenant-facing lookup service that returns registration status, basic property compliance fields, and signposting to LHA enforcement and the PRS Ombudsman, within 12 months of national landlord registration commencement.

**Why This Matters**: The public lookup is the visible benefit to tenants — the constituency the Act exists to protect. Delaying it indefinitely undermines the political and policy case.

**Success Metrics**:
- **Primary Metric**: Public lookup live by month-12 milestone
- **Secondary Metrics**:
  - Tenant satisfaction at ≥ 80% ("easy to use", measured on GOV.UK feedback widget)
  - WCAG 2.2 AA conformance audit passed by independent reviewer
  - Lookup median response time < 1 second under 99th-percentile expected load

**Baseline**: No public-facing lookup exists.

**Target**: Lookup live by month-12, satisfaction ≥ 80% at month-15.

**Measurement Method**: Service telemetry, GOV.UK feedback, accessibility audit report.

**Dependencies**:
- Data scope decision for public view, ratified by ICO consultation
- Bot mitigation / rate limiting design proven in pen test
- Sufficient landlord data quality to make lookup useful

**Risks to Achievement**:
- ICO requiring narrower public scope than policy envisages
- DDoS or scraping attacks on launch
- Data quality on entry being too low to make lookup credible

---

### Goal G-3: LHA enforcement workflow used by ≥ 90% of authorities within 12 months of national availability

**Derived From Drivers**: SD-6 (LHAs), SD-4 (Policy), SD-3 (SRO)

**Goal Owner**: Service Owner (with LGA partnership)

**Goal Statement**: Deliver an LHA enforcement view (with API access for case management system integration where feasible) that has been adopted by at least 90% of the 317 LHAs within 12 months of national rollout, measured by active monthly use.

**Why This Matters**: The register is only enforcement-useful if LHAs use it. Without adoption, the Minister has a database; with it, the Minister has a deterrent.

**Success Metrics**:
- **Primary Metric**: LHA active-monthly-usage rate ≥ 90% at month-12 of national rollout
- **Secondary Metrics**:
  - Number of enforcement actions originated from register data (per LHA, per quarter)
  - LHA satisfaction (CSAT) ≥ 70%
  - API uptake by LHA case management vendors (≥ 5 of the top 8 vendors integrated)

**Baseline**: Currently no central register; LHAs work from local data plus tip-offs.

**Target**: ≥ 90% LHA adoption at month-12 post-national-rollout.

**Measurement Method**: Service telemetry on LHA accounts, LGA-mediated survey, API call volumes.

**Dependencies**:
- New burdens funding flowing to LHAs
- Case management system vendor cooperation
- LHA training and onboarding programme funded

**Risks to Achievement**:
- LHA capacity constraint preventing onboarding
- Mismatch between selective licensing data and central schema
- Vendor lock-in within LHA case management market

---

### Goal G-4: DPIA approved, ICO engaged before public launch, zero enforcement actions in first 24 months

**Derived From Drivers**: SD-8 (ICO), SD-2 (Permanent Secretary), SD-10 (Cyber/NCSC), SD-13 (NRLA on data scope)

**Goal Owner**: SIRO, with MHCLG DPO

**Goal Statement**: Complete and publish (in summary form) a UK GDPR Article 35 DPIA, evidence ICO engagement (including Article 36 prior consultation if residual risk is HIGH), and sustain a record of zero ICO enforcement actions or formal reprimands in the first 24 months of operation.

**Why This Matters**: A regulatory enforcement action against MHCLG on launch would destroy political and public trust in the register. Demonstrably lawful operation is foundational.

**Success Metrics**:
- **Primary Metric**: ICO enforcement action / formal reprimand count = 0 over 24-month operating period
- **Secondary Metrics**:
  - DPIA approved before each major release (alpha, beta, live)
  - Subject access request response within statutory timescales (≥ 99% of requests)
  - Breach notification time < 72 hours from detection on any reportable incident

**Baseline**: No DPIA, no live operation.

**Target**: Zero ICO enforcement actions, DPIA approved at each gate, SAR compliance ≥ 99%.

**Measurement Method**: ICO correspondence, DPIA register, SAR tracker, security incident log.

**Dependencies**:
- DPO continuity
- Clear lawful basis decision in SI
- Operating model with named DPO contact

**Risks to Achievement**:
- Function creep introducing automated risk scoring without ATRS
- Breach due to integration partner
- Aggressive public scope conflicting with proportionality test

---

### Goal G-5: Sustainable cost recovery — landlord fees fund operating cost from Year 2 onwards

**Derived From Drivers**: SD-7 (HMT), SD-2 (Permanent Secretary), SD-11 (Landlords on fee proportionality)

**Goal Owner**: MHCLG Finance / Commercial SCS

**Goal Statement**: From financial year 2027–28 onwards, landlord registration and renewal fees fully cover the operating and ongoing development cost of the PRS register, with a contingency reserve for variance up to ±15% of forecast registration volume.

**Why This Matters**: HMT has limited appetite to continue exchequer funding for a service with an obvious paying user base. A sustainable model is the foundation of long-term operational stability.

**Success Metrics**:
- **Primary Metric**: Annual cost recovery ratio = 100% by FY 2027–28 (excluding initial build cost)
- **Secondary Metrics**:
  - Forecast variance on landlord registration volume within ±15%
  - Per-landlord fee benchmarked against comparable government registers (Companies House, Gambling Commission, FCA)

**Baseline**: 0% recovered (pre-operation).

**Target**: 100% cost recovery in FY 2027–28; per-landlord fee published with itemised rationale.

**Measurement Method**: MHCLG Finance management accounts, HMT reporting.

**Dependencies**:
- Robust take-up forecasting
- Fee schedule signed off by Minister + HMT
- Direct debit / annual payment via GOV.UK Pay working at scale

**Risks to Achievement**:
- Significantly lower registration than forecast (small landlords exit sector)
- Public/political resistance to fee increases when variance occurs
- Hidden costs in enforcement-side functionality

---

### Goal G-6: Tech Code of Practice + GDS Service Standard pass at every gate

**Derived From Drivers**: SD-5 (Service Owner), SD-9 (CDDO), SD-2 (Permanent Secretary)

**Goal Owner**: Service Owner

**Goal Statement**: Pass cross-government service assessments at alpha, beta, and live phases, and demonstrate Technology Code of Practice compliance with no Red ratings at any spend control submission.

**Why This Matters**: These are the formal quality gates that protect the Permanent Secretary's defensibility and CDDO's portfolio-level confidence. Failure at a gate is a release blocker.

**Success Metrics**:
- **Primary Metric**: Pass at all three GDS service assessments without re-assessment required
- **Secondary Metrics**:
  - Zero Red TCoP items at any review
  - Open source publication of non-sensitive components

**Baseline**: No assessments yet undertaken.

**Target**: First-time pass at every assessment gate.

**Measurement Method**: Service assessment reports, spend control submissions.

**Dependencies**:
- Service Owner empowered to descope to protect quality
- Continuous user research evidence base
- Independent accessibility audit

**Risks to Achievement**:
- Political pressure to ship before ready
- Underinvestment in accessibility
- Bespoke builds where common GOV.UK components would suffice

---

### Goal G-7: Secure by Design — CAF profile met, ITHC clean, pen test results actioned

**Derived From Drivers**: SD-10 (NCSC / Cyber Lead), SD-2 (Permanent Secretary), SD-11 (Landlord trust)

**Goal Owner**: MHCLG Cyber Security Lead

**Goal Statement**: Meet the CAF profile target appropriate to a high-impact statutory register, achieve a clean ITHC report (no Critical or High findings open at go-live), and operate within an evidenced Secure by Design assurance regime.

**Why This Matters**: A register of 2.3M landlords' personal data and addresses is a high-value target. A breach destroys trust and triggers ICO and NCSC consequences.

**Success Metrics**:
- **Primary Metric**: Zero Critical or High ITHC findings open at any release gate
- **Secondary Metrics**:
  - CAF assessment outcome at expected target profile
  - Time to detection on simulated security events (mean time to detect < 1 hour for exfiltration patterns)

**Baseline**: No live system, no ITHC yet.

**Target**: Clean ITHC at every release; CAF target met annually.

**Measurement Method**: ITHC reports, CAF assessment, security incident telemetry.

**Dependencies**:
- Sufficient cyber resourcing on the programme
- Threat modelling done early
- Integration with departmental SOC

**Risks to Achievement**:
- Reuse of legacy infrastructure with known weaknesses
- Pressure to expose more landlord data publicly
- Cyber lead departure

---

### Goal G-8: Demonstrable enforcement uplift — reduction in unregistered-let possession notices reaching court

**Derived From Drivers**: SD-1 (Minister visible impact), SD-6 (LHAs), SD-12 (Tenants)

**Goal Owner**: Director, PRS Policy

**Goal Statement**: By end of Year 2 of national operation, reduce by 60% the number of unregistered-let possession notices reaching the county courts, evidenced by HMCTS data sharing.

**Why This Matters**: This is the policy outcome — not the digital metric. It's how Ministers prove the register has changed sector behaviour.

**Success Metrics**:
- **Primary Metric**: 60% reduction in unregistered-let possession notices reaching court by end of Year 2
- **Secondary Metrics**:
  - Number of registered-let possession notices accepted at court
  - Enforcement actions originated using register data
  - Volume of register lookups by HMCTS

**Baseline**: Currently unmeasured at sector level (county court does not currently check landlord registration; the offence does not yet exist).

**Target**: 60% reduction at end of Year 2.

**Measurement Method**: HMCTS data sharing agreement, register query logs.

**Dependencies**:
- HMCTS integration / data sharing MoU
- Sufficient registration coverage to make the metric meaningful
- Court awareness and process change

**Risks to Achievement**:
- Slow HMCTS process change
- Register data quality issues
- Geographic variation masking national signal

---

## Goal-to-Outcome Mapping

### Outcome O-1: Statutory commitment honoured — Ministers can credibly point to a live, working register on the timeline promised

**Supported Goals**: G-1, G-2, G-6

**Outcome Statement**: By 31 December 2026, the Government has delivered the first phase of the Renters' Rights Act 2025 register commitment; by 12 months post-national rollout, the tenant-facing lookup is live.

**Measurement Details**:
- **KPI**: Statutory commencement dates met without slippage > 30 days
- **Current Value**: No service; 0% commencement of Part 2 digital provisions
- **Target Value**: Phase 1 commencement on track; Phase 2 lookup live within 12 months of national rollout
- **Measurement Frequency**: Monthly to Minister; quarterly to Permanent Secretary
- **Data Source**: Programme delivery reporting, commencement order publication
- **Report Owner**: SRO

**Business Value**:
- **Financial Impact**: Avoids ministerial-mandated "rescue mode" cost spike (typically 2–4× planned spend)
- **Strategic Impact**: Renters' Rights Act reform credible; political mandate maintained
- **Operational Impact**: Phased rollout creates evidence base for national scaling
- **Customer Impact**: Tenants in first-rollout area gain visibility within first year

**Timeline**:
- **Phase 1 (Months 1–3 of programme)**: SI commencement date confirmed
- **Phase 2 (Months 4–6)**: Alpha service assessment passed, ICO consultation initiated
- **Phase 3 (Months 7–12)**: Beta released to first area; in-area landlords begin registering
- **Sustainment (Year 2+)**: National rollout completed, public lookup live

**Stakeholder Benefits**:
- **Ministers**: Visible delivery
- **SRO / Permanent Secretary**: Defensibility against NAO
- **Tenants**: Tangible benefit
- **LHAs**: Operational uplift

**Leading Indicators**:
- Spend control approval received on schedule
- GDS alpha assessment booked and passed
- First five LHA onboarding agreements signed

**Lagging Indicators**:
- First-area registrations complete
- Public lookup live and used

---

### Outcome O-2: Zero ICO enforcement actions and a clean DPIA record across the first 24 months of operation

**Supported Goals**: G-4, G-7

**Outcome Statement**: MHCLG operates the PRS register without triggering ICO enforcement, formal reprimands, or NCSC-reported major incidents over the first 24 operational months.

**Measurement Details**:
- **KPI**: Count of ICO enforcement actions, formal reprimands, and reportable security incidents
- **Current Value**: N/A (not yet operating)
- **Target Value**: Zero enforcement / reprimand; any incident managed within incident response SLAs
- **Measurement Frequency**: Quarterly to SIRO, annually published
- **Data Source**: ICO correspondence log, security incident register
- **Report Owner**: MHCLG DPO + Cyber Lead

**Business Value**:
- **Financial Impact**: Avoidance of fines (ICO can fine up to 4% of relevant turnover or higher caps under public-sector mechanisms; reputational cost typically larger)
- **Strategic Impact**: Maintains trust foundation needed for landlord cooperation
- **Operational Impact**: Operational time not consumed firefighting regulatory action
- **Customer Impact**: Landlord and tenant confidence maintained

**Timeline**:
- **Phase 1 (pre-launch)**: DPIA approved, ICO engaged
- **Phase 2 (first 6 months operating)**: SAR / breach response procedures proven
- **Phase 3 (months 7–24)**: Annual independent review, CAF self-assessment refreshed
- **Sustainment**: Continuous DPIA refresh aligned to scope changes

**Stakeholder Benefits**:
- **Permanent Secretary**: Accounting Officer defensibility
- **SIRO**: Risk management track record
- **ICO**: Cooperative regulator relationship
- **Landlords / Tenants**: Personal data handled lawfully

**Leading Indicators**:
- DPIA HIGH residual risks resolved before launch
- ICO consultation closed positively
- ITHC findings closed within SLA

**Lagging Indicators**:
- 24-month operating record clean
- Annual transparency report published

---

### Outcome O-3: Enforcement is materially more effective — fewer unregistered lets reach court, more compliant landlords visibly active

**Supported Goals**: G-3, G-8

**Outcome Statement**: The register changes sector behaviour: enforcement actions become more frequent and better-targeted, unregistered lets reaching county court fall by 60% by end of Year 2, and the sector visibly self-cleanses through registration.

**Measurement Details**:
- **KPI**: Reduction in unregistered-let possession notices at county court; LHA enforcement actions originated from register data
- **Current Value**: Baseline to be established in first 6 months of operation
- **Target Value**: 60% reduction by end of Year 2; ≥ 5,000 LHA enforcement actions per year by end of Year 2
- **Measurement Frequency**: Quarterly published
- **Data Source**: HMCTS data sharing, LHA telemetry, MHCLG statistical release
- **Report Owner**: Director PRS Policy

**Business Value**:
- **Financial Impact**: Sector confidence reduces tenancy turnover cost; tenant displacement costs to LHAs reduced
- **Strategic Impact**: Demonstrates that the Act has bite — strengthens Minister's hand for future reform
- **Operational Impact**: LHAs target enforcement effort at register-evidenced cases
- **Customer Impact**: Tenants in non-compliant tenancies materially better protected

**Timeline**:
- **Phase 1 (Year 1 of national rollout)**: Baseline established, first enforcement uplift visible in pilot LHAs
- **Phase 2 (Year 2)**: National reduction trend evident
- **Phase 3 (Year 3+)**: Reform sustained, possibly extended to other safety/quality fields

**Stakeholder Benefits**:
- **Minister**: Outcome to point to
- **LHAs**: Evidence-led enforcement
- **Tenants**: Real protection
- **Compliant landlords**: Market differentiation

**Leading Indicators**:
- LHA register query volumes rising month-on-month
- HMCTS data sharing live
- Register coverage > 80% in active areas

**Lagging Indicators**:
- Possession notice trend
- Annual statistical release showing enforcement uplift

---

### Outcome O-4: Self-sustaining service — annual operating cost fully recovered from landlord fees from FY 2027–28

**Supported Goals**: G-5

**Outcome Statement**: The PRS register operates as a self-funding service from FY 2027–28, requiring no exchequer top-up for ongoing operating cost, with fees benchmarked against comparable government registers.

**Measurement Details**:
- **KPI**: Annual cost recovery ratio
- **Current Value**: N/A (pre-operation)
- **Target Value**: 100% recovery from FY 2027–28; per-landlord fee within ±25% of comparable register benchmark
- **Measurement Frequency**: Annual (financial year)
- **Data Source**: MHCLG management accounts, HMT reporting
- **Report Owner**: MHCLG Finance SCS

**Business Value**:
- **Financial Impact**: Removes service from departmental running cost line; preserves spending power for other PRS reform
- **Strategic Impact**: Sustainable model decoupled from spending review cycle
- **Operational Impact**: Predictable funding for operational team

**Timeline**:
- **Phase 1 (Year 1)**: Exchequer funded, fee not yet collected
- **Phase 2 (Year 2)**: Partial fee collection
- **Phase 3 (Year 3, FY 2027–28)**: Full cost recovery target

**Stakeholder Benefits**:
- **HMT**: Removes ongoing line from MHCLG settlement
- **Permanent Secretary**: Financial defensibility
- **NRLA**: Fee transparency

**Leading Indicators**:
- Landlord registration volume tracking against forecast
- Direct debit uptake from corporate landlords

**Lagging Indicators**:
- Year-end management accounts showing cost recovery
- Fee review cycle informed by actual cost

---

### Outcome O-5: Local authorities have a working operational tool — 90% adoption and material enforcement uplift

**Supported Goals**: G-3, G-8

**Outcome Statement**: At least 90% of England's 317 local housing authorities are actively using the register in their enforcement work within 12 months of national rollout, with measurable uplift in enforcement throughput and quality.

**Measurement Details**:
- **KPI**: LHA active-monthly-usage rate; enforcement actions per LHA per quarter
- **Current Value**: 0% (no service yet)
- **Target Value**: ≥ 90% active monthly usage; mean enforcement actions per LHA per quarter rising
- **Measurement Frequency**: Monthly usage; quarterly enforcement
- **Data Source**: Register telemetry, LGA-mediated CSAT survey
- **Report Owner**: Service Owner

**Business Value**:
- **Operational Impact**: LHA enforcement effort better targeted
- **Customer Impact**: Tenants in 90% coverage areas materially protected

**Timeline**:
- **Phase 1**: First 30 LHAs onboarded (pilot)
- **Phase 2**: 200 LHAs onboarded (national rollout)
- **Phase 3 (month-12)**: ≥ 90% adoption

**Stakeholder Benefits**:
- **LHAs**: Operational uplift
- **Minister**: Coverage data to cite
- **LGA**: Evidence of central-local cooperation working

**Leading Indicators**:
- LHA onboarding pipeline
- Case management vendor API integration count

**Lagging Indicators**:
- Active monthly usage telemetry
- LHA CSAT score

---

### Outcome O-6: Landlords and tenants both report the service as proportionate and usable

**Supported Goals**: G-2, G-6, G-1

**Outcome Statement**: Independent user research shows ≥ 75% of landlords describe the registration process as "proportionate" or "straightforward" and ≥ 80% of tenant lookup users describe the lookup as "easy to use."

**Measurement Details**:
- **KPI**: Landlord proportionality CSAT; tenant lookup ease-of-use score
- **Current Value**: N/A
- **Target Value**: ≥ 75% landlord; ≥ 80% tenant
- **Measurement Frequency**: Quarterly user research wave
- **Data Source**: User research panels, GOV.UK feedback widget
- **Report Owner**: Service Owner (User Researcher)

**Business Value**:
- **Strategic Impact**: Public legitimacy of the service maintained
- **Operational Impact**: Lower support volume per registration
- **Customer Impact**: Lower friction across both user groups

**Stakeholder Benefits**:
- **Landlords / NRLA**: Sense of proportion
- **Tenants / Generation Rent**: Visible benefit
- **Service Owner**: Service standard evidence

**Leading Indicators**:
- Beta user research findings
- Drop-off rate on registration journey

**Lagging Indicators**:
- Annual user satisfaction publication

---

## Complete Traceability Matrix

### Stakeholder → Driver → Goal → Outcome

| Stakeholder | Driver ID | Driver Summary | Goal ID | Goal Summary | Outcome ID | Outcome Summary |
|-------------|-----------|----------------|---------|--------------|------------|-----------------|
| Secretary of State / Housing Minister | SD-1 | Visible on-time delivery of manifesto commitment | G-1 | First-area registration live end of 2026 | O-1 | Statutory commitment honoured |
| Secretary of State / Housing Minister | SD-1 | Visible on-time delivery | G-2 | Tenant lookup within 12 months | O-1 | Statutory commitment honoured |
| Secretary of State / Housing Minister | SD-1 | Visible on-time delivery | G-8 | Possession notice reduction | O-3 | Enforcement materially more effective |
| Permanent Secretary | SD-2 | Accounting Officer defensibility | G-4 | DPIA + zero ICO actions | O-2 | Zero ICO enforcement actions |
| Permanent Secretary | SD-2 | Accounting Officer defensibility | G-5 | Sustainable cost recovery | O-4 | Self-sustaining service |
| Permanent Secretary | SD-2 | Accounting Officer defensibility | G-6 | TCoP + GDS pass | O-1 | Statutory commitment honoured |
| SRO | SD-3 | Scope/time/cost control + reputation | G-1 | First-area live | O-1 | Statutory commitment honoured |
| SRO | SD-3 | Scope/time/cost control | G-3 | LHA adoption | O-5 | LHAs have working tool |
| Director PRS Policy | SD-4 | Faithful Act implementation | G-2 | Tenant lookup | O-1, O-6 | Statutory + usable for tenants |
| Director PRS Policy | SD-4 | Faithful Act implementation | G-8 | Possession notice reduction | O-3 | Enforcement uplift |
| Service Owner | SD-5 | Pass GDS assessments; usable service | G-2 | Tenant lookup | O-6 | Both user groups find proportionate |
| Service Owner | SD-5 | Pass GDS assessments | G-6 | TCoP + GDS pass | O-1 | Statutory commitment honoured |
| Local Housing Authorities | SD-6 | Usable enforcement intelligence | G-3 | LHA adoption | O-5 | LHAs have working tool |
| Local Housing Authorities | SD-6 | Usable enforcement intelligence | G-8 | Possession notice reduction | O-3 | Enforcement uplift |
| HM Treasury | SD-7 | VfM + credible cost recovery | G-5 | Sustainable cost recovery | O-4 | Self-sustaining service |
| HM Treasury | SD-7 | VfM | G-6 | TCoP + GDS pass | O-1 | Statutory commitment honoured |
| ICO | SD-8 | Lawful, proportionate processing | G-4 | DPIA + zero ICO actions | O-2 | Zero ICO enforcement actions |
| CDDO | SD-9 | Cross-government standards met | G-6 | TCoP + GDS pass | O-1 | Statutory commitment honoured |
| CDDO | SD-9 | Cross-government standards | G-5 | Sustainable cost recovery | O-4 | Self-sustaining service |
| NCSC / Cyber Lead | SD-10 | Secure resilient register | G-7 | Secure by Design / CAF / ITHC | O-2 | Zero ICO enforcement actions |
| Landlords / NRLA | SD-11 | Proportionate low-friction registration | G-1 | First-area live | O-6 | Service felt as proportionate |
| Landlords / NRLA | SD-11 | Proportionate registration | G-5 | Sustainable cost recovery | O-4, O-6 | Fees defensible and usable |
| Tenants / Generation Rent | SD-12 | Meaningful protection and visibility | G-2 | Tenant lookup | O-6 | Tenants find lookup usable |
| Tenants / Generation Rent | SD-12 | Meaningful protection | G-8 | Possession notice reduction | O-3 | Enforcement uplift |
| NRLA | SD-13 | Sector legitimacy, proportionate scope | G-4 | DPIA + zero ICO actions | O-2 | Lawful operation |
| NRLA | SD-13 | Sector legitimacy | G-5 | Sustainable cost recovery | O-4 | Self-sustaining |
| Parliament (HCLG Select Committee, PAC) | SD-14 | Demonstrable delivery and VfM | G-1, G-5, G-6 | Multiple | O-1, O-4 | Honoured commitment + self-sustaining |

### Conflict Analysis

**Competing Drivers**:

- **Conflict C-1 — Ministerial speed vs. quality gates (SD-1 vs. SD-2, SD-5, SD-9)**: The Minister wants visible delivery within an aggressive political window. The Permanent Secretary, Service Owner, and CDDO all want quality gates passed cleanly. A late beta means a missed political milestone; a rushed beta means a failed GDS assessment.
  - **Resolution Strategy**: Phased rollout, with explicit Ministerial agreement that "first-area live by end of 2026" is the political commitment, *not* "national rollout in 2026." Ministerial communications team primed to defend the phased approach. Pre-agreed descope list to protect the critical path.

- **Conflict C-2 — Public data scope (SD-12 Tenants vs. SD-11/SD-13 Landlords vs. SD-8 ICO)**: Tenants want broad visibility; landlords (and NRLA) want minimum-necessary data; ICO will apply proportionality test.
  - **Resolution Strategy**: Three-tier data view — minimum public view (registration status, broad area, compliance flag), restricted view for LHAs (full identity, contact, certificates, banning order history), audit view for ICO/NAO. Public view scope tested with ICO before launch and revisited post-launch with evidence of actual harm/benefit.

- **Conflict C-3 — Cost recovery vs. small landlord burden (SD-7 HMT vs. SD-11 Landlords)**: HMT wants fee that fully recovers cost; small landlords (and NRLA) want low fee.
  - **Resolution Strategy**: Tiered fee (per property, with cap for portfolio landlords; minimum for single buy-to-let), itemised public rationale, fee review cycle anchored to actual operating cost rather than to general inflation.

- **Conflict C-4 — LHA central-tool vs. local autonomy (SD-6 LHAs vs. SD-4 Policy uniformity)**: LHAs want the register to integrate with what they have, not replace it; Policy wants nationally consistent enforcement intelligence.
  - **Resolution Strategy**: API-first design with reference UI; vendor engagement programme with LHA case management providers; new burdens funding tied to integration milestones.

- **Conflict C-5 — Function creep risk: fraud/risk scoring (SD-4 Policy desire vs. SD-8 ICO + SD-13 NRLA)**: Policy will be tempted to introduce automated risk scoring of landlords; ICO and NRLA will resist as algorithmic decisioning without ATRS.
  - **Resolution Strategy**: Explicit non-goal in design: no automated risk scoring of individual landlords in V1. If introduced later, full ATRS publication and Article 22 GDPR assessment required.

- **Conflict C-6 — Identity assurance approach (corporate vs. individual landlords)**: Companies House federation for corporates is straightforward; GOV.UK One Login for individuals is heavier-weight than necessary for many small landlords. Tension between identity proofing rigour and registration friction.
  - **Resolution Strategy**: Step-up identity assurance — minimum verification at registration, increased on serving a possession notice or facing enforcement. Decision to be evidenced via ADR.

**Synergies**:

- **Synergy S-1 — Secure, proportionate data scope serves four stakeholders at once**: SD-8 (ICO), SD-10 (NCSC/Cyber), SD-11 (NRLA on data scope), and SD-2 (Permanent Secretary defensibility) all benefit from a data-minimised public view. This is the highest-leverage design choice in the programme.

- **Synergy S-2 — LHA adoption and possession-notice enforcement reinforce each other**: SD-6 (LHAs operational uplift) directly drives SD-1 (Ministerial visible outcome) via SD-12 (tenant protection). Investing in LHA tooling and new burdens funding pays back across three stakeholder groups.

- **Synergy S-3 — Phased rollout aligns SRO, Service Owner, and Ministers**: A clearly communicated phased rollout gives the SRO control, the Service Owner room to learn, and the Minister a sequence of "live in X area" announcements rather than a single big-bang risk.

- **Synergy S-4 — Cost recovery from landlords supports HMT, Permanent Secretary, and arguably NRLA**: HMT wants fee revenue; Permanent Secretary wants financial defensibility; NRLA wants transparent itemised cost. All three align on a defensible, published, periodically reviewed fee.

---

## Communication & Engagement Plan

### Stakeholder-Specific Messaging

#### Secretary of State / Housing Minister

**Primary Message**: The register is on track for the political commitment; here are the visible milestones over the next 90 days; here are the two risks I am asking you to be aware of.

**Key Talking Points**:
- First-area commencement date is protected; here is the descope plan if needed
- Visible launch story is being prepared with Comms
- ICO engagement is ahead of consultation requirement — no nasty surprises

**Communication Frequency**: Monthly written submission; ad hoc on PQ support and media handling

**Preferred Channel**: Ministerial submission, fortnightly oral readout from SRO via Director PRS Policy

**Success Story**: "First-area register live ahead of schedule; LHA enforcement actions up X%."

---

#### Permanent Secretary

**Primary Message**: Every decision is evidence-backed and audit-defensible.

**Key Talking Points**:
- Business case approved, gate reviews on track
- DPIA in train, ICO engaged
- Cost recovery model holds under sensitivity testing

**Communication Frequency**: Quarterly Accounting Officer assurance meeting

**Preferred Channel**: Written assurance report

**Success Story**: NAO post-implementation review with positive findings.

---

#### Local Housing Authorities (via LGA)

**Primary Message**: This tool will make your enforcement work easier, and you will be funded for the new burden.

**Key Talking Points**:
- API-first, integrates with your existing case management systems
- New burdens funding tied to onboarding
- Co-designed with pilot authorities; you can join the pilot
- Selective licensing data won't be lost

**Communication Frequency**: Monthly LGA forum; quarterly LHA briefing webinar

**Preferred Channel**: LGA-mediated forum, dedicated LHA Slack/Teams channel, in-person regional roadshow

**Success Story**: "I used to wait six months for tip-offs; now I can see in 30 seconds who's not registered."

---

#### Landlords (via NRLA, Propertymark)

**Primary Message**: This is straightforward, proportionate, and the same for everyone in your area.

**Key Talking Points**:
- 15–30 minute registration for a single property
- Fee covers actual cost of running the register, itemised publicly
- Agent-mediated bulk registration available
- Your data is only seen by you, your LHA, and (in narrow scope) the public — not the world

**Communication Frequency**: Monthly NRLA forum; comms campaign in months 3–6 before first-area commencement; ongoing webinars

**Preferred Channel**: NRLA newsletter, Propertymark webinars, GOV.UK Notify reminders

**Success Story**: "Registered in 20 minutes, got the LHA reminder, all good."

---

#### Tenants (via Generation Rent, GOV.UK feedback)

**Primary Message**: You can check your landlord, see safety certificates, and report concerns to your council with evidence.

**Key Talking Points**:
- Plain-language lookup
- Accessible to everyone (WCAG 2.2 AA)
- Free to use
- Reports go directly to enforcement

**Communication Frequency**: Quarterly user research; public roadmap on GOV.UK; press at launch

**Preferred Channel**: GOV.UK, Generation Rent network, Citizens Advice

**Success Story**: "Before I signed, I checked, found the landlord wasn't registered, walked away — and reported it."

---

#### CDDO / GDS

**Primary Message**: We are reusing common platforms; we are running clean service assessments; we have nothing to hide.

**Key Talking Points**:
- One Login, Pay, Notify reused
- Open-source non-sensitive code
- Service assessments booked early

**Communication Frequency**: Per-gate (alpha, beta, live) + monthly spend control update

**Preferred Channel**: Service assessment, spend control submissions, CDDO portfolio review

**Success Story**: First-time pass at alpha, beta, live; cited in CDDO portfolio examples.

---

#### ICO

**Primary Message**: We have engaged you early, our DPIA is live, our scope is proportionate, and we will tell you about incidents.

**Key Talking Points**:
- DPIA published in summary
- Lawful basis: Article 6(1)(c) (legal obligation) + Article 6(1)(e) (public task) where applicable
- Public scope minimised, evidenced through user research and policy intent
- Subject access rights respected

**Communication Frequency**: Pre-launch consultation, then annual review unless incident

**Preferred Channel**: Direct DPO-to-ICO correspondence, formal consultation process

**Success Story**: "MHCLG's PRS DPIA cited as a model of public-task processing at population scale."

---

## Change Impact Assessment

### Impact on Stakeholders

| Stakeholder | Current State | Future State | Change Magnitude | Resistance Risk | Mitigation Strategy |
|-------------|---------------|--------------|------------------|-----------------|---------------------|
| Local Housing Authorities | Reactive enforcement based on tip-offs, council tax data, selective licensing where present | Proactive intelligence-led enforcement from central register, integrated with case management systems | HIGH | MEDIUM | New burdens funding; co-design via pilot; LGA-mediated change; API-first integration |
| Individual landlords (small) | No central register; selective licensing only in some areas | Mandatory annual registration with fee | HIGH | MEDIUM–HIGH | Simple online journey; phased area rollout to spread comms load; NRLA co-design of guidance |
| Corporate landlords | Companies House registration plus piecemeal local licensing | Single national register, bulk registration via agent or API | MEDIUM | LOW–MEDIUM | API for portfolio registration; clear corporate identity flow |
| Letting agents | Variable involvement in local licensing | Bulk registration on behalf of landlord clients | MEDIUM | LOW | Propertymark engagement; agent journey co-designed |
| Tenants | Tip-off-driven complaint routes; no easy way to verify landlord | Public lookup, signposted enforcement route | LOW (passive beneficiary) | LOW | Plain-language design; Generation Rent and Citizens Advice channels |
| HMCTS county courts | Process possession notices without registration check | Statutory requirement that landlord be registered to serve a valid possession notice | MEDIUM | LOW–MEDIUM (procedural) | Data sharing MoU; HMCTS process redesign jointly planned |
| PRS Ombudsman | New scheme starting alongside register | Cross-references register to validate landlord identity | MEDIUM | LOW | Operating model co-design; data-sharing MoU |
| MHCLG Digital team | Existing capability under MHCLG CDIO | New high-profile service, possibly first GDS-assessed register at this scale in MHCLG | MEDIUM | LOW | Recruit ahead, DDaT capability plan, supplier mix |

### Change Readiness

**Champions** (Enthusiastic supporters):
- Generation Rent / Renters' Reform Coalition — register is their policy ask, public lookup is their win
- Pilot LHAs — earliest movers with most to gain from intelligence-led enforcement
- Compliant corporate landlords — register raises the floor in their market
- Compliant letting agents (Propertymark members) — register differentiates them from informal operators

**Fence-sitters** (Neutral, need convincing):
- NRLA — supportive in principle, defensive on scope, fees, and function creep
- Most LHAs — supportive but capacity-constrained; need to see new burdens funding flowing
- HMCTS — willing partner but slow procedural change

**Resisters** (Opposed or skeptical):
- Small landlords without digital channels — resentful of compliance burden, low awareness
- Informal/unregistered landlords — actively resistant; the constituency the register exists to surface
- Some commentators in housing press — will scrutinise launch issues heavily; risk of "register chaos" framing on any go-live problem

---

## Risk Register (Stakeholder-Related)

### Risk R-1: Ministerial pressure forces release before service is ready

**Related Stakeholders**: Secretary of State, Minister, SRO, Service Owner, CDDO

**Risk Description**: Political imperative to demonstrate delivery results in pressure to launch before the service has passed beta assessment, exposing it to early failure and reputational damage.

**Impact on Goals**: Threatens G-1 (in form), G-6 (assessment), G-4 (ICO action triggered by under-tested launch).

**Probability**: HIGH

**Impact**: HIGH

**Mitigation Strategy**: Pre-agreed descope playbook signed by SRO and Director PRS Policy; phased-area rollout that gives Ministers a "live" announcement without national exposure; pre-briefed Ministerial communications; CDDO assessment gating made visible.

**Contingency Plan**: If Minister insists on launch against advice, formal Accounting Officer letter from Permanent Secretary recording professional disagreement.

---

### Risk R-2: ICO requires DPIA rework or prior consultation, delaying beta

**Related Stakeholders**: ICO, SIRO, DPO, SRO

**Risk Description**: ICO scrutiny identifies residual risk requiring narrowed public scope, additional safeguards, or formal Article 36 prior consultation, with timetable knock-on.

**Impact on Goals**: G-1 schedule, G-2 schedule, G-4 record.

**Probability**: MEDIUM

**Impact**: HIGH

**Mitigation Strategy**: ICO engagement from discovery; DPIA iterated each phase; data scope tested with ICO before public commitment.

**Contingency Plan**: Narrow public scope at launch; broaden post-launch with evidence; reuse content from earlier MHCLG / Cabinet Office DPIAs.

---

### Risk R-3: LHA adoption stalls because of funding shortfall or vendor lock-in

**Related Stakeholders**: LHAs, LGA, HMT, Service Owner, case management system vendors

**Risk Description**: New burdens funding doesn't reach LHAs in time, or LHA case management system vendors are slow/expensive to integrate, causing adoption rate to fall short of 90% target.

**Impact on Goals**: G-3, G-8, O-3, O-5.

**Probability**: MEDIUM–HIGH

**Impact**: MEDIUM

**Mitigation Strategy**: Early HMT/MHCLG agreement on new burdens funding; vendor engagement programme from alpha; well-documented open API to avoid vendor gatekeeping; LGA-mediated adoption plan.

**Contingency Plan**: Reference UI provided for any LHA whose case management vendor doesn't integrate in time; phased adoption targets revisited at month-6.

---

### Risk R-4: Major data breach or scraping incident in first 12 months

**Related Stakeholders**: NCSC, Cyber Lead, SIRO, ICO, Minister, landlords, tenants

**Risk Description**: Public lookup or LHA portal is breached or systematically scraped, exposing landlord personal data and contact details at scale.

**Impact on Goals**: G-2, G-4, G-7, all outcomes.

**Probability**: MEDIUM

**Impact**: VERY HIGH

**Mitigation Strategy**: Minimum-necessary public scope; rate limiting and bot mitigation; ITHC and red team testing pre-launch; CAF self-assessment; departmental SOC integration; trained incident response.

**Contingency Plan**: Tested incident response playbook; pre-drafted Ministerial submission; pre-agreed ICO breach notification process; communications playbook.

---

### Risk R-5: NRLA mobilises sustained public opposition to fee level or data scope

**Related Stakeholders**: NRLA, Minister, Director PRS Policy, MHCLG Comms

**Risk Description**: Fee schedule or data scope provokes coordinated NRLA opposition, leading to negative media campaign, MP correspondence surge, and Ministerial reversal mid-programme.

**Impact on Goals**: G-5, G-1.

**Probability**: MEDIUM

**Impact**: MEDIUM

**Mitigation Strategy**: Early and structured NRLA consultation on fee and scope; itemised cost rationale published; periodic fee review committed in writing.

**Contingency Plan**: Adjust fee schedule at next review point; Minister-NRLA engagement to defuse; transparency report.

---

### Risk R-6: Function creep introduces algorithmic risk scoring without ATRS / Article 22 controls

**Related Stakeholders**: ICO, NRLA, Generation Rent, Director PRS Policy

**Risk Description**: Operational team or policy adds a "landlord risk score" feature using ML/heuristics without ATRS publication or DPIA refresh, exposing the department to enforcement and political risk.

**Impact on Goals**: G-4, O-2.

**Probability**: MEDIUM (over multi-year horizon)

**Impact**: HIGH

**Mitigation Strategy**: Architecture Decision Record explicitly prohibiting V1 algorithmic risk scoring; change control requiring ATRS + DPIA refresh for any future scoring; AI Playbook compliance review.

**Contingency Plan**: Withdraw feature; publish ATRS retrospectively; ICO notification.

---

### Risk R-7: SRO or Service Owner departure during delivery

**Related Stakeholders**: Permanent Secretary, SRO, Service Owner, CDDO

**Risk Description**: Senior role turnover loses programme knowledge and momentum mid-delivery.

**Impact on Goals**: All schedule-bound goals.

**Probability**: MEDIUM (over a 24-month delivery)

**Impact**: MEDIUM–HIGH

**Mitigation Strategy**: Senior succession plan documented; deputy/shadow appointments; programme office continuity independent of named individuals.

**Contingency Plan**: Pre-identified internal successor; SRO transition protocol per IPA guidance.

---

## Governance & Decision Rights

### Decision Authority Matrix (RACI)

| Decision Type | Responsible | Accountable | Consulted | Informed |
|---------------|-------------|-------------|-----------|----------|
| Statutory Instrument commencement date | Director PRS Policy | Minister | SRO, Service Owner, Permanent Secretary | All |
| Architecture / technology stack | Tech Lead / Architect | Service Owner | Cyber Lead, SIRO, CDIO, CDDO | Programme Board |
| Public data scope (what tenants see) | Service Owner | SIRO + Director PRS Policy (joint) | ICO, NRLA, Generation Rent, DPO | Minister, all |
| Fee schedule | MHCLG Finance / Commercial | Minister + HMT (joint) | NRLA, NAO | All |
| Service assessment submission | Service Owner | SRO | CDDO assessment lead | Permanent Secretary, Minister |
| DPIA approval | DPO | SIRO | ICO, Cyber Lead, Service Owner | SRO, Permanent Secretary |
| Procurement / supplier contract award | MHCLG Commercial | Accounting Officer (Permanent Secretary) | SRO, Tech Lead, CDDO spend control | Minister |
| Release go / no-go (alpha → beta → live) | Service Owner | SRO | CDDO, SIRO, Cyber Lead | Minister, Director PRS Policy |
| New burdens funding for LHAs | Director PRS Policy | Minister + HMT | LGA, MHCLG Finance | LHAs |
| Incident response activation | Cyber Lead | SIRO | DPO, Service Owner | SRO, Minister (if Cat 1/2) |
| ICO incident notification | DPO | SIRO | Cyber Lead, Service Owner | Permanent Secretary, Minister |
| Scope change (add/remove a register field) | Director PRS Policy | SRO | Service Owner, ICO, NRLA, Generation Rent | All |
| Future algorithmic risk scoring (any V2+) | Director PRS Policy | SIRO + ICO consultation | Service Owner, NRLA, Generation Rent | All |

### Escalation Path

1. **Level 1**: Delivery Manager / Product Manager — day-to-day delivery decisions, sprint-level scope.
2. **Level 2**: Service Owner — service-level decisions including release readiness, design choices.
3. **Level 3**: SRO + Programme Board — scope, time, cost variance; cross-departmental dependencies (One Login, Land Registry, etc.).
4. **Level 4**: Permanent Secretary — Accounting Officer decisions, spending breaches, formal letters of disagreement.
5. **Level 5**: Minister + Secretary of State — political and statutory decisions, scope set by SI, public-facing commitments.

Each step includes a target turnaround (Level 1: 1 working day; Level 2: 3 working days; Level 3: 1 week; Levels 4 and 5: as required, with no implicit SLA but with the SRO maintaining the escalation log).

---

## Validation & Sign-off

### Stakeholder Review

| Stakeholder | Review Date | Comments | Status |
|-------------|-------------|----------|--------|
| SRO, PRS Register Programme | PENDING | Initial draft circulated; review scheduled | PENDING |
| Service Owner | PENDING | — | PENDING |
| Director, PRS Policy | PENDING | — | PENDING |
| MHCLG SIRO | PENDING | — | PENDING |
| MHCLG DPO | PENDING | — | PENDING |
| LGA representative (LHA voice) | PENDING | — | PENDING |
| NRLA policy lead (sector consultation) | PENDING | — | PENDING |
| Generation Rent policy lead (sector consultation) | PENDING | — | PENDING |

### Document Approval

| Role | Name | Signature | Date |
|------|------|-----------|------|
| SRO (Senior Responsible Owner) | PENDING | PENDING | PENDING |
| Service Owner | PENDING | PENDING | PENDING |
| Director, PRS Policy | PENDING | PENDING | PENDING |
| Enterprise Architect (MHCLG CDIO delegate) | PENDING | PENDING | PENDING |

---

## Appendices

### Appendix A: Stakeholder Interview Summaries

> Interviews not yet conducted at v1.0. This appendix will be populated during the discovery phase. Each interview to record key drivers, quotes, and follow-up actions in line with the document body above.

### Appendix B: Survey Results

> No surveys conducted at v1.0. Initial landlord and tenant user-research waves are scheduled to begin in discovery. Survey design will draw on the drivers identified in SD-11 (landlords) and SD-12 (tenants).

### Appendix C: References

- Renters' Rights Act 2025 (UKPGA 2025/26), Part 2 — [legislation.gov.uk/ukpga/2025/26/contents](https://www.legislation.gov.uk/ukpga/2025/26/contents)
- UK GDPR and Data Protection Act 2018 (Article 35 DPIA obligation)
- NCSC Secure by Design principles — [ncsc.gov.uk/collection/cyber-security-design-principles](https://www.ncsc.gov.uk/collection/cyber-security-design-principles)
- GDS Service Standard — [gov.uk/service-manual/service-standard](https://www.gov.uk/service-manual/service-standard)
- Technology Code of Practice — [gov.uk/guidance/the-technology-code-of-practice](https://www.gov.uk/guidance/the-technology-code-of-practice)
- Public Sector Bodies (Websites and Mobile Applications) (No. 2) Accessibility Regulations 2018 (WCAG 2.2 AA target)
- CDDO Digital and Data spend controls
- GovS 005 — Government Functional Standard for Digital
- GovS 007 — Government Functional Standard for Security
- HM Treasury Green Book + Orange Book (Five Case Model + risk management)
- ArcKit Principles (`projects/000-global/`) — to be created in subsequent step

---

## External References

> This section provides traceability from generated content back to source documents.

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| *None at v1.0* | — | — | — | No external documents lodged in `projects/001-prs-database/external/` at time of writing. CLAUDE.md project description used as the primary in-repository context. |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| — | — | — | — | — |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| — | — | — |

---

**Generated by**: ArcKit `/arckit:stakeholders` command
**Generated on**: 2026-05-28
**ArcKit Version**: 5.4.0
**Project**: PRS Database (Project 001)
**AI Model**: Claude Opus 4.7 (1M context) — `claude-opus-4-7[1m]`
