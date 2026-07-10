# CLAUDE.md — Datadog SRE Maturity Kit

This file provides guidance to Claude Code when working in this repository.

---

## Repository Overview

Command-driven framework for SRE teams to assess, plan, and implement Datadog observability best practices using a structured **maturity model (Levels 0–5)**. The kit provides **18 slash commands**, **14 notebook templates**, **7 operational standards**, and a self-service **assessment-tools** directory.

### Entry Points

| Resource | Purpose |
|----------|---------|
| [QUICKSTART.md](QUICKSTART.md) | Start here — 5-minute setup guide |
| [COMMANDS.md](COMMANDS.md) | Complete slash command reference |
| [README.md](README.md) | Project overview with badges and links |
| [docs/overview.md](docs/overview.md) | Architecture overview and components |

---

## Maturity Model

The entire framework is built around 6 levels. Every command, assessment, gap analysis, and upgrade plan references these levels.

| Level | Name | Focus | Typical Duration |
|-------|------|-------|-----------------|
| **Level 0** | Foundation | Discovery & Planning — infrastructure inventory, cost baseline, tagging strategy | 1–2 months |
| **Level 1** | Reactive | Initial Implementation — agent deployment, core monitors, basic dashboards, log collection | 2–3 months |
| **Level 2** | Proactive | Standardization — Unified Service Tagging, SLOs, monitor hygiene, APM, team RBAC | 3–4 months |
| **Level 3** | Managed | Optimized Operations — log efficiency, cost governance, SLO burn-rate alerts, compliance, on-call | 4–6 months |
| **Level 4** | Optimized | Advanced Automation — synthetics, RUM, CI/CD observability, self-healing, fleet automation | 6–9 months |
| **Level 5** | Excellence | Innovation & Scale — ML insights, predictive alerting, platform engineering, SLO-driven dev | 9–12 months |

### Assessment Dimensions (8)

Every assessment evaluates these 8 dimensions:
1. **Infrastructure Coverage** — Agent deployment, host coverage
2. **Tagging Compliance** — Unified Service Tagging completeness
3. **Service Catalog** — Service inventory and ownership
4. **Monitoring Quality** — Monitor coverage, alert fatigue
5. **Log Management** — Pipeline efficiency, indexing, archiving
6. **Cost Optimization** — Cost tracking, allocation, budgets
7. **Incident Management** — MTTR, severity, trend analysis
8. **Dashboard Maturity** — Layout, template variables, drill-down

### Standard Workflow

```
/quick-check → identifies current level
/gap-analysis → identifies gaps to next level
/upgrade-plan → creates implementation roadmap
/quick-check (re-run) → confirms graduation
```

---

## Slash Commands (18)

Commands live in `.claude/commands/` and work via `/command` OR natural language (e.g. "run a maturity assessment").

### Assessment Commands

| Command | Duration | Purpose |
|---------|----------|---------|
| `/quick-check` | 10 min | Quick maturity check across all 8 dimensions |
| `/full-check` | 30 min | Comprehensive deep-dive with gap analysis |
| `/check-level0` | 15 min | Level 0 (Foundation) readiness check |
| `/check-level1` | 15 min | Level 1 (Reactive) readiness check |

### Task Commands (by Level)

| Command | Level | Purpose |
|---------|-------|---------|
| `/level0-infra` | L0 | Infrastructure discovery |
| `/level0-tagging` | L0 | Tagging audit |
| `/level0-cost` | L0 | Cost baseline |
| `/level0-healthcheck` | L0 | Health check report |
| `/level2-tagging` | L2 | Level 2 tagging compliance |
| `/level3-cost` | L3 | Level 3 cost optimization |

### Utility Commands

| Command | Purpose |
|---------|---------|
| `/gap-analysis` | Identify gaps between current and target level |
| `/upgrade-plan` | Create step-by-step upgrade roadmap |
| `/generate-report` | Executive summary report |
| `/help` | List all available commands |

### Notebook Commands

| Command | Purpose |
|---------|---------|
| `/create-starter-notebooks` | Generate all 14 notebook templates |
| `/save-to-notebook` | Save any report to a Datadog Notebook |
| `/append-to-notebook` | Append content to an existing notebook |

---

## Project Structure

```
datadog-sre-maturity-kit/
├── CLAUDE.md                     # ← This file
├── QUICKSTART.md                 # Getting started
├── COMMANDS.md                   # Command reference
├── README.md                     # Project overview
├── mcp.json                      # Datadog MCP server config
│
├── .claude/commands/             # 18 slash command definitions
│   ├── assess.md                 # Quick assessment
│   ├── assess-full.md            # Comprehensive assessment
│   ├── assess-level0.md
│   ├── assess-level1.md
│   ├── gap-analysis.md           # Gap identification
│   ├── upgrade-plan.md           # Upgrade roadmap
│   ├── generate-report.md
│   ├── level0-infra.md
│   ├── level0-tagging.md
│   ├── level0-cost.md
│   ├── level0-healthcheck.md
│   ├── level2-tagging.md
│   ├── level3-cost.md
│   ├── create-starter-notebooks.md
│   ├── save-to-notebook.md
│   ├── append-to-notebook.md
│   ├── help.md
│   └── README.md                 # Command directory overview
│
├── notebooks/                    # All Datadog Notebook templates
│   ├── 00-healthcheck-account-analysis.md
│   ├── 01-operational-standards-platform-preparation.md
│   ├── 02-operational-standards-access-management.md
│   ├── 03-operational-standards-governance.md
│   ├── 04-operational-standards-data-monitoring.md
│   ├── 05-operational-standards-data-visualization.md
│   ├── operational-standards-tagging-strategy.md
│   ├── assessments/              # Weekly, quarterly, level readiness
│   ├── investigations/           # Performance, error spike, cost
│   ├── postmortems/              # Incident, outage
│   ├── runbooks/                 # Onboarding, alert response, cost opt
│   └── reports/                  # Executive, metrics, team health
│
├── assessment-tools/             # Self-service tools (new)
│   ├── maturity-scorecard.md     # Interactive 6-level × 8-dimension scorecard
│   ├── gap-analysis-generator.md # Automated gap detection
│   ├── upgrade-path-planner.md   # Level transition guides
│   └── mcp-query-library/        # Categorized Datadog MCP queries
│       ├── metrics-queries.md    # Host coverage, tags, monitors, SLOs
│       ├── logs-queries.md       # Volume, pipelines, archives
│       ├── apm-queries.md        # Traces, synthetics, CI/CD
│       ├── rum-queries.md        # Sessions, vitals, journeys
│       └── cost-queries.md       # Spend, allocation, anomalies
│
├── docs/                         # Reference documentation
│   ├── commands.md               # Detailed command reference
│   ├── notebooks.md              # Notebook template reference
│   ├── mcp-config.md             # MCP server configuration
│   ├── operational-standards.md  # Standards document reference
│   └── overview.md               # Architecture overview
│
└── planning/                     # Operational standards mapping
    └── operational-standards-mapping.md
```

---

## MCP Integration

### Server Configuration

The Datadog MCP server is pre-configured in `mcp.json`:

```json
{
  "mcpServers": {
    "datadog": {
      "type": "http",
      "url": "https://mcp.us3.datadoghq.com/api/unstable/mcp-server/mcp"
    }
  }
}
```

### MCP Query Tagging

**Every MCP query MUST include `service` and `env` tags.** Always ask the user for these values before running queries.

```yaml
# Always prompt the user for:
service: <service_name>   # e.g. "api-gateway", "user-service"
env:     <environment>     # e.g. "prod", "staging", "dev", "test"
```

Replace `<service>` and `<env>` in all query examples from the MCP Query Library. Never use `filter="*"` or `query="*"` without tag scoping.

### Available MCP Tools

Queries use Datadog MCP tools organized by toolset. Full reference in [datadog-info/README.md](datadog-info/README.md) (~100+ tools across 18 toolsets). Key tools for this kit:

| Category | Tools |
|----------|-------|
| **Logs** | `search_datadog_logs`, `analyze_datadog_logs` |
| **Metrics** | `get_datadog_metric`, `search_datadog_metrics`, `get_datadog_metric_context` |
| **Monitors** | `search_datadog_monitors`, `create_datadog_monitor`, `get_monitor_coverage` |
| **Incidents** | `search_datadog_incidents`, `get_datadog_incident` |
| **Traces** | `search_datadog_spans`, `get_datadog_trace`, `search_datadog_service_dependencies` |
| **Hosts** | `search_datadog_hosts` |
| **Services** | `search_datadog_services` |
| **Events** | `search_datadog_events` |
| **SLOs** | `search_datadog_slos` |
| **Notebooks** | `create_datadog_notebook`, `edit_datadog_notebook`, `search_datadog_notebooks` |
| **Dashboards** | `search_datadog_dashboards`, `get_datadog_dashboard`, `upsert_datadog_dashboard` |
| **RUM** | `search_datadog_rum_events`, `get_rum_insight` |
| **Cases** | `search_datadog_cases`, `create_datadog_case` |
| **Security** | `search_datadog_security_signals`, `get_datadog_security_detection_rules` |
| **Cloud Cost** | `get_datadog_metric(use_cloud_cost=true)` |
| **Workflows** | `search_datadog_workflows`, `execute_datadog_workflow` |
| **DDSQL** | `ddsql_run_query` |

### Regional Endpoints

| Site | MCP URL |
|------|---------|
| US1 | `https://mcp.datadoghq.com/api/unstable/mcp-server/mcp` |
| US3 | `https://mcp.us3.datadoghq.com/api/unstable/mcp-server/mcp` |
| US5 | `https://mcp.us5.datadoghq.com/api/unstable/mcp-server/mcp` |
| EU | `https://mcp.datadoghq.eu/api/unstable/mcp-server/mcp` |
| AP1 | `https://mcp.ap1.datadoghq.com/api/unstable/mcp-server/mcp` |

---

## Key Concepts

### Tagging Strategy

Based on Datadog's **Unified Service Tagging (UST)**:

- **Reserved tags**: `env`, `service`, `version`, `source`, `host`, `device`
- **Critical recommended tags**: `team`, `runtime`, `journey`, `role`, `application`
- **Format**: lowercase with underscores (not hyphens or camelCase)
- Tags must not originate from unbounded sources (timestamps, user IDs, request IDs)

### Access Management Hierarchy

1. **Do not modify OOTB roles** (Datadog Admin, Standard, Read-only)
2. **Baseline**: Use Datadog Standard Role as starting point, exclude API key and user invite permissions
3. **Custom roles**: Developer, Development Manager (add more as needed)
4. **Datadog Teams**: Mirror organizational structure for asset organization and RBAC

### Compliance Requirements

| Standard | Requirement |
|----------|-------------|
| **PCI-DSS** | US1 site only, HTTPS endpoints, Audit Trail required |
| **HIPAA** | BAA required, no Zendesk chat, no log sharing |
| **FedRAMP** | GovCloud instance only (Moderate level) |
| **GDPR** | EU1 site for data residency |

### Log Management Philosophy

- Default "main" index is catch-all (15-day retention)
- Create indexes by log type + environment for granular control
- Use exclusion filters for irrelevant logs (debug, non-critical)
- Archive to external storage (S3, Azure Blob) or use Flex Logs for hybrid approach
- Logs evaluated sequentially through index filters; only one index per log

### Dashboard Design Principles

1. **Monitor/SLO summary at top** for immediate health status
2. **App Overview Dashboard Template** as baseline (clone and customize per application)
3. **Integration-specific widget groups** with context links to core dashboards
4. **Template variables** for dynamic filtering (app, env, integration, service)
5. Dashboards should enable 5-second health assessment with few-click drill-down

---

## Document Conventions

### Action Item Tables

Documents use standardized tables with `STATUS | TITLE | DESCRIPTION` or `STATUS | TASK` columns to track implementation steps.

### Decision Points

Marked with `✅ Decision Point` sections that reference engagement project plans.

### Resource Links

Each section includes "Supported Documentation" with links to official Datadog docs and best practices.

### Frontmatter YAML

Notebook templates use YAML frontmatter:
```yaml
---
title: <Template Name>
type: assessment | investigation | postmortem | runbook | report
version: 1.0
created: YYYY-MM-DD
tags: [category, type]
---
```

---

## Working with These Documents

### When Editing

- Maintain the frontmatter YAML structure (title, author, modified, tags, metadata, time, template_variables)
- Preserve the hierarchical heading structure
- Keep action item tables formatted consistently
- Update `modified` date in frontmatter when making changes
- Maintain the placeholder `<CUSTOMER>` in healthcheck template for customer-specific customization

### When Creating New Content

- **Check existing patterns first** — look at similar files in the same directory before creating
- **Follow naming conventions**: notebooks use `##-operational-standards-<topic>.md`, commands use `<topic>.md`, query library files use `<domain>-queries.md`
- **Include complete frontmatter** with appropriate metadata type
- **Structure with clear sections**: Background, Supported Documentation, Recommended Approach, Decision Points, Action Items
- **Use tables** for structured information (strategies, tag definitions, roles)

### Interaction Model

Users can interact via:
- **Slash commands**: Type `/` + command name (e.g. `/quick-check`)
- **Natural language**: Conversational prompts (e.g. "run a maturity assessment")
- **Self-service tools**: Directly use files in `assessment-tools/`

---

## Special Considerations

### Customer-Specific Information

The healthcheck document (`00-healthcheck-account-analysis.md`) includes:
- Placeholder `<CUSTOMER>` for customer name
- Embedded Datadog dashboard widget images (hosted URLs)
- Pre-formatted queries and links to Datadog UI specific to the US3 site
- Summary tables with empty values to be filled during actual healthcheck

### Compliance Sensitivity

Governance documentation includes regulatory requirements — ensure accuracy when editing compliance-related content as it impacts customer legal obligations.

### API Key Naming Strategy

Documents emphasize meaningful API key naming conventions with components: environment, hosting provider, hosting account/datacenter, optional business unit/region/cluster. Format: `<hosting-provider>_<hosting-account-or-dc>_<environment>`

### When Creating New Slash Commands

New commands go in `.claude/commands/<name>.md`. Follow the format of existing commands. Register a short description so the user knows it exists. Follow Anthropic's Claude Code command format with YAML frontmatter for metadata, allowed-tools, and model selection.
