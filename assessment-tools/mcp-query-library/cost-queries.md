# MCP Query Library — Cost & Optimization

Live Datadog queries for cost baselines, budget tracking, and optimization opportunities.

---

> **Reference**: See [Specialized Toolsets (datadog-info/specialized-toolsets.md)](/datadog-info/specialized-toolsets.md) — Cloud Cost section for cost analysis tools.

## ⚠️ Required Parameters

**Before running any query below, ask the user for their `service` and `env` tag values.**

```yaml
service: <service_name>   # e.g. "api-gateway", "data-pipeline"
env:     <environment>     # e.g. "prod", "staging", "dev", "test"
```

Replace all `<service>` and `<env>` placeholders below with the user's values.

---

## Cost Baseline (Level 0–1)

### Total spend (90-day, scoped)
```
get_datadog_metric(
  queries=["sum:all.cost{service:<service>,env:<env>}.rollup(sum, daily)"],
  use_cloud_cost=true,
  timeframe="last_90d"
)
```
**Validates**: Cost baseline established
**Success**: 90-day spend data available

### Cost by cloud provider (scoped)
```
get_datadog_metric(
  queries=[
    "sum:aws.cost{service:<service>,env:<env>}.rollup(sum, daily)",
    "sum:azure.cost{service:<service>,env:<env>}.rollup(sum, daily)",
    "sum:gcp.cost{service:<service>,env:<env>}.rollup(sum, daily)"
  ],
  use_cloud_cost=true,
  timeframe="last_30d"
)
```
**Validates**: Cloud provider distribution
**Success**: Cost broken down by provider

### Monthly trend (scoped)
```
get_datadog_metric(
  queries=["sum:all.cost{service:<service>,env:<env>}.rollup(sum, monthly)"],
  use_cloud_cost=true,
  timeframe="last_6months"
)
```
**Validates**: Cost trend visibility
**Success**: Month-over-month trend available

---

## Cost Allocation (Level 2–3)

### Cost by team (scoped)
```
get_datadog_metric(
  queries=["sum:all.cost{service:<service>,env:<env>}.rollup(sum, daily)"],
  use_cloud_cost=true,
  timeframe="last_30d"
)
  → group_by: team tag
```
**Validates**: Cost allocated to teams
**Success**: ≥ 90% of costs assigned to a team

### Cost by service (scoped)
```
get_datadog_metric(
  queries=["sum:all.cost{service:<service>,env:<env>}.rollup(sum, daily)"],
  use_cloud_cost=true,
  timeframe="last_30d"
)
  → group_by: service tag
```
**Validates**: Cost per service visible
**Success**: Top 10 cost drivers identified

### Top cost drivers (scoped)
```
get_datadog_metric(
  queries=["sum:all.cost{service:<service>,env:<env>}.rollup(sum, daily)"],
  use_cloud_cost=true,
  timeframe="last_30d"
)
  → group_by: service, team
  → order_by: cost DESC
  → limit: 10
```
**Validates**: Cost optimization targeting
**Success**: Top 10 cost drivers known

---

## Cost Optimization (Level 3–4)

### Anomaly detection (scoped)
```
get_datadog_metric(
  queries=["sum:all.cost{service:<service>,env:<env>}.rollup(sum, daily)"],
  use_cloud_cost=true,
  timeframe="last_90d"
)
  → detect: anomalies (deviation > 2σ from trailing 30d avg)
```
**Validates**: Cost anomaly detection active
**Success**: All cost anomalies investigated

### Budget vs actual (scoped)
```
Compare monthly budget to actual spend within scope:
  budget = $[AMOUNT]
  actual = get_datadog_metric(queries=["sum:all.cost{service:<service>,env:<env>}.rollup(sum, monthly)"], ...)
  variance = (actual - budget) / budget × 100
```
**Validates**: Budget tracking
**Success**: Variance < 10%

### Idle resource cost (scoped)
```
get_datadog_metric(
  queries=[
    "avg:aws.ec2.cpu{service:<service>,env:<env>}.rollup(avg, 7d)",
    "avg:aws.rds.cpu{service:<service>,env:<env>}.rollup(avg, 7d)"
  ],
  use_cloud_cost=true,
  timeframe="last_7d"
)
  → filter: cpu_avg < 5%
  → estimate: cost of idle resources
```
**Validates**: Waste identification
**Success**: Idle resource cost < 5% of total

---

## Efficiency Metrics (Level 4–5)

### Cost per transaction (scoped)
```
Compare total cost to business metrics within scope:
  total_cost = get_datadog_metric(queries=["sum:all.cost{service:<service>,env:<env>}.rollup(sum, monthly)"], ...)
  transactions = [business metric from APM/RUM]
  cost_per_transaction = total_cost / transactions
```
**Validates**: Business efficiency
**Success**: Cost per transaction trending down

### Log cost efficiency (scoped)
```
logs_indexed = analyze_datadog_logs(query="service:<service> AND env:<env>", timeframe="last_30d")[count]
logs_total = [total incoming log volume within scope]
exclusion_ratio = (logs_total - logs_indexed) / logs_total
estimated_savings = exclusion_ratio × estimated_log_cost
```
**Validates**: Log cost optimization
**Success**: Exclusion ratio ≥ 60%

### Host cost per service (scoped)
```
get_datadog_metric(
  queries=["sum:datadog.agent.host_count{service:<service>,env:<env>}.rollup(sum, daily)"],
  timeframe="last_30d"
)
  → group_by: service
  → calculate: avg hosts per service
  → compare: host count vs cost allocation
```
**Validates**: Infrastructure cost alignment
**Success**: Host-to-cost ratio consistent across services
