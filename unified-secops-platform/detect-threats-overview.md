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
# customer intent: As a security operations center business decision maker, I want to learn about the tools available to detect threats in Microsoft's unified security platform to help me determine whether it meets my organization's requirements.
---

# Threat detection in Microsoft's unified SecOps platform

Each portion of your organization that sends data to Microsoft's unified security platform increases the ability to detect threats in your environment. When a security gap or threat is detected, automated and manual responses can be unleashed to neutralize them.

:::image type="content" source="/azure/defender-for-cloud/media/alerts-overview/security-center-detection-capabilities.png" alt-text="Diagram showing ":::

Microsoft's unified SecOps platform in the Microsoft Defender portal brings together threat detection from all your Microsoft security services into a single dashboard.

## Microsoft Defender XDR threat detection

Threat detection is sourced from the many services that are part of Microsoft Defender XDR as well as unifying threat detection from Microsoft Sentinel and Microsoft Defender for Cloud. The correlation and merging of these signals brings rich context and prioritization of the alerts and incidents highlighting threats. For the current list of Microsoft security products that natively add their detections to Microsoft Defender XDR, see [What is Microsoft Defender XDR?](/defender-xdr/microsoft-365-defender). For each of those Microsoft security products enabled, more signals are unlocked and streamed into Defender XDR.

For more information on how these signals are stitched together and prioritized, see [Incidents and alerts in the Microsoft Defender portal](/defender-xdr/incidents-overview).

## Microsoft Sentinel threat detection

Microsoft Sentinel enables data collection from all your Microsoft and 3rd party sources, but doesn't stop there. With Microsoft Sentinel's threat management capabilities, you gain the tools needed to detect and organize threats to your environment.

| Threat management feature | Detection capability | For more information |
|---|---|---|
| MITRE ATT&CK coverage | Organize your threat detection coverage and understand gaps. | [Understand security coverage by the MITRE ATT&CK® framework](/azure/sentinel/mitre-coverage) |
| Analytics | Rules constantly dig through your data to generate alerts and incidents and integrates those signals in the Defender portal. | [Detect threats out-of-the-box](/azure/sentinel/threat-detection) |
| Watchlists | Curate meaningful relationships in your environment to improve the quality and prioritization of detections. | [Watchlists in Microsoft Sentinel](/azure/sentinel/watchlists) |
| Workbooks | Detect threats with visual insights, especially to monitor the health of your data collection and understand gaps that prevent proper threat detection. | [Visualize your data with workbooks](/azure/sentinel/monitor-your-data?tabs=defender-portal) |

For more information, see [Detect threats in Microsoft Sentinel](/azure/sentinel/overview?tabs=azure-portal#detect-threats).

## Microsoft Defender for Cloud threat detection

Defender for Cloud provides threat detection to generate alerts and incidents by continuously monitoring your clouds' assets with advanced security analytics. Those signal are integrated directly into Microsoft Defender XDR for correlation and severity classification. Although Defender for cloud is licensed separately from Defender for XDR, additional plans enabled in Defender for Cloud add to the detection signals streamed into Defender XDR.

For more information, see [Security alerts and incidents](/azure/defender-for-cloud/alerts-overview).

## Related content

- [Protect assets](overview-unified-security.md#protect-assets)
- [Microsoft Defender for Cloud integration with Microsoft Defender XDR](/azure/defender-for-cloud/concept-integration-365)
- [Microsoft Sentinel integration with Microsoft Defender XDR](/azure/sentinel/microsoft-365-defender-sentinel-integration)
