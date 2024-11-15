---
title: Microsoft Defender portal overview
description: Learn about the Microsoft services and features available in the Microsoft Defender portal.
search.appverid: met150
ms.service: unified-secops-platform
ms.author: cwatson
author: cwatson-cat
ms.localizationpriority: medium
ms.date: 11/14/2024
audience: ITPro
ms.collection:
- M365-security-compliance
- tier1
- usx-security
ms.topic: conceptual
---

# Microsoft Defender portal

[Microsoft's unified security SecOps platform](overview-unified-security.md) combines Microsoft security services in the [Microsoft Defender portal](https://security.microsoft.com).

The portal provides a single location to monitor, manage, and configure pre-breach and post-breach security across on-premises and multicloud assets.

- **Pre-breach security**: Proactively visualize, assess, remediate, and monitor organizational security posture to reduce attack surfaces.
- **Post-breach security**: Continuously monitor, detect, investigate, and respond to real-time and emerging cybersecurity threats against organizational assets.


:::image type="content" source="media/overview-defender-portal/defender-portal.png" alt-text="Screenshot of Microsoft Defender portal landing page" lightbox="media/overview-defender-portal/defender-portal.png":::


## Portal services

The Defender portal combines a number of Microsoft security services. 

**Service** | **Details**
--- | ---
**Microsoft Defender XDR**<br/><br/> Detect and respond to cybersecurity threats.| Stop cybersecurity threats.<br/><br/> [Defender XDR's suite of services](/defender-xdr/microsoft-365-defender) provides unified protection across endpoints and devices, identities, email, apps, and OT/IoT assets.<br/><br/> Monitor, collect, correlate, and analyze threat data. Investigate and manage threat alerts and incidents.<br/><br/>Respond to threats, and automatically disrupt attacks.
**Microsoft Defender Threat Intelligence**<br/><br/> Integrate threat intelligence into SOC operations. | The [Defender Threat Intelligence](/defender/threat-intelligence/what-is-microsoft-defender-threat-intelligence-defender-ti) platform extends threat intelligence capabilities included in Defender XDR and Microsoft Sentinel.<br/><br/> Gather data from multiple sources to provide a pool of threat intelligence data and signals.<br/><br/> Security teams use data and signals to understand adversary activities, analyze attacks, and hunt for security threats.  
**Microsoft Security Exposure Management**<br/><br/> Proactively reduce security risk.| Use [Security Exposure Management](/security-exposure-management/microsoft-security-exposure-management)to reduce attack surfaces.<br/><br/> Continuously discover assets and get a unified view of security posture.<br/><br/>Add context to gathered data. Visualize, query, and analyze, and remediate attack surfaces to reduce organizational risk.
**Microsoft Defender for Cloud**<br/><br/> Protect cloud workloads. | [Defender for Cloud](/defender-xdr/microsoft-365-security-center-defender-cloud) improves multicloud and on-premises security posture, and protects cloud workloads against security threats.<br/><br/> Defender for Cloud in the Azure portal, integrates into the Defender portal for a unified view of security alerts, providing a single location for investigations.
**Microsoft Defender for IoT**<br/><br/> Protect OT/IoT assets | [Defender for IoT](/defender-for-iot/microsoft-defender-iot) integrates into the Defender portal, extending Defender XDR protection to OT/Enteprise IoT environments.

## Accessing the portal

In the **Permissions** page, control access to the Defender portal. 

Portal access can use a variety of permission methods.


**Methods** | **Details**
--- | ---
[Global Microsoft Entra roles](/defender-xdr/m365d-permissions) | Accounts assigned the following Global Microsoft Entra roles can access Microsoft Defender XDR functionality and data: Global administrator, Security administrator, Security Operator, Global Reader, Security Reader.
[Custom roles](/defender-xdr/custom-roles) | Allow access to specific data, tasks, and features using custom roles. Custom roles are more granular, and can be used together with Entra global roles.
[Unified RBAC](/defender-xdr/manage-rbac) | Unified RBAC provides a single permissions management model for controlling user permissions in the Defender portal, and across services within the portal.


### Microsoft Sentinel permissions

When Microsoft Sentinel is connected to the Defender portal, existing Azure RBAC permissions are used to work with Microsoft Sentinel features in the Defender portal.

- Manage roles and permissions for Microsoft Sentinel users in the Azure portal.
- Any Azure RBAC changes are reflected in the Defender portal.

## Working in the portal

On the **Home** page, your view is determined by the services included in your subscriptions, and access settings based on your portal permissions.

:::image type="content" source="media/overview-defender-portal/home-page.png" alt-text="Screenshot of the Home page in the Microsoft Defender portal" lightbox="media/overview-defender-portal/home-page.png":::

**Feature** | **Details**
--- | ---
**Home page** | The Home page provides a summary of security state. Review active threats, resources at risk, and a summary of your all-up security posture. Use the dashboard as an up-to-date snapshot, and drill down to details as needed.
**Portal notifications** | Portal notifications keep you up-to-date about important events and updates. A notification provides information about events, complete or in-progress actions, and relevant warnings and errors.<br/><br/> Notifications are sorted by their generated time in the notification panel, with the most recent ones displayed first. You can scroll through the list of notifications to see older ones.
**Search** | Search across the portal. Results are categorized by sections related to your search terms.<br/><br/> Search also provides results from relevant links in the Microsoft Tech Community portal, relevant documentation in Microsoft Learn, navigation items within the portal, and a link where you can provide feedback. Search history is stored in your browser and is accessible for the next 30 days.
**Guided tour** | Get a guided tour of managing endpoint security, or managing email and collaboration security.
**What's new** | Links to the [Microsoft Defender XDR blog](https://techcommunity.microsoft.com/category/microsoftsecurityandcompliance/blog/microsoftthreatprotectionblog).
**Community** | Links to the [security discussion spaces](https://techcommunity.microsoft.com/category/MicrosoftSecurityandCompliance) on Tech Community.
**Add cards** | Customize the Home page, including adding a security news feed with the latest security stories.



## Exposure management

In **Exposure management**, review the overall state of your security posture, exposure, and risk. 

:::image type="content" source="media/overview-defender-portal/exposure-management-page.png" alt-text="Screenshot of the Exposure Management page in the Microsoft Defender portal" lightbox="media/overview-defender-portal/exposure-management-page.png":::

**Feature** | **Details**
--- | ---
**Exposure management overview** | This dashboard provides provides a quick view of devices and cloud resources, including internet-facing devices and critical assets. Learn how well your key security initiatives are doing, drill down into top metrics for high-value vulnerabilities, get exposure levels for different types of resources, and track your progress over time.
**Attack surfaces** | Visualize exposure data with the attack surface map. Explore assets and connection on the map and drill down to focus on specific assets as needed. In the Attack path management dashboard, review potential attack paths across your organizatoin, together with choke points and critical assets in the path. Use attack paths to understand how attackers might move across your organization and compromise critical assets.
**Exposure insights** | Review and explore aggregrated security posture data and insights, across resources and workloads. Assess posture and security readiness for specific security projects (initiatives, ) and track metrics over time for those projects.  Get security recommendations to remediate exposure issues.
**Secure score** | Review posture metrics based on [Microsoft Secure Score](/defender-xdr/microsoft-secure-score). [Compare the differences](/exposure-management/compare-secure-score-security-exposure-management) between Secure Score and Security Exposure Management. 
**Data connectors** | Connect third-party products to Security Exposure Management, and request new connectors.

For more information, see [Microsoft Security Exposure Management](/security-exposure-management/microsoft-security-exposure-management).

## Investigation and response 

The **Investigation and response** section provides a single location for investigating incidents and responding to threats across the enterprise.


### Investigate incidents and alerts

Manage and investigate security incidents in a single location and from a single queue in the Defender portal. The Alerts queue shows the current set of alerts from different Microsoft security solutions.

:::image type="content" source="media/overview-defender-portal/incidents-page.png" alt-text="Screenshot of the Incidents page in the Microsoft Defender portal" lightbox="media/overview-defender-portal/incidents-page.png":::

**Feature** | **Details**
--- | ---
**Incidents** | An incident is a set of correlated alerts and associated data that make up an attack. On the Incidents dashboard, you can review a list of the latest incidents and prioritize those with high severity. Drill down into a specific incident to get a full attack story, including information about associated alerts, devices, users, investigations, and evidence.
**Alerts** | Alerts are signals that result from threat detection activity across services in the Defender portal. In the Alerts dashboard, review alerts that have been issued by portal services.<br/><br/> The alerts queue disaplays new and in progress alerts from the last seven days, with the most recent alerts at the top of the list. You can filter on alerts to investigate as needed.

For more information, see [Incidents and alerts in the Microsoft Defender portal](/defender-xdr/incidents-overview).

### Hunt for threats

Hunting allows you to proactively inspect security events and data to locate known and potential threats. 

:::image type="content" source="media/overview-defender-portal/advanced-hunting-page.png" alt-text="Screenshot of the Advanted Hunting page in the Microsoft Defender portal" lightbox="media/overview-defender-portal/advanced-hunting-page.png":::

**Feature** | **Details**
--- | ---
**Advanced hunting** | Explore and query up to 30 days of raw data. You can query using a guided query tool, use sample queries, or use KQL to build your own queries
**Custom detection rules** | Create custom detection rules to proactively monitor and respond to events and system states. Use custom detection rules to trigger alerts or automatic response actions.

For more information, see [Proactively hunt for threats with advanced hunting](/defender-xdr/advanced-hunting-overview) and [Custom detections overview](/defender-xdr/custom-detections-overview).

### Review pending threat remediations

Threat protection features result in remediation actions. Actions might be automated and require or not require approval. Remediation actions might also be manual. Actions that need approval or manual intervention are available in the Action center.

:::image type="content" source="media/overview-defender-portal/action-center-page.png" alt-text="Screenshot of the Action Center page in the Microsoft Defender portal" lightbox="media/overview-defender-portal/action-center-page.png":::

**Feature** | **Details**
--- | ---
**Action center** | Review the list of actions that need attention. Approve or reject actions one at a time, or in bulk. You can review action history to track remediation.
**Submissions** | Submit suspect spam, URLs, email issues and more to Microsoft.

For more information, see [Automated investigation and response](/defender-xdr/m365d-autoir) and [The Action center](/defender-xdr/m365d-action-center).

## Partner catalog

The **Partner catalog** section provides information about Defender partners.

:::image type="content" source="media/overview-defender-portal/technology-partners-page.png" alt-text="Screenshot of the Technology Partners page in the Microsoft Defender portal" lightbox="media/overview-defender-portal/technology-partners-page.png":::

The Defender portal has a couple of kinds of partner integration:

- Third-party integrations to help secure users with effective threat protection, detection, investigation, and response in various security fields of endpoints, vulnerability management, email, identities, and cloud apps.
- Professional services where organizations can enhance the detection, investigation, and threat intelligence capabilities of the platform.

## Threat intelligence

In the **Threat intelligence** section of the portal, get direct visibility into active and ongoing threat campaigns, and access threat intelligence provided by the Defender Threat Intelligence platform.

:::image type="content" source="media/overview-defender-portal/threat-analytics-page.png" alt-text="Screenshot of the Threat Analytics page in the Microsoft Defender portal" lightbox="media/overview-defender-portal/threat-analytics-page.png":::

**Feature** | **Details**
--- | ---
**Threat analytics** | Learn what threats are currently relevant in your organization, assess threat severity, drill down into specific threat reports, and identity what actions are needed. Different types of threat analytics reports are available.
**Intel profiles** | Review curated threat intelligence content organized by threat actors, tools,and known vulnerabilities.
**Intel Explorer** | Review threat intelligence, and drill down to search and investigate.
**Intel projects** | Review and create porjects to organize indicators of interest and indicators of compromize from an investigation. A project includes associated artifacts and a detailed history of names, descriptions, collaborators, and monitoring profiles.

For more information, see [Threat analytics](/defender-xdr/threat-analytics).

## Assets

The **Assets** page provides a unified view of all your discovered and protected assets, including devices, users, mailboxes, and apps. You can see the total number of assets of each types, and drill down into specific asset details.

:::image type="content" source="media/overview-defender-portal/device-inventory-page.png" alt-text="Screenshot of the Device Inventory page in the Microsoft Defender portal" lightbox="media/overview-defender-portal/device-inventory-page.png":::


**Feature** | **Details**
--- | ---
**Devices** |On the Device Inventory page, get an overview of discovered devices in each tenant you have access to. Review devices by type, understand which devices are high risk or critical.<br/><br/> You can group devices logically by adding tags for context, exclude devices you don't want to assess, or start an automated investigation for devices.
**Identities** | Get a summary of user and account inventory.

For more information, see [Device entity page](/defender-xdr/entity-page-device) and [User entity page](/defender-xdr/investigate-users).

## Microsoft Sentinel

Access Microsoft Sentinel capabilities in the Defender portal with an unified platform that brings together full Microsoft Sentinel and Defender XDR capabilities.

:::image type="content" source="media/overview-defender-portal/sentinel-search-page.png" alt-text="Screenshot of the Sentinel Search page in the Microsoft Defender portal" lightbox="media/overview-defender-portal/sentinel-search-page.png":::

**Feature** | **Details**
--- | ---
**Search** | [Search](/azure/sentinel/investigate-large-datasets) across logs, and access past searches.
**Threat management** | Visualize and monitor connected data with [workbooks](/azure/sentinel/monitor-your-data?tabs=defender-portal).<br/><br/>[Investigate incidents](/azure/sentinel/investigate-incidents) and [classify alerts with entities](/azure/sentinel/customize-entity-activities?tabs=defender).<br/><br/>Proactively [hunt for threats](/azure/sentinel/hunts) and [use notebooks](/azure/sentinel/hunting?tabs=azure-portal#notebooks-to-power-investigations) to power investigations.<br/><br/> [Integrate threat intelligence](/azure/sentinel/threat-intelligence-integration) into threat detection, and [use the MITRE ATT&CK framework](/azure/sentinel/mitre-coverage) in analytics and incidents.
**Content management** | Discover and install out-of-the-box (OOTB) content from the [Content hub](/azure/sentinel/sentinel-solutions#discover-and-manage-microsoft-sentinel-content).<br/><br/> Connect to external source systems for continuous integration and delivery (CI/CD) rather than manually deploying and updating custom content by using [Microsoft Sentinel repositories](/azure/sentinel/ci-cd-custom-content).
**Configuration** | Ingest data by using [data connectors](/azure/sentinel/best-practices-data).<br/><br/>[Create watchlists](/azure/sentinel/watchlists) to correlate and organize data sources.<br/><br/>[Set up analytics rules](/azure/sentinel/threat-detection) to query and analyze collected data.<br/><br/> [Automate](/azure/sentinel/automation/automation#automation-with-the-unified-security-operations-platform) threat responses.

For more information, see [Microsoft Sentinel](/azure/sentinel/overview) and [Microsoft Sentinel in the Microsoft Defender portal](/azure/sentinel/microsoft-sentinel-defender-portal).

## Identities

In the **Identities** section of the Defender portal, monitor user and account health, and proactively monitor and manage identity-related risks with Microsoft Defender for Identity.

:::image type="content" source="media/overview-defender-portal/identity-dashboard.png" alt-text="Screenshot of the Identity Dashboard page in the Microsoft Defender portal" lightbox="media/overview-defender-portal/identity-dashboard.png":::

**Feature** | **Details**
--- | ---
**ITDR dashboard** | On the [Identity threat detection and response (ITDR) dashboard](/defender-for-identity/dashboard), you can get insights and real-time data about the security state of users and accounts.<br/><br/> The dashboard includes information about Defender for Identity deployment, information about highly privileged identities, and information about identity-related incidents. Drill down into information about different types of users.<br/><br/> If there's a problem with a Defender for Identity workspace, it's raised as an issue on the [Health issues page](/defender-for-identity/health-alerts).
**Health issues** | Any Defender for Identity global or sensor-based health issues are displayed on this page.
**Tools** | You can access common tools to help you manage Defender for Identity on this page.

For more information, see [Microsoft Defender for Identity](/defender-for-identity).

## Endpoints

In the **Endpoints** section of the portal, monitor and manage asset vulnerabilities with Microsoft Defender Vulnerability Management.

:::image type="content" source="media/overview-defender-portal/vulnerability-management-dashboard.png" alt-text="Screenshot of the Microsoft Defender Vulnerability Management dashboard in the Microsoft Defender portal" lightbox="media/overview-defender-portal/vulnerability-management-dashboard.png":::

**Feature** | **Details**
--- | ---
**Vulnerability management** | Review exposure and vulnerability state in the dashboard. Get recommendations based on vulnerability assessment of devices, and remediate vulnerabilities.<br/><br/> Review your organization's software inventory, including vulnerable components, certificates, and hardware.<br/><br/> Review CVEs and security advisories.<br/><br/> Review the event timeline for vulnerability impacts.<br/><br/> Use security baseline profiles to assess devices against security benchmarks.
**Connected applications** | Get information about the [Microsoft Entra applications connected to Defender for Endpoint](/defender-endpoint/connected-applications).
**API explorer** | [Use the API explorer](/defender-endpoint/api/api-explorer) to construct and run API queries, test, and sent requests for available Defender for Endpoint API endpoints. 

For more information, see [Microsoft Defender Vulnerability Management](/defender-vulnerability-management/defender-vulnerability-management) and [Microsoft Defender for Endpoint](/defender-endpoint/microsoft-defender-endpoint).

## Email and collaboration

In the **Email & collaboration** section, monitor, investigate, and manage security threats and responses to email and collaboration apps with Microsoft Defender for Office 365. 


:::image type="content" source="media/overview-defender-portal/email-investigations.png" alt-text="Screenshot of the Email Investigations page in the Microsoft Defender portal" lightbox="media/overview-defender-portal/email-investigations.png":::

**Feature** | **Details**
--- | ---
**Investigations** | Run and review automated investigations.
**Explorer** | Hunt, investigate, and explore threats to emails and documents. Drill down into specific types of threats, including malware, phishing, and campaigns.
**Review** | Manage quarantined items and restricted senders.
**Campaigns** | Analyze coordinated attacks against your organization.
**Threat tracker** | Review saved and tracked queries, and follow trending campaigns.
**Policies and rules** | Configure and manage security policies to protect against threats, and receive activity alerts.

For more information, see [Microsoft Defender for Office 365](/defender-office-365/mdo-about).

## Cloud apps

In the **Cloud apps** section, review security to minimize risk and exposure to cloud apps using Microsoft Defender for Cloud Apps.

:::image type="content" source="media/overview-defender-portal/cloud-apps-sample-report.png" alt-text="Screenshot of a Cloud Apps sample report in the Microsoft Defender portal" lightbox="media/overview-defender-portal/cloud-apps-sample-report.png":::

**Feature** | **Details**
--- | ---
**Cloud discovery** | Get a overview of cloud app security with discovery reports. Review a sample report, and create new reports.
**Cloud app catalog** | Get an overview of well-known cloud apps and their associated risk. You can sanction and unsanction apps as needed.
**OAuth apps** | Get visibility in OAuth apps. Review apps, and filter settings to drill down.
**Activity log** | Review connected app activity by cloud name, IP address, and related devices.
**Governance log** | Revuew governance tasks.
**Policies** | Configure security policies for cloud apps. 

For more information, see [Microsoft Defender for Cloud Apps](/defender-cloud-apps/what-is-defender-for-cloud-apps).

## SOC optimization

In the **SOC optimization** page, tighten up security controls to close threat coverage gaps, and tighten data ingestion rates  based on high-fidelity and actionable recommendations. SOC optimizations are tailored to your environment and based on your current coverage and threat landscape.

:::image type="content" source="media/overview-defender-portal/soc-optimization-page.png" alt-text="Screenshot of the SOC Optimization page in the Microsoft Defender portal" lightbox="media/overview-defender-portal/soc-optimization-page.png":::

For more information, see [Optimize your security operations](/azure/sentinel/soc-optimization/soc-optimization-access).

## Reports

In the **Reports** page, review security reports across all areas, assets, and workloads.

:::image type="content" source="media/overview-defender-portal/reports-page.png" alt-text="Screenshot of the Reports page in the Microsoft Defender portal" lightbox="media/overview-defender-portal/reports-page.png":::

## Trials

In the **Trials** page, review trial solutions, designed to help you make decisions about upgrades and purchases.

:::image type="content" source="media/overview-defender-portal/trials-page.png" alt-text="Screenshot of the  page iMicrosoft Security Trials page in the Microsoft Defender portal" lightbox="media/overview-defender-portal/trials-page.png":::






