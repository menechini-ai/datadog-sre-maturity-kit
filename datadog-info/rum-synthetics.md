# RUM & Synthetics

Real User Monitoring and Synthetic monitoring tools.

> **Usage Rules**: See [README.md](README.md) — always ask user for `service` and `env` tags before querying.

---

## RUM (toolset: `rum`)

### `search_datadog_rum_events`

Search RUM events (views, actions, errors, resources, long tasks).

**Required permissions**: `RUM`

**Parameters**:
- `query` (required) — RUM event query
- `from` — Start time (default: `now-15m`)
- `to` — End time (default: `now`)
- `head_limit` — Max results (default: 100)
- `max_tokens` — Token limit for output

**RUM event types** (`@type` field):
- `@type:view` — Page views
- `@type:action` — User interactions (clicks, taps)
- `@type:error` — Frontend errors
- `@type:resource` — Network requests
- `@type:long_task` — Long tasks (>50ms)

**Example prompts**:
- Show slow page loads (>3s) from the last hour
- Find frontend errors on the checkout page
- Analyze RUM performance by country

### `get_rum_insight`

Get RUM insight/analysis for performance or error patterns.

### `get_rum_summary`

Get RUM summary statistics (sessions, page views, error rates).

### `delete_rum_metric`

Delete a RUM custom metric.

### `delete_rum_retention_filter`

Delete a RUM retention filter.

---

## Synthetics (toolset: `synthetics`)

### `get_synthetics_tests`

Get synthetic test configuration and results.

**Required permissions**: `Synthetics`

**Example prompts**:
- Show all synthetic tests for the checkout flow
- Get the status of API tests in production

### `edit_synthetics_tests`

Edit synthetic test configuration.

**Required permissions**: `Synthetics`
