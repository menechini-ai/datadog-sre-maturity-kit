# Core Tools (toolset: `core`)

Always enabled. Covers logs, metrics, monitors, incidents, events, traces, hosts, services, SLOs, and workflows.

> **Usage Rules**: See [README.md](README.md) — always ask user for `service` and `env` tags before querying.

---

## Logs

### `search_datadog_logs`

Search application and infrastructure logs with powerful filtering.

**Required permissions**: `Logs`

**Parameters**:
- `query` (required) — Log search query (e.g. `service:api-gateway env:prod status:error`)
- `from` — Start time (default: `now-1h`)
- `to` — End time (default: `now`)
- `head_limit` — Max results (default: 100)
- `max_tokens` — Token limit for output
- `group_by_message` — Group similar logs into patterns with counts
- `extra_fields` — Additional attributes/fields to include

**Example prompts**:
- Find errors in the API gateway for the last hour
- Search for authentication errors in production, show custom field
- Show error log patterns from web-store-ui, group by message

### `analyze_datadog_logs`

Analyze log patterns with grouping, aggregation, and anomaly detection.

**Required permissions**: `Logs`

**Parameters**: Same as `search_datadog_logs` plus aggregation options.

**Example prompts**:
- Analyze error trends by service over the last 7 days
- Show log volume by index across all environments

---

## Metrics

### `get_datadog_metric`

Query time-series metrics with optional Cloud Cost Management support.

**Required permissions**: `Timeseries`

**Parameters**:
- `queries` (required) — Array of metric query strings or formula objects
- `from` — Start time
- `to` — End time
- `raw_data` — Return raw datapoints vs binned
- `use_cloud_cost` — Query Cloud Cost Management data (AWS/GCP)
- `formulas` — Formula expressions (e.g. `query0 + query1`)

**Example prompts**:
- Show CPU usage for the API service over the last hour
- Compare error rates across environments for the last week
- Summarize AWS cost data for the last 30 days by service

### `get_datadog_metric_context`

Get metric metadata including description, unit, and tags.

**Required permissions**: `Metrics`

### `search_datadog_metrics`

Search available metric names and their metadata.

**Required permissions**: `Metrics`

**Example prompts**:
- Find metrics related to database performance
- List all custom metrics in my account

### `get_metric_definition`

Get the schema/definition of a specific metric.

---

## Monitors

### `search_datadog_monitors`

Search alerting monitors with flexible filtering.

**Required permissions**: `Monitors`

**Parameters**:
- `query` — Monitor search query (e.g. `status:alert env:prod`)
- `sort` — Sort field (prefix with `-` for descending, e.g. `-title`)

**Example prompts**:
- Show all alerting monitors in production
- Find monitors tagged with team:billing that are muted
- List monitors with the highest alert frequency

### `create_datadog_monitor`

Create a new monitor programmatically.

**Required permissions**: `Monitors`

**Example prompts**:
- Create a CPU threshold monitor for the API service
- Set up an anomaly monitor for request latency

### `get_datadog_monitor_templates`

Get monitor template suggestions.

### `validate_datadog_monitor`

Validate a monitor configuration before creating.

### `search_datadog_monitor_groups`

Search monitor groups for scoped alert evaluation.

### `get_monitor_coverage`

Get monitor coverage analysis across services.

---

## Incidents

### `search_datadog_incidents`

Search incidents by title, team, severity, and date range.

**Required permissions**: `Incidents`

**Example prompts**:
- Show all active incidents from the last week
- Find incidents related to the checkout service
- Get incidents with severity SEV-1 or SEV-2

### `get_datadog_incident`

Get full details for a specific incident (timeline, updates, affected services).

**Required permissions**: `Incidents`

**Parameters**:
- `incident_id` (required) — Incident ID

---

## Events

### `search_datadog_events`

Search events like monitor alerts, deployment notifications, infrastructure changes, security findings, and service status changes.

**Required permissions**: `Events`, `Timeseries`

**Parameters**:
- `query` — Event search query
- `from` — Start time
- `to` — End time
- `sort` — Sort order (`timestamp` / `-timestamp` or `asc` / `desc`)

**Example prompts**:
- Show all deployment events from the last 24 hours
- Find events related to production with error status
- Get events tagged with service:api from the past hour

---

## Traces

### `search_datadog_spans`

Search APM spans with flexible filtering. Can return custom attributes.

**Required permissions**: `APM`

**Parameters**:
- `query` (required) — Span search query (e.g. `service:checkout env:prod`)
- `from` — Start time (default: `now-1h`)
- `to` — End time (default: `now`)
- `head_limit` — Max results (default: 100)
- `max_tokens` — Token limit

**Example prompts**:
- Find slow checkout operations in the last 4 hours
- Search for error spans from web-store with custom attributes
- Show traces with duration > 5s in the last hour

### `get_datadog_trace`

Get complete trace details by trace ID (all spans and relationships).

**Required permissions**: `APM`

**Parameters**:
- `trace_id` (required) — Trace ID to retrieve

---

## Hosts & Services

### `search_datadog_hosts`

Search infrastructure hosts with tag filtering.

**Required permissions**: `Hosts`

**Parameters**:
- `filter` — Tag filter string (e.g. `service:api-gateway,env:prod`)
- `include_all_tags` — Return all tags for each host

**Example prompts**:
- List all hosts in production with their tags
- Find hosts running outdated agent versions

### `search_datadog_services`

List APM services with optional details.

**Required permissions**: `APM`

**Example prompts**:
- Show all instrumented services with trace counts
- List services missing ownership tags

### `search_datadog_service_dependencies`

Get service dependency graph (upstream/downstream).

**Required permissions**: `APM`

**Example prompts**:
- Show all services that depend on the database
- Map the dependency chain for the checkout service

---

## SLOs

### `search_datadog_slos`

Search SLOs by query or tags.

**Required permissions**: `SLOs`

**Example prompts**:
- Show all SLOs that are burning their error budget
- Find SLOs for the checkout service in production

---

## Workflows

### `search_datadog_workflows`

Search workflows by name or tags.

### `get_datadog_workflow`

Get workflow definition details.

### `get_datadog_workflow_instance`

Get workflow run details.

### `execute_datadog_workflow`

Execute a workflow.

**Example prompts**:
- Trigger the auto-remediation workflow for the API service
- Find all workflows tagged with team:platform
