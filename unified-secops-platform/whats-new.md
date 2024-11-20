---
title: What's new in the Microsoft unified security operations platform
description: Lists the new features and functionality in the Microsoft unified security operations platform
search.appverid: met150
ms.service: unified-secops-platform
ms.author: cwatson
author: cwatson-cat
ms.localizationpriority: medium
ms.date: 07/16/2024
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- tier1
- usx-security
ms.topic: conceptual
---

# What's new in the Microsoft unified security operations platform

<!--Need to define when something goes here versus other what's new articles. Maybe we just focus on updates within this library and things tied directly to USX (features that unblock onboarding, parity features with Sentinel, enhancements to core USX features?) -->

This article lists recent features added into the Microsoft unifed security operations platform within the Microsoft Defender portal, and new features in related services that provide an enhanced user experience in the platform.

The listed features were released in the last three months. For information about earlier features delivered, see our [Tech Community blogs](https://techcommunity.microsoft.com/t5/azure-sentinel/bg-p/AzureSentinelBlog/label-name/What's%20New).

For more information on what's new with other Microsoft Defender security products and Microsoft Sentinel, see:

- [What's new in Microsoft Sentinel](/azure/sentinel/whats-new)
- [What's new in Microsoft Defender XDR](/defender-xdr/whats-new)
- [What's new in Microsoft Defender for Office 365](/defender-office-365/defender-for-office-365-whats-new)
- [What's new in Microsoft Defender for Endpoint](/defender-endpoint/whats-new-in-microsoft-defender-endpoint)
- [What's new in Microsoft Defender for Identity](/defender-for-identity/whats-new)
- [What's new in Microsoft Defender for Cloud Apps](/cloud-app-security/release-notes)

You can also get product updates and important notifications through the [message center](https://admin.microsoft.com/Adminportal/Home#/MessageCenter).


## July 2024

- [SOC optimizations now generally available](#soc-optimizations-now-generally-available)
- [SAP Business Technology Platform (BTP) connector now generally available](#sap-business-technology-platform-btp-connector-now-generally-available-ga)
- [Microsoft unified security platform now generally available](#microsoft-unified-security-platform-now-generally-available)

### SOC optimizations now generally available

The SOC optimization experience in both the Azure and Defender portals is now generally available for all Microsoft Sentinel customers, including both data value and threat-based recommendations.

- **Use data value recommendations** to improve your data usage of ingested billable logs, gain visibility to underused logs, and discover the right detections for those logs or the right adjustments to your log tier or ingestion.

- **Use threat-based recommendations** to help identify gaps in coverage against specific attacks based on Microsoft research and mitigate them by ingesting the recommended logs and adding recommended detections.

The [`recommendations`](/azure/sentinel/soc-optimization/soc-optimization-api) API is still in Preview. 

For more information, see:

- [Optimize your security operations](/azure/sentinel/soc-optimization/soc-optimization-access)
- [SOC optimization reference of recommendations](/azure/sentinel/soc-optimization/soc-optimization-reference)

### SAP Business Technology Platform (BTP) connector now generally available (GA)

The Microsoft Sentinel Solution for SAP BTP is now generally available (GA). This solution provides visibility into your SAP BTP environment, and helps you detect and respond to threats and suspicious activities.

For more information, see:

- [Microsoft Sentinel Solution for SAP Business Technology Platform (BTP)](/azure/sentinel/sap/sap-btp-solution-overview)
- [Deploy the Microsoft Sentinel solution for SAP BTP](/azure/sentinel/sap/deploy-sap-btp-solution)
- [Microsoft Sentinel Solution for SAP BTP: security content reference](/azure/sentinel/sap/sap-btp-security-content)

### Microsoft unified security platform now generally available

Microsoft Sentinel is now generally available within the Microsoft unified security operations platform in the Microsoft Defender portal. The Microsoft unified security operations platform brings together the full capabilities of Microsoft Sentinel, Microsoft Defender XDR, and Microsoft Copilot in Microsoft Defender. For more information, see the following resources:

- Blog post: [General availability of the  Microsoft unified security operations platform](https://aka.ms/unified-soc-announcement)
- [Microsoft Sentinel in the Microsoft Defender portal](/azure/sentinel/microsoft-sentinel-defender-portal)
- [Connect Microsoft Sentinel to Microsoft Defender XDR](/defender-xdr/microsoft-sentinel-onboard)
- [Microsoft Copilot in Microsoft Defender](/defender-xdr/security-copilot-in-microsoft-365-defender)