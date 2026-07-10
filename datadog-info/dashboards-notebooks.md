# Dashboards & Notebooks

Dashboard and Notebook management tools. Available via `core` toolset (default) or `dashboards` toolset (standalone).

> **Usage Rules**: See [README.md](README.md) — always ask user for `service` and `env` tags before querying.

---

## Dashboards

### `search_datadog_dashboards`

Search dashboards by query, tags, or title.

**Required permissions**: `Dashboards`

**Parameters**:
- `query` — Dashboard search query
- `sort` — Sort field (prefix with `-` for descending)

**Example prompts**:
- Find dashboards related to the payment service
- List dashboards with high traffic in the last 30 days

### `get_datadog_dashboard`

Get full dashboard definition (layout, widgets, queries).

**Required permissions**: `Dashboards`

### `upsert_datadog_dashboard`

Create or update a dashboard (idempotent).

**Required permissions**: `Dashboards`

### `delete_datadog_dashboard`

Delete a dashboard by ID.

**Required permissions**: `Dashboards`

### `get_widget_reference`

Get reference documentation for widget types and configurations.

### `get_widget_reference_compressed`

Same as `get_widget_reference` but compressed for token efficiency.

### `validate_dashboard_widget`

Validate a dashboard widget configuration before saving.

### `ask_widget_expert`

Get expert guidance on dashboard widget design and best practices.

---

## Notebooks

### `search_datadog_notebooks`

Search notebooks by query or tags.

**Required permissions**: `Notebooks`

### `get_datadog_notebook`

Get full notebook definition (cells, layout, metadata).

**Required permissions**: `Notebooks`

### `create_datadog_notebook`

Create a new Datadog Notebook with cells.

**Required permissions**: `Notebooks`

**Parameters**:
- `name` (required) — Notebook title
- `type` — Notebook type (e.g. `documentation`, `report`)
- `cells` — Array of cell objects (markdown, timeseries, etc.)
- `time` — Time span configuration
- `tags` — Tags for the notebook

**Example prompts**:
- Create a weekly assessment report notebook
- Save my incident investigation as a notebook

### `edit_datadog_notebook`

Edit an existing notebook. Supports `append_only=true` to append cells.

**Required permissions**: `Notebooks`

**Example prompts**:
- Append the latest metrics to the weekly report
- Update the executive summary in the quarterly review notebook
