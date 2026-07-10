# MCP Query Library — RUM & User Experience

Live Datadog queries for Real User Monitoring (RUM), browser sessions, and frontend performance.

---

> **Reference**: See [RUM & Synthetics (datadog-info/rum-synthetics.md)](/datadog-info/rum-synthetics.md) for complete documentation of RUM and synthetic test tools.

## ⚠️ Required Parameters

**Before running any query below, ask the user for their `service` and `env` tag values.**

```yaml
service: <service_name>   # e.g. "web-frontend", "mobile-app"
env:     <environment>     # e.g. "prod", "staging", "dev"
```

Replace all `<service>` and `<env>` placeholders below with the user's values.

---

## RUM Coverage (Level 4)

### Active RUM applications (scoped)
```
search_datadog_rum_applications(filter="service:<service>,env:<env>")
```
**Validates**: RUM implementation
**Success**: All customer-facing web/mobile apps instrumented

### Session volume by application (scoped)
```
analyze_datadog_rum(
  query="service:<service> AND env:<env>",
  timeframe="last_24h"
)
  → group_by: application
  → calculate: session_count
```
**Validates**: RUM data flowing
**Success**: Sessions recorded for all applications

### Browser distribution (scoped)
```
analyze_datadog_rum(
  query="service:<service> AND env:<env>",
  timeframe="last_7d"
)
  → group_by: browser_family
  → calculate: session_count
```
**Validates**: Browser support coverage
**Success**: Top 3 browser families represented

---

## Frontend Performance (Level 4)

### Core Web Vitals (scoped)
```
analyze_datadog_rum(
  query="service:<service> AND env:<env>",
  timeframe="last_24h"
)
  → calculate:
    - LCP (Largest Contentful Paint) — p75
    - FID (First Input Delay) — p75
    - CLS (Cumulative Layout Shift) — p75
```
**Validates**: User experience quality
**Success**: LCP < 2.5s, FID < 100ms, CLS < 0.1

### Page load breakdown (scoped)
```
analyze_datadog_rum(
  query="service:<service> AND env:<env>",
  timeframe="last_24h"
)
  → calculate:
    - First Byte (TTFB)
    - DOM Interactive
    - DOM Complete
    - Load Event End
```
**Validates**: Frontend performance
**Success**: TTFB < 800ms p75

### Error rate by page (scoped)
```
analyze_datadog_rum(
  query="service:<service> AND env:<env> AND @type:error",
  timeframe="last_24h"
)
  → group_by: view_url
  → calculate: count, error_rate
```
**Validates**: Frontend error visibility
**Success**: Error rate < 1% per page

---

## User Journeys (Level 4–5)

### Top user flows (scoped)
```
analyze_datadog_rum(
  query="service:<service> AND env:<env>",
  timeframe="last_7d"
)
  → group_by: view_url
  → calculate: session_count, bounce_rate
  → order_by: session_count DESC
  → limit: 10
```
**Validates**: Critical journeys identified
**Success**: Top 10 user flows documented

### Frustration signals (scoped)
```
analyze_datadog_rum(
  query="service:<service> AND env:<env> AND (@session.has_rage_clicks:true OR @session.has_error:true OR @session.has_long_task:true)",
  timeframe="last_24h"
)
  → group_by: application
  → calculate: frustration_rate
```
**Validates**: UX issues visibility
**Success**: Frustration rate < 5% of sessions

### Geographic performance (scoped)
```
analyze_datadog_rum(
  query="service:<service> AND env:<env>",
  timeframe="last_24h"
)
  → group_by: geo.country
  → calculate: avg(load_time), session_count
```
**Validates**: Regional performance parity
**Success**: Max regional variance < 2x
