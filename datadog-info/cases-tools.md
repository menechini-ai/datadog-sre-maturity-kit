# Cases & Collaboration (toolset: `cases`)

Case management, Jira integration, and user management tools.

> **Usage Rules**: See [README.md](README.md) — always ask user for `service` and `env` tags before querying.

---

## Cases

### `search_datadog_cases`

Search cases by title, status, or tags.

**Required permissions**: `Cases`

**Example prompts**:
- Show all open cases related to the checkout service
- Find cases assigned to the platform team

### `get_datadog_case`

Get full case details including timeline and comments.

**Required permissions**: `Cases`

### `create_datadog_case`

Create a new case.

**Required permissions**: `Cases`

**Example prompts**:
- Create a case for the database latency incident
- Open a case to track the API error budget burn

### `update_datadog_case`

Update case fields (status, priority, assignee).

**Required permissions**: `Cases`

### `add_comment_to_datadog_case`

Add a comment to an existing case.

**Required permissions**: `Cases`

### `link_jira_issue_to_datadog_case`

Link a Jira issue to a Datadog case.

**Required permissions**: `Cases`

### `list_datadog_case_projects`

List available case projects.

**Required permissions**: `Cases`

### `get_datadog_case_project`

Get project details and configuration.

**Required permissions**: `Cases`

---

## Users

### `search_datadog_users`

Search Datadog users by name, email, or role.

**Required permissions**: `Users`

**Example prompts**:
- Find users in the SRE team
- List all admin users in the organization
