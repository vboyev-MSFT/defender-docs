---
title: Threat detection features across the Microsoft unified security platform
description: Learn about the features that help detect threats in the Microsoft unified security platform
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

Cybersecurity threats abound in the current technology landscape. A lot of noise is created by the constant specter of breach and an abundance of signals available to security operation centers. Microsoft's unified SecOps platform separates actionable threats from the noise. Each service in Microsoft's unified SecOps platform adds its own finely tuned detections to match the complexion of the solution it provides and puts it all together into a single dashboard.

The Microsoft Defender portal pulls detections together in the form of alerts and incidents from Microsoft Defender XDR, Microsoft Defender for Cloud and Microsoft Sentinel.

## Threat detection in the Microsoft Defender portal

Security teams need focus and clarity to eliminate false positives. Microsoft Defender portal correlates and merges alerts and incidents from all Microsoft security and compliance solutions as well as unifying threat detection from external solutions through Microsoft Sentinel and Microsoft Defender for Cloud. The correlation and merging of these signals brings rich context and prioritization. For example, an Adversary-in-The-Middle (AiTM) phishing attack might have pieces of the threat puzzle scattered across multiple sources. Defender XDR puts those pieces together into an attack story while providing attack disrupt and guided response to remediate the threat.

The following image shows the incidents dashboard correlating signals from multiple services, including the individual detection sources for a complete AiTM attack story.

:::image type="content" source="media/detect-threats-overview/defender-xdr-multiple-source-example.png" alt-text="Screenshot showing an incident stitched together from multiple detection streams." lightbox="media/detect-threats-overview/defender-xdr-multiple-source-example.png":::

Each Microsoft security product enabled unlocks more signals to stream into the Defender portal. For more information on how these signals are stitched together and prioritized, see [Incidents and alerts in the Microsoft Defender portal](/defender-xdr/incidents-overview).

## Microsoft Defender XDR threat detection

Defender XDR has a unique correlation capability that provides another layer of data analysis and threat detection. The following table gives examples of how each Defender XDR security service is tuned to detect threats matching the character of its solution.

| Defender XDR service | Threat detection specialty |
|---|---|
| [**Microsoft Defender for Endpoint**](/defender-endpoint/microsoft-defender-endpoint) | Microsoft Defender antivirus detects polymorphic malware with behavior-based and heuristic analytics on endpoints such as mobile devices, desktops, and more.|
| [**Microsoft Defender for Office 365**](/defender-office-365/mdo-about#defender-for-office-365-plan-1-vs-plan-2-cheat-sheet) | Detects phishing, malware, weaponized links and more in email, Teams, and OneDrive.|
| [**Microsoft Defender for Identity**](/defender-for-identity/what-is) | Detects privilege escalation, lateral movement, discovery, defense evasion, persistence, and more across on-premises identities.|
| [**Microsoft Defender for Cloud Apps**](/defender-cloud-apps/what-is-defender-for-cloud-apps) | Detects suspicious activities through user and entity behavioral analytics (UEBA) across cloud applications.|
| [**Microsoft Defender Vulnerability Management**](/defender-vulnerability-management/defender-vulnerability-management) | Detects vulnerabilities in devices providing meaningful context for investigations.|
| [**Microsoft Entra ID Protection**](/azure/active-directory/identity-protection/overview-identity-protection) | Detects risks associated with sign-ins like impossible travel, verified threat actor IPs, leaked credentials, password sprays and more.|
| [**Microsoft Data Loss Prevention**](/microsoft-365/compliance/dlp-learn-about-dlp) | Detects risks and behavior associated with oversharing and exfiltration of sensitive information across Microsoft 365 services, Office applications, endpoints, and more.|
| [**App Governance**](/defender-cloud-apps/app-governance-manage-app-governance) | Detects anomalies in cloud app activity, especially when noncompliant, malicious, or risky apps are used.|

For more information, see [What is Microsoft Defender XDR?](/defender-xdr/microsoft-365-defender)

## Microsoft Sentinel threat detection

Microsoft Sentinel enables data collection from a vast number of Microsoft and non-Microsoft sources, but doesn't stop there. With Microsoft Sentinel's threat management capabilities, you gain the tools needed to detect and organize threats to your environment.

:::image type="content" source="/azure/sentinel/media/overview/mitre-coverage-defender.png" alt-text="Screenshot showing " lightbox="/azure/sentinel/media/overview/mitre-coverage-defender.png":::

| Threat management feature | Detection capability | For more information |
|---|---|---|
| MITRE ATT&CK coverage | Organize your threat detection coverage and understand gaps. | [Understand security coverage by the MITRE ATT&CK® framework](/azure/sentinel/mitre-coverage) |
| Analytics | Rules constantly dig through your data to generate alerts and incidents and integrates those signals in the Defender portal. | [Detect threats out-of-the-box](/azure/sentinel/threat-detection) |
| Watchlists | Curate meaningful relationships in your environment to improve the quality and prioritization of detections. | [Watchlists in Microsoft Sentinel](/azure/sentinel/watchlists) |
| Workbooks | Detect threats with visual insights, especially to monitor the health of your data collection and understand gaps that prevent proper threat detection. | [Visualize your data with workbooks](/azure/sentinel/monitor-your-data?tabs=defender-portal) |
| Summary rules | Optimizes noisy, high volume logs to detect threat in low-security value data. | [Generate alerts on threat intelligence matches against network data](/azure/sentinel/summary-rules#generate-alerts-on-threat-intelligence-matches-against-network-data) |

## Microsoft Defender for Cloud threat detection

Defender for Cloud provides threat detection to generate alerts and incidents by continuously monitoring your clouds' assets with advanced security analytics. Those signals are integrated directly into Microsoft Defender XDR for correlation and severity classification. Although Defender for cloud is licensed separately from Defender for XDR, each extra plan enabled in Defender for Cloud adds to the detection signals streamed into Defender XDR. For more information, see [Alerts and incidents in Microsoft Defender XDR](/azure/defender-for-cloud/concept-integration-365).

Defender for Cloud detects threats across a wide variety of workloads. The following table gives examples of some of the threats it detects. For more information on specific alerts, see [Security alerts reference list](/azure/defender-for-cloud/alerts-reference).

| Defender for Cloud plan | Threat detection specialty |
|---|---|
| [Defender for Servers](/azure/defender-for-cloud/tutorial-enable-servers-plan) | Detects threats for Linux and Windows based on antimalware failures, fileless attacks, crypto mining and ransomware attacks, brute force attacks and many more. |
| [Defender for Storage](/azure/defender-for-cloud/tutorial-enable-storage-plan) | Detects phishing content and malware distribution, suspicious access and discovery, unusual data extraction and more. |
| [Defender for Containers](/azure/defender-for-cloud/tutorial-enable-containers-azure) | Detects threats at the control plane and workload runtime for risky exposure, malicious or crypto mining activity, web shell activity, custom simulations and more. |
| [Defender for Databases](/azure/defender-for-cloud/tutorial-enable-databases-plan) | Detects SQL injection, fuzzing, unusual access, brute force attempts and more.  |
| [Defender for APIs](/azure/defender-for-cloud/defender-for-apis-introduction) | Detects suspicious spikes in traffic, access from malicious IPs, discovery and enumeration techniques of API endpoints and more. |
| [AI threat protection](/azure/defender-for-cloud/ai-threat-protection) | Detects threats across generative AI applications for jailbreak attempts, sensitive data exposure, corrupted AI and more. |

For more information, see [Security alerts and incidents](/azure/defender-for-cloud/alerts-overview).

## Related content

- [Protect assets](overview-unified-security.md#protect-assets)
- [Microsoft Defender for Cloud integration with Microsoft Defender XDR](/azure/defender-for-cloud/concept-integration-365)
- [Microsoft Sentinel integration with Microsoft Defender XDR](/azure/sentinel/microsoft-365-defender-sentinel-integration)
