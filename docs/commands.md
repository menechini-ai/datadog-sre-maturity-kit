---
description: Complete reference for all 18 Claude Code slash commands
---

# Slash Commands — Reference

All 18 commands follow the [Anthropic Claude Code command format](https://code.claude.com/docs/en/skills) with YAML frontmatter for metadata, tool permissions, and model selection.

> **Note:** These commands are defined in `.claude/commands/`. Each file listed below maps to a Claude Code slash command.

---

## 📊 Assessment Commands

### `/check-quick`

```yaml
---
description: Quick SRE maturity check across all 8 dimensions
allowed-tools: Read, Bash(datadog:*)
model: sonnet
---
```

**Duration:** 10 minutes

Run a quick SRE maturity assessment covering all 8 dimensions:
1. Infrastructure Coverage — Agent deployment percentage
2. Tagging Compliance — Unified service tagging coverage
3. Service Catalog — Service inventory completeness
4. Monitoring Quality — Monitor coverage and alert quality
5. Log Management — Log pipeline efficiency
6. Cost Optimization — Cost tracking and optimization
7. Incident Management — Incident response process
8. Dashboard Maturity — Visualization completeness

**Output:** Overall maturity level (0-5), dimension scores (0-100), top 3 strengths, top 3 gaps, recommended next steps.

**When to use:** First time assessment, monthly check-ins.

**Notebook naming:** `Level [N] - [Level Name] - Quick Assessment - YYYY-MM-DD`

---

### `/check-full`

```yaml
---
description: Comprehensive 30-minute maturity deep-dive
allowed-tools: Read, Bash(datadog:*)
model: sonnet
---
```

**Duration:** 30 minutes

Comprehensive assessment with detailed analysis across all 8 dimensions.

**Output:** Detailed dimensional analysis, prioritized gap analysis, actionable recommendations, upgrade path to next level, cost-benefit analysis.

**When to use:** Quarterly reviews, executive reporting, initial discovery.

**Notebook naming:** `Level [N] - [Level Name] - Comprehensive Assessment - YYYY-MM-DD`

---

### `/check-level0`

```yaml
---
description: Level 0 Foundation validation assessment
allowed-tools: Read, Bash(datadog:*)
model: sonnet
---
```

**Duration:** 15 minutes

Assesses readiness for Level 0 (Discovery & Planning).

**Checks:** Infrastructure inventory completeness, cost baseline establishment, tagging strategy planning, team structure documentation.

**Output:** Level 0 readiness score, completed vs missing items, recommended actions, time to completion.

**When to use:** Starting SRE maturity journey.

**Notebook naming:** `Level 0 - Foundation - Validation Report - YYYY-MM-DD`

---

### `/check-level1`

```yaml
---
description: Level 1 Standardization validation assessment
allowed-tools: Read, Bash(datadog:*)
model: sonnet
---
```

**Duration:** 15 minutes

Assesses readiness for Level 1 (Initial Implementation).

**Checks:** Agent deployment (≥80%), monitor coverage (≥5 critical), dashboard creation, log collection, incident tracking process.

**Output:** Level 1 compliance percentage, pass/fail per capability, gaps preventing Level 2, remediation steps.

**When to use:** Validating basic monitoring deployment.

**Notebook naming:** `Level 1 - Standardization - Validation Report - YYYY-MM-DD`

---

## 📍 Level 0 — Foundation Commands

### `/level0-infra`

```yaml
---
description: Complete infrastructure discovery and inventory
allowed-tools: Read, Bash(datadog:*)
model: sonnet
---
```

**Duration:** 15 minutes

Complete infrastructure inventory and service discovery.

**Executes:** Query all monitored hosts, analyze cloud provider distribution, environment breakdown, calculate agent coverage, service discovery.

**Output:** Infrastructure inventory report, coverage statistics, identified monitoring gaps.

**Notebook naming:** `Level 0 - Foundation - Infrastructure Discovery - YYYY-MM-DD`

---

### `/level0-tagging`

```yaml
---
description: Comprehensive tagging compliance audit
allowed-tools: Read, Bash(datadog:*)
model: sonnet
---
```

**Duration:** 15 minutes

Comprehensive audit of current tagging practices.

**Executes:** Query all hosts with tags, analyze required tag coverage (env, service, version, team), identify tag format issues, service-level tagging check.

**Output:** Tag compliance rates, identified format issues, recommended tagging standard.

**Notebook naming:** `Level 0 - Foundation - Tagging Audit - YYYY-MM-DD`

---

### `/level0-cost`

```yaml
---
description: Establish observability cost baseline
allowed-tools: Read, Bash(datadog:*)
model: sonnet
---
```

**Duration:** 15 minutes

Establish observability cost baseline.

**Executes:** Query total cloud spend (90 days), cost breakdown by service/team/environment, identify top cost drivers.

**Output:** Cost baseline report, top cost drivers, cost optimization opportunities.

**Notebook naming:** `Level 0 - Foundation - Cost Baseline - YYYY-MM-DD`

---

### `/level0-healthcheck`

```yaml
---
description: Generate comprehensive health check report
allowed-tools: Read, Bash(datadog:*)
model: sonnet
---
```

**Duration:** 20 minutes

Generate comprehensive Level 0 health check report combining all discovery findings.

**Output:** Executive summary, infrastructure overview, tagging compliance, cost analysis, maturity assessment, recommendations.

**Notebook naming:** `Level 0 - Foundation - Health Check - YYYY-MM-DD`

---

## 📈 Level 2+ Commands

### `/level2-tagging`

```yaml
---
description: Advanced tagging strategy and compliance
allowed-tools: Read, Bash(datadog:*)
model: sonnet
---
```

**Duration:** 20 minutes

Advanced tagging strategy for Level 2 (Optimization).

**Executes:** Automated detection of tag schema violations, services without required tags, root cause analysis for tag drift, team-level ownership verification.

**Output:** Advanced tagging compliance report, enforcement recommendations, tagging governance framework.

**Notebook naming:** `Level 2 - Optimization - Advanced Tagging Strategy - YYYY-MM-DD`

---

### `/level3-cost`

```yaml
---
description: Cost optimization analysis for Level 3
allowed-tools: Read, Bash(datadog:*)
model: sonnet
---
```

**Duration:** 20 minutes

Cost optimization for Level 3 (Intelligence).

**Executes:** Analyze cost trends, identify savings opportunities, inefficient resource usage, team-level cost allocation.

**Output:** Cost optimization report, recommended actions, projected savings, team-level breakdown.

**Notebook naming:** `Level 3 - Intelligence - Cost Optimization - YYYY-MM-DD`

---

## 🔧 Utility Commands

### `/gap-analysis`

```yaml
---
description: Identify gaps between current and target maturity level
allowed-tools: Read, Bash(datadog:*)
model: sonnet
---
```

**Duration:** 10 minutes

Generate comprehensive gap analysis between current and target maturity level.

**Output:** Current vs target comparison, gap breakdown by category, prioritized action items.

**Notebook naming:** `Level [N] to Level [M] - Gap Analysis - YYYY-MM-DD`

---

### `/upgrade-plan`

```yaml
---
description: Generate step-by-step upgrade roadmap
allowed-tools: Read, Bash(datadog:*)
model: sonnet
---
```

**Duration:** 15 minutes

Generate upgrade roadmap from current to target level.

**Output:** Phased upgrade plan, resource requirements, timeline estimates, dependency mapping.

**Notebook naming:** `Level [N] to Level [N+1] - Upgrade Plan - YYYY-MM-DD`

---

### `/generate-report`

```yaml
---
description: Executive-level maturity report for leadership
allowed-tools: Read, Bash(datadog:*)
model: sonnet
---
```

**Duration:** 5 minutes

Generate executive-level maturity report suitable for leadership presentation.

**Output:** Executive summary, maturity overview, key achievements, gap analysis, strategic recommendations, ROI analysis.

**Notebook naming:** `Level [N] - [Level Name] - Executive Report - YYYY-MM-DD`

---

## 📓 Notebook Integration Commands

### `/check-to-notebook`

```yaml
---
description: Run assessment and save results to a Datadog Notebook
allowed-tools: Read, Bash(datadog:*)
model: sonnet
---
```

**Duration:** 12 minutes

Run quick assessment and automatically save results to a Datadog Notebook.

**Output:** Console summary with maturity level + Datadog Notebook with full report and visualizations.

**When to use:** Monthly assessments for team sharing, executive reporting.

---

### `/save-to-notebook`

```yaml
---
description: Save any report or findings to a Datadog Notebook
allowed-tools: Read, Bash(datadog:*)
model: sonnet
---
```

**Duration:** 3 minutes

Utility to save any report or findings to a Datadog Notebook.

**Parameters:** Report type (assessment, investigation, incident-postmortem, cost-analysis, gap-analysis), title, include graphs, time range.

**Type Mapping:**
- `assessment` → "report"
- `investigation` → "investigation"
- `incident-postmortem` → "postmortem"
- `cost-analysis` → "documentation"
- `gap-analysis` → "runbook"

---

### `/append-to-notebook`

```yaml
---
description: Append new findings to an existing Datadog Notebook
allowed-tools: Read, Bash(datadog:*)
model: sonnet
---
```

**Duration:** 2 minutes

Add new findings or updates to an existing Datadog Notebook.

**Requires:** Notebook ID, content type (markdown, metric-graph, log-query), section title, content.

**When to use:** Ongoing investigations, weekly progress updates, multi-phase projects.

---

### `/create-starter-notebooks`

```yaml
---
description: Generate all 14 starter notebook templates
allowed-tools: Read, Write, Bash(datadog:*)
model: sonnet
---
```

**Duration:** 2 minutes

Generate starter notebook templates in `notebooks/` directory for common SRE observability workflows.

**Creates:** Templates for assessments, investigations, runbooks, postmortems, and reports.

---

## ℹ️ Help

### `/help`

```yaml
---
description: List all available slash commands and usage
allowed-tools: Read
model: haiku
---
```

List all available slash commands for the Datadog SRE Maturity Kit, organized by category.

---

## Usage Patterns

### New User
```bash
/check-quick         # Quick assessment
/check-full    # Deep dive
/gap-analysis   # Identify gaps
/upgrade-plan   # Create roadmap
```

### Monthly Check-in
```bash
/check-quick         # Quick assessment
# Compare to previous month
```

### Level 0 Setup
```bash
/level0-infra
/level0-tagging
/level0-cost
/level0-healthcheck
/check-level0
```

### Quarterly Review
```bash
/check-full
/generate-report
```

## Notebook Naming Convention

All commands that create notebooks follow this format:

```
Level [N] - [Level Name] - [Report Type] - YYYY-MM-DD
```

Examples:
- `Level 0 - Foundation - Health Check - 2026-07-10`
- `Level 2 - Optimization - Quick Assessment - 2026-07-10`
- `Level 2 to Level 3 - Gap Analysis - 2026-07-10`
