# SRE Spec Kit for Datadog

**A comprehensive maturity assessment and implementation framework for Datadog observability**

![Maturity Levels](https://img.shields.io/badge/Maturity%20Levels-6%20(0--5)-blue)
![Commands](https://img.shields.io/badge/Slash%20Commands-18-green)
![Notebook Templates](https://img.shields.io/badge/Notebook%20Templates-14-orange)

---

## 🚀 Quick Start

**New here?** Start with the [Quick Start Guide](./QUICKSTART.md) to run your first assessment in 5 minutes.

```bash
# Your first command - assess your current maturity
/assess
```

**Already familiar?** Jump to:
- [Command Reference](./COMMANDS.md) - All 18 slash commands
- [Level Definitions](./planning/level-definitions.md) - Detailed maturity criteria
- [Implementation Plan](./PLAN.md) - Project roadmap and status

---

## What is This?

The **SRE Spec Kit for Datadog** is a command-driven framework that helps SRE and platform engineering teams:

1. **Assess** current Datadog observability maturity (Levels 0-5)
2. **Identify** gaps in monitoring, tagging, cost optimization, and incident management
3. **Plan** step-by-step upgrades to advance SRE practices
4. **Document** investigations, postmortems, and reports using proven templates
5. **Track** progress over time with repeatable assessments

### Why Use This Kit?

- ✅ **Objective Assessment**: Uses real Datadog data via MCP (not surveys)
- ✅ **Industry Standards**: Based on SRE best practices and Datadog recommendations
- ✅ **Actionable Plans**: Get specific, prioritized steps to improve
- ✅ **Save Time**: Pre-built commands and templates (not starting from scratch)
- ✅ **Track Progress**: Repeatable assessments show maturity growth

---

## Maturity Levels Overview

| Level | Name | Focus | Timeline |
|-------|------|-------|----------|
| **Level 0** | Foundation | Basic observability setup | 1-2 months |
| **Level 1** | Standardization | Operational excellence | 2-3 months |
| **Level 2** | Optimization | Efficiency & scale | 3-4 months |
| **Level 3** | Intelligence | Proactive operations | 4-6 months |
| **Level 4** | Innovation | Advanced capabilities | 6-9 months |
| **Level 5** | Excellence | Industry leadership | 9-12 months |

**Total journey from Level 0 to Level 5**: Approximately 2-3 years

See [Level Definitions](./planning/level-definitions.md) for detailed requirements.

---

## 📋 Command Categories

### Assessment Commands (6 commands)
Run maturity assessments and generate reports:
- `/assess` - Quick 10-minute maturity check
- `/assess-full` - Comprehensive 30-minute assessment
- `/assess-level0`, `/assess-level1` - Level-specific validation
- `/gap-analysis` - Identify gaps between current and target levels
- `/upgrade-plan` - Generate step-by-step upgrade roadmap

### Level 0 Foundation Commands (4 commands)
Establish baseline visibility:
- `/level0-infra` - Infrastructure discovery and inventory
- `/level0-tagging` - Tagging compliance audit
- `/level0-cost` - Cost baseline establishment
- `/level0-healthcheck` - Complete health check report

### Advanced Commands (2 commands)
Level 2+ capabilities:
- `/level2-tagging` - Advanced tagging strategy
- `/level3-cost` - Detailed cost optimization analysis

### Reporting & Documentation (4 commands)
Generate and share results:
- `/generate-report` - Executive summary generation
- `/save-to-notebook` - Save markdown to Datadog Notebook
- `/assess-to-notebook` - Assessment with Datadog export
- `/create-starter-notebooks` - Generate 14 template files

### Utilities (2 commands)
Helper commands:
- `/help` - List all available commands
- `/append-to-notebook` - Append to existing Datadog Notebook

**Total**: 18 slash commands

See [COMMANDS.md](./COMMANDS.md) for detailed command reference.

---

## 📊 8 Assessment Dimensions

Every assessment evaluates your Datadog implementation across:

1. **Infrastructure Coverage** (25 points)
   - Agent deployment coverage
   - Cloud integration status
   - Service discovery

2. **Service Catalog** (10 points)
   - Service registration completeness
   - Ownership assignment
   - Metadata quality

3. **Tagging Compliance** (15 points)
   - UST tag coverage (env, service, version)
   - Tag consistency and format
   - Custom tag strategy

4. **Monitoring Quality** (15 points)
   - Monitor coverage by service tier
   - Alert quality and actionability
   - SLO tracking

5. **Log Management** (10 points)
   - Log collection coverage
   - Pipeline efficiency
   - Retention and archiving strategy

6. **Cost Optimization** (10 points)
   - Cost visibility by service/team
   - Resource efficiency
   - Optimization opportunities

7. **Incident Management** (10 points)
   - MTTR and MTTD metrics
   - Postmortem quality
   - Automation level

8. **Advanced Capabilities** (5 points)
   - APM, Synthetics, RUM usage
   - Automation and workflows
   - ML-powered features

**Maximum Score**: 100 points

See [Assessment Methodology](./planning/assessment-methodology.md) for scoring details.

---

## 📁 Repository Structure

```
spec-kit-sre-datadog/
│
├── README.md                   ← You are here
├── QUICKSTART.md              ← Start here for new users
├── COMMANDS.md                 ← Complete command reference
├── PLAN.md                     ← Implementation plan and status
├── CLAUDE.md                   ← Claude Code integration guide
│
├── .claude/
│   └── commands/              ← 18 slash commands
│       ├── assess.md
│       ├── assess-full.md
│       ├── level0-infra.md
│       └── ... (16 more)
│
├── planning/                   ← Framework documentation
│   ├── README.md
│   ├── level-definitions.md   ← Detailed maturity criteria
│   ├── assessment-methodology.md
│   ├── mcp-query-patterns.md
│   ├── claude-md-strategy.md
│   └── notebook-templates-spec.md
│
├── notebooks/                  ← 14 ready-to-use templates
│   ├── README.md
│   ├── assessments/           ← 3 assessment templates
│   ├── investigations/        ← 3 investigation templates
│   ├── postmortems/           ← 2 postmortem templates
│   ├── runbooks/              ← 3 runbook templates
│   └── reports/               ← 3 report templates
│
└── datadog-info/              ← Datadog account reference
    └── (operational standards docs)
```

---

## 🎯 Common Use Cases

### Use Case 1: New to Datadog SRE
**Goal**: Understand your starting point

```bash
# Day 1: Quick assessment
/assess

# Day 2: Baseline your infrastructure
/level0-infra
/level0-tagging
/level0-cost

# Day 3: Create improvement plan
/gap-analysis
/upgrade-plan
```

### Use Case 2: Quarterly Review
**Goal**: Track progress and report to leadership

```bash
# Run comprehensive assessment
/assess-full

# Generate executive report
/generate-report

# Save to Datadog for sharing
/save-to-notebook
```

### Use Case 3: Preparing for Next Level
**Goal**: Validate readiness to advance

```bash
# Check current level validation
/assess-level1

# Identify remaining gaps
/gap-analysis

# Create upgrade roadmap
/upgrade-plan
```

### Use Case 4: Incident Investigation
**Goal**: Document root cause and learnings

```bash
# Create investigation from template
/create-starter-notebooks

# Use notebooks/investigations/error-spike-investigation-template.md
# Customize for your incident
# Run embedded MCP queries
# Document findings

# Save to Datadog
/save-to-notebook
```

---

## 📚 Documentation

### Getting Started
- **[QUICKSTART.md](./QUICKSTART.md)** - Start here! 5-minute quick start guide
- **[COMMANDS.md](./COMMANDS.md)** - Complete command reference with examples

### Planning & Methodology
- **[PLAN.md](./PLAN.md)** - Implementation plan and current status
- **[planning/level-definitions.md](./planning/level-definitions.md)** - Detailed maturity criteria
- **[planning/assessment-methodology.md](./planning/assessment-methodology.md)** - How assessments work
- **[planning/mcp-query-patterns.md](./planning/mcp-query-patterns.md)** - Common Datadog MCP queries

### Templates & Guides
- **[notebooks/README.md](./notebooks/README.md)** - Template library guide
- **[planning/notebook-templates-spec.md](./planning/notebook-templates-spec.md)** - Template specifications

### Integration
- **[CLAUDE.md](./CLAUDE.md)** - Claude Code integration strategy
- **[planning/claude-md-strategy.md](./planning/claude-md-strategy.md)** - MCP usage patterns

---

## 🔧 Prerequisites

### Required
1. **Datadog Account** with API access
2. **Datadog MCP Server** installed and configured
   - See: https://docs.datadoghq.com/bits_ai/mcp_server/setup/
3. **Claude Code CLI** installed and running
4. **API/App Keys** with read permissions for:
   - Hosts, services, metrics
   - Logs, traces, events
   - Monitors, dashboards, notebooks

### Recommended Permissions
For full assessment capabilities, your API key should have:
- ✅ Read access to all Datadog resources
- ✅ Write access to notebooks (for `/save-to-notebook` commands)
- ✅ Cloud cost data access (for cost optimization)

---

## 🎓 Learning Path

### Week 1: Foundation
1. Read [QUICKSTART.md](./QUICKSTART.md)
2. Run `/assess` to understand your current level
3. Review [Level Definitions](./planning/level-definitions.md)
4. Run `/gap-analysis` to see what's missing

### Week 2-4: Level 0 Completion
1. Run `/level0-infra`, `/level0-tagging`, `/level0-cost`
2. Fix critical gaps (especially tagging)
3. Run `/assess-level0` to validate
4. Run `/level0-healthcheck` for complete report

### Month 2-3: Level 1 Advancement
1. Run `/upgrade-plan` for Level 1
2. Implement monitoring and SLOs
3. Set up log management
4. Run `/assess-level1` to validate

### Ongoing: Continuous Improvement
1. Run `/assess` weekly to track progress
2. Run `/assess-full` monthly for detailed review
3. Run `/generate-report` quarterly for leadership
4. Use notebook templates for investigations and postmortems

---

## 💡 Best Practices

### Assessment Best Practices
1. **Start with Level 0** - Don't skip the foundation
2. **Run regularly** - Weekly quick checks, monthly deep dives
3. **Track progress** - Save assessment results over time
4. **Share results** - Use `/generate-report` for leadership updates

### Implementation Best Practices
1. **Follow the levels** - Each builds on the previous
2. **Fix tagging first** - It's the foundation for everything else
3. **Use templates** - Don't reinvent the wheel
4. **Document everything** - Use notebook templates for incidents

### Tool Usage
1. **Use slash commands** - Pre-built and tested
2. **Save to Datadog** - Use `/save-to-notebook` for collaboration
3. **Refer to planning docs** - When you need details
4. **Check COMMANDS.md** - For syntax and examples

---

## 🆘 Troubleshooting

### "Datadog MCP not found"
- Install Datadog MCP server: https://docs.datadoghq.com/bits_ai/mcp_server/setup/
- Verify configuration in Claude Code settings

### "Permission denied" errors
- Check API key permissions
- Ensure read access to all Datadog resources
- Verify API key is not expired

### Assessment shows unexpected low scores
- Check tagging compliance - it's often the culprit
- Verify data is flowing (agents reporting, logs ingesting)
- Run `/assess-full` for detailed breakdown

### Commands not found
- Commands are in `.claude/commands/` directory
- Use `/help` to list all available commands
- Check that you're using slash syntax: `/assess` not `assess`

---

## 🤝 Contributing

This is an internal tool framework. To improve:

1. **Add new templates** - Create in `notebooks/` and document in README
2. **Enhance commands** - Update `.claude/commands/` files
3. **Improve docs** - Update planning documents
4. **Share learnings** - Document patterns in `planning/`

---

## 📈 Success Metrics

Track your SRE maturity journey:

- ✅ Initial assessment completed
- ✅ Current level identified and validated
- ✅ Gaps documented with priorities
- ✅ Upgrade plan created and approved
- ✅ Quarterly assessments scheduled
- ✅ Team aligned on SRE goals
- ✅ Executive reporting established
- ✅ Level advancement achieved

---

## 📞 Getting Help

### Within This Repository
- **General usage**: [QUICKSTART.md](./QUICKSTART.md)
- **Command syntax**: [COMMANDS.md](./COMMANDS.md)
- **Assessment details**: [planning/assessment-methodology.md](./planning/assessment-methodology.md)
- **Level requirements**: [planning/level-definitions.md](./planning/level-definitions.md)

### External Resources
- **Datadog MCP**: https://docs.datadoghq.com/bits_ai/mcp_server/
- **Datadog Best Practices**: https://docs.datadoghq.com/
- **SRE Fundamentals**: https://sre.google/

---

## 📊 Project Status

**Current Implementation Status**: ~80% Complete

### ✅ Completed (Phases 1-7)
- Planning and methodology documentation
- Level definitions (Levels 0-5)
- 18 slash commands
- 14 notebook templates
- Assessment framework
- Quick start guide
- Command reference

### 🚧 In Progress (Phase 8)
- Maturity levels directory structure (P1)

### 📋 Planned (Phases 9-11)
- Additional assessment commands (P2)
- Assessment automation tools (P2)
- Advanced level commands (P3)

See [PLAN.md](./PLAN.md) for detailed status and roadmap.

---

## 📄 License

MIT License - See LICENSE file for details

---

## 🚀 Ready to Start?

**Your first command awaits:**

```bash
/assess
```

Or read the [Quick Start Guide](./QUICKSTART.md) for a guided introduction.

---

**Version**: 1.0
**Last Updated**: 2026-07-10
**Maintained By**: SRE Platform Team
