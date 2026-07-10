# Datadog MCP Server — Tool Reference

Complete reference of all tools available in the Datadog MCP Server, organized by toolset.

> **Source**: [Datadog MCP Server Tools docs](https://docs.datadoghq.com/mcp_server/tools/) + [datadog-labs/mcp-server CHANGELOG](https://github.com/datadog-labs/mcp-server)
>
> **Updated**: 2026-07-10

---

## Tool Usage Rules

### Always Ask for Tags

**Every MCP query MUST include `service` and `env` tags.** Prompt the user before running any query:

```
service: <service_name>   # e.g. "api-gateway", "user-service"
env:     <environment>     # e.g. "prod", "staging", "dev", "test"
```

Never use `filter="*"` or `query="*"` without tag scoping.

### MCP Server Endpoint

```
https://mcp.datadoghq.com/api/unstable/mcp-server/mcp
```

### Toolset Selection

Enable toolsets via the `toolsets` query parameter:

```
<MCP_ENDPOINT>?toolsets=apm,security,error-tracking
```

### Regional Endpoints

| Site | MCP URL |
|------|---------|
| US1 | `https://mcp.datadoghq.com/api/unstable/mcp-server/mcp` |
| US3 | `https://mcp.us3.datadoghq.com/api/unstable/mcp-server/mcp` |
| US5 | `https://mcp.us5.datadoghq.com/api/unstable/mcp-server/mcp` |
| EU | `https://mcp.datadoghq.eu/api/unstable/mcp-server/mcp` |
| AP1 | `https://mcp.ap1.datadoghq.com/api/unstable/mcp-server/mcp` |

---

## Toolsets Overview

| Toolset | Category | Tools Count | When to Enable |
|---------|----------|-------------|----------------|
| **core** (default) | Logs, Metrics, Traces, Dashboards, Monitors, Incidents, Hosts, Services, Events, Notebooks | ~25 | Always enabled |
| **apm** | APM, Watchdog, Change Tracking, Recommendations | ~15 | Debugging traces & performance |
| **dashboards** | Dashboard CRUD, Widgets | ~8 | Creating/editing dashboards |
| **cases** | Case management, Jira integration | ~10 | Incident response & case tracking |
| **security** | Security signals, detection rules, findings, IOC | ~25 | Security investigations |
| **error-tracking** | Error tracking issues, source maps | ~4 | Frontend error analysis |
| **llmobs** | LLM Observability experiments | ~10 | AI/LLM performance analysis |
| **database-monitoring** | Database query perf, explain plans, schemas | ~12 | Database troubleshooting |
| **code-coverage** | Code coverage reports, PR summaries | ~4 | CI/CD quality gates |
| **profiling** | Continuous Profiling data | ~10 | Performance optimization |
| **rum** | RUM events, metrics, retention filters | ~4 | Frontend monitoring |
| **synthetics** | Synthetic tests, browser tests | ~2 | API/browser test management |
| **workflows** | Datadog Workflows | ~4 | Workflow automation |
| **reference-tables** | Reference table CRUD | ~3 | Enrichment data |
| **feature-flags** | Feature flag management | ~8 | Flag lifecycle management |
| **cloud-cost** | Cloud Cost Management | ~2 | Cost analysis |
| **ndm** | Network Device Monitoring | ~4 | Network monitoring |
| **kubernetes** | Kubernetes resources, manifests | ~3 | K8s troubleshooting |
| **sheets** | Spreadsheet management | ~1 | Dashboard-as-code |
| **experimental** | Beta/experimental tools | varies | New features |

---

## Files

| File | Covers |
|------|--------|
| [core-tools.md](core-tools.md) | Logs, Metrics, Monitors, Incidents, Events, Traces, Hosts & Services, SLOs, Workflows |
| [dashboards-notebooks.md](dashboards-notebooks.md) | Dashboards, Notebooks, Widgets |
| [apm-tools.md](apm-tools.md) | APM spans, Watchdog, Change Stories, Recommendations |
| [cases-tools.md](cases-tools.md) | Cases, User Management |
| [security-tools.md](security-tools.md) | Security Signals, Detection Rules, Suppressions, IOC |
| [rum-synthetics.md](rum-synthetics.md) | RUM events, Synthetics tests |
| [specialized-toolsets.md](specialized-toolsets.md) | Error Tracking, LLM Obs, Database, Profiling, Code Coverage, K8s, NDM, Cloud Cost, Feature Flags, Reference Tables, DDSQL, Sheets |

---

## Quick Reference by Use Case

### Incident Response
```
get_datadog_incident → search_datadog_monitors → search_datadog_spans → analyze_datadog_logs
```

### Performance Investigation
```
search_datadog_spans → get_datadog_trace → apm_latency_bottleneck_summary → get_datadog_metric
```

### Cost Analysis
```
get_datadog_metric(use_cloud_cost=true) → search_datadog_metrics → get_datadog_metric_context
```

### SLO Monitoring
```
search_datadog_slos → search_datadog_monitors → search_datadog_events
```

### Security Investigation
```
search_datadog_security_signals → get_datadog_security_signal → search_datadog_events
```

### Error Tracking
```
search_datadog_error_tracking_issues → get_datadog_error_tracking_issue → search_datadog_logs
```

### Frontend Performance
```
search_datadog_rum_events → get_rum_insight → get_rum_summary
```
