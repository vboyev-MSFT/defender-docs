---
title: Microsoft Defender XDR in the Defender portal 
description: Learn about the services and features available with Microsoft Defender XDR in the Microsoft Defender portal.
search.appverid: met150
ms.service: unified-secops-platform
ms.author: cwatson
author: cwatson-cat
ms.localizationpriority: medium
ms.date: 11/15/2024
audience: ITPro
ms.collection:
- M365-security-compliance
- tier1
- usx-security
ms.topic: concept-article

# customer intent: As a security operations center leader, I want to learn about the services and features available with Defender XDR to help me determine whether it meets my organization's requirements.
---

# Microsoft Defender XDR in the Defender portal

Microsoft Defender XDR in the Microsoft unified SecOps platform unifies and coordinates threat prevention, detection, investigation, and response across a broad range of assets, including devices and endpoints, identities, email, Microsoft 365 services, and SaaS apps.

Defender XDR consolidates threat signals and data across assets, so that you can monitor and manage organizational threat protection from a single location in the [Microsoft Defender portal](https://security.microsoft.com). 


Defender XDR combines many Microsoft security services.

**Service** | **Details**
--- | ---
**[Protect against email threats with Defender for Office 365](/defender-office-365/mdo-sec-ops-guid)** | Helps secure organizations with a set of prevention, detection, investigation and hunting features to protect email, and Office 365 resources. 
**[Protect devices with Defender for Endpoint](/defender-endpoint/mde-sec-ops-guide)** | Delivers preventative protection, post-breach detection, automated investigation, and response for devices in the organization.
**[Protect Active Directory with Defender for Identity](/defender-xdr/microsoft-365-security-center-mdi)** | Provides a cloud-based security solution that uses on-premises Active Directory signals to identify, detect, and investigate advanced threats, compromised identities, and malicious insider actions directed at your organization.
**[Protect SaaS cloud apps with Defender for Cloud Apps](/defender-xdr/microsoft-365-security-center-defender-cloud-app)** | Provides a comprehensive cross-SaaS and PaaS solution that brings deep visibility, strong data controls, and enhanced threat protection to your cloud apps.
**[Protect against a broad range of threats with Microsoft Sentinel](/azure/sentinel/microsoft-365-defender-sentinel-integration)** | Microsoft Sentinel is a cloud security solution for security information and event management (SIEM) and security orchestration, automation, and response (SOAR).<br/><br/> Collect security data from a broad range of Microsoft and third-party services and products.<br/><br/> Microsoft Sentinel seamlessly integrates with Defender XDR in the Defender portal to combine the capabilities of both products into a unified security platform for threat detection, investigation, hunting, and response.



## Detecting threats

Defender XDR provides continuous monitoring our enterprise and detects security threats. When threats are detected [security alerts](/defender-xdr/alerts-incidents-correlation) are created. 

Defender XDR automatically aggregates related alerts and security signals into [security incidents](/defender-xdr/alerts-incidents-correlation#incident-creation-and-alert-correlation). Incidents enable your SOC teams to quickly get the full picture of an attack, understand the attack scope and progress, and review all involved entities and assets. This information helps SOC teams to respond to attacks more efficiently and effectively. 

A [single incident queue](/defender-xdr/incident-queue) provides full visibility into the latest alerts and incidents, and historical data. You can search and query the incident queue to drill down, and prioritize response based on alert severity.

:::image type="content" source="media/defender-xdr-portal/incidents-page.png" alt-text="Screenshot of the Incidents page in the Microsoft Defender portal" lightbox="media/defender-xdr-portal/incidents-page.png":::


### Detecting lateral movement attacks

Defender for XDR includes [deception capability](/defender-xdr/deception-overview) to detection human-operated lateral movement, often used for common attacks such as ransomware and business email compromise. 

The deception capability generates decoy assets. When attackers interact with these assets, the deception capability raises high-confidence alerts. You can review deception-related alerts in the Alerts page in the portal.

## Automatically disrupting threats

Defender XDR uses [automatic attack disruption](/defender-xdr/automatic-attack-disruption) to contain attacks in progress, which limit the attack impact, and provide more time for security teams to remediate attacks.

Automatic disruption relies on the high-fidelity signals that use incident correlation across million of Defender product signals, and continuous investigation insights from Microsoft's security research team, to ensure a high signal-to-noise ratio (SNR).

Automatic disruption uses Defender XDR response actions, including containing devices, and disabling or containing user accounts.

It's easy to identify attack disruptions in the Defender XDR incident queue and on specific incident pages.


## Hunting for threats

Threat hunting is a proactive approach to inspect and investigate security events and data to locate known and potential threats. 

Defender XDR provides threat hunting capabilities in the Defender portal. 

By using [advanced hunting](/defender-xdr/advanced-hunting-overview), SOC teams can create custom queries and rules to hunt for threats across the enterprise. By using Kusto Query Language (KQL), analysts can search for indicators of compromise, anomalies, and suspicious activities across Defender XDR data sources. Data can be filtered, aggregated, and analyzed. 

For those who aren't familiar with KQL, Defender XDR provides a guided mode to create queries visually. Predefined query templates are also available.

In addition to advanced hunting, SOC teams can create [custom detection rules](/defender-xdr/custom-detections-overview) to proactively monitor and respond to events and system states. Rules can trigger alerts or automatic response actions.

## Responding to threats

Defender for XDR provides [automated investigation and response](/defender-xdr/m365d-autoir) capabilities, reducing the volume of alerts to which SOC teams must respond. 

As alerts create incidents, automated investigation results in a verdict that determines whether a threat was found. For suspicious and malicious threats, remediation can include actions such as sending a file to quarantine, stopping a process, blocking a URL, or isolating a device. 

You can view a summary of automated investigations and responses in the Home page of the portal. Pending remediation actions are handled in the portal Action Center.



