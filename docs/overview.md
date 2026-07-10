---
description: Overview and architecture of the Datadog SRE Maturity Kit
---

# Datadog SRE Maturity Kit — Overview

## Purpose

The **Datadog SRE Maturity Kit** is a command-driven framework that helps SRE and platform engineering teams assess, plan, and implement observability best practices using Datadog. It provides a structured maturity model (Levels 0–5), pre-built slash commands for Claude Code, and ready-to-use notebook templates for assessments, investigations, runbooks, and reports.

## Maturity Model

| Level | Name | Focus | Timeline |
|-------|------|-------|----------|
| **Level 0** | Foundation | Basic observability setup | 1–2 months |
| **Level 1** | Standardization | Operational excellence | 2–3 months |
| **Level 2** | Optimization | Efficiency & scale | 3–4 months |
| **Level 3** | Intelligence | Proactive operations | 4–6 months |
| **Level 4** | Innovation | Advanced capabilities | 6–9 months |
| **Level 5** | Excellence | Industry leadership | 9–12 months |

Each level builds progressively on the previous. Teams must demonstrate capability at one level before advancing.

## Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    Claude Code CLI                       │
├─────────────────────────────────────────────────────────┤
│  ┌──────────────┐  ┌──────────────┐  ┌───────────────┐  │
│  │   Slash      │  │   Natural    │  │   Notebook    │  │
│  │  Commands    │  │  Language    │  │   Templates   │  │
│  │  (18 cmds)   │  │  Prompts     │  │   (14 files)  │  │
│  └──────┬───────┘  └──────┬───────┘  └───────┬───────┘  │
│         │                 │                  │           │
│  ┌──────┴─────────────────┴──────────────────┴───────┐  │
│  │              Datadog MCP Server                    │  │
│  │  (mcp.us3.datadoghq.com/api/unstable/mcp-server)   │  │
│  └──────────────────────┬─────────────────────────────┘  │
├─────────────────────────┴───────────────────────────────┤
│                    Datadog Platform                       │
│  (Metrics ┆ Logs ┆ Traces ┆ Dashboards ┆ Monitors ┆ ...) │
└─────────────────────────────────────────────────────────┘
```

## Components

### Slash Commands (18)
Assessment, task execution, gap analysis, upgrade planning, report generation, and notebook integration. See [commands.md](./commands.md).

### Notebook Templates (14)
Pre-built Datadog Notebook templates for common SRE workflows. See [notebooks.md](./notebooks.md).

### Operational Standards (7)
Strategic frameworks for platform preparation, access management, governance, data monitoring, visualization, and tagging. See [operational-standards.md](./operational-standards.md).

### MCP Configuration
Datadog MCP Server connection for AI-driven observability queries. See [mcp-config.md](./mcp-config.md).

## Quick Start

```bash
# 1. First assessment
/assess

# 2. Level 0 discovery
/level0-infra

# 3. Generate report
/generate-report
```

See the [Quick Start Guide](../QUICKSTART.md) for a full walkthrough.
