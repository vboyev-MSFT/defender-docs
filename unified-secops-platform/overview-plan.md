---
title: Plan to deploy Microsoft's unified security operations platform | Microsoft Defender
description: Plan to deploy Microsoft's unified security operations platform with the Microsoft Defender portal, Microsoft Sentinel, and other Microsoft Defender services.
author: batamig
ms.author: bagol
ms.service: unified-secops-platform
ms.topic: concept-article #Don't change.
ms.date: 10/28/2024
ms.collection:
- usx-security


#customer intent: As a security administrator, I want to plan my unified security operations platform deployment so that I can access Microsoft Sentinel services together with other Microsoft Defender services in the Microsoft Defender portal.

---



# Microsoft's unified security operations platform planning overview

This article outlines activities to plan a deployment of Microsoft's security products to Microsoft's unified security operations platform for end-to-end security operations (SecOps). Unify your SecOps on Microsoft's platform to help you reduce risk, prevent attacks, detect and disrupt cyberthreats in real time, and respond faster with AI-enhanced security capabilities, all from the [Microsoft Defender portal](https://security.microsoft.com).

<!--need to update links so that they stay in the TOC if we're including them-->

## Review service prerequisites

The unified security operations platform pulls Microsoft Sentinel and several Microsoft Defender services together in the Microsoft Defender portal. Make sure to review prerequisites for each of the following services that you'll be using:

- **Microsoft Sentinel**: [Prerequisites to deploy Microsoft Sentinel](/azure/sentinel/prerequisites)
- **Microsoft Defender XDR and Microsoft Defender for Office 365**: [Microsoft Defender XDR prerequisites](/defender-xdr/prerequisites)
- **Microsoft Defender for Identity**: [Microsoft Defender for Identity prerequisites](/defender-for-identity/deploy/prerequisites)
- **Microsoft Defender for Cloud Apps**: [Get started with Microsoft Defender for Cloud Apps](/defender-cloud-apps/get-started)
- **Microsoft Defender for Endpoint**: [Set up Microsoft Defender for Endpoint deployment](/defender-endpoint/production-deployment)

Complete your deployment planning by checking prerequisites for both Microsoft Entra ID Protection and Microsoft Defender for Cloud, which are separate from Microsoft Defender XDR and Microsoft Sentinel. For more information, see:

- **Microsoft Entra ID Protection**: [Plan an ID Protection deployment](/entra/id-protection/how-to-deploy-identity-protection?form=MG0AV3)
- **Microsoft Defender for Cloud**: [Start planning multicloud protection](/azure/defender-for-cloud/plan-multicloud-security-get-started) and other articles in the same section.

## Design a governence strategy

<!--shared from zt / ops content-->

If your organization has many Azure subscriptions, you might need a way to efficiently manage access, policies, and compliance for those subscriptions, especially when keeping Zero Trust principles in mind. Management groups provide a governance scope for subscriptions. When you organize your subscriptions within management groups, the governance conditions you configure for a management group apply to the subscriptions it contains. For more information, see Organize your resources with management groups.

For example, the Microsoft Sentinel workspace in the following diagram is in the Security subscription under the Platform management group, which is part of the Microsoft Entra ID tenant.

:::image type="content" source="media/overview-plan/sentinel-workspaces.svg" alt-text="Diagram for applying Zero Trust principles for Azure IaaS infrastructure.":::

## Plan your Log Analytics workspace architecture

To use Microsoft Sentinel, you need a Log Analytics workspace. A single Log Analytics workspace might be sufficient for many environments, but many organizations create multiple workspaces to optimize costs and better meet different business requirements. Microsoft's unified security operations platform supports only a single workspace.

Design the Log Analytics workspace you want to enable for Microsoft Sentinel. Consider parameters such as any compliance requirements you have for data collection and storage and how to control access to Microsoft Sentinel data.

Review these articles:

1. [Design workspace architecture](/azure/azure-monitor/logs/workspace-design?toc=%2Fazure%2Fsentinel%2FTOC.json&bc=%2Fazure%2Fsentinel%2Fbreadcrumb%2Ftoc.json)
1. [Review sample workspace designs](/azure/sentinel/sample-workspace-designs)

## Prioritize data connectors

Determine which data sources you need and the data size requirements to help you accurately project your deployment's budget and timeline.

You might determine this information during your business use case review, or by evaluating a current SIEM that you already have in place. If you already have a SIEM in place, analyze your data to understand which data sources provide the most value and should be ingested into Microsoft Sentinel.

For more information, see [Prioritize data connectors](/azure/sentinel/prioritize-data-connectors).

## Plan roles and permissions

Use Azure role based access control (RBAC) to create and assign roles within your security operations team to grant appropriate access to services incuded in the Microsoft Sentinel and. The different roles give you fine-grained control over what Microsoft Sentinel users can see and do. Azure roles can be assigned in the workspace directly, or in a subscription or resource group that the workspace belongs to, which Microsoft Sentinel inherits.

For more information, see:

- **Microsoft Defender XDR**:

    - [Manage access to Microsoft Defender XDR with Microsoft Entra global roles](/defender-xdr/m365d-permissions)
    - [Microsoft Defender XDR Unified role-based access control (RBAC)](/defender-xdr/manage-rbac) <!--are these both relevant?-->

- **Microsoft Sentinel**: [Roles and permissions in Microsoft Sentinel](/azure/sentinel/roles)
- **Microsoft Defender for Identity**: [Microsoft Defender for Identity role groups](/defender-for-identity/role-groups)
- **Microsoft Defender for Cloud Apps**: [Configure admin access](/defender-cloud-apps/manage-admins)
- **Microsoft Defender for Endpoint**: [Assign roles and permissions for Microsoft Defender for Endpoint deployment](/defender-endpoint/prepare-deployment)
- **Microsoft Defender for Office 365**: [Microsoft Defender for Office 365 permissions in the Microsoft Defender portal](/defender-office-365/mdo-portal-permissions)

## Plan Microsoft Sentinel costs

Start planning your budget, considering cost implications for each planned scenario. Make sure that your budget covers the cost of data ingestion for both Microsoft Sentinel and Azure Log Analytics, any playbooks that will be deployed, and so on.

For more information, see:

- [Log retention plans in Microsoft Sentinel](/azure/sentinel/log-plans)
- [Plan costs and understand Microsoft Sentinel pricing and billing](/azure/sentinel/billing?tabs=simplified%2Ccommitment-tiers)

## Next step

[Deploy Microsoft's unified security operations platform](overview-deploy.md)

## Related content

For more information, see [Use SIEM and XDR to respond to incidents with Zero Trust](/security/operations/siem-xdr-overview?bc=%2Fsecurity%2Fzero-trust%2Fbreadcrumb%2Ftoc.json&toc=%2Fsecurity%2Fzero-trust%2Ftoc.json&tabs=defender-portal).