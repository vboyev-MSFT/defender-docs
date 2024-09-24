---
title: Microsoft Defender portal overview
description: Learn about the Microsoft Defender portal
search.appverid: met150
ms.service: defender-xdr
ms.author: cwatson
author: cwatson-cat
ms.localizationpriority: medium
ms.date: 07/16/2024
audience: ITPro
ms.collection:
- M365-security-compliance
- tier1
- usx-security
ms.topic: conceptual
---

# Defender XDR in the Defender portal

Microsoft's unified security platform combines services in the [Microsoft Defender portal](https://security.microsoft.com). In the Defender portal, you can monitor and manage pre-breach and post-breach security across your organization's on-premises and multicloud assets and workloads.

Defender XDR in the Defender portal combines protection, detection, investigation, and response to threats across your entire organization and all its components, in a central place. Defender XDR combines a number of Microsoft's security services into a single location.


**[Defender for Office 365](/defender-office-365/mdo-sec-ops-guid)** | Helps secure organizations with a set of prevention, detection, investigation and hunting features to protect email, and Office 365 resources. 
**[Defender for Endpoint](/defender-endpoint/mde-sec-ops-guide)** | Delivers preventative protection, post-breach detection, automated investigation, and response for devices in the organization.
**[Defender for Identity](/defender-xdr/microsoft-365-security-center-mdi)** | Provides a cloud-based security solution that uses on-premises Active Directory signals to identify, detect, and investigate advanced threats, compromised identities, and malicious insider actions directed at your organization.
**[Defender for Cloud Apps](/defender-xdr/microsoft-365-security-center-defender-cloud-app)** | Provides a comprehensive cross-SaaS and PaaS solution that brings deep visibility, strong data controls, and enhanced threat protection to your cloud apps.
**[Microsoft Sentinel](/azure/sentinel/microsoft-365-defender-sentinel-integration)** Microsoft Sentinel is a cloud services that enables security information and event management (SIEM) and Provides in the Defender portal, Microsoft Sentinel integrates with Defender XDR to provide threat protection in the unified security operations platform. Microsoft Sentinel is a a cloud-native security information and event management (SIEM) solution and security orchestration automation response. Sentinel integrates with Defender XDR to provided a unified security platform for threat detection, investigation, hunting, and response.


> [!NOTE]
> When you open the portal, you see only the security services included in your subscriptions. For example, if you have Defender for Office 365 but not Defender for Endpoint, you see features and capabilities for Defender for Office 365, but not for device protection. 


## Investigate incidents and alerts

Centralizing security information creates a single place to investigate security incidents across your entire organization and all its components including:

- Hybrid identities
- Endpoints
- Cloud apps
- Business apps
- Email and docs
- IoT
- Network
- Business applications
- Operational technology (OT)
- Infrastructure and cloud workloads

A primary example is **Incidents** under **Incidents & alerts**.

:::image type="content" source="/defender/media/incidents-queue/incidents-ss-incidents.png" alt-text="The Incidents page in the Microsoft Defender portal." lightbox="/defender/media/incidents-queue/incidents-ss-incidents.png":::

Selecting an incident name displays a page that demonstrates the value of centralizing security information as you get better insights into the full extend of a threat, from email, to identity, to endpoints.

:::image type="content" source="/defender/media/incidents-overview/incidents-ss-incident-summary.png" alt-text="Screenshot that shows the attack story page for an incident in the Microsoft Defender portal." lightbox="/defender/media/incidents-overview/incidents-ss-incident-summary.png":::

Take the time to review the incidents in your environment, drill down into each alert, and practice building an understanding of how to access the information and determine next steps in your analysis.

Learn more about [incidents in the Defender portal](incidents-overview.md), and [managing incidents and alerts](manage-incidents.md).

## Hunt for threats

You can build custom detection rules and hunt for specific threats in your environment. **Hunting** uses a query-based threat hunting tool that lets you proactively inspect events in your organization to locate threat indicators and entities. These rules run automatically to check for, and then respond to, suspected breach activity, misconfigured machines, and other findings.

Learn about [proactive threat hunting](advanced-hunting-overview.md), and [hunting for threats across devices, emails, apps, and identities](./advanced-hunting-query-emails-devices.md).


## Respond to emerging threats

Threat analytics is the Microsoft threat intelligence solution from expert Microsoft security researchers.In the portal, track and respond to emerging threats with these threat analytics:

- Active threat actors and their campaigns
- Popular and new attack techniques
- Critical vulnerabilities
- Common attack surfaces
- Prevalent malware

Learn about [tracking and responding to emerging threats with threat analytics](threat-analytics.md).

