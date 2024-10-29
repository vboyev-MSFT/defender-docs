---
title: Microsoft Defender XDR in the Defender portal 
description: Learn about Microsoft Defender XDR in the Defender portal
search.appverid: met150
ms.service: unified-secops-platform
ms.author: cwatson
author: cwatson-cat
ms.localizationpriority: medium
ms.date: 10/08/2024
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


**[Defender for Office 365](/defender-office-365/mdo-about)** | Helps secure organizations with a set of prevention, detection, investigation and hunting features to protect email, and Office 365 resources. 
**[Defender for Endpoint](/defender-endpoint/)** | Delivers preventative protection, post-breach detection, automated investigation, and response for devices in the organization.
**[Defender for Identity](/defender-for-identity/what-is)** | Provides a cloud-based security solution that uses on-premises Active Directory signals to identify, detect, and investigate advanced threats, compromised identities, and malicious insider actions directed at your organization.
**[Defender for Cloud Apps](/cloud-app-security/)** | Provides a comprehensive cross-SaaS and PaaS solution that brings deep visibility, strong data controls, and enhanced threat protection to your cloud apps.

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

<!-- commenting this out as the file path will move soon and I don't want to fight with this broken link anymore. File path is changing anyway. :::image type="content" source="../../media/incidents-overview/incidents-ss-incident-summary.png" alt-text="Screenshot that shows the attack story page for an incident in the Microsoft Defender portal." lightbox="../../media/incidents-overview/incidents-ss-incident-summary.png"::: -->

Take the time to review the incidents in your environment, drill down into each alert, and practice building an understanding of how to access the information and determine next steps in your analysis.

Learn more about [incidents in the Defender portal](/defender-xdr/incidents-overview), and [managing incidents and alerts](/defender-xdr/manage-incidents).

## Hunt for threats

You can build custom detection rules and hunt for specific threats in your environment. **Hunting** uses a query-based threat hunting tool that lets you proactively inspect events in your organization to locate threat indicators and entities. These rules run automatically to check for, and then respond to, suspected breach activity, misconfigured machines, and other findings.

Learn about [proactive threat hunting](/defender-xdr/advanced-hunting-overview), and [hunting for threats across devices, emails, apps, and identities](/defender-xdr/advanced-hunting-query-emails-devices).


## Respond to emerging threats

Threat analytics is the Microsoft threat intelligence solution from expert Microsoft security researchers.In the portal, track and respond to emerging threats with these threat analytics:

- Active threat actors and their campaigns
- Popular and new attack techniques
- Critical vulnerabilities
- Common attack surfaces
- Prevalent malware

Learn about [tracking and responding to emerging threats with threat analytics](/defender-xdr/threat-analytics).

