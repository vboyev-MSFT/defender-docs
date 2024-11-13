---
title: Microsoft Defender XDR in the Defender portal 
description: Learn about Microsoft Defender XDR in the Defender portal
search.appverid: met150
ms.service: unified-secops-platform
ms.author: cwatson
author: cwatson-cat
ms.localizationpriority: medium
ms.date: 11/13/2024
audience: ITPro
ms.collection:
- M365-security-compliance
- tier1
- usx-security
ms.topic: conceptual
---

# Defender XDR in the Defender portal

Microsoft Defender XDR in the Microsoft unified SecOps platform unifies and coordinates threat prevention, detection, investigation, and response across a broad range of assets, including devices and endpoints, identities, email, and SaaS apps.

Defender XDR consolidates threat signals and data across assets, so that you can monitor and manage organizational threat protection from a single location in the [Microsoft Defender portal](https://security.microsoft.com). 


Defender XDR combines a number of Microsoft security services.

**Service** | **Details**
--- | ---
**[Protect against email threats with Defender for Office 365](/defender-office-365/mdo-sec-ops-guid)** | Helps secure organizations with a set of prevention, detection, investigation and hunting features to protect email, and Office 365 resources. 
**[Protect devices with Defender for Endpoint](/defender-endpoint/mde-sec-ops-guide)** | Delivers preventative protection, post-breach detection, automated investigation, and response for devices in the organization.
**[Protect Active Directory with Defender for Identity](/defender-xdr/microsoft-365-security-center-mdi)** | Provides a cloud-based security solution that uses on-premises Active Directory signals to identify, detect, and investigate advanced threats, compromised identities, and malicious insider actions directed at your organization.
**[Protect SaaS cloud apps with Defender for Cloud Apps](/defender-xdr/microsoft-365-security-center-defender-cloud-app)** | Provides a comprehensive cross-SaaS and PaaS solution that brings deep visibility, strong data controls, and enhanced threat protection to your cloud apps.
**[Protect against a broad range of threats with Microsoft Sentinel](/azure/sentinel/microsoft-365-defender-sentinel-integration)** | Microsoft Sentinel is a cloud services that enables security information and event management (SIEM) and Provides in the Defender portal, Microsoft Sentinel integrates with Defender XDR to provide threat protection in the unified security operations platform. Microsoft Sentinel is a a cloud-native security information and event management (SIEM) solution and security orchestration automation response. Sentinel integrates with Defender XDR to provided a unified security platform for threat detection, investigation, hunting, and response.


## Investigate incidents and alerts

Defender XDR in the Defender portal consolidates threat events across all assets, including Defender XDR services, Microsoft Sentinel, Microsoft Defender for Cloud, Microsoft Defender for IoT, and third-party services. 

Threat detection activity across Defender portal services trigger alerts. In the portal, you can monitor and review alerts, and filter alerts to investigate as needed.

Incidents define contextual attack stories by associating related alert data, suspicious events, and impacted assets under an incident instance. Incident correlation and context enables you to visualize, understand, and respond to threats across the enterprise.

A combined incidents queue helps your security team to focus on critical issues. Attack scope, impacted assets, and automated remediation actions are group together and surfaced in the queue.


:::image type="content" source="/defender/media/incidents-queue/incidents-ss-incidents.png" alt-text="The Incidents page in the Microsoft Defender portal." lightbox="/defender/media/incidents-queue/incidents-ss-incidents.png":::


Learn more about [incidents in the Defender portal](/defender-xdr/incidents-overview), and [managing incidents and alerts](/defender-xdr/manage-incidents).

## Hunt for threats

Hunting in the Defender portal allows you to proactively inspect security events and data to locate known and potential threats. 

You can explore and query up to 30 days of raw data. Query using a guided query tool and sample queries, or use KQL to build your own custom queries.

Create custom detection rules to proactively monitor and respond to events and system states. Rules can trigger alerts or automatic response actions.

Learn about [proactive threat hunting](/defender-xdr/advanced-hunting-overview), and [hunting for threats across devices, emails, apps, and identities](/defender-xdr/advanced-hunting-query-emails-devices).

## Remediate threats

Threat protection results in remediation actions that can be automated or manual, and require approval. In the Defender XDR action center, review remediation actions that need attention, or access remediation auditing. 


