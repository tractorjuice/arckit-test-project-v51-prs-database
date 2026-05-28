# CLAUDE.md

## Project: PRS Database

UK national Private Rented Sector (PRS) database — a mandatory register of landlords and rental properties under the Renters' Rights Act 2025 ([UKPGA 2025/26](https://www.legislation.gov.uk/ukpga/2025/26/contents)). Delivered by MHCLG (Ministry for Housing, Communities and Local Government), rolled out from late 2026 in two stages: landlord/property registration first (area-by-area), public tenant lookup second.

### Domain context

- **Owner:** MHCLG; PRS Ombudsman links downstream.
- **Users:** ~2.3M landlords, ~5.5M PRS tenants in England, ~317 local housing authorities, letting agents.
- **Statutory basis:** Renters' Rights Act 2025, Part 2.
- **Penalties:** civil £5,000 baseline → £40,000 for serious/repeated breach; unregistered landlords cannot serve a valid possession notice.
- **Data scope:** landlord identity + contact, full property address, beds/occupancy/furnishing, gas/electrical/EPC safety certificates, banning orders, rent enforcement history.
- **Compliance surface:** UK GDPR (DPIA mandatory — Article 35), NCSC Secure by Design, GDS Service Standard, Technology Code of Practice, Accessibility Regulations 2018 (WCAG 2.2 AA), CDDO standards, AI Playbook + ATRS if any automated risk-scoring or fraud detection is introduced.
- **Integration points:** HM Land Registry (title verification), Companies House (corporate landlords), local authority HMO/selective licensing schemes, GOV.UK One Login, GOV.UK Pay (annual fee), GOV.UK Notify.

### Open architecture questions for this test repo

- Identity assurance for individual vs corporate landlords (GOV.UK One Login vs Companies House federation).
- Property uniqueness — UPRN as canonical key vs free-text address resolution.
- Public-vs-restricted views: what tenants see vs what enforcement officers see.
- Performance under enforcement-driven access spikes.
- Migration paths from existing local authority licensing databases.
- Data-quality / fraud signals without crossing into automated-decisioning (ATRS) territory.

## Architecture Toolkit

This project uses the **ArcKit plugin** (v5.4.0) for enterprise architecture governance. All commands are provided by the plugin — no local command files are needed.

### Key Commands

- `/arckit.start` - Orient and choose a workflow
- `/arckit.principles` - Architecture principles (start here)
- `/arckit.stakeholders` - Stakeholder analysis
- `/arckit.requirements` - Requirements specification
- `/arckit.sobc` - Strategic Outline Business Case (Green Book)
- `/arckit.dpia` - Data Protection Impact Assessment (Article 35)
- `/arckit.secure` - Secure by Design assessment
- `/arckit.tcop` - Technology Code of Practice review
- `/arckit.service-assessment` - GDS Service Standard readiness
- `/arckit.adr` - Architecture Decision Records
- `/arckit.diagram` - Architecture diagrams (C4, sequence, etc.)

### Project Structure

- `projects/000-global/` - Cross-project artifacts (principles, standards)
- `projects/001-*/` - Numbered project directories with architecture documents
- `docs/` - Documentation and guides

### Document Naming Convention

All documents follow: `ARC-{PROJECT_ID}-{TYPE_CODE}-v{VERSION}.md`

- Example: `ARC-001-REQ-v1.0.md` (Requirements for project 001)
- Multi-instance types (ADR, DIAG): `ARC-001-ADR-001-v1.0.md`
