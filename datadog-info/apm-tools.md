# APM Tools (toolset: `apm`)

Enable via: `<MCP_ENDPOINT>?toolsets=apm`

> **Usage Rules**: See [README.md](README.md) — always ask user for `service` and `env` tags before querying.

---

## Span & Trace Analysis

### `apm_search_spans`

Advanced span search with APM-specific filters.

### `apm_query_trace`

Query a specific trace for detailed analysis.

### `apm_latency_bottleneck_summary`

Identify latency bottlenecks in a trace. Returns a summary key spans contributing to overall latency.

**Example prompts**:
- Find the bottleneck in the checkout trace
- What's causing the slow response in the payment service?

### `apm_discover_span_tags`

Discover unique tag values across spans for filtering and analysis.

### `apm_get_primary_tag_keys`

Get APM primary tag keys for an environment.

---

## Watchdog

### `apm_search_watchdog_stories`

Search Watchdog anomaly stories. Watchdog automatically detects anomalies in metrics and traces.

**Example prompts**:
- Are there any Watchdog alerts for the API service?
- Show anomaly stories from the last 24 hours

### `apm_get_watchdog_story`

Get full details of a specific Watchdog story.

**Parameters**:
- `story_id` (required) — Watchdog story ID

---

## Change Stories

### `get_change_stories`

Get change tracking stories — deployments, feature flags, configuration changes.

**Example prompts**:
- What changed in production in the last hour?
- Show me recent deployments to the checkout service

---

## Recommendations

### `apm_search_recommendations`

Search APM recommendations for performance improvements.

### `apm_get_recommendation`

Get detailed recommendation information.
