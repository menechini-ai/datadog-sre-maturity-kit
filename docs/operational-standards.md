---
description: Reference for all 7 operational standards documents
---

# Operational Standards — Reference

Strategic frameworks for deploying and operating Datadog at enterprise scale.

## Documents

| # | Standard | Description |
|---|----------|-------------|
| 00 | [HealthCheck Account Analysis](../notebooks/00-healthcheck-account-analysis.md) | Initial Datadog account health assessment template with embedded dashboards |
| 01 | [Platform Preparation](../notebooks/01-operational-standards-platform-preparation.md) | Network egress, proxy configuration, API/App key strategies |
| 02 | [Access Management](../notebooks/02-operational-standards-access-management.md) | RBAC roles, Datadog Teams setup, permission management, SAML/SSO |
| 03 | [Governance](../notebooks/03-operational-standards-governance.md) | Compliance strategies (GDPR, HIPAA, FedRAMP, PCI-DSS), agent deployment |
| 04 | [Data Monitoring](../notebooks/04-operational-standards-data-monitoring.md) | Log management, indexing strategies, archiving approaches |
| 05 | [Data Visualization](../notebooks/05-operational-standards-data-visualization.md) | Dashboard design patterns, template variables, visualization best practices |
| — | [Tagging Strategy](../notebooks/operational-standards-tagging-strategy.md) | Comprehensive tagging framework based on Unified Service Tagging |

## Key Principles

### Tagging
Based on Datadog's **Unified Service Tagging (UST)**:
- **Reserved tags**: `env`, `service`, `version`, `source`, `host`, `device`
- **Critical recommended tags**: `team`, `runtime`, `journey`, `role`, `application`
- **Format**: lowercase with underscores (not hyphens or camelCase)
- Tags must not originate from unbounded sources

### Access Management
1. Do **not** modify OOTB roles (Datadog Admin, Standard, Read-only)
2. Baseline: Datadog Standard Role, exclude API key and user invite permissions
3. Custom roles as needed (Developer, Development Manager)
4. Datadog Teams mirror organizational structure

### Compliance

| Standard | Requirement |
|----------|-------------|
| **PCI-DSS** | US1 site only, HTTPS endpoints, Audit Trail required |
| **HIPAA** | BAA required, no Zendesk chat, no log sharing |
| **FedRAMP** | GovCloud instance only (Moderate level) |
| **GDPR** | EU1 site for data residency |

### Log Management
- Default "main" index is catch-all (15-day retention)
- Create indexes by log type + environment for granular control
- Use exclusion filters for irrelevant logs (debug, non-critical)
- Archive to external storage (S3, Azure Blob) or Flex Logs

### Dashboard Design
1. Monitor/SLO summary at top for immediate health status
2. App Overview Dashboard Template as baseline
3. Integration-specific widget groups with context links
4. Template variables for dynamic filtering (app, env, integration, service)
