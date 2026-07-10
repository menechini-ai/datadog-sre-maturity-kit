# MCP Query Library — APM & Traces

Live Datadog queries for APM instrumentation, trace health, span analysis, and synthetic monitoring.

---

> **Reference**: See [APM Tools (datadog-info/apm-tools.md)](/datadog-info/apm-tools.md) for complete documentation of APM, Watchdog, and trace analysis tools.

## ⚠️ Required Parameters

**Before running any query below, ask the user for their `service` and `env` tag values.**

```yaml
service: <service_name>   # e.g. "api-gateway", "user-service"
env:     <environment>     # e.g. "prod", "staging", "dev", "test"
```

Replace all `<service>` and `<env>` placeholders below with the user's values.

---

## APM Instrumentation (Level 2–3)

### Instrumented services (scoped)
```
search_datadog_services(filter="service:<service>,env:<env>")
  → filter: has(traces)
  → calculate: (instrumented / total) × 100
```
**Validates**: APM coverage
**Success**: ≥ 80% of critical services with traces

### Trace volume by service (scoped)
```
search_datadog_spans(
  filter="service:<service>,env:<env>",
  timeframe="last_1h"
)
  → group_by: service
  → calculate: count
```
**Validates**: Trace data flowing
**Success**: All critical services have > 0 traces in last hour

### Error traces (scoped)
```
search_datadog_spans(
  filter="service:<service>,env:<env> AND status:error",
  timeframe="last_1h"
)
  → group_by: service, operation
  → calculate: count
```
**Validates**: Error tracking
**Success**: Error traces identified and ≤ baseline

---

## Performance (Level 2–3)

### p95 latency by service (scoped)
```
search_datadog_spans(
  filter="service:<service>,env:<env>",
  timeframe="last_1h"
)
  → calculate: p50, p95, p99 latency
```
**Validates**: Service performance
**Success**: p95 ≤ SLO target for all P1 services

### Slowest endpoints (scoped)
```
search_datadog_spans(
  filter="service:<service>,env:<env> AND status:ok",
  timeframe="last_24h"
)
  → group_by: resource
  → order_by: p95_latency DESC
  → limit: 10
```
**Validates**: Performance bottlenecks
**Success**: Top 10 slow endpoints identified

### Dependency map (scoped)
```
search_datadog_spans(
  filter="service:<service>,env:<env>",
  timeframe="last_1h"
)
  → extract: service dependencies (client → server)
```
**Validates**: Service topology known
**Success**: Full dependency graph available

---

## Synthetic Monitoring (Level 4)

### Synthetic test status (scoped)
```
search_datadog_synthetics(
  filter="service:<service>,env:<env>"
)
```
**Validates**: Synthetic coverage
**Success**: All P1 user journeys have passing browser/API tests

### Uptime by critical journey (scoped)
```
(Via MCP — query synthetic test uptime within scope)
  → group_by: test
  → calculate: uptime_percentage (last 30d)
```
**Validates**: Service availability
**Success**: All P1 tests ≥ 99.9% uptime

---

## CI/CD Visibility (Level 4)

### Pipeline metrics (scoped)
```
search_datadog_spans(
  filter="service:<service>,env:ci",
  timeframe="last_24h"
)
  → group_by: pipeline_name
  → calculate: duration, pass_rate
```
**Validates**: CI/CD observability
**Success**: All pipelines sending telemetry
