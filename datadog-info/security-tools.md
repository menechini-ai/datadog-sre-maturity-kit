# Security Tools (toolset: `security`)

Security signals, detection rules, findings, suppressions, and IOC management.

Enable via: `<MCP_ENDPOINT>?toolsets=security`

> **Usage Rules**: See [README.md](README.md) — always ask user for `service` and `env` tags before querying.

---

## Signals & Findings

### `search_datadog_security_signals`

Search security signals.

**Required permissions**: `Security Signals`

**Example prompts**:
- Show all security signals from the last 24 hours
- Find signals related to the production environment

### `analyze_datadog_security_signals`

Analyze security signal patterns.

### `get_datadog_security_signal`

Get full signal details including evidence and timeline.

**Required permissions**: `Security Signals`

### `update_datadog_security_signals_triage`

Triage a security signal (archive, escalate, etc.).

### `analyze_datadog_security_findings`

Analyze security findings across resources.

### `create_datadog_security_findings_ticket`

Create a ticket from security findings.

### `get_datadog_security_findings_schema`

Get the schema for security findings.

### `get_datadog_security_findings_ticket_suggestions`

Get suggestions for ticketing findings.

---

## Detection Rules

### `search_datadog_security_detection_rules`

Search detection rules by name, type, or status.

**Required permissions**: `Security Rules`

**Example prompts**:
- List all detection rules that are disabled
- Find rules related to AWS CloudTrail

### `get_datadog_security_detection_rules`

Get detection rule details. Supports requesting a subset of fields.

**Required permissions**: `Security Rules`

### `get_datadog_security_detection_rules_schema`

Get the schema for detection rule configuration.

### `create_datadog_security_detection_rule`

Create a new detection rule.

**Required permissions**: `Security Rules`

### `delete_datadog_security_detection_rules`

Delete detection rules by ID.

**Required permissions**: `Security Rules`

---

## Suppressions & Denylist

### `search_datadog_security_suppressions`

Search suppression rules.

### `create_datadog_security_suppression`

Create a suppression rule.

### `get_datadog_security_suppressions`

Get suppression rule details.

### `delete_datadog_security_suppression`

Delete a suppression rule.

### `get_datadog_security_denylist`

Get the denylist configuration.

### `delete_datadog_security_denylist_entry`

Remove an entry from the denylist.

### `get_datadog_security_passlist`

Get the passlist configuration.

### `delete_datadog_security_passlist`

Remove an entry from the passlist.

---

## IOC (Indicators of Compromise)

### `get_datadog_security_ioc_indicator`

Get IOC indicator details.

### `get_datadog_security_ioc_schema`

Get IOC schema definition.
