---
title: "Overview - Detect threats"
description: Provides an overview of the features that help detect threats in the Microsoft unified security platform
search.appverid: met150
ms.service: unified-secops-platform
ms.author: austinmc
author: austinmccollum
ms.localizationpriority: medium
ms.date: 11/19/2024
audience: ITPro
ms.collection:
- M365-security-compliance
- tier1
- usx-security
ms.topic: conceptual
# customer intent: I want to learn detecting threats with the tools available in the Microsoft unified security platform and get visibility into, and disrupt attacks in real time across identities, endpoints, email, cloud apps, data in hybrid and multicloud environments.
---

# Overview - Detect threats

Each portion of your organization that sends data to your Microsoft unified security platform increases the ability to detect threats in your environment. When a security gap or threat is detected, automated and manual responses can be unleashed to neutralize them.

:::image type="content" source="/azure/defender-for-cloud/media/alerts-overview/security-center-detection-capabilities.png" alt-text="Diagram showing ":::

Microsoft Defender portal is the single dashboard that brings together threat detection from all your Microsoft security services.

## Microsoft Sentinel threat detection

Microsoft Sentinel enables data collection from all your Microsoft and 3rd party sources, but doesn't stop there. With Microsoft Sentinel's **Threat management** capabilities, you gain the tools needed to detect and organize threats to your environment.

| Threat management feature | Detection capability | For more information |
|---|---|---|
| MITRE ATT&CK coverage | Organize your threat detection coverage and understand gaps. | [Understand security coverage by the MITRE ATT&CK® framework](/azure/sentinel/mitre-coverage) |
| Analytics | Rules constantly dig through your data to generate alerts and incidents and integrates those signals in the Defender portal. | [Detect threats out-of-the-box](/azure/sentinel/detect-threats-built-in) |
| Watchlists | Curate meaningful relationships in your environment to improve the quality and prioritization of detections. | [Watchlists in Microsoft Sentinel](/azure/sentinel/watchlists) |
| Workbooks | Detect threats with visual insights, especially to monitor the health of your data collection and understand gaps that prevent proper threat detection. | [Visualize collected data](azure/sentinel/get-visibility) |

For more information, see [Detect threats in Microsoft Sentinel](/azure/sentinel/overview?tabs=azure-portal#detect-threats).

## Microsoft Defender for Cloud threat detection

Continuously monitoring your clouds' assets with advanced security analytics, Defender for Cloud provides threat detection to generate alerts and incidents. Those signal are integrated directly into Microsoft Defender XDR for correlation and severity classification.

For more information, see [Security alerts and incidents](/azure/defender-for-cloud/alerts-overview).

## Microsoft Defender XDR threat detection

Threat detection is sourced from the many services that are part of Microsoft Defender XDR as well as unifying threat detection from Microsoft Sentinel and Microsoft Defender for Cloud. The correlation and merging of these signals brings rich context and prioritization of the alerts and incidents highlighting threats.

For more information, see [Incidents and alerts in the Microsoft Defender portal](/defender-xdr/incidents-overview).

## Threat intelligence helps detect threats

Threat detection vs. threat protection
Defender XDR - defender-xdr/incident-response-overview [looking at narrower slice here though to focus on detection vs. the response]
