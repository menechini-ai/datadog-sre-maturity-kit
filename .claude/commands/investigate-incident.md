# Investigate Incident

Deep-dive investigation of a specific Datadog incident — correlates events, APM traces, error logs, monitors, and security signals around the incident timeframe.

> **Required**: Ask the user for the `incident_id` and at minimum `service` and `env` tags.
> ```
> incident_id: <incident_id>     # e.g. "123456789"
> service:     <service_name>    # e.g. "api-gateway"
> env:         <environment>     # e.g. "prod"
> ```
> The command will also extract additional tags from the incident's own context to scope downstream queries.
>
> **Reference**: [MCP Tools](../../datadog-info/README.md) | [Core Tools](../../datadog-info/core-tools.md)

---

**Overview**

1. Fetch incident details via `get_datadog_incident`
2. Extract context: tags, severity, state, customer impact scope, timeframe
3. Run 5 parallel signal queries (events, APM errors, logs, monitors, security)
4. Consolidate into a correlated investigation report

---

**Step 1: Fetch Incident Details**

```
get_datadog_incident(
    incident_id="<incident_id>"
)
```

Extract from the response:
- `title`, `severity`, `state`, `detection_method`
- `customer_impact_started_at` / `customer_impact_ended_at` — incident timeframe
- `customer_impact_scope` — affected services
- Tags from incident attributes (merged with user-provided `service`, `env`)
- `responders` — teams involved

---

**Step 2: Parallel Signal Correlation**

Use the timeframe and tags from Step 1 to scope all queries below.
Run these in **parallel** — they are independent.

**A. Events** (deployments, alerts, infrastructure changes)
```
search_datadog_events(
    query="service:<service> env:<env> tags:incident_id:<incident_id>",
    from="<customer_impact_start>",
    to="<now>"
)
```

**B. APM Error Spans** (traces with errors during incident)
```
search_datadog_spans(
    query="service:<service> env:<env> @error:true",
    from="<customer_impact_start>",
    to="<now>",
    head_limit=100
)
```

**C. Error Logs** (logs at error/fatal level during incident)
```
search_datadog_logs(
    query="service:<service> env:<env> status:error OR status:fatal",
    from="<customer_impact_start>",
    to="<now>",
    head_limit=100
)
```

**D. Monitors in Alert** (monitors that fired during the incident)
```
search_datadog_monitors(
    filter="service:<service>,env:<env>",
    query="status:alert"
)
```

**E. Security Signals** (security findings in the same window)
```
search_datadog_security_signals(
    query="service:<service> env:<env>"
)
```

---

**Step 3: Correlate & Investigate**

Cross-reference the 5 result sets to identify:

| Question | Data Source |
|---|---|
| What changed right before the incident? | Events (deployments, config changes) |
| Which services returned errors? | APM spans, error logs |
| Was there a monitor that should have caught this? | Monitors |
| Is there a security component? | Security signals |
| What's the error pattern? | Logs (group by message) |

**Signal Correlation Matrix:**

```
Timeline:
  [Event: deployment api-gateway v2.3.1] ─────┐
                                               ├── [Incident Starts] ── [Error Spike] ── [Monitor Alert]
  [Log: connection pool exhausted] ────────────┘
  [APM: /checkout P99 5.2s → 30s] ────────────────────────────────────────────────────── [Incident Resolved]
```

---

**Step 4: Deliver Report**

Generate a structured investigation report:

```markdown
## Incident Investigation Report

### Summary
- **Incident**: [title] ([id])
- **Severity**: [severity] | **State**: [state]
- **Duration**: [start] → [end] ([duration])
- **Affected Services**: [scope]

### Timeline
| Time | Event | Source |
|------|-------|--------|
| T-5min | [event] | Events |
| T-0 | Incident declared | Incidents |
| T+2min | Error spike | APM/Logs |
| T+5min | Monitor alert | Monitors |
| T+30min | Incident resolved | Incidents |

### Root Cause Candidates
1. [candidate 1] — evidence from [source]
2. [candidate 2] — evidence from [source]

### Error Patterns
- [pattern 1]: [count] occurrences
- [pattern 2]: [count] occurrences

### Recommendations
- [recommendation 1]
- [recommendation 2]
```

**Optional**: Save report to Datadog Notebook
```
create_datadog_notebook(
    name="Incident Investigation - [title] - [DATE]",
    type="investigation",
    cells=... # Include full investigation report
)
```

Return notebook URL if created, otherwise return the markdown report directly.
