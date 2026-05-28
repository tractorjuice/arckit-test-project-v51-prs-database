# PRS Database

UK national Private Rented Sector (PRS) database — a mandatory register of landlords and rental properties under the Renters' Rights Act 2025. Operated by MHCLG, the database underpins enforcement, tenant transparency, and a public-facing landlord-lookup service rolling out from late 2026.

## Project Context

The Renters' Rights Act 2025 ([UKPGA 2025/26](https://www.legislation.gov.uk/ukpga/2025/26/contents)) created a statutory PRS Database. Every landlord letting a property in England must register themselves and each dwelling before serving a possession notice or marketing the property. The database is delivered by MHCLG in two stages:

1. **Stage 1 — Registration (late 2026, rolled out area-by-area):** landlord and property registration, fee collection, safety certificate upload (gas, electrical, EPC).
2. **Stage 2 — Public access:** tenant-facing search/lookup, enforcement portal for local authorities, integration with the PRS Ombudsman.

This repo is an ArcKit governance workspace exploring the architecture of a national-scale public register: identity assurance for landlords, data quality, GDPR/Article 35 obligations, NCSC Secure by Design, GDS Service Standard, accessibility, and integration with HM Land Registry, Companies House, and local authority HMO/selective licensing systems.

## Overview

This repository uses **ArcKit v5.4.0** for enterprise architecture governance and documentation.

## Getting Started

### Prerequisites

- [Claude Code](https://claude.ai/code) installed
- GitHub Codespaces (recommended) or local development environment

### Setup

1. Open this repo in a GitHub Codespace (or clone locally)
2. Claude Code will auto-install via `.devcontainer/devcontainer.json`
3. The ArcKit plugin is auto-enabled via `.claude/settings.json`
4. Restart Claude Code once to resolve the marketplace plugin

### Suggested Command Sequence

```bash
# Get oriented
/arckit.start

# Strategic framing
/arckit.stakeholders PRS Database
/arckit.sobc PRS Database          # Green Book 5-case business case
/arckit.principles                  # Architecture principles
/arckit.requirements PRS Database   # BR / FR / NFR / INT / DR

# UK Gov compliance pack
/arckit.dpia                        # Article 35 DPIA (landlord PII + property data)
/arckit.secure                      # Secure by Design (civilian dept)
/arckit.tcop                        # Technology Code of Practice
/arckit.service-assessment          # GDS Service Standard readiness
/arckit.ai-playbook                 # If using AI for fraud/risk scoring
/arckit.atrs                        # ATRS record (if automated decisions)

# Design and roadmap
/arckit.diagram                     # C4 + sequence diagrams
/arckit.data-model                  # Entity model + GDPR mapping
/arckit.adr                         # Architecture decisions
/arckit.risk                        # Orange Book risk register
/arckit.roadmap                     # Multi-year capability evolution
```

## Project Structure

```text
projects/
├── 000-global/          # Cross-project artifacts (principles, standards)
└── 001-prs-database/    # Project-specific artifacts (created by commands)
```

## Available Commands

This project uses the ArcKit plugin which provides 71 slash commands for architecture governance. See the [full command reference](https://tractorjuice.github.io/arc-kit/).

## Links

### Primary sources

- [Renters' Rights Act 2025 (legislation.gov.uk)](https://www.legislation.gov.uk/ukpga/2025/26/contents)
- [House of Commons Library briefing — Renters' reform: what's happening and when (CBP-10669)](https://commonslibrary.parliament.uk/research-briefings/cbp-10669/)
- [MHCLG: Historic Renters' Rights Act now protecting millions (May 2026)](https://mhclgmedia.blog.gov.uk/2026/05/01/historic-renters-rights-act-now-protecting-millions-know-your-rights/)
- [MHCLG: One month to go — know your rights (April 2026)](https://mhclgmedia.blog.gov.uk/2026/04/01/one-month-to-go-know-your-rights-before-the-renters-rights-act-kicks-in/)

### Implementation analysis

- [Hogan Lovells — Renters' Rights Act: Implementation roadmap now published](https://www.hoganlovells.com/en/publications/renters-rights-act-implementation-roadmap-now-published)
- [Pinsent Masons — The Renters' Rights Act 2025: a guide for private landlords in England](https://www.pinsentmasons.com/out-law/guides/renters-rights-act-2025-guide-private-landlords-england)
- [RICS Property Journal — Renters' Rights Act: what's happening and when?](https://ww3.rics.org/uk/en/journals/property-journal/renters-rights-act-implementation-roadmap.html)
- [August App — PRS landlord database 2026: what it is and how to register](https://www.augustapp.com/blog/private-rented-sector-database)
- [Howard Morley & Sons — The Private Rented Sector Database: What is It & How Will It Work?](https://hmorley.co.uk/private-rented-sector-database/)

### ArcKit

- [ArcKit Documentation](https://tractorjuice.github.io/arc-kit/)
- [ArcKit Repository](https://github.com/tractorjuice/arc-kit)
