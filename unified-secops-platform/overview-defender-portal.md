---
title: Microsoft Defender portal overview
description: Learn about the Microsoft Defender portal
search.appverid: met150
ms.service: unified-secops-platform
ms.author: cwatson
author: cwatson-cat
ms.localizationpriority: medium
ms.date: 11/07/2024
audience: ITPro
ms.collection:
- M365-security-compliance
- tier1
- usx-security
ms.topic: conceptual
---

# Defender portal

[Microsoft's unified security SecOps platform](overview-unified-security.md) combines Microsoft security services in the [Microsoft Defender portal](https://security.microsoft.com). The portal provides a single location to monitor, manage, and configure pre-breach and post-breach security 

- **Pre-breach security**: Visualize, monitor, assess, and improve security posture to reduce attack surfaces.
- **Post-breach security**: Continuously monitor, detect, investigate, and respond to real-time and emerging cybersecurity threats.

## Portal services

The Defender portal combines a number of Microsoft security services. 

**Service** | **Details**
--- | ---
**[Microsoft Defender XDR](/defender-xdr/microsoft-365-defender)** | Defender XDR's suite of products protect assets and workloads against security threats.<br/><br/> Defender XDR integrates threat detection, prevention, investigation, and response across multiple resource types, including endpoint devices, identities, email, apps, and OT/IT resources.
**[Microsoft Defender Threat Intelligence](/defender/threat-intelligence/what-is-microsoft-defender-threat-intelligence-defender-ti)** | Defender Threat Intelligence adds additional threat intelligence capabilities to those included in Defender XDR and Microsoft Sentinel.<br/><br/> The Defender Threat Intelligence platform gathers threat intelligence data from multiple sources, to provide a pool data and signals that security teams can use to effectively understand adversary activities, and to analyze and hunt for security threats.  
**[Microsoft Security Exposure Management](/security-exposure-management/microsoft-security-exposure-management)** | Security Exposure Management provides single location for managing organizational security posture. It continuously discovers assets and workloads, and gathers discovered data into a unified view, making it simple to get a snapshot of security posture.<br/><br/>Security Exposure Management adds context to data, so that you can effectively visualize, query, and analyze attack surfaces to remediate organizational risk.
**[Microsoft Defender for Cloud](/defender-xdr/microsoft-365-security-center-defender-cloud)** | Defender for Cloud improves multicloud and on-premises security posture, and protect cloud workloads against security threats.<br/><br/> Defender for Cloud is an Azure service, but it integrates into the Defender portal so that security teams can access Defender for Cloud alerts in the portal, providing a single location for security investigations.
**[Microsoft Defender for IoT](/defender-for-iot/microsoft-defender-iot)** | Defender for IoT integrates into the Defender portal, extending Defender XDR protection to OT/Enteprise IoT environments.

## Accessing the portal

Access to the Defender portal can be controlled with a range of permission systems.

**Role type** | **Details**
--- | ---
[Global Microsoft Entra roles](/defender-xdr/m365d-permissions) | Accounts assigned the following Global Microsoft Entra roles can access Microsoft Defender XDR functionality and data: Global administrator, Security administrator, Security Operator, Global Reader, Security Reader.
[Custom roles](/defender-xdr/custom-roles) | Allow access to specific data, tasks, and features using custom roles. Custom roles are more granular, and can be used together with Entra global roles.
[Unified RBAC](/defender-xdr/manage-rbac) | Unified RBAC provides a single permissions management model for controlling user permissions in the Defender portal, and across services within the portal.

Portal permissions are configured and managed on the Permissions page of the Defender portal.

:::image type="content" source="/defender/media/microsoft-365-defender-portal/defender-portal-permissions.png" alt-text="Screenshot of the permissions page in the Microsoft Defender portal" lightbox="/defender/media/microsoft-365-defender-portal/defender-portal-permissions.png":::

### Microsoft Sentinel permissions

When you connect Microsoft Sentinel to the Defender portal, existing Azure RBAC permissions allow you to work with the Microsoft Sentinel features in the Defender portal for which you have access.  Continue to manage roles and permissions for your Microsoft Sentinel users from the Azure portal. Any Azure RBAC changes are reflected in the Defender portal.



## Working in the portal

When you open the Defender portal, you see the services included in your subscriptions, and settings based on your portal permissions.

:::image type="content" source="/defender/media/microsoft-365-defender-portal/notifications-panel.png" alt-text="Screenshot of the notifications icon in the Microsoft Defender portal." lightbox="/defender/media/microsoft-365-defender-portal/notifications-panel.png":::

<Add new graphic>

**Feature** | **Details**
--- | ---
**Home page** | The Home page provides a summary of security state. Review active threats, resources at risk, and a summary of your all-up security posture. Use the dashboard as an up-to-date snapshot, and drill down to details as needed.
**Portal notifications** | Portal notifications keep you up-to-date about important events and updates. A notification provides information about events, complete or in-progress actions, and relevant warnings and errors.<br/><br/> Notifications are sorted by their generated time in the notification panel, with the most recent ones displayed first. You can scroll through the list of notifications to see older ones.
**Search** | Search across the portal. Results are categorized by sections related to your search terms.<br/><br/> Search also provides results from relevant links in the Microsoft Tech Community portal, relevant documentation in Microsoft Learn, navigation items within the portal, and a link where you can provide feedback. Search history is stored in your browser and is accessible for the next 30 days.


## Exposure management

In **Exposure management**, review the overall state of your security posture, exposure, and risk. 

<Add graphic>

**Feature** | **Details**
--- | ---
**Exposure management overview** | This dashboard provides provides a quick view of devices and cloud resources, including internet-facing devices and critical assets. Learn how well your key security initiatives are doing, drill down into top metrics for high-value vulnerabilities, get exposure levels for different types of resources, and track your progress over time.
**Attack surfaces** | Visualize exposure data with the attack surface map. Explore assets and connection on the map and drill down to focus on specific assets as needed. In the Attack path management dashboard, review potential attack paths across your organizatoin, together with choke points and critical assets in the path. Use attack paths to understand how attackers might move across your organization and compromise critical assets.
**Exposure insights** | Review and explore aggregrated security posture data and insights, across resources and workloads. Assess posture and security readiness for specific security projects (initiatives, ) and track metrics over time for those projects.  Get security recommendations to remediate exposure issues.
**Secure score** | Review posture metrics based on [Microsoft Secure Score](/defender-xdr/microsoft-secure-score). [Compare the differences](../exposure-management/compare-secure-score-security-exposure-management.md) between Secure Score and Security Exposure Management. 
**Data connectors** | Connect third-party products to Security Exposure Management, and request new connectors.


## Investigation and response 

The Defender portal provides a single location for investigating and responding to threats across the enterprise.

<Add graphic>

### Investigate incidents and alerts

**Feature** | **Details**
--- | ---
**Incidents** | An incident is a set of correlated alerts and associated data that make up an attack. On the Incidents dashboard, you can review a list of the latest incidents and prioritize those with high severity. Drill down into a specific incident to get a full attack story, including information about associated alerts, devices, users, investigations, and evidence.
**Alerts** | Alerts are signals that result from threat detection activity across services in the Defender portal. In the Alerts dashboard, review alerts that have been issued by portal services.<br/><br/> The alerts queue disaplays new and in progress alerts from the last seven days, with the most recent alerts at the top of the list. You can filter on alerts to investigate as needed. 

### Hunt for threats

Hunting allows you to proactively inspect security events and data to locate known and potential threats. 

**Feature** | **Details**
--- | ---
**Advanced hunting** | Explore and query up to 30 days of raw data. You can query using a guided query tool, use sample queries, or use KQL to build your own queries
**Custom detection rules** | Create custom detection rules to proactively monitor and respond to events and system states. Use custom detection rules to trigger alerts or automatic response actions.


### Review pending threat remediations

Threat protection features result in remediation actions. Actions might be automated and require or not require approval. Remediation actions might also be manual. Actions that need approval or manual intervention are available in the Action center.

**Feature** | **Details**
--- | ---
**Action center** | Review the list of actions that need attention. Approve or reject actions one at a time, or in bulk. You can review action history to track remediation.
**Submissions** | Submit suspect spam, URLs, email issues and more to Microsoft.

## Partner catalog

The Defender portal has a couple of kinds of partner integration:

- Third-party integrations to help secure users with effective threat protection, detection, investigation, and response in various security fields of endpoints, vulnerability management, email, identities, and cloud apps.
- Professional services where organizations can enhance the detection, investigation, and threat intelligence capabilities of the platform.

## Threat intelligence

In the Defender portal, you can get direct visibility into active and ongoing threat campaigns, and access threat intelligence provided by Defender Threat Intelligence. 

**Feature** | **Details**
--- | ---
**Threat analytics** | Learn what threats are currently relevant in your organization, assess threat severity, drill down into specific threat reports, and identity what actions are needed. Different types of threat analytics reports are available.
**Intel profiles** | Review curated threat intelligence content organized by threat actors, tools,and known vulnerabilities.
**Intel Explorer** | Review threat intelligence, and drill down to search and investigate.
**Intel projects** | Review and create porjects to organize indicators of interest and indicators of compromize from an investigation. A project includes associated artifacts and a detailed history of names, descriptions, collaborators, and monitoring profiles.

## Assets

The Assets page provides a unified view of all your discovered and protected assets, including devices, users, mailboxes, and apps. You can see the total number of assets of each types, and drill down into specific asset details.


**Feature** | **Details**
--- | ---
[**Devices**](/defender-xdr/mto-tenant-devices) | On the Tenants page, review each tenant you have access to. Tenant information includes the number of devices and device types, devices that are highly exposed, and devices that aren't yet onboarded to the Defender portal.<br/><br/> On the Device Inventory page, get an overview of discovered devices in each tenant you have access to. Review devices by type, understand which devices are high risk or critical.<br/><br/> You can group devices logically by adding tags for context, exclude devices you don't want to assess, or start an automated investigation for devices.
**Identities** | On the [Identities (ITDR dashboard)](/defender-for-identity/dashboard), you can get insights and real-time data about identity threat detection and response (ITDR). The dashboard includes a summary of ITDR health, and information about threats such as unauthorized access, account compromise, insider threats, and abnormal activity. Proactively monitor and manage identity-related risks from the dashboard.<br/><br/> If there's a problem with a Defender for Identity workspace, it's raised as an issue on the [Health issues page](/defender-for-identity/health-alerts). Drill down on specific issues to address, suppress, or close as needed.<br/><br/> Tools - TBD


## Microsoft Sentinel

Onboarding Microsoft Sentinel to Defender XDR in the Defender portal creates a unified platofrm that brings together full Microsoft Sentinel and Defender XDR capabilities.

**Feature** | **Details**
--- | ---
[**Search**]() | 
**Threat management** | Visualize and monitor connected data with [workbooks](/azure/sentinel/monitor-your-data?tabs=defender-portal).<br/><br/>[Investigate incidents](/azure/sentinel/investigate-incidents) and [classify alerts with entities](/azure/sentinel/customize-entity-activities?tabs=defender).<br/><br/>Proactively [hunt for threats](/azure/sentinel/hunts) and [use notebooks](/azure/sentinel/hunting?tabs=azure-portal#notebooks-to-power-investigations) to power investigations.<br/><br/> [Integrate threat intelligence](/azure/sentinel/threat-intelligence-integration) into threat detection, and [use the MITRE ATT&CK framework](/azure/sentinel/mitre-coverage) in analytics and incidents.
**Content management** | Use the [Content hub](/azure/sentinel/sentinel-solutions#discover-and-manage-microsoft-sentinel-content) to discover and install out-of-the-box (OOTB) content.<br/><br/> Use [Microsoft Sentinel repositories](/azure/sentinel/ci-cd-custom-content) to connect to external source systems for continuous integration and delivery (CI/CD) rather than manually deploying and updating custom content.<br/><br/>Community - TBD
**Configuration** | [Use data connectors](/azure/sentinel/best-practices-data) to ingest data.<br/><br/>[Create watchlists](/azure/sentinel/watchlists) to correlate and organize data sources.<br/><br/>[Set up analytics rules](/azure/sentinel/threat-detection) to query and analyze collected data.<br/><br/> [Automate](/azure/sentinel/automation/automation#automation-with-the-unified-security-operations-platform) threat responses.<br/><br/> Settings - TBD

## Identities

## Endpoints

## Email and collaboration

## Cloud apps

## Operational technology

## SOC optimization

## Reports

In the portal, you can start with a general security report, and branch into specific reports. Report links are dynamically generated based on  your configuration.

## Learning hub





