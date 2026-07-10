# MCP Query Library — Log Management

Live Datadog queries for log pipeline efficiency, indexing strategy, and archive configuration.

---

> **Reference**: See [Core Tools (datadog-info/core-tools.md)](/datadog-info/core-tools.md) — Logs section for complete documentation of log search and analysis tools.

## ⚠️ Required Parameters

**Before running any query below, ask the user for their `service` and `env` tag values.**

```yaml
service: <service_name>   # e.g. "api-gateway", "user-service"
env:     <environment>     # e.g. "prod", "staging", "dev", "test"
```

Replace all `<service>` and `<env>` placeholders below with the user's values.

---

## Log Volume & Indexing (Level 2–3)

### Daily log volume by service (scoped)
```
analyze_datadog_logs(
  query="service:<service> AND env:<env>",
  index="main",
  timeframe="last_7d"
)
  → group_by: service
  → calculate: count per day
```
**Validates**: Log collection active
**Success**: Production services logging consistently

### Index distribution (scoped)
```
analyze_datadog_logs(
  query="service:<service> AND env:<env>",
  timeframe="last_1d"
)
  → group_by: datadog_index
  → calculate: count per index
```
**Validates**: Index strategy is working
**Success**: Logs distributed across indexes, not all in "main"

### Exclusion filter efficiency (scoped)
```
Compare total incoming vs indexed volume within scope:
  total = sum(all logs pre-filter, service:<service> AND env:<env>)
  indexed = sum(logs after exclusion filters, service:<service> AND env:<env>)
  efficiency = (total - indexed) / total × 100
```
**Validates**: Exclusion filters effective
**Success**: ≥ 60% of logs excluded from indexing (saved costs)

---

## Log Pipeline Health (Level 2–3)

### Pipeline coverage (scoped)
```
analyze_datadog_logs(
  query="service:<service> AND env:<env>",
  timeframe="last_1h"
)
  → filter: has(pipeline_processed)
  → calculate: (processed / total) × 100
```
**Validates**: Pipeline processing active
**Success**: ≥ 90% of logs processed by pipelines

### Error log pattern (scoped)
```
analyze_datadog_logs(
  query="service:<service> AND env:<env> AND (status:error OR status:critical)",
  timeframe="last_24h"
)
  → group_by: service
  → calculate: count, top error messages
```
**Validates**: Error monitoring
**Success**: Error patterns identified, rate trending

### Unstructured log detection (scoped)
```
analyze_datadog_logs(
  query="service:<service> AND env:<env>",
  timeframe="last_1h"
)
  → filter: NOT has(json_parsed) AND NOT has(parsed_message)
```
**Validates**: Log structure quality
**Success**: < 20% of logs unstructured

---

## Archive Configuration (Level 3)

### Archive storage status (scoped)
```
get_datadog_metric(
  queries=[
    "datadog.logs.indexed_volume{service:<service>,env:<env>}",
    "datadog.logs.archived_volume{service:<service>,env:<env>}"
  ],
  timeframe="last_30d"
)
```
**Validates**: Archiving configured
**Success**: Archived volume > 0 (storage active)

### Retention compliance
```
For each index, verify retention matches policy:
  - main: 15 days default
  - critical: 30–90 days
  - audit: 365+ days
```
**Validates**: Retention policy adherence
**Success**: All indexes match documented retention policy

---

## Log-Based Monitors (Level 2+)

### Error rate monitors (scoped)
```
analyze_datadog_logs(
  query="service:<service> AND env:<env> AND status:error",
  timeframe="last_1h"
)
  → calculate: count / total_logs × 100 = error_rate
```
**Validates**: Error alerting
**Success**: Error rate ≤ baseline + 2σ
