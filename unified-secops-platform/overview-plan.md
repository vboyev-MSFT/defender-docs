---
title: Plan for your unified security operations platform deployment | Microsoft Defender
description: Plan to deploy a Microsoft unified security operations platform with the Microsoft Defender portal, Microsoft Sentinel, and other Microsoft Defender services.
author: batamig
ms.author: bagol
ms.service: unified-secops-platform
ms.topic: concept-article #Don't change.
ms.date: 10/28/2024
ms.collection:
- usx-security


#customer intent: As a security administrator, I want to plan my unified security operations platform deployment so that I can access Microsoft Sentinel services together with other Microsoft Defender services in the Microsoft Defender portal.

---

<!-- --------------------------------------

- Use this template with pattern instructions for:

Concept

- Before you sign off or merge:

Remove all comments except the customer intent.

- Feedback:

https://aka.ms/patterns-feedback

-->


# Unified security operations platform planning overview

This article outlines activities for planning a deployment of Microsoft's unified security operations platform for end-to-end security operations (SecOps). Microsoft's unified security operations platform helps you reduce risk, prevent attacks, detect and disrupt cyberthreats in real time, and respond faster with AI-enhanced security capabilities, all from the [Microsoft Defender portal](https://security.microsoft.com).

<!--need to update links so that they stay in the TOC if we're including them-->

## Review service prerequisites

The unified security operations platform pulls Microsoft Sentinel and several Microsoft Defender services together in the Microsoft Defender portal. Make sure to review prerequisites for each of the following services that you'll be using:

- **Microsoft Sentinel**: [Prerequisites to deploy Microsoft Sentinel](/azure/sentinel/prerequisites)
- **Microsoft Defender XDR and Microsoft Defender for Office 365**: [Microsoft Defender XDR prerequisites](/defender-xdr/prerequisites)
- **Microsoft Defender for Identity**: [Microsoft Defender for Identity prerequisites](/defender-for-identity/deploy/prerequisites)
- **Microsoft Defender for Cloud Apps**: [Get started with Microsoft Defender for Cloud Apps](/defender-cloud-apps/get-started)
- **Microsoft Defender for Endpoint**: [Set up Microsoft Defender for Endpoint deployment](/defender-endpoint/production-deployment)

## Design a governence strategy

<!--shared from zt / ops content-->

If your organization has many Azure subscriptions, you might need a way to efficiently manage access, policies, and compliance for those subscriptions, especially when keeping Zero Trust principles in mind. Management groups provide a governance scope for subscriptions. When you organize your subscriptions within management groups, the governance conditions you configure for a management group apply to the subscriptions it contains. For more information, see Organize your resources with management groups.

For example, the Microsoft Sentinel workspace in the following diagram is in the Security subscription under the Platform management group, which is part of the Microsoft Entra ID tenant.

:::image type="content" source="media/overview-plan/sentinel-workspaces.svg" alt-text="Diagram for applying Zero Trust principles for Azure IaaS infrastructure.":::

## Plan your Log Analytics workspace architecture

To use Microsoft Sentinel, the first step is to create your Log Analytics workspaces. A single Log Analytics workspace might be sufficient for many environments, but many organizations create multiple workspaces to optimize costs and better meet different business requirements.

It's a best practice to create separate workspaces for the operational and security data for data ownership and cost management for Microsoft Sentinel. For example, if there’s more than one person administering operational and security roles, your first decision for Zero Trust is whether to create separate workspaces for those roles.

The unified security operations platform, which provides access to Microsoft Sentinel in the Defender portal, supports only a single workspace. <!--isn't this no longer true? if so we need to update in ZT too-->

Design the Log Analytics workspace you want to enable for Microsoft Sentinel. Consider parameters such as:

- Whether you'll use a single tenant or multiple tenants
- Any compliance requirements you have for data collection and storage
- How to control access to Microsoft Sentinel data

Review these articles:

1. [Design workspace architecture](/azure/azure-monitor/logs/workspace-design?toc=%2Fazure%2Fsentinel%2FTOC.json&bc=%2Fazure%2Fsentinel%2Fbreadcrumb%2Ftoc.json)
1. [Review sample workspace designs](/azure/sentinel/sample-workspace-designs)
1. [Prepare for multiple workspaces](/azure/sentinel/prepare-multiple-workspaces) <!--is this relevant?-->

## Prioritize data connectors

Determine which data sources you need and the data size requirements to help you accurately project your deployment's budget and timeline.

You might determine this information during your business use case review, or by evaluating a current SIEM that you already have in place. If you already have a SIEM in place, analyze your data to understand which data sources provide the most value and should be ingested into Microsoft Sentinel.

For more information, see [Prioritize data connectors](/azure/sentinel/prioritize-data-connectors).

## Plan roles and permissions

Use Azure role based access control (RBAC) to create and assign roles within your security operations team to grant appropriate access to services incuded in the Microsoft Sentinel and. The different roles give you fine-grained control over what Microsoft Sentinel users can see and do. Azure roles can be assigned in the workspace directly, or in a subscription or resource group that the workspace belongs to, which Microsoft Sentinel inherits.

For more information, see:

- **Microsoft Defender XDR**:

    - [Manage access to Microsoft Defender XDR with Microsoft Entra global roles](https://learn.microsoft.com/en-us/defender-xdr/m365d-permissions)
    - [Microsoft Defender XDR Unified role-based access control (RBAC)](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac) <!--are these both relevant?-->

- **Microsoft Sentinel**: [Roles and permissions in Microsoft Sentinel](/azure/sentinel/roles)
- **Microsoft Defender for Identity**: [Microsoft Defender for Identity role groups](https://learn.microsoft.com/en-us/defender-for-identity/role-groups)
- **Microsoft Defender for Cloud Apps**: [Configure admin access](https://learn.microsoft.com/en-us/defender-cloud-apps/manage-admins)
- **Microsoft Defender for Endpoint**: [Assign roles and permissions for Microsoft Defender for Endpoint deployment](https://learn.microsoft.com/en-us/defender-endpoint/prepare-deployment)
- **Microsoft Defender for Office 365**: [Microsoft Defender for Office 365 permissions in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-office-365/mdo-portal-permissions)

## Plan costs

Start planning your budget, considering cost implications for each planned scenario. Make sure that your budget covers the cost of data ingestion for both Microsoft Sentinel and Azure Log Analytics, any playbooks that will be deployed, and so on.

For more information, see:

- [Log retention plans in Microsoft Sentinel](/azure/sentinel/log-plans)
- [Plan costs and understand Microsoft Sentinel pricing and billing](/azure/sentinel/billing?tabs=simplified%2Ccommitment-tiers)

## Next step

Deployment overview

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

<!-- Required: Article headline - H1

Identify the product, service, or feature the
article covers.

-->

[Introduce and explain the purpose of the article.]

<!-- Required: Introductory paragraphs (no heading)

Write a brief introduction that can help the user
determine whether the article is relevant for them
and to describe the concept the article covers.

For definitive concepts, it's better to lead with a
sentence in the form, "X is a (type of) Y that does Z."

-->

## Prerequisites

<!--Optional: Prerequisites - H2

If this section is needed, make "Prerequisites" your
first H2 in the article.

Use clear and unambiguous language and use
an unordered list format. 

-->

## [Main idea]

[Describe a main idea.]

<!-- Required: Main ideas - H2

Use one or more H2 sections to describe the main ideas
of the concept.

Follow each H2 heading with a sentence about how
the section contributes to the whole. Then, describe 
the concept's critical features as you define what it is.

-->

## Related content

- [Related article title](link.md)
- [Related article title](link.md)
- [Related article title](link.md)

<!-- Optional: Related content - H2

Consider including a "Related content" H2 section that 
lists links to 1 to 3 articles the user might find helpful.

-->

<!--

Remove all comments except the customer intent
before you sign off or merge to the main branch.

-->