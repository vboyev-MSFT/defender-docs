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

## Configure Microsoft Entra ID Protection

Microsoft Defender XDR can also ingest and include signals from Microsoft Entra ID Protection, which evaluates risk data from billions of sign-in attempts and evaluates the risk of each sign-in to your environment. Microsoft Entra ID Protection data is used by Microsoft Entra ID to allow or prevent account access, depending on how Conditional Access policies are configured.

Configure Microsoft Entra ID Protection to enhance your security posture and add Microsoft Entra signals to your unified security operations. For more information, see [Configure your Microsoft Entra ID Protection policies](/entra/id-protection/how-to-deploy-identity-protection).

## Deploy Microsoft Defender for Cloud

Complete deploying Microsoft Defender XDR tools by deploying Microsoft Defender for Cloud. Microsoft Defender for Cloud provides a unified security management experience for your cloud resources, and can also send signals to Microsoft Defender XDR. For example, you might want to start by connecting your Azure subscriptions to Microsoft Defender for Cloud, and then move on to other cloud environments.

For more information, see [Connect your Azure subscriptions](/azure/defender-for-cloud/connect-azure-subscription).

## Architect your workspace and onboard to Microsoft Sentinel

The first step in using Microsoft Sentinel is to create a Log Analytics workspace, if you don't have one already. A single Log Analytics workspace might be sufficient for many environments, but many organizations create multiple workspaces to optimize costs and better meet different business requirements. Microsoft's unified security operations platform supports only a single workspace.

1. Create a Security resource group for governance purposes, which allows you to isolate Microsoft Sentinel resources and role-based access to the collection.
1. Create a Log Analytics workspace in the Security resource group and onboard Microsoft Sentinel into it.

For more information, see [Onboard Microsoft Sentinel](/azure/sentinel/quickstart-onboard).

## Configure roles and permissions

To comply with Zero Trust, we recommend that you configure Azure RBAC based on the resources that are allowed to your users instead of providing them with access to the entire Microsoft Sentinel environment.

For more information, see [Grant a user access - Portal](/azure/role-based-access-control/quickstart-assign-role-user-portal) and [Plan roles and permissions](overview-plan.md#plan-roles-and-permissions).

## Onboard to the unified security operations platform

When you onboard Microsoft Sentinel to the Defender portal, you unify capabilities with Microsoft Defender XDR like incident management and advanced hunting. Reduce tool switching and build a more context-focused investigation that expedites incident response and stops breaches faster.

For more information, see [Connect Microsoft Sentinel to Microsoft Defender](../defender-xdr/microsoft-sentinel-onboard.md).

## Post-deployment tasks

After completing the full unified security operations platform deployment, you can start using the platform to monitor and respond to security incidents. Here are some tasks to start with:

## Configure Microsoft Sentinel content

Based on the [data sources you selected](overview-plan.md#prioritize-data-connectors) when planning your deployment, install Microsoft Sentinel solutions and configure your data connectors. 

Microsoft Sentinel provides a wide range of built-in solutions and data connectors, but you can also build custom connectors and set up connectors to ingest CEF or Syslog logs. Many solutions also provide out-of-the-box analytics rule templates that you can use to create scheduled rules to start detecting threats in your environment.

For more information, see:

- [Configure content](/azure/sentinel/configure-content).
- Microsoft Sentinel content hub catalog
- Discover and manage Microsoft Sentinel out-of-the-box content
- Set up free data sources



Enable health and auditing /azure/sentinel/enable-monitoring?tabs=azure-portal
Configure content /azure/sentinel/configure-content
Enable User and Entity Behavior Analytics (UEBA)	Enable and use the UEBA feature to streamline the analysis process. /azure/sentinel/enable-entity-behavior-analytics?tabs=azure
Set up interactive and long-term data retention	Set up interactive and long-term data retention, to make sure your organization retains the data that's important in the long term. /azure/sentinel/configure-data-retention-archive

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

<!--what's our first step after deployment?-->