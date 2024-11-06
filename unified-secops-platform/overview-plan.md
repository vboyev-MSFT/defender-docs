---
title: Plan to deploy Microsoft's unified security operations platform | Microsoft Defender
description: Plan to deploy Microsoft's unified security operations platform with the Microsoft Defender portal, Microsoft Sentinel, and other Microsoft Defender services.
author: batamig
ms.author: bagol
ms.service: unified-secops-platform
ms.topic: concept-article #Don't change.
ms.date: 11/06/2024
ms.collection:
- usx-security


#customer intent: As a security administrator, I want to plan my unified security operations platform deployment so that I can access Microsoft Sentinel services together with other Microsoft Defender services in the Microsoft Defender portal.

---

# Unified security operations platform planning overview

This article outlines activities for planning a deployment of Microsoft's unified security operations (SecOps) platform. Microsoft's unified SecOps platform helps you reduce risk, prevent attacks, detect and disrupt cyberthreats in real time, and respond faster with AI-enhanced security capabilities, all from the [Microsoft Defender portal](https://security.microsoft.com).

## Plan your deployment

Microsoft's unified SecOps platform combines services like Microsoft Defender XDR, Microsoft Sentinel, Microsoft Security Exposure Management, and more in the Microsoft Defender portal.

The first step in planning your deployment is to select the services you want to use.

As a basic prerequisite, you'll need both [Microsoft Sentinel](/azure/sentinel/overview) and [Microsoft Defender XDR](../defender-xdr/microsoft-365-defender.md) to monitor and protect both Microsoft and non-Microsoft services and solutions, including both cloud and on-premises resources. <!--is this correct?-->

Deploy any of the following services to add security across your endpoints, identities, email, and applications to provide integrated protection against sophisticated attacks:

|Capability  |Security product  |
|---------|---------|
|Protect against threats posed by email messages, URL links, and Office 365 collaboration tools.     |   [Microsoft Defender for Office 365](/defender-office-365/mdo-about)      |
|Monitor and protect endpoint devices. Monitor, detect, and investigate device breaches, and automatically respond to security threats.    |     [Microsoft Defender for Endpoint](/defender-endpoint/microsoft-defender-endpoint)    |
|Identify assets and software inventory, and assess device posture to find security vulnerabilities.|[Microsoft Defender Vulnerability Management](/defender-vulnerability-management/defender-vulnerability-management)|
|Protect and control access to SaaS cloud apps.|[Microsoft Defender for Cloud Apps](/defender-cloud-apps/what-is-defender-for-cloud-apps)|
|Identify, detect, and investigate Microsoft Entra ID threats.|[Microsoft Defender for Identity](/defender-for-identity/what-is)|
|Improve multicloud and on-premises security posture, and protect cloud workloads against threats.|[Microsoft Defender for Cloud](/azure/defender-for-cloud/defender-for-cloud-introduction)|
|Discover and assess assets, and remediate risk to reduce attack surfaces.|[Microsoft Security Exposure Management](/security-exposure-management/microsoft-security-exposure-management)|
|Identify and protect operational technology (OT) and IT resources by extending Defender XDR protection to OT environments.|[Microsoft Defender for IoT](/defender-for-iot/microsoft-defender-iot)|

<!--what about entra?-->

## Review service prerequisites

Before you deploy Microsoft's unified security operations platform, review the prerequisites for each service you plan to use. The following table lists the services and links to their prerequisites:

|Security service  |Link to prerequisites  |
|---------|---------|
|Microsoft Defender XDR and Microsoft Defender for Office|[Microsoft Defender XDR prerequisites](/defender-xdr/prerequisites) |
|Microsoft Sentinel | [Prerequisites to deploy Microsoft Sentinel](/azure/sentinel/prerequisites)|
|Microsoft Defender for Endpoint     | [Set up Microsoft Defender for Endpoint deployment](/defender-endpoint/production-deployment)        |
|Microsoft Defender Vulnerability Management     |    [Prerequisites & Permissions for Microsoft Defender Vulnerability Management](../defender-vulnerability-management/tvm-prerequisites.md)    |
|Microsoft Defender for Cloud Apps     | [Get started with Microsoft Defender for Cloud Apps](/defender-cloud-apps/get-started)        |
|Microsoft Defender for Identity     | [Microsoft Defender for Identity prerequisites](/defender-for-identity/deploy/prerequisites)        |
|Microsoft Defender for Cloud     | [Start planning multicloud protection](/azure/defender-for-cloud/plan-multicloud-security-get-started) and other articles in the same section.        |
|Microsoft Security Exposure Management     |    [Prerequisites and support](../exposure-management/prerequisites.md)      |
|Microsoft Defender for IoT     |  [Plan your OT monitoring system with Defender for IoT](/azure/defender-for-iot/organizations/best-practices/plan-corporate-monitoring)       |

<!--do we need entra? [Plan an ID Protection deployment](/entra/id-protection/how-to-deploy-identity-protection?form=MG0AV3)-->

<!--we don't need this until mult tenants i think
## Design a governence strategy

<!--shared from zt / ops content

If your organization has many Azure subscriptions, you might need a way to efficiently manage access, policies, and compliance for those subscriptions, especially when keeping Zero Trust principles in mind. Management groups provide a governance scope for subscriptions. When you organize your subscriptions within management groups, the governance conditions you configure for a management group apply to the subscriptions it contains. For more information, see Organize your resources with management groups.

For example, the Microsoft Sentinel workspace in the following diagram is in the Security subscription under the Platform management group, which is part of the Microsoft Entra ID tenant.

:::image type="content" source="media/overview-plan/sentinel-workspaces.svg" alt-text="Diagram for applying Zero Trust principles for Azure IaaS infrastructure.":::
-->

## Plan your Log Analytics workspace architecture

To use Microsoft's unified SecOps platform, you need a Log Analytics workspace enabled for Microsoft Sentinel. A single Log Analytics workspace might be sufficient for many environments, but many organizations create multiple workspaces to optimize costs and better meet different business requirements. Microsoft's unified SecOps platform supports only a single workspace.

Design the Log Analytics workspace you want to enable for Microsoft Sentinel. Consider parameters such as any compliance requirements you have for data collection and storage and how to control access to Microsoft Sentinel data.

For more information, see:

1. [Design workspace architecture](/azure/azure-monitor/logs/workspace-design?toc=%2Fazure%2Fsentinel%2FTOC.json&bc=%2Fazure%2Fsentinel%2Fbreadcrumb%2Ftoc.json)
1. [Review sample workspace designs](/azure/sentinel/sample-workspace-designs)

## Plan Microsoft Sentinel costs and data sources

In addition to the data streaming in from Defender services, Microsoft's unified SecOps platform ingests data from other sources with Microsoft Sentinel.

- Determine which data sources and the data size requirements to help you accurately project your deployment's budget and timeline.

    You might determine this information during your business use case review, or by evaluating a current SIEM that you already have in place. If you already have a SIEM in place, analyze your data to understand which data sources provide the most value and should be ingested into Microsoft Sentinel.

    For more information, see [Prioritize data connectors](/azure/sentinel/prioritize-data-connectors).

- Plan your Microsoft Sentinel budget, considering cost implications for each planned scenario. Make sure that your budget covers the cost of data ingestion for both Microsoft Sentinel and Azure Log Analytics, any playbooks that will be deployed, and so on.  For more information, see:

    - [Log retention plans in Microsoft Sentinel](/azure/sentinel/log-plans)
    - [Plan costs and understand Microsoft Sentinel pricing and billing](/azure/sentinel/billing?tabs=simplified%2Ccommitment-tiers)

## Plan roles and permissions

Use Azure role based access control (RBAC) to create and assign roles within your security operations team to grant appropriate access to services incuded in Microsoft's unified SecOps platform. The different roles give you fine-grained control over what users can see and do. Azure roles can be assigned in the workspace directly, or in a subscription or resource group that the workspace belongs to, which Microsoft Sentinel inherits.

For more information, see:

|Security service  |Link to prerequisites  |
|---------|---------|
|Microsoft Defender XDR and Microsoft Defender for Office| - [Manage access to Microsoft Defender XDR with Microsoft Entra global roles](/defender-xdr/m365d-permissions) <br>- [Microsoft Defender XDR Unified role-based access control (RBAC)](/defender-xdr/manage-rbac)|
|Microsoft Sentinel | [Roles and permissions in Microsoft Sentinel](/azure/sentinel/roles) |
|Microsoft Defender for Office | [Microsoft Defender for Office 365 permissions in the Microsoft Defender portal](/defender-office-365/mdo-portal-permissions) |
|Microsoft Defender for Endpoint     | [Assign roles and permissions for Microsoft Defender for Endpoint deployment](/defender-endpoint/prepare-deployment)      |
|Microsoft Defender Vulnerability Management     | [Relevant permission options](/defender-vulnerability-management/tvm-prerequisites#relevant-permission-options)     |
|Microsoft Defender for Cloud Apps     | [Configure admin access](/defender-cloud-apps/manage-admins)      |
|Microsoft Defender for Identity     |  [Microsoft Defender for Identity role groups](/defender-for-identity/role-groups)      |
|Microsoft Defender for Cloud     |   [User roles and permissions](/azure/defender-for-cloud/permissions)    |
|Microsoft Security Exposure Management     |  [Permissions](../exposure-management/prerequisites.md)    |
|Microsoft Defender for IoT     | [Azure user roles and permissions for Defender for IoT](/azure/defender-for-iot/organizations/roles-azure)       |


## Next step

[Deploy Microsoft's unified security operations platform](overview-deploy.md)

## Related content

For more information, see [Use SIEM and XDR to respond to incidents with Zero Trust](/security/operations/siem-xdr-overview?bc=%2Fsecurity%2Fzero-trust%2Fbreadcrumb%2Ftoc.json&toc=%2Fsecurity%2Fzero-trust%2Ftoc.json&tabs=defender-portal).