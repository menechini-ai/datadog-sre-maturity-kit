<p align="center">
  <img alt="Datadog SRE Maturity Kit" src="https://img.shields.io/badge/SRE%20Spec%20Kit-Datadog-632CA6?logo=datadog&logoColor=white&style=for-the-badge" width="400px">
</p>

<h1 align="center">Datadog SRE Maturity Kit</h1>

<p align="center">
  <strong>A comprehensive maturity assessment and implementation framework for Datadog Observability</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Maturity%20Levels-6%20(0--5)-blue" alt="Maturity Levels"/>
  <img src="https://img.shields.io/badge/Slash%20Commands-18-green" alt="Commands"/>
  <img src="https://img.shields.io/badge/Notebook%20Templates-14-orange" alt="Notebook Templates"/>
  <img src="https://img.shields.io/badge/license-MIT-green" alt="License"/>
</p>

<p align="center">
  <a href="#overview">Overview</a> •
  <a href="docs/commands.md">Commands</a> •
  <a href="docs/notebooks.md">Notebooks</a> •
  <a href="docs/operational-standards.md">Standards</a> •
  <a href="docs/mcp-config.md">MCP Config</a> •
  <a href="#quick-start">Quick Start</a> •
  <a href="#project-structure">Structure</a>
</p>

---

## Overview

The **Datadog SRE Maturity Kit** is a command-driven framework that helps SRE and platform engineering teams assess, plan, and implement observability best practices using Datadog. It provides a structured maturity model (Levels 0–5), pre-built slash commands for Claude Code, and ready-to-use notebook templates for assessments, investigations, runbooks, and reports.

This kit was built to bridge the gap between Datadog's raw capabilities and the operational standards required for production-grade observability at scale.

### What's inside

| Feature | Description |
|---------|-------------|
| **Maturity Assessment** | 6-level framework (Level 0–5) covering foundation to industry excellence |
| **Slash Commands** | 18 Claude Code commands for assessments, reports, gap analysis, and upgrades |
| **Notebook Templates** | 14 pre-built Datadog Notebook templates for common SRE workflows |
| **Tagging Strategy** | Comprehensive framework based on Datadog's Unified Service Tagging |
| **Operational Standards** | Platform preparation, access management, governance, data monitoring, visualization |
| **MCP Integration** | Datadog MCP Server configuration for AI-driven observability queries |
| **Gap Analysis** | Structured process to identify and plan maturity level upgrades |
| **Executive Reports** | Leadership-ready reporting templates with cost and health metrics |

## Features

### 📊 Maturity Assessment Framework

- **6 Levels**: Foundation (0) → Excellence (5) with clear graduation criteria
- **Objective Scoring**: Uses real Datadog data via MCP queries (not surveys)
- **Repeatable**: Track progress over time with reassessments
- **Comprehensive Checks**: Infrastructure, tagging, monitors, logs, APM, cost, incidents, dashboards

### 🎮 Slash Commands for Claude Code

- **Assessment Commands**: `/check-quick`, `/check-full`, `/check-level0`, `/check-level1`
- **Task Commands**: `/level0-infra`, `/level0-tagging`, `/level0-cost`, `/level0-healthcheck`, `/level2-tagging`, `/level3-cost`
- **Utility Commands**: `/gap-analysis`, `/upgrade-plan`, `/generate-report`, `/create-starter-notebooks`, `/save-to-notebook`, `/append-to-notebook`, `/help`
- **Smart Defaults**: Each command runs the right MCP queries, analyzes results, and formats output

### 📓 Notebook Templates

- **Assessments**: Level readiness, quarterly review, weekly assessment
- **Investigations**: Error spike, performance, cost investigation templates
- **Runbooks**: Alert response, service onboarding, cost optimization
- **Postmortems**: Incident postmortem, outage analysis
- **Reports**: Executive report, team health, monthly metrics

### 🏷️ Tagging Strategy

- **Reserved Tags**: `env`, `service`, `version`, `source`, `host`, `device` — per Unified Service Tagging
- **Critical Tags**: `team`, `runtime`, `journey`, `role`, `application`
- **Format Standards**: Lowercase with underscores — no hyphens, no unbounded sources
- **Compliance Checks**: Automated validation against tagging best practices

### 🔐 Governance & Compliance

- **PCI-DSS**: US1 site only, HTTPS endpoints, Audit Trail required
- **HIPAA**: BAA required, no Zendesk chat, no log sharing
- **FedRAMP**: GovCloud instance only (Moderate level)
- **GDPR**: EU1 site for data residency

## Maturity Levels

| Level | Name | Focus | Timeline |
|-------|------|-------|----------|
| **Level 0** | Foundation | Basic observability setup | 1–2 months |
| **Level 1** | Standardization | Operational excellence | 2–3 months |
| **Level 2** | Optimization | Efficiency & scale | 3–4 months |
| **Level 3** | Intelligence | Proactive operations | 4–6 months |
| **Level 4** | Innovation | Advanced capabilities | 6–9 months |
| **Level 5** | Excellence | Industry leadership | 9–12 months |

**Total journey**: Approximately 2–3 years. See [Level Definitions](./planning/level-definitions.md) for detailed requirements.

## Quick Start

```bash
# 1. Open this project in Claude Code

# 2. Run your first assessment
/check-quick

# 3. Check a specific level
/check-level0

# 4. Generate a report
/generate-report
```

See the [Quick Start Guide](./QUICKSTART.md) for a 5-minute walkthrough.

## Commands

### Assessment Commands

| Command | Description |
|---------|-------------|
| `/check-quick` | Quick 10-minute maturity check across all levels |
| `/check-full` | Comprehensive 30-minute deep-dive assessment |
| `/check-level0` | Level 0 (Foundation) validation |
| `/check-level1` | Level 1 (Standardization) validation |

### Task Commands

| Command | Description |
|---------|-------------|
| `/level0-infra` | Infrastructure discovery and inventory |
| `/level0-tagging` | Tagging compliance audit |
| `/level0-cost` | Cost baseline analysis |
| `/level0-healthcheck` | Account health check report |
| `/level2-tagging` | Advanced tagging strategy (Level 2) |
| `/level3-cost` | Cost optimization (Level 3) |

### Utility Commands

| Command | Description |
|---------|-------------|
| `/gap-analysis` | Identify gaps between current and target level |
| `/upgrade-plan` | Generate step-by-step upgrade roadmap |
| `/generate-report` | Create executive summary report |
| `/check-to-notebook` | Save assessment results to Datadog Notebook |
| `/save-to-notebook` | Save any output to a Datadog Notebook |
| `/append-to-notebook` | Append content to existing Datadog Notebook |
| `/create-starter-notebooks` | Bootstrap initial notebook library |
| `/help` | Show available commands and usage |

## Notebook Templates

```
notebooks/
├── assessments/
│   ├── level-readiness-template.md      # Level graduation validation
│   ├── quarterly-review-template.md      # Quarterly business review
│   └── weekly-assessment-template.md     # Weekly health check
├── investigations/
│   ├── error-spike-investigation.md      # Error spike root cause
│   ├── performance-investigation.md      # Performance regression
│   └── cost-investigation.md             # Cost anomaly analysis
├── runbooks/
│   ├── alert-response-runbook.md         # Standard alert response
│   ├── service-onboarding-runbook.md     # New service setup
│   └── cost-optimization-runbook.md      # Cost reduction playbook
├── postmortems/
│   ├── incident-postmortem-template.md   # Post-incident review
│   └── outage-analysis-template.md       # Outage impact analysis
└── reports/
    ├── executive-report-template.md      # Leadership summary
    ├── team-health-report.md             # Team health dashboard
    └── monthly-metrics-report.md         # Monthly KPI report
```

## Project Structure

```
datadog-sre-maturity-kit/
├── .claude/commands/            # Slash command definitions (18 commands)
│   ├── assess.md                # Quick assessment
│   ├── assess-full.md           # Comprehensive assessment
│   ├── assess-level0.md         # Level 0 validation
│   ├── assess-level1.md         # Level 1 validation
│   ├── level0-infra.md          # Infrastructure discovery
│   ├── level0-tagging.md        # Tagging audit
│   ├── level0-cost.md           # Cost baseline
│   ├── level0-healthcheck.md    # Health check
│   ├── level2-tagging.md        # Advanced tagging
│   ├── level3-cost.md           # Cost optimization
│   ├── gap-analysis.md          # Gap identification
│   ├── upgrade-plan.md          # Upgrade roadmap
│   ├── generate-report.md       # Executive report
│   ├── create-starter-notebooks.md
│   ├── save-to-notebook.md
│   ├── append-to-notebook.md
│   ├── assess-to-notebook.md
│   └── help.md
├── notebooks/                   # Datadog Notebook templates (14)
│   ├── 00-healthcheck-account-analysis.md
│   ├── 01-operational-standards-platform-preparation.md
│   ├── 02-operational-standards-access-management.md
│   ├── 03-operational-standards-governance.md
│   ├── 04-operational-standards-data-monitoring.md
│   ├── 05-operational-standards-data-visualization.md
│   ├── operational-standards-tagging-strategy.md
│   ├── assessments/
│   ├── investigations/
│   ├── runbooks/
│   ├── postmortems/
│   └── reports/
├── planning/                    # Planning & methodology docs
│   ├── level-definitions.md     # Maturity level criteria
│   ├── assessment-methodology.md
│   ├── operational-standards-mapping.md
│   ├── notebook-templates-spec.md
│   └── notebook-naming-conventions.md
├── docs/                        # Documentation hub
│   ├── overview.md              # Architecture and maturity model
│   ├── commands.md              # Slash command reference (Anthropic format)
│   ├── notebooks.md             # Template reference
│   ├── operational-standards.md # Standards reference
│   └── mcp-config.md            # MCP configuration guide
├── datadog-info/                # Datadog reference
├── mcp.json                     # Datadog MCP Server (US3)
├── mcp.env.example              # MCP environment variables
├── COMMANDS.md                  # Full command reference
├── QUICKSTART.md                # Quick start guide
├── PLAN.md                      # Project roadmap
└── CLAUDE.md                    # Claude Code guidance
```

## Configuration

### Environment Variables (`.env`)

```env
DD_SITE=datadoghq.com
DD_API_KEY=your-api-key
DD_APP_KEY=your-app-key
```

### MCP Configuration (`mcp.json`)

```json
{
  "mcpServers": {
    "datadog": {
      "type": "http",
      "url": "https://mcp.datadoghq.com/api/unstable/mcp-server/mcp"
    }
  }
}
```

For other Datadog sites, replace `us3` with your [site subdomain](https://docs.datadoghq.com/getting_started/site/) (e.g., `us1`, `eu`, `us5`).

## Operational Standards

| Standard | Description |
|----------|-------------|
| [Platform Preparation](./notebooks/01-operational-standards-platform-preparation.md) | Network egress, proxy config, API/App key strategies |
| [Access Management](./notebooks/02-operational-standards-access-management.md) | RBAC roles, Datadog Teams, permission management |
| [Governance](./notebooks/03-operational-standards-governance.md) | Compliance (GDPR, HIPAA, FedRAMP, PCI-DSS), agent deployment |
| [Data Monitoring](./notebooks/04-operational-standards-data-monitoring.md) | Log management, indexing, archiving |
| [Data Visualization](./notebooks/05-operational-standards-data-visualization.md) | Dashboard design patterns, template variables |
| [Tagging Strategy](./notebooks/operational-standards-tagging-strategy.md) | Unified Service Tagging, reserved & recommended tags |

## Contributing

1. Pick a maturity level or operational standard to work on
2. Update the corresponding notebook or planning document
3. Run `/check-quick` to validate your changes
4. Submit a pull request

---

## Documentation

All detailed documentation is in the [`docs/`](./docs/) directory:

| Document | Description |
|----------|-------------|
| [Overview](./docs/overview.md) | Architecture, components, maturity model |
| [Commands Reference](./docs/commands.md) | All 18 slash commands with Anthropic-format frontmatter |
| [Notebook Templates](./docs/notebooks.md) | 14 template reference with frontmatter schemas |
| [Operational Standards](./docs/operational-standards.md) | 7 standards documents and key principles |
| [MCP Configuration](./docs/mcp-config.md) | Server setup, env vars, regional endpoints |

---

**Version**: 1.0
**Last Updated**: 2026-07-10
**Maintained By**: SRE Platform Team

---

*This project is a fork of [nuttea/spec-kit-sre-datadog](https://github.com/nuttea/spec-kit-sre-datadog/tree/main), the original SRE Spec Kit for Datadog.*
