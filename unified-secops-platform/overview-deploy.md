---
title: Deploy Microsoft's unified security operations platform | Microsoft Defender
description: Deploy Microsoft's unified security operations platform with the Microsoft Defender portal, Microsoft Sentinel, and other Microsoft Defender services.
author: batamig
ms.author: bagol
ms.service: unified-secops-platform
ms.topic: how-to #Don't change.
ms.date: 10/31/2024
ms.collection:
- usx-security


#customer intent: As a security administrator, I want to deploy Microosft's unified security operations platform so that I can access Microsoft Sentinel services together with other Microsoft Defender services in the Microsoft Defender portal.

---

# Deploy Microsoft's unified security operations platform

Microsoft's unified security operations platform combines the capabilities of Microsoft Defender portal, Microsoft Sentinel, and other Microsoft Defender services. This platform provides a comprehensive view of your organization's security posture and helps you to detect, investigate, and respond to threats across your organization.

## Prerequisites

- Before you deploy Microsoft's unified security operations platform, make sure that you have a plan in place, including a workspace design and an understanding of Microsoft Sentinel costs and billing. 

    For more information, see [Unified security operations platform planning overview](overview-plan.md).

## Pilot and deploy Microsoft Defender services

Microsoft Defender XDR unifies your incident response process by integrating key capabilities across Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Microsoft Defender for Cloud Apps, and Microsoft Defender for Identity. This unified experience adds powerful features you can access in the Microsoft Defender portal.

1. Microsoft Defender XDR automatically turns on when eligible customers with the required permissions visit Microsoft Defender portal. For more information, see [Turn on Microsoft Defender XDR](../defender-xdr/m365d-enable.md).

1. Continue by piloting and deploying Microsoft Defender services. We recommend using the following order:

    1. [Pilot and deploy Microsoft Defender for Identity](../defender-xdr/pilot-deploy-defender-identity.md)
    1. [Pilot and deploy Defender for Office 365](../defender-xdr/pilot-deploy-defender-office-365.md)
    1. [Pilot and deploy Microsoft Defender for Endpoint](../defender-xdr/pilot-deploy-defender-endpoint.md)
    1. [Pilot and deploy Microsoft Defender for Cloud Apps](../defender-xdr/pilot-deploy-defender-cloud-apps.md)

## Enable Microsoft Entra ID Protection

Microsoft Defender XDR also ingests and includes the signals of Microsoft Entra ID Protection. 

Microsoft Entra ID Protection evaluates risk data from billions of sign-in attempts and uses this data to evaluate the risk of each sign-in to your environment. This data is used by Microsoft Entra ID to allow or prevent account access, depending on how Conditional Access policies are configured.

For more information, see [Configure your Microsoft Entra ID Protection policies](/entra/id-protection/how-to-deploy-identity-protection).

## Deploy Microsoft Defender for Cloud

Complete deploying Microsoft Defender XDR tools by deploying Microsoft Defender for Cloud. Microsoft Defender for Cloud provides a unified security management experience for your cloud resources. For example, you might want to start by connecting your Azure subscriptions to Microsoft Defender for Cloud, and then move on to other cloud environments.

For more information, see [Connect your Azure subscriptions](https://learn.microsoft.com/en-us/azure/defender-for-cloud/connect-azure-subscription).

## Architect your workspace

The first step in using Microsoft Sentinel is to create a Log Analytics workspace, if you don't have one already. A single Log Analytics workspace might be sufficient for many environments, but many organizations create multiple workspaces to optimize costs and better meet different business requirements.

It's a best practice to create separate workspaces for the operational and security data for data ownership and cost management for Microsoft Sentinel. For example, if there’s more than one person administering operational and security roles, your first decision for Zero Trust is whether to create separate workspaces for those roles.

The unified security operations platform, which provides access to Microsoft Sentinel in the Defender portal, supports only a single workspace. <!--is this still true?-->

- Create a Security resource group for governance purposes, which allows you to isolate Microsoft Sentinel resources and role-based access to the collection. For more information, see Design a Log Analytics workspace architecture.

- Create a Log Analytics workspace in the Security resource group and onboard Microsoft Sentinel into it. This automatically gives you 31 days of data ingestion up to 10 Gb a day free as part of a free trial.

- Set your Log Analytics Workspace supporting Microsoft Sentinel to 90 day retention at a minimum.

Once you onboard Microsoft Sentinel to a Log Analytics workspace, you get 90 days of data retention at no extra cost, and ensure a 90-day rollover of log data. You'll incur costs for the total amount of data in the workspace after 90 days. You might consider retaining log data for longer based on governmental requirements. For more information, see Create Log Analytics workspaces and Quickstart: Onboard in Microsoft Sentinel.

<!--do we want to include this here?-->

## Configure roles and permissions

To comply with Zero Trust, we recommend that you configure Azure RBAC based on the resources that are allowed to your users instead of providing them with access to the entire Microsoft Sentinel environment.

For more information, see [Grant a user access - Portal](/azure/role-based-access-control/quickstart-assign-role-user-portal) and [Plan roles and permissions](overview-plan.md#plan-roles-and-permissions).

## Onboard to the unified security operations platform

When you onboard Microsoft Sentinel to the Defender portal, you unify capabilities with Microsoft Defender XDR like incident management and advanced hunting. Reduce tool switching and build a more context-focused investigation that expedites incident response and stops breaches faster.

For more information, see [Connect Microsoft Sentinel to Microsoft Defender](../defender-xdr/microsoft-sentinel-onboard.md).

## Post-deployment tasks



### Ingest data sources

Use the following recommendations to get started with installing solutions and configuring data connectors. For more information, see:

Microsoft Sentinel content hub catalog
Discover and manager Microsoft Sentinel out-of-the-box content
Set up free data sources
Start by focus on setting up free data sources to ingest, including:

Azure activity logs: Ingesting Azure activity Logs is critical in enabling Microsoft Sentinel to provide a single-pane of glass view across the environment.

Office 365 audit Logs, including all SharePoint activity, Exchange admin activity, and Teams.

Security alerts, including alerts from Microsoft Defender for Cloud, Microsoft Defender XDR, Microsoft Defender for Office 365, Microsoft Defender for Identity, and Microsoft Defender for Endpoint.

If you haven't onboarded your workspace to the unified security operations platform and are working in the Azure portal, ingesting security alerts into Microsoft Sentinel enables the Azure portal to be the central pane of incident management across the environment. In such cases, incident investigation starts in Microsoft Sentinel and should continue in the Microsoft Defender portal or Defender for Cloud, if deeper analysis is required.

For more information, see Microsoft Defender XDR incidents and Microsoft incident creation rules.

Microsoft Defender for Cloud Apps alerts.

For more information, see Microsoft Sentinel Pricing and Free data sources.

Set up paid data sources
To provide broader monitoring and alerting coverage, focus on adding the Microsoft Entra ID and Microsoft Defender XDR data connectors. There's a charge for ingesting data from these sources.

Make sure to send Microsoft Defender XDR logs to Microsoft Sentinel if any of the following are required:

Onboarding to the unified security operations platform, which provides a single portal for incident management in Microsoft Defender.
Microsoft Sentinel fusion alerts, which correlate data sources from multiple products to detect multi-stage attacks across the environment.
Longer retention than what is offered in Microsoft Defender XDR.
Automation not covered by the built-in remediations offered by Microsoft Defender for Endpoint.
For more information, see:

Integrate Microsoft 365 Defender
Connect data from Microsoft Defender XDR to Microsoft Sentinel
Connect Microsoft Entra data to Microsoft Sentinel
Set up data sources per your environment
This section describes data sources you might want to use, depending on the services and deployment methods used in your environment.

Scenario	Data sources
Azure services	If any of the following services are deployed in Azure, use the following connectors to send these resources' Diagnostic Logs to Microsoft Sentinel:

- Azure Firewall
- Azure Application Gateway
- Keyvault
- Azure Kubernetes Service
- Azure SQL
- Network Security Groups
- Azure-Arc Servers

We recommend that you set up Azure Policy to require that their logs be forwarded to the underlying Log Analytics workspace. For more on information, see Create diagnostic settings at scale using Azure Policy.
Virtual machines	For virtual machines hosted on-premises or in other clouds that require their logs collected, use the following data connectors:

- Windows Security Events using AMA
- Events via Defender for Endpoint (for server)
- Syslog
Network virtual appliances / on-premises sources	For network virtual appliances or other on-premises sources that generate Common Event Format (CEF) or SYSLOG logs, use the following data connectors:

- Syslog via AMA
- Common Event Format (CEF) via AMA

For more information, see Ingest Syslog and CEF messages to Microsoft Sentinel with the Azure Monitor Agent.
When you're done, search in the Microsoft Sentinel Content hub for other devices and software as a service (SaaS) apps that require logs to be sent to Microsoft Sentinel.

For more information, see Discover and manage Microsoft Sentinel out-of-the-box content .

### Configure incident detection and response

After setting up data connectors in Microsoft Sentinel, make sure to enable user entity behavior analytics to identify suspicious behavior that could lead to phishing exploits and eventually attacks such as ransomware. Often, anomaly detection through UEBA is the best method for detecting Zero-day exploits early on.

Using UEBA allows Microsoft Sentinel to build behavioral profiles of your organization's entities across time and peer group to identify anomalous activity. This added utility aids in an expedition of determining if an asset has been compromised. Since it identifies peer group association this can also aid in determining the blast radius of said compromise.

For more information, see Identify threats with entity behavior analytics

Step 3: Enable analytic rules
The brains of Microsoft Sentinel come from the analytic rules. These are rules you set to tell Microsoft Sentinel to alert you to events with a set of conditions that you consider to be important. The out-of-the-box decisions Microsoft Sentinel makes are based on user entity behavioral analytics (UEBA) and on correlations of data across multiple data sources.

When turning on analytic rules for Microsoft Sentinel, prioritize enabling by connected data sources, organizational risk, and MITRE tactic.

Avoid duplicate incidents
If you enabled the Microsoft Defender XDR connector, a bi-directional sync between 365 Defender incidents and Microsoft Sentinel is automatically established.

To avoid creating duplicate incidents for the same alerts, we recommend that you turn off all Microsoft incident creation rules for Microsoft Defender XDR-integrated products, including Defender for Endpoint, Defender for Identity, Defender for Office 365, Defender for Cloud Apps, and Microsoft Entra ID Protection.

For more information, see Microsoft Defender XDR incidents and Microsoft incident creation rules.

Use fusion alerts
By default, Microsoft Sentinel enables the Fusion advanced multistage attack detection analytic rule to automatically identify multistage attacks.

Using anomalous behavior and suspicious activity events observed across the cyber kill chain, Microsoft Sentinel generates incidents that allow you to see the compromise incidents with two or more alert activities in it with a high degree of confidence.

Fusion alert technology correlates broad points of data signals with extended machine learning (ML) analysis to help determine known, unknown, and emerging threats. For example, fusion detection can take the anomaly rule templates and the scheduled queries created for the Ransomware scenario and pair them with alerts from Microsoft Security Suite services, such as:

Microsoft Entra ID Protection
Microsoft Defender for Cloud
Microsoft Defender for IoT
Microsoft Defender XDR
Microsoft Defender for Cloud Apps
Microsoft Defender for Endpoint
Microsoft Defender for Identity
Microsoft Defender for Office 365
Use anomaly rules
Microsoft Sentinel anomaly rules are available out-of-the-box and enabled by default. Anomaly rules are based on machine learning models and UEBA that train on the data in your workspace to flag anomalous behavior across users, hosts, and others.

Often, a phishing attack leads to an execution step such as local or cloud account manipulation/control or malicious script execution. Anomaly rules look exactly for those types of activities, such as:

Anomalous Account Access Removal
Anomalous Account Creation
Anomalous Account Deletion
Anomalous Account Manipulation
Anomalous Code Execution (UEBA)
Anomalous Data Destruction
Anomalous Defensive Mechanism Modification
Anomalous Failed Sign-in
Anomalous Password Reset
Anomalous Privilege Granted
Anomalous Sign-in
Review the anomaly rules and anomaly score threshold for each one. If you're observing false positives for example, consider duplicating the rule and modifying the threshold by following the steps outlined in Tune anomaly rules.

Use the Microsoft Threat Intelligence analytics rule
After reviewing and modifying fusion and anomaly rules, enable the out-of-the-box Microsoft Threat Intelligence analytics rule. Verify that this rule matches your log data with Microsoft-generated threat intelligence. Microsoft has a vast repository of threat intelligence data, and this analytic rule uses a subset of it to generate high fidelity alerts and incidents for SOC (security operations centers) teams to triage.

Conduct a MITRE Att&ck crosswalk
With fusion, anomaly, and threat intelligence analytic rules enabled, conduct a MITRE Att&ck crosswalk to help you decide which remaining analytic rules to enable and to finish implementing a mature XDR (extended detection and response) process. This empowers you to detect and respond throughout the lifecycle of an attack.

The MITRE Att&ck research department created the MITRE method, and it's provided as part of Microsoft Sentinel to ease your implementation. Ensure you have analytic rules that stretch the length and breadth of the attack vectors approach.

Review the MITRE techniques that are covered by your existing active analytic rules.

Select 'Analytic rule templates' and 'Anomaly Rules' in the Simulated dropdown. This shows you where you have the adversary tactic and/or technique covered and where there are available analytic rules you should consider enabling to improve your coverage.

For example, to detect potential phishing attacks, review the Analytic rule templates for the Phishing technique, and prioritize enabling the rules that specifically query the data sources you have onboarded to Microsoft Sentinel.

In general, there are five phases to a human-operated Ransomware attack, and Phishing falls under Initial Access, as shown in the following images:

Defender portal (Preview)
Azure portal
Screenshot of the MITRE ATT&CK dashboard in the unified security operations portal.

Continue through the remaining steps to cover the entire kill chain with appropriate analytic rules:

Initial access
Credential theft
Lateral movement
Persistence
Defense evasion
Exfiltration (this is where ransomware itself is detected)



This article introduces the activities that help you plan your Microsft unified security operations platform deployment.


1. Preparation and Planning
Assess Requirements: Identify the specific security needs and objectives of your organization.
Gather Resources: Ensure you have the necessary licenses, permissions, and access to the Microsoft Defender portal.
Review Documentation: Familiarize yourself with the relevant documentation on Microsoft Learn, such as the An external link was removed to protect your privacy.1.
2. Initial Setup
Create a Microsoft Defender Portal Account: If you don't already have one, create an account and log in to the Microsoft Defender portal.
Configure Basic Settings: Set up your organization's basic security settings and preferences in the portal.
3. Deploy Microsoft Defender Services
Microsoft Defender for Endpoint: Deploy and configure Microsoft Defender for Endpoint to protect your devices.
Microsoft Defender for Office 365: Set up Microsoft Defender for Office 365 to secure your email and collaboration tools.
Microsoft Defender for Identity: Implement Microsoft Defender for Identity to protect your identities and detect threats.
Microsoft Defender for Cloud Apps: Integrate Microsoft Defender for Cloud Apps to secure your cloud applications.
Microsoft Defender XDR: Deploy Microsoft Defender XDR to unify and enhance threat detection and response across all Defender services1.
4. Integrate Microsoft Sentinel
Connect Microsoft Sentinel: Integrate Microsoft Sentinel with the Defender portal to enhance threat detection and response capabilities.
Configure Data Connectors: Set up data connectors to ingest data from various sources into Microsoft Sentinel.
Create and Customize Workbooks: Use workbooks to visualize and analyze security data in Microsoft Sentinel.
5. Advanced Configuration
Set Up Advanced Hunting: Enable advanced hunting capabilities to query and analyze security data across your environment.
Configure Automated Response: Set up automated response actions to quickly mitigate threats.
Implement Security Playbooks: Create and deploy security playbooks to automate common response actions.
6. Monitoring and Maintenance
Continuous Monitoring: Regularly monitor your security operations platform for alerts and incidents.
Update and Patch: Keep your security tools and systems up to date with the latest patches and updates.
Review and Optimize: Periodically review your security configurations and optimize them based on new threats and best practices.
7. Training and Support
Provide Training: Ensure your security team is trained on using the Microsoft Defender portal and its features.
Access Support: Utilize Microsoft support resources and community forums for assistance and troubleshooting.

## Next step
