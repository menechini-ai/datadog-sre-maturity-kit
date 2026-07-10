# Gap Analysis Generator

Automated gap detection between current and target maturity levels. Use after completing the [Maturity Scorecard](maturity-scorecard.md) to translate scores into actionable work items.

---

## Quick Start

```
1. Fill maturity-scorecard.md → get current level + dimension scores
2. Run this generator → produces gap inventory + priority matrix
3. Hand off to upgrade-path-planner.md → roadmap with milestones
```

---

## Gap Detection Process

### Step 1: Identify Current State

From your [Maturity Scorecard](maturity-scorecard.md), extract:

| Metric | Value |
|--------|-------|
| Current Level | Level [N] |
| Target Level | Level [N+1] |
| Overall Score | __ / 190 (__%) |
| Lowest Dimension | [Name] — [Score]% |
| Highest Dimension | [Name] — [Score]% |

### Step 2: Map Missing Capabilities

Compare current scores against target-level graduation criteria. For each missing or underperforming capability, create a gap record:

```
## Gap: [Capability Name]

**Current State**: [Description — where you are today]
**Target State**: [Description — where you need to be]
**Gap Size**: [Quantified delta, e.g. "40% tagging compliance vs 90% target"]

**Category**: [Critical / Recommended / Optional]
**Business Impact**: [High / Medium / Low — what breaks if unfixed]
**Effort**: [Low / Medium / High — person-days to close]
**Dependencies**: [What must be in place first]
```

### Step 3: Categorize & Prioritize

Use the **Impact × Effort** matrix to sequence work:

```
                | High Impact    | Medium Impact    | Low Impact
----------------|----------------|------------------|---------------
Low Effort      | 🟢 DO NOW      | 🟢 DO NOW        | 🟡 QUICK WIN
Medium Effort   | 🟡 PLAN NEXT    | 🟡 SCHEDULE       | 🟠 LATER
High Effort     | 🟠 MILESTONE    | 🔴 BACKLOG        | 🔴 BACKLOG
```

### Step 4: Phase Gaps into Roadmap

Organize by effort level and dependencies:

| Phase | Focus | Timeline | Typical Gaps |
|-------|-------|----------|--------------|
| **Quick Wins** | Low effort, high impact | 0–30 days | Tagging cleanup, untagged monitors |
| **Foundation** | Medium effort, foundational | 30–60 days | Agent rollout, log pipelines |
| **Advanced** | High effort, transformative | 60–90 days | RUM, synthetics, automation |

---

## Gap Templates by Level

### Level 0 → Level 1

| Gap | Impact | Effort | Dependency |
|-----|--------|--------|------------|
| No agent on production hosts | Critical | Medium | Network egress open |
| Missing core monitors | Critical | Low | Agent deployed |
| No log collection pipeline | High | Medium | Agent configured |
| No incident tracking process | Medium | Low | Tool selected |

**Validation queries**: [Metrics Queries](mcp-query-library/metrics-queries.md) — Host coverage  
**Tool Reference**: See [datadog-info/README.md](/datadog-info/README.md) for the complete MCP tool reference index.

### Level 1 → Level 2

| Gap | Impact | Effort | Dependency |
|-----|--------|--------|------------|
| env/service/version tags missing | Critical | High | Tagging policy agreed |
| SLOs not defined | Critical | Medium | Service catalog complete |
| Monitor alert fatigue (>15/week) | High | Low | Monitor audit |
| APM not instrumented | High | High | Dev team onboarding |
| Dashboards inconsistent | Medium | Medium | Template chosen |

**Validation queries**: [Metrics Queries](mcp-query-library/metrics-queries.md) — Tag compliance

### Level 2 → Level 3

| Gap | Impact | Effort | Dependency |
|-----|--------|--------|------------|
| No log exclusion filters | Critical | Low | Log pipeline exists |
| Cost not allocated by team | High | Medium | Tags on all resources |
| No SLO burn-rate alerts | High | Medium | SLOs defined |
| No on-call integration | Critical | Medium | Monitors tagged |
| Compliance not addressed | High (regulated only) | High | Legal review |

**Validation queries**: [Logs Queries](mcp-query-library/logs-queries.md) — Index efficiency

### Level 3 → Level 4

| Gap | Impact | Effort | Dependency |
|-----|--------|--------|------------|
| No synthetic tests | High | Medium | Critical journeys documented |
| No RUM instrumentation | Medium | High | Web app teams buy-in |
| Manual remediation only | High | High | Runbooks documented |
| Agent versions drifting | Medium | Medium | Fleet management tooling |

**Validation queries**: [APM Queries](mcp-query-library/apm-queries.md), [RUM Queries](mcp-query-library/rum-queries.md)

### Level 4 → Level 5

| Gap | Impact | Effort | Dependency |
|-----|--------|--------|------------|
| No ML-driven insights | Medium | Medium | Historical data available |
| No predictive alerting | Medium | High | Forecast monitors configured |
| No self-service observability | High | High | Platform team |
| No SLO gating in CI/CD | High | High | CI/CD pipeline maturity |

**Validation queries**: [Cost Queries](mcp-query-library/cost-queries.md) — Trend analysis

---

## Deliverable

Run this generator and produce a gap analysis report:

```markdown
# Gap Analysis: Level [N] → Level [N+1]

## Executive Summary
Current level: [N] — Score: [X]%
Target level: [N+1]
Total gaps identified: [N]
Quick wins: [N] — Foundation: [N] — Advanced: [N]

## Gap Inventory
[Detailed records from Step 2]

## Priority Matrix
[Visual from Step 3]

## Implementation Roadmap

### Phase 1 — Quick Wins (0–30 days)
- [ ] [Gap] — Owner, effort

### Phase 2 — Foundation (30–60 days)
- [ ] [Gap] — Owner, effort

### Phase 3 — Advanced (60–90 days)
- [ ] [Gap] — Owner, effort

## MCP Validation Queries
[Links to specific queries from mcp-query-library/]

## Risk Assessment
- [Risk]: [Mitigation]
```

---

## MCP Integration

Validate every closed gap with a live Datadog query:

1. Run the matching query from [MCP Query Library](mcp-query-library/).
2. Confirm result meets threshold.
3. Mark gap ✅ verified.

**Example**: After deploying agents to meet 80% coverage:
```
search_datadog_hosts(filter="service:<service>,env:<env>") → confirm count / expected ≥ 0.80
```
