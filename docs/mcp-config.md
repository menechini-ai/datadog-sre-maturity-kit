---
description: Datadog MCP Server configuration reference
---

# Datadog MCP Server — Configuration

## Server Endpoint

The kit is pre-configured for the **US3** Datadog site. The MCP server uses HTTP transport:

```json
{
  "mcpServers": {
    "datadog": {
      "type": "http",
      "url": "https://mcp.datadoghq.com/api/unstable/mcp-server/mcp"
    }
  }
}
```

## Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `DD_SITE` | Datadog site (e.g., `datadoghq.com`) | Yes |
| `DD_API_KEY` | Datadog API key | Yes |
| `DD_APP_KEY` | Datadog Application key | Yes |

Generate keys at:
- API Keys: `https://datadoghq.com/organization-settings/api-keys`
- Application Keys: `https://datadoghq.com/organization-settings/application-keys`

## Regional Endpoints

| Site | MCP URL |
|------|---------|
| US1 | `https://mcp.datadoghq.com/api/unstable/mcp-server/mcp` |
| US3 | `https://mcp.us3.datadoghq.com/api/unstable/mcp-server/mcp` |
| US5 | `https://mcp.us5.datadoghq.com/api/unstable/mcp-server/mcp` |
| EU | `https://mcp.datadoghq.eu/api/unstable/mcp-server/mcp` |
| AP1 | `https://mcp.ap1.datadoghq.com/api/unstable/mcp-server/mcp` |

## Full Tool Reference

See [datadog-info/README.md](/datadog-info/README.md) for the complete MCP tool reference index with documentation of all ~100+ MCP tools organized by toolset.

## Verification

After configuration, verify the connection:

```bash
# Ask Claude to verify
Tell me about my Datadog organization
```

If the MCP server responds, the configuration is working.
