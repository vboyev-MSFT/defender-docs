---
title: Work with results containing Microsoft Sentinel data
description: Work with advanced hunting in the portal unifying Defender XDR and Sentinel data
search.appverid: met150
ms.service: defender-xdr
ms.subservice: adv-hunting
f1.keywords: 
  - NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: 
  - m365-security
  - m365initiative-m365-defender
  - tier1
  - usx-security
ms.topic: conceptual
ms.custom:
- cx-ti
- cx-ah
appliesto:
    - Microsoft Defender XDR
    - Microsoft Sentinel in the Microsoft Defender portal
ms.date: 08/07/2024
---

# Work with advanced hunting results containing Microsoft Sentinel data

## Explore results

Results of queries that were run appear in the **Results** tab. You can export the results to a CSV file by selecting **Export**. 

:::image type="content" source="/defender/media/advanced-hunting-unified-results.png" alt-text="Screenshot of advanced hunting results with options to expand result rows in the Microsoft Defender portal" lightbox="/defender/media/advanced-hunting-unified-results.png":::

You can also explore the results in-line with the following features:

- Expand a result by selecting the dropdown arrow at the left of each result
- Where applicable, expand details for results that are in JSON or array format by selecting the dropdown arrow at the left of applicable result row for added readability
- Open the side pane to see a record's details (concurrent with expanded rows)

You can also right-click on any result value in a row so that you can use it to:
- Add more filters to the existing query
- Copy the value for use in further investigation
- Update the query to extend a JSON field to a new column

For Microsoft Defender XDR data, you can take further action by selecting the checkboxes to the left of each result row. Select **Link to incident** to link the selected results to an incident (read [Link query results to an incident](advanced-hunting-link-to-incident.md)) or **Take actions** to open the Take actions wizard (read [Take action on advanced hunting query results](advanced-hunting-take-action.md)).

