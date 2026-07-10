---
title: 'Operational Standards: Governance (3)'
author: Datadog Support
modified: 2026-07-10T06:47:06.382Z
tags: []
metadata:
  type: Documentation
time:
  live_span: 1h
template_variables: []
---


# Governance

_Governance Workflow_

## 

# Account Compliance Strategy

## Background

Depending on your industry, you are likely under compliance requirements for how your data is managed, secured, audited and accessed. For those reasons Datadog adheres to a variety of common compliance standards. Below we detail which adhere to. If you require something not listed, please contact your Account team.

## Supported Documentation

* [Datadog Trust Site](https://trust.datadoghq.com/)

* [Datadog Security Site](https://www.datadoghq.com/security/?tab=security)

* [PCI Compliance](https://docs.datadoghq.com/data_security/pci_compliance/?tab=logmanagement)

* [Datadog Data Security](https://docs.datadoghq.com/data_security/)

## Recommended Approach

Know what compliance level you need. If you aren’t already familiar with this, consider a different career.

#### _GDPR_

Datadog is compliant with the General Data Protection Regulation (GDPR) which went into effect on May 25, 2018. Datadog has worked to enhance its products, processes, and procedures to meet its obligations as a data processor. For more information about our position on the GDPR, please visit <https://www.datadoghq.com/gdpr/>.

To keep data within the EU region, use the **EU1 Datadog site** for your organization. See [this page](https://docs.datadoghq.com/getting_started/site/#:~:text=https%3A//app.datadoghq.eu) for more information.

#### _HIPAA_

Datadog will sign a Business Associate Agreement (BAA) with customers that transmit protected health information (ePHI) through [Datadog’s HIPAA-eligible services](https://docs.datadoghq.com/logs/explorer/#share-views).

These restrictions are imposed on customers who have signed Datadog’s BAA:

* Users cannot request support through Zendesk Live Chat.

* Users cannot share logs or security signals from the Datadog explorer.

HIPAA-enabled customers do not need to use specific endpoints to submit logs to enforce specific encryptions. The encryptions are enabled on all log submission endpoints. See [this blogpost](https://www.datadoghq.com/blog/hipaa-compliant-log-management/) for more details around HIPAA compliance and Datadog.

#### _FedRamp_

Datadog is currently authorized to operate at the FedRamp Moderate level. This is exclusive to our [GovCloud](https://www.datadoghq.com/blog/monitor-aws-govcloud-datadog/) instance that is hosted in AWS GovCloud.

Requirements to be FedRamp Moderate compliant within Datadog:

* Your Datadog account must be within the Datadog GovCloud instance.

#### _PCI-DSS_

Datadog offers PCI-compliant Log Management and Application Performance Monitoring (APM) within the \*\*US1 site only \*\*so that you can collect all of your logs, whether they are PCI-regulated or not, in one place.

Requirements to be PCI compliant within Datadog:

* Audit Trail must be enabled and remain enabled for PCI DSS compliance. If you haven’t already enabled Audit Trail, it is automatically enabled once the org is configured as PCI-compliant (after following the steps below).

* Your Datadog organization is in the US1 site.

* All logs and/or spans sent to the PCI endpoints using HTTPS only. If you are using the Agent to send logs and/or spans, you should enforce HTTPS transport.

* All your logs and/or spans endpoints need to be changed to the PCI endpoints for the logs and/or spans.

See [Set up a PCI-compliant Datadog organization](https://docs.datadoghq.com/data_security/pci_compliance/?tab=logmanagement#overview) for more details on how to get started.

#### _Protecting Sensitive Data_

Datadog works together with you to reduce data risk by providing you tools to appropriately limit the data you send and securing data during and after its transmission. When building your account compliance strategy, consider and implement the relevant options in Datadog’s [Reducing Data Related Risks documentation](https://docs.datadoghq.com/data_security/).

### ✅ Decision Point

* Reference your [\*\*Engagement Project Plan \*\*](https://docs.google.com/spreadsheets/d/1ok2QB6lyIshN6KPnzRrerfopiERnqt5-lQ9P8ZvLseA/edit?gid=671465123#gid=671465123)to input your decisions and create your strategy.

### ⭕ Action Items

| | |
|-|-|
| **STATUS**| **TASK**|
| Not Started| Determine which compliance your organization currently is adhering to and select the correct Datadog Organization and Region|
| Not Started| Determine if your organization requires PCI-DSS Scanning for Datadog products.|

# Datadog Agent Strategies

## 

# Datadog Update Agent Strategy

### Background

The Datadog Agent follows a regular release schedule, with minor and bug fix versions released approximately every six weeks. Emergency patches may be issued outside of this cycle. Datadog Agent releases adhere to Semantic Versioning (SemVer) standards, ensuring backward compatibility for minor and patch releases. These frequent updates include critical security patches, performance enhancements, and bug fixes, as outlined in the[ Datadog Agent release notes](https://github.com/DataDog/datadog-agent/releases).

Given the frequency of updates, managing upgrades at scale can be challenging, but it’s critical to avoid outdated software, performance degradation, and potential security vulnerabilities. Datadog Agent release numbering follows [SemVer rules](https://semver.org/).

### Supported Documentation

* [Release Notes](https://github.com/DataDog/datadog-agent/releases)

* [Datadog Agent Documentation](https://docs.datadoghq.com/agent/?tab=Linux)

* [Datadog Agent Repository](https://github.com/DataDog/datadog-agent)

* [Upgrade the Datadog Agent Documentation](https://docs.datadoghq.com/agent/upgrade?tab=linux)

* [Best Practices for Seamless Datadog Upgrades](https://blog.psa-dd.io/best-practices-for-seamless-datadog-upgrades-d9fd444f366e)

### Recommended Approach

To ensure consistent performance, security, and compatibility, organizations should adopt a proactive strategy for upgrading Datadog Agents. This approach includes:

1. **Pin Versioning**:

* Pinning the desired Datadog Agent version in your deployment pipelines is crucial to avoid unexpected failures due to untested or incompatible new releases. Pinning ensures that your environments remain stable and consistent by controlling when specific updates are applied.

2. **Regular Upgrade Cadence**:

* Schedule Agent updates with every minor and patch release, or at a minimum, on a monthly basis. Delaying updates can lead to increased risk of security vulnerabilities and missed performance optimizations.

* Ensure that major version upgrades are part of your update plan to leverage new features and enhancements fully. Waiting for major version releases alone is not recommended, as regular updates are essential for maintaining functionality and security.

3. **Leverage Configuration Management Tools**:

* Automate the upgrade process using configuration management tools like **Ansible** or \*\*AWS SSM \*\*or any other tooling solutions to ensure that updates are deployed consistently across environments at scale. This helps maintain control over versioning and limits potential human errors during the upgrade process. Datadog provides sample code to facilitate automated upgrades in their upgrade documentation.

4. **Pre-Upgrade Validation**:

* \[_Commercial Datadog Accounts_\] Before upgrading, use **Datadog Fleet Automation** to validate the current version of the Datadog Agents across your infrastructure. Fleet Automation provides an easy way to ensure that all Agents are running the expected version, making it a reliable reference point before proceeding with the upgrade. This ensures compatibility with your environment and observability needs.

* \[_GovCloud Datadog Accounts_\] Before upgrading, use the **Infrastructure Host list** to validate the current version of the Datadog Agents across your infrastructure. Use the “Group by” section to group hosts by **field:metadata_agent_version** and any other tag that is relevant to your upgrade process (ie. app, team, etc).

* \[_K8s Workloads_\] If there is an issue with a deployment on Kubernetes, the orchestrator view provides additional information on the state of the pods. This includes the Kubernetes events coming from the agent. Note: This data depends on the information collected by the Cluster Agent, so the view may be limited if the Cluster Agent is not responding. ([source](https://blog.psa-dd.io/best-practices-for-seamless-datadog-upgrades-d9fd444f366e#:~:text=If%20there%20is,is%20not%20responding.))

5. **Post-Upgrade Validation**:

* \[_Commercial Datadog Accounts_\] After upgrading, leverage **Datadog Fleet Automation** to confirm that all Datadog Agents have been updated to the desired version. Fleet Automation simplifies the process of verifying the Agent version across your entire infrastructure, ensuring that the upgrade was successful and that all Agents are functioning as expected.

* \[_GovCloud Datadog Accounts_\] After upgrading, use the **Infrastructure Host list** to validate the current version of the Datadog Agents across your infrastructure. Use the “Group by” section to group hosts by **field:metadata_agent_version** and any other tag that is relevant to your upgrade process (ie. app, team, etc).

* \[_K8s Workloads_\] If there is an issue with a deployment on Kubernetes, the orchestrator view provides additional information on the state of the pods. This includes the Kubernetes events coming from the agent. Note: This data depends on the information collected by the Cluster Agent, so the view may be limited if the Cluster Agent is not responding. ([source](https://blog.psa-dd.io/best-practices-for-seamless-datadog-upgrades-d9fd444f366e#:~:text=If%20there%20is,is%20not%20responding.))

6. **Quarterly Major Version Review**:

* Schedule a quarterly review of the current major version of the Datadog Agent to determine if a major upgrade is necessary. This review should coincide with the release cadence of your application and infrastructure updates, ensuring compatibility.

### ✅ Decision Point

* Define your Datadog Agent Upgrade strategy with your determined organization tooling solution for pin version control and the update process

### ⭕ Action Items

| | |
|-|-|
| **STATUS**| **DESCRIPTION**|
| Not Started| Determine your Version Pinning Strategy for Datadog Agents across your organization|
| Not Started| Determine which version of the Datadog agent is desired for your deployment and pin that version in the agent configuration file(s)|
| Not Started| Determine your Datadog Agent Artifact storage mechanism|
| Not Started| Determine your Datadog Agent Upgrade Automation solution|

## 

# Host Agent Secrets Management Strategy

### Background

The Datadog agent allows you to reference configuration values from secret providers like HashiCorp Vault and AWS Secrets Manager. This feature enables you to securely manage sensitive information, such as Datadog API keys and database credentials, from a centralized location. Implementing a secrets management strategy for your agents enhances the security of your business assets and streamlines the centralized governance of credentials used by the Datadog agent.

### Supported Documentation

* [Secret Management](https://docs.datadoghq.com/agent/configuration/secrets-management/?tab=linux)

### Recommended Approach

#### Determine Source of Your Secrets

Start by determining where the Datadog Agent should pull secrets from. We recommend you use a dedicated secrets provider for this purpose, such as AWS Secrets Manager, or HashiCorp Vault.

#### Implement Script to Pull Secrets

Your secrets provider should offer an API that allows you to create a script for extracting secrets. After identifying the necessary API calls to retrieve your desired secret values, you can implement those calls in an executable script, such as a shell or bash script. We recommend incorporating CLI arguments into the script to allow for reuse and customization across multiple agents in your environment.

Here is an example script that retrieves secrets from AWS Secrets Manager for reference:

```
#!/bin/bash

# Check if AWS CLI is installed
if ! command -v aws &> /dev/null
then
    echo '{"error": "AWS CLI is not installed. Please install it to continue."}'
    exit 1
fi

# Check if a secret name is provided
if [ -z "$1" ]; then
    echo '{"error": "Usage: ./get-secret.sh <secret-name>"}'
    exit 1
fi

# Assign the first argument to the secret name variable
SECRET_NAME=$1

# Retrieve the secret value from AWS Secrets Manager
SECRET_OUTPUT=$(aws secretsmanager get-secret-value --secret-id "$SECRET_NAME" --query 'SecretString' --output json)

# Check if the secret retrieval was successful
if [ $? -ne 0 ]; then
    echo "{\"error\": \"Failed to retrieve secret: $SECRET_NAME\"}"
    exit 1
fi

# Output the secret value in JSON format
echo "$SECRET_OUTPUT"
```

#### Configure Secret Polling For Agent

After installing a script that the Datadog agent can use to retrieve secrets, the next step is to configure both the Datadog agent and the host to invoke the script with the appropriate command-line arguments.

First, ensure that your host has the necessary credentials to access the secrets. These credentials should be securely stored in an encrypted location, such as a restricted-access file. Make sure that the Datadog agent user has permission to read this file.

Then, update the base agent configuration file (found at `<DD_HOME>/datadog.yaml`) with the following attributes:

```
secret_backend_command: /path/to/my-secrets-helper.sh
secret_backend_arguments:
 - my-secret1-key
 - my-secret2-key
```

See our [base agent configuration template](https://github.com/DataDog/datadog-agent/blob/main/pkg/config/config_template.yaml#L827) for more information about secrets backend configuration options.

#### Reference Secrets In Configuration

With your secrets backend configured, the final step is to reference secret values in your configuration. This is done using the `ENC\['secret-key'\]` annotation.

Below is an example of how this might look when configuring a database integration for the agent:

```
init_config:
instances:
  - host: my-db.company.com
    username: 'ENC["my-db-username"]'
    password: 'ENC["my-db-password"]'
  - host: my-db2.company.com
    username: 'ENC["my-db2-username"]'
```

After referencing your secrets in the configuration, restart the agent to apply the changes.

### ✅ Decision Point

### ⭕ Action Items

| | |
|-|-|
| **STATUS**| **TASK**|
| Not Started| Determine source of your secrets|
| Not Started| Implement script to pull secrets|
| Not Started| Configure secret polling for agent|
| Not Started| Reference Secrets in Configuration|

# Tagging Strategy

## Tagging Standards Strategy

![][img-0.5115855970718434]

### Background

Tagging is Datadog’s implementation of [metadata](https://en.wikipedia.org/wiki/Metadata), similar to AWS’s tags and GCP’s labels. [Tags](https://docs.datadoghq.com/getting_started/tagging/) ensure that your telemetry can be queried, aggregated, and correlated efficiently and effectively. Having a rich, consistent, and accurate tagging strategy across your whole organization is essential to get the most out of Datadog.

If your company does not have a company wide tagging strategy yet, Datadog strongly recommends creating one.

### Supported Documentation

* [Getting Started with Tags](https://docs.datadoghq.com/getting_started/tagging/)

* [Unified Service Tagging](https://docs.datadoghq.com/getting_started/tagging/unified_service_tagging)

* [Best Practices for Tagging Your Infrastructure and Applications | Datadog](https://www.datadoghq.com/blog/tagging-best-practices/)

### Formatting

Tags are converted to lowercase. Therefore, CamelCase tags are not recommended. Authentication (crawler) based integrations convert camelcase tags to underscores, for example TestTag –> test_tag. Underscores are preferred over hyphens for consistency.

### Recommended Approach

#### _Initiating an Effective Tagging Strategy_

#### 1. Understanding Scopes and Dimensions

_Scopes_ refer to the context in which a tag applies, such as environments or services, while _Dimensions_ provide specific attributes that describe an object within that scope.

* **Global Scope**: Tags like env (environment) apply universally across all resources.

* **Service-Specific Scope**: Tags like service provide context specific to application services.

* **Location Scope**: Tags that specify where resources are located, such as region or datacenter.

#### 2. Key Tagging Categories

Based on Datadog's Unified Service Tagging (UST) approach, here are the recommended tagging categories:

| | | |
|-|-|-|
| **TAGGING CATEGORY**| **RECOMMENDED KEY VALUE(S)**| |
| **Infrastructure**| Environment| env: (e.g., dev, prod, qa|
| Location| region: (e.g., us-west-1)datacenter: (e.g., us1.prod)availability-zone: (e.g., us-west-1a)| |
| Specifications| os: (e.g., linux, windows)instance-type: (auto-inferred)| |
| Ownership| cost_center: (e.g., sales-001)business_unit: (e.g., support)| |
| Team| team: (e.g., dev-team, ops-team)| |
| **Service (APM)**| Unified Service Tags| service: (e.g., payment-gateway)env: (e.g., prod)version: (e.g., v1.0)|
| Ownership| support_team: (e.g., support-team)business_unit: (e.g., finance)| |
| Function| function: (e.g., webserver, middleware)| |
| Custom Span Tags| For added granularity in tracing, implement custom span tags as needed| |

#### 3. Implementation of Tags

* **Automatic Inheritance**: Leverage tags from cloud providers and integrations automatically collected by Datadog (see[ Unified Service Tagging](https://docs.datadoghq.com/getting_started/tagging/unified_service_tagging)).

* **Manual Configuration**: For integrations without inherited tags, implement tags via configuration files (e.g., datadog.yaml).

#### 4. Log Tags

Ensure logs include necessary tags:

* service: (e.g., web-store)

* source: (e.g., nginx)

#### 5. Tagging Best Practices

* **Consistency**: Maintain consistent naming conventions for keys and values across all telemetry. Refer to[ tagging best practices](https://www.datadoghq.com/blog/tagging-best-practices/).

* **Documentation**: Document all tags and their purposes, ensuring clarity for all teams.

* **Automation**: Use infrastructure as code (IaC) to enforce tagging policies.

* **Dynamic Alerts**: Configure alerts that utilize tags for efficient routing and context in notifications.

By implementing this tagging strategy, you can effectively organize and manage your observability data in Datadog, providing valuable context for monitoring and troubleshooting across your applications and infrastructure.

#### _Reserved Tags_

Datadog reserved tags are predefined tags that the platform automatically applies to resources based on specific attributes, providing a standardized way to categorize and manage monitoring data. These tags include attributes like service, env, region, and host, which help users filter and aggregate metrics, logs, and traces across their infrastructure. By using reserved tags, organizations can gain quick insights into their system's performance and health, as these tags facilitate easy querying and visualization in dashboards. Additionally, reserved tags enhance alerting capabilities by ensuring that notifications are appropriately routed based on common attributes, streamlining incident response and improving overall observability.

| | | | |
|-|-|-|-|
| [RESERVED TAGS](https://docs.datadoghq.com/getting_started/tagging/#overview)| | | |
| **TAG KEY**| **SAMPLE TAG VALUES**| **DESCRIPTION**| **BUSINESS VALUE**|
| **env**| dev, stage, prod| The environment in which the service or application is running.| Ensures critical telemetry can be easily identified. Essential for enabling appropriate monitoring, and access control.|
| **service**| auth-server,  middleware, api-gateway| Defines the specific service or function being monitored. Should be descriptive, concise and easily understandable.| Important for tracking performance and availability of distinct services, ensuring targeted alerts and diagnostics.|
| **version**| 2.1.3, v1.0, 06142ee, etc…| Specifies the version of the application or service being deployed. Can include semantic versioning or specific commit hashes.| Essential for tracking changes, identifying issues related to specific versions, and ensuring compatibility and compliance with release management practices.|
| **source**| python, cisco, nginx| Ensures logs get routed to their appropriate pipelines to be parsed and processed.| Allows logs to be logically grouped based on their underlying technology and logger. Makes log processing more efficient.|
| **host**| [fqdn.domain.com](http://fqdn.domain.com)| Where applicable, identifies where telemetry is shipping from. Usually automatically inferred, can be set.| Allows telemetry to be filtered by what infrastructure it is shipped from|
| **device**| c:, d:, eth0| Where applicable, identifies disk drives or network devices for relevant telemetry| Crucial dimension for storage and network telemetry.|

#### _Integration Tags_

Certain integrations, like those for AWS, Azure, or GCP, come with built-in tags that are automatically applied to relevant resources. For example, the AWS integration provides tags such as region, availability-zone, and account-id. This feature eliminates the need to manually assign specific tags to resources that are discovered automatically through these integrations.

#### _Recommended Tags_

The recommended tags for Datadog provide a structured approach to organizing and managing monitoring data across services and applications. Key tags include **team**, which identifies the responsible group (e.g., integrations, SRE, DevOps) and facilitates accountability and communication; **framework**, which names the software being used (e.g., Apache, Tomcat) and aids in technology stack insights; and **role**, describing the function of a service (e.g., web, app, cache) to enhance understanding of system dependencies. Other important tags include **tier**, indicating the criticality of the service for prioritizing monitoring efforts, and **backup**, which classifies data protection strategies (e.g., bronze, silver, gold) to ensure business continuity. Tags like **platform**, **product**, and **network** help clarify infrastructure dependencies, business domains, and network segments, while **compliance** and **datatype** tags ensure adherence to regulatory requirements and data protection standards. Finally, the **datacenter** tag specifies the physical location of services, supporting disaster recovery planning and compliance with data residency regulations. Overall, these tags enhance observability, streamline incident management, and align monitoring efforts with business objectives.

| | | | |
|-|-|-|-|
| **RECOMMENDED TAGS**| | | |
| **TAG KEY (PRIORITY)**| **SAMPLE TAG VALUES**| **DESCRIPTION**| **BUSINESS VALUE**|
| **team (critical)**| integrations, sre, devops| Identifies the team responsible for the service or application. Examples include integrations, site reliability engineering (SRE), and DevOps teams.| Helps in assigning responsibility, facilitating communication, and streamlining incident response and resolution processes.|
| **runtime (high)**| apache, tomcat, weblogic, etc…| Names the application or software being used. Common examples are web servers and application servers like Apache, Tomcat, and WebLogic.| Provides insight into the technology stack, aiding in configuration management, compatibility checks, and resource allocation.|
| **Journey (high)**| login, checkout, browsing, registration, file_upload, password_reset, order_tracking| Tracks key user journeys across various processes, such as logging in, browsing products, completing checkout, uploading files, resetting passwords, and tracking orders.| Ensures high reliability and performance of critical user flows, improving user experience, reducing churn, and driving revenue by minimizing disruptions.|
| **role (high)**| app, web, cache, worker, leader| Indicates the role of a host or service within a larger system. This tag is useful for distinguishing key components in a distributed system, where each component has a specific responsibility.| Helps teams quickly isolate issues, optimize performance, and maintain system reliability in complex distributed systems.|
| **tier (medium)**| 1, 2, 3,4| Indicates the criticality or priority level of the service. Tier 1 typically represents the most critical services, while higher numbers indicate lower criticality.| Essential for prioritizing monitoring efforts, resource allocation, and incident management based on the criticality of the service.|
| **backup (medium)**| bronze, silver, gold| Classifies the backup and recovery strategy for the service. Bronze, Silver, and Gold often represent increasing levels of backup frequency and retention.| Important for ensuring data protection and business continuity, helping to manage risk and meet recovery time objectives (RTO) and recovery point objectives (RPO).|
| **platform (medium)**| middleware, ecosystem, common platform, etc…| Specifies the underlying platform or ecosystem on which the service operates. Examples include middleware solutions, broader technology ecosystems, or shared platforms.| Critical for understanding the infrastructure dependencies, facilitating integration, and ensuring compatibility and standardization across services.|
| **application (high)**| store-platform, payments, ads, etc.| Identifies how services and resources are grouped together into a larger business workload.Represents the name of the application defined internally by the customer. This could include derivative applications that are part of a larger platform.| Allows grouping, organizing, and filtering of resources relating to a large business application, such as microservices, hosts, and containers. This tag enables effective monitoring, performance analysis, and alignment of applications compared with business goals.|
| **product (medium)**| crm, cms, etc.| Identifies the business product or application domain. Examples include customer relationship management (CRM) systems and content management systems (CMS).| Helps in aligning monitoring and optimization efforts with business objectives and ensuring the performance of key business applications.|
| **network (medium)**| dmz, internal, external, etc…| Describes the network segment where the service is running. DMZ (demilitarized zone), internal, and external networks are common examples.| Important for understanding network security considerations, traffic patterns, and potential vulnerabilities, enabling appropriate security measures and monitoring.|
| **compliance (medium)**| pci-dss, non-pci, sox, fedramp, gdpr, hipaa, etc…| Specifies the compliance standards or regulations applicable to the service. Examples include PCI-DSS (Payment Card Industry Data Security Standard), SOX (Sarbanes-Oxley Act), FedRAMP (Federal Risk and Authorization Management Program), GDPR (General Data Protection Regulation), and HIPAA (Health Insurance Portability and Accountability Act).| Essential for ensuring adherence to regulatory requirements, managing legal and financial risks, and maintaining customer trust and business reputation.|
| **datatype (medium)**| financial, phii, pii,| Identifies the type of data handled by the service. Examples include financial data, PHI (protected health information), and PII (personally identifiable information).| Critical for data classification, implementing appropriate security controls, and ensuring compliance with data protection regulations and best practices.|
| **datacenter (medium)**| fdc, mdc, wdc, etc…| Specifies the physical data center location where the service or application is hosted. Examples include FDC (Primary Data Center), MDC (Main Data Center), and WDC (West Data Center).| Important for understanding the geographical and physical hosting environment, enabling effective disaster recovery planning, latency management, and compliance with data residency regulations.|

### ✅ Decision Point

* Reference your [\*\*Engagement Project Plan \*\*](https://docs.google.com/spreadsheets/d/1ok2QB6lyIshN6KPnzRrerfopiERnqt5-lQ9P8ZvLseA/edit?gid=671465123#gid=671465123)to input your decisions and create your strategy.

### ⭕ Action Items

| | |
|-|-|
| **STATUS**| **TASK**|
| Not Started| Define the Tagging Standards Strategy for all entities within your organization|

## 

# Tagging Governance Strategy

### Background

Tagging governance is the management and control of your tagging. It usually falls within a company wide metadata or data governance strategy, but often time using Datadog is the first time a company has to build one. This includes policies, catalogs, enforcement, personnel and auditing of tagging implementation.

### Supported Documentation

* [Resource Catalog](https://docs.datadoghq.com/infrastructure/resource_catalog/)

* [Resource Catalog Blog](https://www.datadoghq.com/blog/datadog-resource-catalog/)

### Recommended Approach

#### _Governance Principles_

The following principles are important to keep in mind while developing the tagging strategy:

* **Standardization**: Establish standardized naming conventions and tagging structures to facilitate uniformity across environments.

* **Accountability**: Assign ownership and responsibilities for tags to specific teams or individuals to ensure proper management and adherence to governance practices.

* **Automation**: Leverage automation tools to enforce tagging policies, ensuring that all resources are tagged upon creation.

* **Compliance**: Ensure that tagging strategies align with organizational policies and regulatory requirements.

#### _Tagging Standards Overview_

When developing tagging standards that include key tags and their intended usage, prioritize the following categories:

* **Environment**: env (e.g., dev, prod, qa)

* **Location**: region, datacenter

* **Ownership**: cost_center, business_unit, team

* **Service Specific**: service, role, version

#### _Cloud Provider Methodologies_

Below are considerations for tagging implementation across the three major cloud providers - AWS, Azure, and GCP.

##### AWS Tagging Governance

_AWS Tagging Policies:_ AWS provides the Tag Editor, enabling users to define tagging policies across AWS resources. Administrators can enforce rules to ensure that required tags are applied to resources upon creation.

* **Resource Groups**: Use AWS Resource Groups to organize resources based on tags, facilitating management and reporting.

* **AWS Organizations**: Implement service control policies (SCPs) to enforce tagging standards across multiple accounts within an organization.

* **Cost Allocation Tags**: Use cost allocation tags to track costs associated with different departments or projects.

_Example Implementation:_

* Create an AWS CloudFormation template that includes required tags to ensure compliance upon resource creation.

* Use AWS Config to monitor compliance with tagging standards and notify teams of any non-compliant resources.

##### GCP Tagging Governance

_GCP Resource Tagging:_ Google Cloud provides labels that allow for organizing and categorizing resources. Labels can be defined at the project level, enabling consistent application across all resources.

* **Labeling Policies**: Establish organizational policies to enforce the use of specific labels for billing and management purposes.

* **IAM Roles**: Utilize Identity and Access Management (IAM) roles to restrict or allow modifications to labels based on user permissions.

_Example Implementation:_

* Use Google Cloud Deployment Manager to enforce label requirements in resource configurations.

* Implement monitoring solutions (e.g., Stackdriver) to track compliance with labeling policies and generate alerts for non-compliance.

##### Azure Tagging Governance

_Azure Tagging Best Practices:_ Azure allows users to apply tags to resources, resource groups, and subscriptions. Azure Policy can be leveraged to enforce tag requirements.

* **Azure Policy**: Use Azure Policy to create policies that enforce tagging requirements, such as ensuring specific tags are present on all new resources.

* **Management Groups**: Organize resources under management groups to apply tag policies uniformly across multiple subscriptions.

_Example Implementation:_

* Create an Azure Policy definition to require specific tags for all resources in a subscription.

* Utilize Azure Monitor to report on resource compliance with tagging policies, enabling teams to remediate non-compliant resources.

#### _Implementation Steps_

1. **Define Tagging Standards:** Establish clear tagging standards and communicate them across teams.

2. **Automate Tagging**: Use automation tools (CloudFormation, Deployment Manager, Azure Policy) to enforce tagging at the resource creation stage.

3. **Monitor Compliance**: Implement monitoring tools to continuously check for compliance with tagging standards and generate reports.

4. **Review and Iterate**: Regularly review tagging policies and governance strategies, adapting them as necessary to meet changing organizational needs.

#### _Documentation and Training_

* **Documentation**: Create comprehensive documentation outlining tagging standards, governance policies, and compliance monitoring processes.

* **Training**: Conduct training sessions for teams to ensure they understand the importance of tagging governance and how to apply it effectively.

#### _Auditing_

There are multiple ways to check how well your tagging policies have been implemented. At the time of writing this, Resource Catalog is in beta for doing this work. There are also individual views that allow you to check for essential tags:

#### Tagging Review Dashboard

[Tagging review dashboard in demo](https://app.datadoghq.com/dashboard/iyk-6e3-y5w/implementation-services---tagging-review-v2?fromUser=false&refresh_mode=sliding&from_ts=1727113463078&to_ts=1727117063078&live=true)

[This is the link in Github](https://github.com/datadog-expert-services/customer-assets/blob/main/tools/deployment/templates/dashboards/DD_Services-TaggingReview_v2.json)

#### _Conclusion_

By implementing a robust Tagging Governance Strategy that draws from the methodologies of major cloud providers, organizations can ensure effective resource management, compliance with standards, and enhanced observability across their cloud environments. This strategic approach not only streamlines operations but also fosters a culture of accountability and continuous improvement.

### 

### ✅ Decision Point

* Define your Governance Strategy that your Organization will be adopting to enforce your Tagging Standards Strategy defined in the [Tagging Standards Strategy](https://docs.google.com/document/d/1HhJSpluTu6ivgHs0TlptjuuLKhQTUJOX74vL9sja_us/edit#heading=h.4p1aezj557c9) Section.

### ⭕ Action Items

| | |
|-|-|
| **STATUS**| **TASK**|
| Not Started| Define your Governance Strategy that your Organization will be adopting to enforce your Tagging Standards Strategy defined in the [Tagging Standards Strategy](https://docs.google.com/document/d/1HhJSpluTu6ivgHs0TlptjuuLKhQTUJOX74vL9sja_us/edit#heading=h.4p1aezj557c9) Section based on your Maturity|



[img-0.5115855970718434]:
./assets/governance-agent-deployment-diagram.png