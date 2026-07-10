# Upgrade Path Planner — Level Transition Guide

Step-by-step implementation plans for advancing from one maturity level to the next. Use after completing [gap analysis](gap-analysis-generator.md).

---

## How to Use

1. Identify your current level and target level.
2. Follow the corresponding transition guide below.
3. Complete each step in order (dependencies noted).
4. Validate each step using the linked MCP queries.
5. Re-score on the [Maturity Scorecard](maturity-scorecard.md) to confirm graduation.

---

## Level 0 → Level 1: Foundation to Reactive

**Goal**: Discover infrastructure, deploy agents, establish basic monitoring.

### Prerequisites
- [ ] Datadog org created with Admin access
- [ ] API/App keys generated
- [ ] Network egress to Datadog endpoints open (see Notebook 01)

### Implementation Steps

| Step | Action | Owner | Duration | Validation |
|------|--------|-------|----------|------------|
| 1.1 | Run infrastructure discovery — `search_datadog_hosts("*")` to inventory all assets | SRE | 1 day | Complete host list |
| 1.2 | Deploy Datadog Agent on production hosts | Platform | 1–2 weeks | ≥ 80% coverage |
| 1.3 | Create 5 critical monitors (CPU, memory, disk, error rate, latency) | SRE | 2 days | Monitors active |
| 1.4 | Configure log collection on production hosts | Platform | 3 days | Logs flowing |
| 1.5 | Create 1 dashboard per service with key health metrics | SRE | 1 week | Dashboards published |
| 1.6 | Set up incident tracking — connect to PagerDuty/Opsgenie | SRE | 1 day | Incidents created |
| 1.7 | Register services in Service Catalog with ownership | SRE | 3 days | Catalog populated |

**Validation**: Run [Host Coverage Query](mcp-query-library/metrics-queries.md) — confirm ≥ 80%.

**Operational Standards**: Notebooks 01 (Platform), 02 (Access), 00 (Healthcheck)

---

## Level 1 → Level 2: Reactive to Proactive

**Goal**: Standardize tagging, define SLOs, improve monitor hygiene.

### Prerequisites
- [ ] Level 1 attained (score ≥ 80%)
- [ ] Agent deployed on all production hosts
- [ ] Basic dashboards and monitors exist

### Implementation Steps

| Step | Action | Owner | Duration | Validation |
|------|--------|-------|----------|------------|
| 2.1 | Adopt Unified Service Tagging — apply env/service/version to all telemetry | All teams | 2–4 weeks | ≥ 90% compliance |
| 2.2 | Define SLOs for all P1/P2 services | SRE + Dev | 2 weeks | SLOs created |
| 2.3 | Audit and deduplicate monitors — tag all with team + priority | SRE | 1 week | < 5 alerts/monitor/week |
| 2.4 | Standardize dashboards — use template variables | SRE | 2 weeks | All dashboards follow template |
| 2.5 | Build log pipelines for structured logs | Platform | 1 week | Pipelines active |
| 2.6 | Instrument critical services with APM | Dev teams | 2–4 weeks | Traces flowing |
| 2.7 | Set up Datadog Teams matching org structure | Admin | 3 days | Teams created |

**Validation**: Run [Tag Compliance Query](mcp-query-library/metrics-queries.md) — confirm ≥ 90%.

**Operational Standards**: Notebooks 05 (Visualization), Tagging Strategy

---

## Level 2 → Level 3: Proactive to Managed

**Goal**: Optimize costs, automate responses, mature operations.

### Prerequisites
- [ ] Level 2 attained (score ≥ 75%)
- [ ] UST compliance ≥ 90%
- [ ] SLOs defined for critical services

### Implementation Steps

| Step | Action | Owner | Duration | Validation |
|------|--------|-------|----------|------------|
| 3.1 | Audit log indexes — set exclusion filters, archive to S3/blob | Platform | 1 week | Index efficiency ≥ 60% |
| 3.2 | Establish cost governance — budgets, allocation, anomaly alerts | FinOps | 1 week | Cost tracked by team |
| 3.3 | Configure SLO burn-rate alerts on all SLOs | SRE | 2 days | Burn-rate alerts active |
| 3.4 | Build automated remediation workflows | SRE | 2–3 weeks | 3+ workflows active |
| 3.5 | Address compliance requirements (GDPR/HIPAA/PCI) | Security | Varies | Audit pass |
| 3.6 | Enable Audit Trail | Admin | 1 day | Audit logs accessible |
| 3.7 | Integrate on-call with escalation policies | SRE | 1 week | End-to-end alert tested |

**Validation**: Run [Log Index Efficiency Query](mcp-query-library/logs-queries.md) — confirm ≥ 60%.

**Operational Standards**: Notebooks 03 (Governance), 04 (Data Monitoring)

---

## Level 3 → Level 4: Managed to Optimized

**Goal**: Synthetics, RUM, self-healing automation.

### Prerequisites
- [ ] Level 3 attained (score ≥ 80%)
- [ ] Log efficiency ≥ 60%
- [ ] SLO burn-rate alerts active

### Implementation Steps

| Step | Action | Owner | Duration | Validation |
|------|--------|-------|----------|------------|
| 4.1 | Identify P1 user journeys, create synthetic browser/API tests | QA + SRE | 2–3 weeks | Tests passing |
| 4.2 | Implement RUM on customer-facing web apps | Frontend | 2–4 weeks | RUM data flowing |
| 4.3 | Add CI/CD pipeline visibility | Platform | 1 week | Pipeline metrics |
| 4.4 | Convert manual runbooks to automated workflows | SRE | 3–4 weeks | 3+ automated remediations |
| 4.5 | Enable Fleet Automation for agent upgrades | Platform | 1 week | Auto-upgrade active |
| 4.6 | Build cross-org dashboards | SRE | 1 week | Org-wide visibility |

**Validation**: Run [Synthetic Test Query](mcp-query-library/apm-queries.md) — confirm all P1 journeys covered.

**Additional resources**: Datadog Synthetic Monitoring docs, RUM setup guide

---

## Level 4 → Level 5: Optimized to Excellence

**Goal**: ML-driven insights, platform engineering, industry leadership.

### Prerequisites
- [ ] Level 4 attained (score ≥ 75%)
- [ ] Synthetic and RUM active
- [ ] Automated remediation established

### Implementation Steps

| Step | Action | Owner | Duration | Validation |
|------|--------|-------|----------|------------|
| 5.1 | Enable Watchdog and ML-based anomaly detection | SRE | 1 week | Watchdog alerts active |
| 5.2 | Create forecast-based monitors for capacity planning | SRE | 2 weeks | Forecast alerts active |
| 5.3 | Build self-service observability portal for dev teams | Platform | 1–2 months | Dev teams using self-service |
| 5.4 | Implement cross-org analytics with unified dashboards | SRE | 2 weeks | Cross-org views live |
| 5.5 | Integrate SLOs into CI/CD gating | Platform | 1 month | Deployments blocked on SLO breach |
| 5.6 | Conduct external benchmarking, publish results | SRE Lead | 2 weeks | Benchmark report |

**Validation**: Run [Cost Trend Query](mcp-query-library/cost-queries.md) — demonstrate cost efficiency improvement.

**Additional resources**: Datadog Watchdog docs, Forecast alerts guide

---

## Transition Summary

| Transition | Typical Duration | Key Risk | Success Metric |
|-----------|-----------------|----------|----------------|
| L0 → L1 | 2–4 weeks | Network egress blocking agents | 80% host coverage |
| L1 → L2 | 4–8 weeks | Dev team adoption of UST | 90% tag compliance |
| L2 → L3 | 4–6 weeks | Cost allocation data missing | 60% log efficiency |
| L3 → L4 | 4–8 weeks | No synthetic test definitions | P1 journeys covered |
| L4 → L5 | 6–12 weeks | Self-service platform adoption | Dev team NPS > 70 |

---

> **Tool Reference**: See [datadog-info/README.md](/datadog-info/README.md) for the complete MCP tool reference index.

## Validation Loop

After completing each transition:

1. Re-run the [Maturity Scorecard](maturity-scorecard.md) and verify all critical capabilities ≥ 4.
2. Confirm target level score ≥ threshold.
3. Run matching MCP queries to validate live state.
4. Graduate and begin next level transition.
