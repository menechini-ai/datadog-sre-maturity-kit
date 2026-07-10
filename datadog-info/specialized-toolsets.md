# Specialized Toolsets

Error Tracking, LLM Observability, Database Monitoring, Profiling, Code Coverage, Kubernetes, Network Device Monitoring, Cloud Cost, Feature Flags, Reference Tables, DDSQL, and more.

> **Usage Rules**: See [README.md](README.md) — always ask user for `service` and `env` tags before querying.

---

## Error Tracking (toolset: `error-tracking`)

| Tool | Purpose |
|------|---------|
| `search_datadog_error_tracking_issues` | Search error tracking issues |
| `get_datadog_error_tracking_issue` | Get error tracking issue details (includes linked GitHub PRs) |
| `analyze_datadog_error_tracking_errors` | Analyze error patterns across issues |

**Example prompts**:
- Show top error tracking issues for the web-ui service
- Find unhandled errors in production

---

## LLM Observability (toolset: `llmobs`)

| Tool | Purpose |
|------|---------|
| `create_experiment` | Create a new experiment |
| `get_experiment` | Get experiment details |
| `get_experiment_results` | Get experiment results |
| `get_experiment_diagnostics` | Get experiment diagnostics |
| `get_experiment_segmentation_property_values` | Get segmentation values |

**Example prompts**:
- Show results for the latest LLM experiment
- Compare experiment performance across models

---

## Database Monitoring (toolset: `database-monitoring`)

| Tool | Purpose |
|------|---------|
| `find_datadog_database_instances` | Discover database instances |
| `get_datadog_database_calling_services` | Services calling a database |
| `get_datadog_database_explain_plans` | Get explain plans for queries |
| `get_datadog_database_health_signals` | Database health alerts |
| `get_datadog_database_query_performance` | Query performance metrics |
| `get_datadog_database_query_statement` | Full query statement |
| `get_datadog_database_recommendations` | Optimization recommendations |
| `get_datadog_database_schemas` | Database schema info |
| `optimize_datadog_database_query` | Get query optimization suggestions |
| `search_datadog_database_plans` | Search query plans |
| `search_datadog_database_samples` | Search query samples |

**Example prompts**:
- Find slow queries on the checkout database
- Get optimization recommendations for the top 5 expensive queries

---

## Profiling (toolset: `profiling`)

| Tool | Purpose |
|------|---------|
| `search_datadog_profiles` | Search profiling data |
| `get_profiling_services` | List profiled services |
| `get_profiling_service_insights` | Get profiling insights per service |
| `get_profiling_runtime_ids` | Get runtime IDs |
| `get_profiling_profile_types` | Get available profile types |
| `get_profiling_fields` | Get available profiling fields |
| `get_profiling_field_values` | Get field values |
| `get_profiling_tag_names` | Get profiling tag names |
| `get_profiling_tag_values` | Get profiling tag values |
| `get_profiling_timeseries` | Get profiling time-series data |

**Example prompts**:
- Show profiling data for the API service
- What's the CPU hot spot in the checkout service?

---

## Code Coverage (toolset: `code-coverage`)

| Tool | Purpose |
|------|---------|
| `get_datadog_code_coverage_branch_summary` | Coverage summary for a branch |
| `get_datadog_code_coverage_commit_summary` | Coverage summary for a commit |
| `get_datadog_code_coverage_files` | File-level coverage data |
| `get_datadog_code_coverage_pr_summary` | PR coverage diff summary |
| `get_datadog_flaky_tests` | Get flaky test data |
| `get_datadog_flaky_tests_management_policies` | Get flaky test policies |
| `get_datadog_test_optimization_settings` | Get test optimization settings |

---

## Feature Flags (toolset: `feature-flags`)

| Tool | Purpose |
|------|---------|
| `list_datadog_feature_flags` | List all feature flags |
| `get_datadog_feature_flag` | Get feature flag details |
| `create_datadog_feature_flag` | Create a new feature flag |
| `list_datadog_feature_flag_environments` | List environments per flag |
| `list_datadog_feature_flag_allocations` | List allocation rules |
| `update_datadog_feature_flag_environment` | Update env configuration |
| `check_datadog_flag_implementation` | Check code implementation |
| `sync_datadog_feature_flag_allocations` | Sync allocation rules |

---

## Kubernetes (toolset: `kubernetes`)

| Tool | Purpose |
|------|---------|
| `search_datadog_k8s_resources` | Search Kubernetes resources |
| `describe_datadog_k8s_resource` | Describe a K8s resource |
| `get_datadog_k8s_manifest` | Get K8s manifest |

---

## Network Device Monitoring (toolset: `ndm`)

| Tool | Purpose |
|------|---------|
| `search_ndm_devices` | Search network devices |
| `get_ndm_device` | Get device details |
| `search_ndm_interfaces` | Search network interfaces |
| `analyze_cloud_network_monitoring` | Analyze cloud network monitoring data |

---

## Cloud Cost Management (toolset: `cloud-cost`)

| Tool | Purpose |
|------|---------|
| `get_datadog_metric` with `use_cloud_cost=true` | Query cloud cost data |
| `get_datadog_metric_context` with cost metrics | Get cost metric metadata |

**Example prompts**:
- Summarize AWS cost data for last 30 days by service
- Show GCP compute costs by region for the past week

---

## Reference Tables (toolset: `reference-tables`)

| Tool | Purpose |
|------|---------|
| `create_reference_table` | Create a reference table |
| `get_reference_table_rows` | Get rows from a reference table |
| `upsert_reference_table_rows` | Insert or update rows by primary key |

---

## Sheets (toolset: `sheets`)

| Tool | Purpose |
|------|---------|
| `upsert_datadog_spreadsheet` | Create or update a spreadsheet |

---

## DDSQL (toolset: `experimental`)

| Tool | Purpose |
|------|---------|
| `ddsql_get_spec` | Get DDSQL specification |
| `ddsql_run_query` | Run a SQL query on Datadog data |
| `ddsql_schema_search_tables` | Search available tables |
| `ddsql_schema_get_table_columns` | Get table column schema |
| `ddsql_schema_search_unstructured_fields` | Search unstructured fields |
| `ddsql_create_link` | Create a shareable link for a query |

---

## Browser Onboarding (toolset: `experimental`)

| Tool | Purpose |
|------|---------|
| `browser_onboarding` | Browser test onboarding and setup |

---

## Other

| Tool | Toolset | Purpose |
|------|---------|---------|
| `execute_code` | varies | Execute arbitrary code |
| `get_data` | varies | Generic data retrieval |
| `get_logs` | varies | Get log data |
| `get_type` | varies | Get type information |
