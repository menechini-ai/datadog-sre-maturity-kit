---
description: Level 0 Foundation readiness assessment (15 min)
allowed-tools: Read, Bash
model: sonnet
---

<!--
COMMAND: check-level0
VERSION: 1.0.0
LAST UPDATED: 2026-07-10

PURPOSE:
  Level 0 Foundation readiness assessment (15 min)

USAGE:
  /check-level0 

REQUIREMENTS:
  - Datadog MCP server configured (mcp.json)
  - User must provide required tags (service, env)

RELATED COMMANDS:
  /help - List all commands
-->
# Level 0: Foundation Assessment

Assess readiness for Level 0 (Foundation - Discovery & Planning phase).

**Level 0 Core Capabilities:**
- Complete infrastructure inventory
- Current state analysis and gap identification
- Cost baseline establishment
- Tagging strategy planning
- Team structure documentation

**Execute these checks:**

1. **Infrastructure Discovery**
   - Query: `search_datadog_hosts(filter="env:<env>", include_all_tags=True)`
   - Count total hosts vs cloud instances
   - Identify monitored vs unmonitored resources
   - List all environments and services

2. **Current Coverage Analysis**
   - Query: `get_datadog_metric(queries=["count:datadog.agent.running{env:<env>}"])`
   - Calculate baseline agent coverage
   - Identify monitoring gaps
   - Document existing tools

3. **Cost Baseline**
   - Query: `get_datadog_metric(queries=["sum:all.cost{env:<env>}.rollup(sum, monthly)"], use_cloud_cost=True)`
   - Establish cost baseline
   - Identify top cost drivers
   - Document current spend

4. **Tagging Audit**
   - Analyze existing tag usage
   - Identify tag inconsistencies
   - Document current tagging patterns
   - Recommend tagging strategy

**Success Criteria for Level 0:**
- ✅ Infrastructure inventory complete
- ✅ Cost baseline documented
- ✅ Monitoring gaps identified
- ✅ Tagging strategy drafted
- ✅ Team ownership mapped

**Deliver:**
- Level 0 readiness score
- Checklist of completed items
- Missing prerequisites
- Recommended actions to complete Level 0
- Estimated time to completion

**After completing validation:**

Automatically create Datadog Notebook with Level 0 validation results:

```
create_datadog_notebook(
    name="Level 0 - Foundation - Validation Report - [DATE]",
    type="documentation",
    cells=... # Include validation checklist and readiness score
)
```

**Notebook naming format:**
- "Level 0 - Foundation - Validation Report - YYYY-MM-DD"
- Example: "Level 0 - Foundation - Validation Report - 2026-07-10"

Return notebook URL for graduation milestone tracking.