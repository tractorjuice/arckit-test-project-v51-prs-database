# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

This is an **ArcKit governance workspace**, not a software project. There is no application code, no build, no test suite, no linter. The deliverables are markdown artifacts under `projects/` produced by the ArcKit plugin's `/arckit:*` slash commands. The subject of those artifacts is the UK national Private Rented Sector (PRS) Database delivered by MHCLG under the Renters' Rights Act 2025.

If a future task asks to "build" or "test" something here, clarify with the user — it almost certainly means producing or refreshing an ArcKit artifact, not running a toolchain.

## Project: PRS Database

UK national Private Rented Sector (PRS) database — a mandatory register of landlords and rental properties under the Renters' Rights Act 2025 ([UKPGA 2025/26](https://www.legislation.gov.uk/ukpga/2025/26/contents)). Delivered by MHCLG (Ministry for Housing, Communities and Local Government), rolled out from late 2026 in two stages: landlord/property registration first (area-by-area), public tenant lookup second.

### Domain context

- **Owner**: MHCLG; PRS Ombudsman links downstream.
- **Users**: ~2.3M landlords, ~5.5M PRS tenants in England, ~317 local housing authorities, letting agents.
- **Statutory basis**: Renters' Rights Act 2025, Part 2.
- **Penalties**: civil £5,000 baseline → £40,000 for serious/repeated breach; unregistered landlords cannot serve a valid possession notice.
- **Data scope**: landlord identity + contact, full property address, beds/occupancy/furnishing, gas/electrical/EPC safety certificates, banning orders, rent enforcement history.
- **Compliance surface**: UK GDPR (Article 35 DPIA mandatory), NCSC Secure by Design, GDS Service Standard, Technology Code of Practice, Accessibility Regulations 2018 (WCAG 2.2 AA), CDDO standards, AI Playbook + ATRS if automated risk-scoring or fraud detection is added.
- **Integration points**: GOV.UK One Login, Companies House, HM Land Registry / OS UPRN, GOV.UK Pay, GOV.UK Notify, HMCTS, PRS Ombudsman, LHA case management systems.

## Existing artifacts and the decisions they encode

Three artifacts exist; future work should be consistent with them or explicitly version-bump them.

- `projects/000-global/ARC-000-PRIN-v1.0.md` — 23 architecture principles (P-1…P-23). Six are non-exceptable: P-4 Security by Design, P-6 Data Sovereignty & UK GDPR, P-7 Data Minimisation, P-19 Accessibility (WCAG 2.2 AA), P-21 Algorithmic Accountability/ATRS. Principles are technology-agnostic by policy.
- `projects/001-prs-database/ARC-001-STKE-v1.0.md` — 14 stakeholder driver groups (SD-1…SD-14), 8 goals (G-1…G-8), 6 outcomes (O-1…O-6), 6 conflicts (C-1…C-6), 7 risks (R-1…R-7).
- `projects/001-prs-database/ARC-001-REQ-v1.0.md` — 64 requirements (BR×8, FR×20, NFR×23, INT×8, DR×10) with traceability to SD/G/O and P-N IDs.

**Load-bearing decisions already taken**:

- **V1 explicitly excludes algorithmic risk-scoring of landlords or tenants** (FR-020, P-21). Adding any automated decisioning requires DPIA refresh + ATRS publication + AI Playbook review + Article 22 GDPR assessment.
- **Three-projection data model**: registrant view, LHA restricted view, public lookup view are *separate projections*, not filters over a master query (FR-007, DR-008/9). Public scope is DPIA-driven, not policy-decided.
- **UPRN is the canonical property identifier** (FR-003, P-8). Manual addresses are moderation-only.
- **Identity assurance is stepped-up**: minimum at registration, elevated for high-consequence actions (FR-001, resolves conflict C-6). The full step-up model is still to be captured in an ADR.
- **LHA integration is API-first** with a reference UI fallback (FR-010, resolves C-4).
- **Phased rollout protects the Ministerial date**: "first-area live by end of 2026" is the political commitment, not "national live" (resolves C-1).
- **Scope is England only, English only, v1** — Wales/Scotland/NI and Welsh-language alternatives are out of scope.

## ArcKit working model

### Slash commands

Plugin commands are invoked as `/arckit:<name>` (colon, not dot). Some templates and older docs still use `/arckit.X`; the colon form is authoritative in this environment. The plugin lists 71 commands; the ones most relevant here are:

- `/arckit:start` — orient and choose a workflow
- `/arckit:principles` — global architecture principles (in `000-global`)
- `/arckit:stakeholders` — stakeholder drivers, goals, outcomes
- `/arckit:requirements` — BR / FR / NFR / INT / DR with MoSCoW priority
- `/arckit:sobc` — Strategic Outline Business Case (Green Book 5-case)
- `/arckit:dpia` — Article 35 DPIA (mandatory for this programme)
- `/arckit:secure` — NCSC Secure by Design assessment
- `/arckit:tcop` — Technology Code of Practice review
- `/arckit:service-assessment` — GDS Service Standard readiness
- `/arckit:risk` — Orange Book risk register
- `/arckit:adr` — Architecture Decision Records (multi-instance under `decisions/`)
- `/arckit:diagram` — Mermaid/C4 architecture diagrams (multi-instance under `diagrams/`)
- `/arckit:data-model` — entity model + GDPR mapping
- `/arckit:traceability` — requirements traceability matrix
- `/arckit:pages` — regenerate the `docs/` documentation site
- `/arckit:health` — diagnostic scan for stale/orphaned artifacts (writes `docs/health.json`)

### Document naming

All artifacts use `ARC-{PROJECT_ID}-{TYPE}-v{VERSION}.md`:

- Single-instance: `ARC-001-REQ-v1.0.md` (one per project)
- Multi-instance: `ARC-001-ADR-001-v1.0.md`, `ARC-001-DIAG-002-v1.0.md` (numbered sequence)
- Cross-project / global: `000` is the project ID, lives in `projects/000-global/`

### Traceability conventions (used throughout the existing artifacts)

- Stakeholder drivers: `SD-1`…`SD-N`
- Goals: `G-1`…`G-N`
- Outcomes: `O-1`…`O-N`
- Conflicts: `C-1`…`C-N`
- Principles: `P-1`…`P-N`
- Risks: `R-1`…`R-N`
- Business requirements: `BR-001`…
- Functional requirements: `FR-001`…
- Non-functional, by category: `NFR-P-`, `NFR-A-`, `NFR-S-`, `NFR-SEC-`, `NFR-C-`, `NFR-U-`, `NFR-M-`, `NFR-I-`
- Integration: `INT-001`…
- Data entities: `DR-001`…

When producing a new artifact, link back to the IDs from the upstream artifact (REQ traces to STKE drivers and PRIN principles; ADR traces to REQ; HLD/DLD trace to ADR and REQ; etc.).

## Project structure

```text
projects/
├── 000-global/                    # Cross-project artifacts (principles, policies)
│   ├── ARC-000-PRIN-v1.0.md       # Architecture principles (exists)
│   ├── external/                  # Enterprise reference docs (empty)
│   └── policies/                  # Governance policies (empty)
└── 001-prs-database/              # PRS Database artifacts
    ├── README.md
    ├── external/                  # Project-specific reference docs (empty)
    ├── ARC-001-STKE-v1.0.md       # Stakeholder analysis (exists)
    ├── ARC-001-REQ-v1.0.md        # Requirements (exists)
    └── (future: decisions/, diagrams/, reviews/, research/, etc.)

docs/                              # Generated documentation site (regenerated by hook)
├── index.html
├── manifest.json
├── llms.txt
├── health.json
└── guides/                        # 159 plugin guide files synced on each /arckit:pages run

.arckit/memory/                    # Plugin state (telemetry rewrites every interaction)
```

## Hook behaviour to be aware of

- **`sync-guides` hook**: runs on every `/arckit:pages` invocation. It rewrites `docs/index.html`, `docs/manifest.json`, `docs/llms.txt`, syncs `docs/guides/`, and provides document stats in the prompt context. When this hook fires, do **not** call read/write/glob/grep tools to produce the page summary — the hook context already contains the stats. Output only the summary.
- **`graph-inject` / health pre-processor**: runs on `/arckit:health`. Same pattern — findings come from the hook context; skip the manual scanning steps when the hook context is present.
- **Telemetry churn**: `.arckit/memory/.telemetry.jsonl` and `docs/telemetry.json` are touched by the plugin on every command. They will show up dirty in `git status` even when no user-meaningful change happened. When committing, include them; when pulling/rebasing, stash them first (the user previously approved `git stash push -- .arckit/memory/.telemetry.jsonl` before `git pull --rebase`).
- **Commands include `arckit:` skill invocations**: when the user types `/arckit:<name>`, treat it as a Skill invocation (the harness loads the skill automatically) — don't try to re-invoke or look up the implementation elsewhere.

## Working preferences from prior sessions

- Commit messages follow Conventional Commits style (`feat(NNN-name): …`). Confirmed: the user accepts the `Co-Authored-By: Claude Opus 4.7 (1M context) <noreply@anthropic.com>` trailer.
- The user prefers `git pull --rebase` for integration when local and remote have diverged (confirmed in prior session for the README-only remote commit).
- Don't push without an explicit "push" instruction.
- The user normally runs `/arckit:pages` after each new artifact and then asks to commit and push; the typical commit therefore bundles the new artifact + regenerated `docs/` + `.arckit/memory/` telemetry.

## Open questions still worth asking before producing artifacts

These were raised in the original CLAUDE.md and are not yet fully resolved in the existing artifacts. They are likely to come up in `/arckit:adr`, `/arckit:dpia`, `/arckit:data-model`, `/arckit:secure`:

- Identity assurance step-up: at what point does One Login assurance need to be re-verified (only at registration, at renewal, at possession notice)?
- Performance envelope under enforcement-driven access spikes (e.g., a high-profile court case causes a media-driven lookup surge).
- Migration paths from existing local-authority selective licensing schemes — what data, with what provenance, can be ingested?
- Public view scope — needs ICO consultation; FR-007 / DR-008 currently leave the exact fields DPIA-driven.
- Cost recovery sensitivity: what happens to the fee model if a material portion of small landlords exit the sector at commencement?

## Links

- ArcKit: <https://tractorjuice.github.io/arc-kit/>
- Renters' Rights Act 2025: <https://www.legislation.gov.uk/ukpga/2025/26/contents>
- See `README.md` for the full source list (Hogan Lovells, Pinsent Masons, RICS, MHCLG blog, etc.).
