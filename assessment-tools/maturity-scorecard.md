# Maturity Scorecard — Interactive Self-Assessment

Use this scorecard to self-assess your Datadog SRE maturity across 8 dimensions and 6 levels (0–5). Score each capability, sum by level, and identify readiness to graduate.

---

## How to Use

1. For each capability below, score **0–5** using the rubric.
2. Sum scores per level; divide by max possible for a percentage.
3. A level is **attained** when all its critical capabilities score ≥ 4.
4. Use the results with `/gap-analysis` to plan your next steps.

---

## Level 0 — Foundation (Discovery & Planning)

Max score: 25 (5 capabilities × 5)

| # | Capability | Score (0–5) | Notes |
|---|-----------|-------------|-------|
| 0.1 | **Infrastructure Inventory** — Complete host/asset discovery with `search_datadog_hosts` | | |
| 0.2 | **Tagging Strategy** — Documented UST baseline (env, service, version) | | |
| 0.3 | **Cost Baseline** — 90-day spend breakdown by service/team | | |
| 0.4 | **Team Structure** — SRE ownership model documented | | |
| 0.5 | **Access Model** — Basic RBAC roles defined (Admin, Standard, Read-only) | | |

**Score: / 25 ( %)** | **Pass threshold: 80% (20/25) with criticals ≥ 4**

### Scoring Rubric (0–5)

| Score | Meaning |
|-------|---------|
| 0 | Not started |
| 1 | Acknowledged but no action |
| 2 | Partial ad-hoc effort |
| 3 | Defined in documentation |
| 4 | Implemented and verified |
| 5 | Automated, measured, iterated |

---

## Level 1 — Reactive (Initial Implementation)

Max score: 30 (6 capabilities × 5)

| # | Capability | Score (0–5) | Notes |
|---|-----------|-------------|-------|
| 1.1 | **Agent Deployment** — ≥ 80% host coverage, consistent versions | | |
| 1.2 | **Core Monitors** — ≥ 5 critical monitors (CPU, memory, disk, error rate, latency) | | |
| 1.3 | **Core Dashboards** — 1 per service showing health metrics | | |
| 1.4 | **Log Collection** — Production logs flowing to Datadog | | |
| 1.5 | **Incident Tracking** — Incidents created and classified | | |
| 1.6 | **Service Catalog** — Services registered with ownership | | |

**Score: / 30 ( %)** | **Pass threshold: 80% (24/30) with criticals ≥ 4**

### Graduation Criteria — Level 1

- [ ] Agent coverage ≥ 80%
- [ ] 5+ critical monitors active and alerting
- [ ] Incident tracking in use for P1/P2 events

---

## Level 2 — Proactive (Standardization)

Max score: 35 (7 capabilities × 5)

| # | Capability | Score (0–5) | Notes |
|---|-----------|-------------|-------|
| 2.1 | **Unified Service Tagging** — env/service/version on ALL telemetry | | |
| 2.2 | **SLOs Defined** — Service-level objectives for critical services | | |
| 2.3 | **Monitor Hygiene** — All monitors tagged (team, priority), < 5 alerts/monitor/week | | |
| 2.4 | **Dashboard Standards** — Templates with template variables, consistent layout | | |
| 2.5 | **Log Pipeline** — Processing pipelines for structured logs | | |
| 2.6 | **APM Traces** — Critical services instrumented with tracing | | |
| 2.7 | **Team-based RBAC** — Datadog Teams mirror org structure | | |

**Score: / 35 ( %)** | **Pass threshold: 75% (27/35) with criticals ≥ 4**

### Graduation Criteria — Level 2

- [ ] UST compliance ≥ 90%
- [ ] SLOs defined for all P1/P2 services
- [ ] APM traces for ≥ 80% of critical services

---

## Level 3 — Managed (Optimized Operations)

Max score: 35 (7 capabilities × 5)

| # | Capability | Score (0–5) | Notes |
|---|-----------|-------------|-------|
| 3.1 | **Log Efficiency** — Exclusion filters, indexes by type/env, archiving configured | | |
| 3.2 | **Cost Governance** — Budget alerts, cost allocation by team, anomaly detection | | |
| 3.3 | **SLO Burn-Rate Alerts** — Burn-rate based alerting on all SLOs | | |
| 3.4 | **Automated Remediation** — Workflows for common incident responses | | |
| 3.5 | **Compliance Controls** — GDPR/HIPAA/PCI-DSS requirements addressed | | |
| 3.6 | **Audit Trail** — All configuration changes logged | | |
| 3.7 | **On-Call Integration** — Monitors routed to PagerDuty/Opsgenie with escalation | | |

**Score: / 35 ( %)** | **Pass threshold: 80% (28/35) with criticals ≥ 4**

### Graduation Criteria — Level 3

- [ ] Log management efficiency ≥ 60% (excluded vs indexed ratio)
- [ ] Cost allocation by team/service implemented
- [ ] SLO burn-rate alerts active for all SLOs

---

## Level 4 — Optimized (Advanced Automation)

Max score: 35 (7 capabilities × 5)

| # | Capability | Score (0–5) | Notes |
|---|-----------|-------------|-------|
| 4.1 | **Synthetic Monitoring** — Critical user journeys tested via browser/API tests | | |
| 4.2 | **RUM Implementation** — Real User Monitoring for web/mobile frontends | | |
| 4.3 | **CI/CD Observability** — Pipeline visibility, test impact analysis | | |
| 4.4 | **Automatic Remediation** — Self-healing workflows without manual approval | | |
| 4.5 | **Fleet Automation** — Agent auto-upgrade, config-as-code | | |
| 4.6 | **Cross-Org Dashboards** — Multi-account/org visibility | | |
| 4.7 | **Drift Detection** — Config drift monitoring and alerting | | |

**Score: / 35 ( %)** | **Pass threshold: 75% (27/35) with criticals ≥ 4**

### Graduation Criteria — Level 4

- [ ] Synthetic tests covering P1 user journeys
- [ ] RUM active on all customer-facing apps
- [ ] Automated remediation for ≥ 3 incident types

---

## Level 5 — Excellence (Innovation & Scale)

Max score: 30 (6 capabilities × 5)

| # | Capability | Score (0–5) | Notes |
|---|-----------|-------------|-------|
| 5.1 | **ML-Driven Insights** — Watchdog, outlier monitoring, forecast alerts | | |
| 5.2 | **Predictive Alerting** — Forecast-based monitors for capacity planning | | |
| 5.3 | **Platform Engineering** — Self-service observability for dev teams | | |
| 5.4 | **Cross-Org Analytics** — Unified view across business units | | |
| 5.5 | **SLO-Driven Development** — SLOs gate deployments and feature releases | | |
| 5.6 | **Industry Benchmarking** — External maturity comparisons and gap closure | | |

**Score: / 30 ( %)** | **Pass threshold: 80% (24/30) with criticals ≥ 4**

### Graduation Criteria — Level 5

- [ ] ML-driven alerts covering ≥ 50% of services
- [ ] Self-service observability portal available to all dev teams
- [ ] SLOs integrated into CI/CD gating

---

## Summary Scorecard

| Level | Score | Max | % | Attained? |
|-------|-------|-----|---|-----------|
| 0 — Foundation | | 25 | | ❌ |
| 1 — Reactive | | 30 | | ❌ |
| 2 — Proactive | | 35 | | ❌ |
| 3 — Managed | | 35 | | ❌ |
| 4 — Optimized | | 35 | | ❌ |
| 5 — Excellence | | 30 | | ❌ |
| **Overall** | | **190** | | |

**Current Maturity Level**: Level [ ]

**Overall score interpretation**:
- < 30%: Pre-foundation — start with Level 0
- 30–50%: Early reactive — focus on Level 1
- 50–65%: Becoming proactive — target Level 2
- 65–80%: Managed operations — push for Level 3
- 80–90%: Optimized — ready for Level 4
- > 90%: Excellence — maintain Level 5

---

## Next Steps

1. Transfer scores to `gap-analysis-generator.md` for detailed gap analysis.
2. Run `/upgrade-plan` to create an implementation roadmap.
3. Run `/check-quick` to generate an executive report with these results.

**MCP Validation**: Verify scorecard claims with live Datadog queries from the [MCP Query Library](mcp-query-library/).  
**Tool Reference**: See [datadog-info/README.md](/datadog-info/README.md) for the complete MCP tool reference index.
