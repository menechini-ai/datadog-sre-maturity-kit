---
description: Reference for all 14 Datadog Notebook templates
---

# Notebook Templates — Reference

14 pre-built Datadog Notebook templates organized by workflow category.

## 📊 Assessment Templates (3)

| Template | Purpose | Frequency | Duration |
|----------|---------|-----------|----------|
| [weekly-assessment-template.md](../notebooks/assessments/weekly-assessment-template.md) | Quick weekly checkpoint | Weekly | 15 min |
| [quarterly-review-template.md](../notebooks/assessments/quarterly-review-template.md) | Comprehensive business review | Quarterly | 2-3 hours |
| [level-readiness-template.md](../notebooks/assessments/level-readiness-template.md) | Validate level graduation | As needed | 1-2 hours |

**Frontmatter schema:**
```yaml
---
title: <Template Name>
type: assessment
version: 1.0
created: YYYY-MM-DD
tags: [assessment, ...]
---
```

## 🔍 Investigation Templates (3)

| Template | Purpose | Pre-filled Queries |
|----------|---------|-------------------|
| [performance-investigation-template.md](../notebooks/investigations/performance-investigation-template.md) | Latency and throughput issues | Spans, traces, metrics |
| [error-spike-investigation-template.md](../notebooks/investigations/error-spike-investigation-template.md) | Error rate increases | Logs, traces, events |
| [cost-investigation-template.md](../notebooks/investigations/cost-investigation-template.md) | Cost anomalies | Cloud cost metrics |

**Frontmatter schema:**
```yaml
---
title: <Template Name>
type: investigation
version: 1.0
created: YYYY-MM-DD
tags: [investigation, ...]
---
```

## 📝 Postmortem Templates (2)

| Template | Purpose | Severity |
|----------|---------|----------|
| [incident-postmortem-template.md](../notebooks/postmortems/incident-postmortem-template.md) | Standard incident analysis | SEV-2 to SEV-4 |
| [outage-analysis-template.md](../notebooks/postmortems/outage-analysis-template.md) | Complete outage impact assessment | SEV-0 to SEV-1 |

**Frontmatter schema:**
```yaml
---
title: <Template Name>
type: postmortem
version: 1.0
created: YYYY-MM-DD
tags: [postmortem, ...]
---
```

## 📖 Runbook Templates (3)

| Template | Purpose | Use Case |
|----------|---------|----------|
| [service-onboarding-runbook.md](../notebooks/runbooks/service-onboarding-runbook.md) | Onboard new services | New service monitoring setup |
| [alert-response-runbook.md](../notebooks/runbooks/alert-response-runbook.md) | Respond to common alerts | On-call alert triage |
| [cost-optimization-runbook.md](../notebooks/runbooks/cost-optimization-runbook.md) | Cost reduction workflow | Monthly/quarterly cost reviews |

**Frontmatter schema:**
```yaml
---
title: <Template Name>
type: runbook
version: 1.0
created: YYYY-MM-DD
tags: [runbook, ...]
---
```

## 📈 Report Templates (3)

| Template | Audience | Frequency | Focus |
|----------|----------|-----------|-------|
| [executive-report-template.md](../notebooks/reports/executive-report-template.md) | Leadership, C-suite | Quarterly | Business impact, ROI, strategy |
| [monthly-metrics-report.md](../notebooks/reports/monthly-metrics-report.md) | Engineering team, management | Monthly | KPIs, trends, metrics |
| [team-health-report.md](../notebooks/reports/team-health-report.md) | Team lead, HR, management | Monthly/Quarterly | Team performance, morale, capacity |

**Frontmatter schema:**
```yaml
---
title: <Template Name>
type: report
version: 1.0
created: YYYY-MM-DD
tags: [report, ...]
---
```

## Usage

### Copy & Customize
```bash
# Copy template to new investigation
cp notebooks/investigations/performance-investigation-template.md \
   notebooks/investigations/my-incident-2026-07-10.md

# Run assessment and use template
/check-quick
```

### Save to Datadog Notebook
```bash
# Save completed work to Datadog
/save-to-notebook

# Update existing notebook
/append-to-notebook
```

## Template Conventions

All templates follow these conventions:

1. **Frontmatter YAML** — title, type, version, created date, tags
2. **Owner placeholder** — `{{OWNER}}` for assignment
3. **Pre-filled queries** — Datadog MCP queries ready to execute
4. **Action item tables** — Consistent STATUS | TASK format
5. **Decision points** — Marked with `✅ Decision Point`
