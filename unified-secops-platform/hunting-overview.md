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

Hunting for security threats is a highly customizable activity that is most effective when accomplished in all three stages: proactive, reactive, and post incident. Microsoft's unified SecOps platform provides effective hunting tools for every stage of threat hunting. These tools are well fit for analysts just starting out in their career or experienced threat hunters using advance hunting methods. Threat hunters of all levels benefit from hunting tool features that allow them to share their techniques, queries, and findings with their team along the way.

## Hunting stages

Make the most of your hunting tools in three stages. Refer to **bolded terms** from each stage in the [hunting tools](#hunting-tools) section for more information.

|**Hunting stage**|**Hunting tools**|
|---|---|
| **Proactive** - Find the weak areas in your environment before threat actors do. | - Take proactive steps to build and test queries against data from new or updated sources.<br> - Conduct end-to-end **hunts**.<br> - **Advanced hunting** has many ways to find attacks just beginning or detect threats not alerted to yet.<br> - Use the **MITRE ATT&CK map** to identify gaps in your detection coverage by running predefined hunting queries for specific techniques as a starting point to develop new logic.<br> - Insert new threat intelligence into proven queries to tune your detections and confirm if a compromise is in process.|
| **Reactive** - Hunting tools to use during an active investigation. | - Use **livestream** to run specific queries at consistent intervals to actively monitor events.<br> - Defender portal incidents pivot quickly with **go hunt** to search more broadly for suspicious entities found during an investigation.<br> - Hunt through threat intelligence to perform **infrastructure chaining**<br> - Tap into **Security Copilot in advanced hunting** to generate queries at machine speed and scale.|
| **Post incident** - Improve coverage and insight to prevent similar incidents. | - Turn successful hunting queries into new analytics and detection rules or refine existing ones.<br> - **Restore historical data** and **search large datasets** for specialized hunting as part of full incident investigations.|

## Hunting tools

Kusto Query Language (KQL) is a powerful and flexible language optimized for searching through big-data stores in cloud environments. The foundation of hunting queries in Defender portal rests on KQL. But crafting complex queries isn't the only way to hunt for threats. Here are some hunting tools and resources within Defender portal designed to bring hunting into your reach:

- [**Security Copilot in advanced hunting**](/defender-xdr/advanced-hunting-security-copilot) generates KQL from natural language prompts.
- [**Guided hunting**](/defender-xdr/advanced-hunting-query-builder) uses a query builder for crafting meaningful hunting queries without knowing KQL or the data schema.
- [**Get help as you write queries**](/defender-xdr/advanced-hunting-query-language#get-help-as-you-write-queries) with features like autosuggest, schema tree, and sample queries.
- [**Content hub**](/azure/sentinel/sentinel-solutions-deploy?tabs=azure-portal#hunting-query) provides expert queries to match out-of-the-box solutions in Microsoft Sentinel.
- [Microsoft Defender Experts for Hunting](/defender-xdr/advanced-hunting-overview) compliments even the best threat hunters that want assistance.

Maximize the full extent of your team's hunting prowess with the following hunting tools in Defender portal:

| **Hunting tool** | **Description** |
|---|---|
|[**Advanced hunting**](/defender-xdr/advanced-hunting-microsoft-defender) | View and query data sources available within Microsoft's unified SecOps platform and share queries with your team. |
|[**Microsoft Sentinel hunting**](/azure/sentinel/hunting) | Search and query tools to hunt for security threats across data sources.|
|[**Go hunt**](/defender-xdr/advanced-hunting-go-hunt) | Quickly pivot an investigation to entities found within an incident. |
|[**Hunts**](/azure/sentinel/hunts) | An end-to-end, proactive threat hunting process with collaboration features. |
|[**Bookmarks**](/azure/sentinel/bookmarks) | Preserve queries and their results, adding notes and contextual observations.|
|[**Livestream**](/azure/sentinel/livestream) | Start an interactive hunting session and use any Log Analytics query. |
|[**Hunting with summary rules**](/azure/sentinel/summary-rules#quickly-find-a-malicious-ip-address-in-your-network-traffic) | Use summary rules to save costs hunting for threats in verbose logs.|
|[**MITRE ATT&CK map**](/azure/sentinel/mitre-coverage#use-the-mitre-attck-framework-in-analytics-rules-and-incidents) | When creating a new hunting query, select specific tactics and techniques to apply.|
|[**Restore historical data**](/sentinel/restore) | Restore data from archived logs to use in high performing queries. |
|[**Search large data sets**](/sentinel/search-jobs?tabs=defender-portal) | Search for specific events in logs up to seven years ago using KQL. |
|[**Infrastructure chaining**](/defender/threat-intelligence/infrastructure-chaining) | Hunt for new connections between threat actors, group similar attack activity and substantiate assumptions.|
|[**Threat explorer**](/defender-office-365/threat-explorer-threat-hunting) | Hunt for specialized threats related to email. |

## Related content

- [Threat detection in Microsoft's unified SecOps platform](/unified-secops-platform/detect-threats-overview)
- [Security posture management and risk reduction](/unified-secops-platform/reduce-risk-overview)
- [Service integration](/unified-secops-platform/overview-defender-portal)
