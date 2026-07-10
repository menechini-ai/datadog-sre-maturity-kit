# MCP Query Library — Metrics & Infrastructure

Live Datadog queries for infrastructure coverage, tagging compliance, and service health. Run these via Datadog MCP to validate maturity levels.

---

> **Reference**: See [Core Tools (datadog-info/core-tools.md)](/datadog-info/core-tools.md) for complete documentation of hosts, metrics, monitors, and SLO tools.

## ⚠️ Required Parameters

**Before running any query below, ask the user for their `service` and `env` tag values.**

```yaml
service: <service_name>   # e.g. "api-gateway", "user-service", "checkout"
env:     <environment>     # e.g. "prod", "staging", "dev", "test"
```

Replace all `<service>` and `<env>` placeholders below with the user's values.

---

## Host Coverage (Level 0–1)

### All hosts with tags (scoped to service and env)
```
search_datadog_hosts(filter="service:<service>,env:<env>", include_all_tags=true)
```
**Validates**: Infrastructure inventory complete
**Success**: All hosts in the service/env scope returned

### Agent version distribution (scoped)
```
search_datadog_hosts(filter="service:<service>,env:<env>")
  → group_by: agent_version
  → calculate: count per version
```
**Validates**: Agent consistency
**Success**: ≤ 2 distinct agent versions within scope

### Host coverage percentage (scoped)
```
search_datadog_hosts(filter="service:<service>,env:<env>")
  → count / expected total hosts within scope
```
**Validates**: Level 1 graduation (≥ 80%)
**Success**: Coverage ratio ≥ 0.80

---

## Tagging Compliance (Level 1–2)

### Tag coverage by resource (scoped)
```
search_datadog_hosts(filter="service:<service>,env:<env>", include_all_tags=true)
  → filter: has(env) AND has(service) AND has(version)
  → calculate: (compliant / total) × 100
```
**Validates**: UST baseline
**Success**: ≥ 90% of hosts have all 3 UST tags

### Untagged resources (scoped)
```
search_datadog_hosts(filter="service:<service>,env:<env>", include_all_tags=true)
  → filter: NOT has(env) OR NOT has(team)
```
**Validates**: Tag hygiene
**Success**: < 5% of resources untagged

### Team tag distribution (scoped)
```
search_datadog_monitors(filter="service:<service>,env:<env>")
  → group_by: team tag
```
**Validates**: Team-based RBAC
**Success**: All monitors assigned to a team

---

## Monitor Health (Level 1–2)

### All monitors with status (scoped)
```
search_datadog_monitors(filter="service:<service>,env:<env>")
```
**Validates**: Monitor coverage
**Success**: ≥ 5 critical monitors, all tagged

### Alert fatigue check (scoped)
```
search_datadog_monitors(filter="service:<service>,env:<env>")
  → filter: alerts_per_week > 15
```
**Validates**: Monitor hygiene
**Success**: No monitors exceeding 15 alerts/week

### SLO status (scoped)
```
search_datadog_slos(filter="service:<service>,env:<env>")
```
**Validates**: SLO coverage
**Success**: SLOs defined for all P1/P2 services

---

## Service Health (Level 2+)

### Service Catalog (scoped)
```
search_datadog_services(filter="service:<service>,env:<env>")
```
**Validates**: Service Catalog completeness
**Success**: All critical services registered with ownership

### APM trace count (scoped)
```
search_datadog_spans(filter="service:<service>,env:<env>")
  → calculate: count over 1h
```
**Validates**: APM instrumentation
**Success**: Traces flowing for ≥ 80% of critical services
