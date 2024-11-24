---
title: Threat hunting features across the Microsoft unified security platform
description: Learn about threat hunting features across the Microsoft unified security platform
search.appverid: met150
ms.service: unified-secops-platform
ms.author: austinmc
author: austinmccollum
ms.localizationpriority: medium
ms.date: 11/23/2024
audience: ITPro
ms.collection:
- M365-security-compliance
- tier1
- usx-security
ms.topic: conceptual

# customer intent: As a security operations center business decision maker, I want to learn about threat hunting tools available in the Microsoft unified security platform so I can get visibility into, and disrupt attacks in real time across identities, endpoints, email, cloud apps, data in hybrid and multicloud environments.
---

# Hunting in the Microsoft unified security platform

Hunting for security threats is a highly customizable activity that is most effective when accomplished in all three stages: proactive, reactive and post incident. Microsoft's unified SecOps platform provides hunting tools for every stage to fit analysts with experience from beginner to advanced. At any point, threat hunters can seamlessly share information with their team along the way.

## Hunting stages

Make the most of your hunting tools in three stages. Refer to **bolded terms** in the [hunting tools](#hunting-tools) section for more information.

- **Proactive**: Before an incident occurs, take proactive steps to build and test queries against data from new or updated sources. **Advanced hunting** has many ways to find attacks just beginning or detect threats not alerted to yet. Use the **MITRE ATT&CK map** to identify gaps in your detection coverage by running predefined hunting queries for specific techniques as a starting point to develop new logic. Plug new threat intelligence into proven queries to tune your detections and confirm if a compromise is in process. Find the weak areas in your environment before threat actors do.
- **Reactive**: Use **livestream** to run specific queries at consistent intervals to actively monitor events. Defender portal incidents can **go hunt** for threats using known entities to quickly pivot during an investigation. Tap into **Security Copilot in advanced hunting** to generate queries at machine speed and scale.
- **Post incident**: Turn successful hunting queries into new analytics rules and detection rules. **Restore historical data** and **search large datasets** to understand  

## Hunting tools

Complex queries and sophisticated notebooks aren't the only way to hunt for threats. Although Kusto Query Language (KQL) is a  and no code (query builder) searches, sample queries, use Copilot helps each experience level. Even the best need assistance some times. Microsoft Defender Experts for Hunting.

Incubate hunting queries matching connected data sources with Sentinel
Perform hunts to find gaps or investigate threats
Use advanced hunting in Defender to pull all your tables together.
Copilot assisted hunting with KQL generation from natural language.
Infrastructure chaining in MDTI

Advanced hunting, custom detections, hunts in Sentinel
[Microsoft Sentinel hunting](/azure/sentinel/hunting)
- [Hunting with summary rules](/azure/sentinel/summary-rules#quickly-find-a-malicious-ip-address-in-your-network-traffic)
- searching large data sets or historical data
[Defender XDR advanced hunting] - (/defender-xdr/advanced-hunting-overview)
Go hunt
- [Defender for Office 365](/defender-office-365/threat-explorer-threat-hunting)
- [Defender for Cloud tables for hunting](/azure/defender-for-cloud/concept-integration-365?branch=main#advanced-hunting-in-xdr) - Advanced hunting (Preview) Information about cloud audit events for various cloud platforms protected by the organization's Defender for Cloud is available through the CloudAuditEvents table in advanced hunting.
MDTI provides resources to accomplish infrastructure chaining
