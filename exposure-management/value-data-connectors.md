---
title: Working with the data connectors in Microsoft Security Exposure Management
description: Learn about using the data connectors in Microsoft Security Exposure Management.
ms.author: dlanger
author: dlanger
manager: rayne-wiselman
ms.topic: overview
ms.service: exposure-management
ms.date: 09/11/2024
---

# Getting value from your data connectors

[Microsoft Security Exposure Management](microsoft-security-exposure-management.md) consolidates security posture data from all your digital assets enabling you to map your attack surface and focus your security efforts on areas at greatest risk. The data from Microsoft products gets ingested automatically once connected to Exposure Management, and you can add more data connectors from external data sources.

## Imported assets and types

There are various types of assets available for consumption, such as digital assets and mobile applications.

- Devices
- Vulnerabilities
- Users (future)
- Software (future)
- SaaS Applications (future)

The asset information imported into Exposure Management includes data from external data sources like Qualys, Rapid7, and ServiceNow CMDB environments. This data is consolidated to provide a comprehensive view of the security posture across all digital assets.

The imported assets will appear in the device inventory and is incorporated into the exposure graph. Microsoft Security Exposure Management also offers integration with critical asset protection, attack paths, metrics, and initiatives. It provides insights into potential attack paths and entry points that could compromise critical assets. It also offers metrics and recommendations to help prioritize actions to protect these assets.

:::image type="content" source="media/value-data-connectors/device inventory with 3P.png" alt-text="Screenshot of device inventory with discovery source highlighted" lightbox="media/value-data-connectors/device inventory with 3P.png":::

The information brought into the system includes:

- Device and service data from systems
- OS
- Distribution
- Interfaces
- Network details
- Last users  

To explore your discovered and ingested data from the external data sources, you can [run queries](query-enterprise-exposure-graph.md) on the Exposure Graph in Advanced Hunting.

**Examples**:

```kusto
ExposureGraphNodes
| where NodeProperties contains ("serviceNowCmdbAssetInfo")
| extend SnowInfo = NodeProperties.rawData.serviceNowCmdbAssetInfo
```

```kusto
ExposureGraphNodes
| where EntityIds contains ("QualysAssetId")
```

```kusto
ExposureGraphEdges
| where EdgeLabel == "affecting"
| where tostring(EdgeProperties.rawData.reportInfo.reportedBy) == "rapid7"
| project AssetName = TargetNodeName, CVE = SourceNodeName
```

```kusto
ExposureGraphEdges
| where EdgeLabel == "affecting"
| where tostring(EdgeProperties.rawData.reportInfo.reportedBy) == "tenable"
| project AssetName = TargetNodeName, CVE = SourceNodeName
```

> **Note:** When troubleshooting Advanced Hunting (AH) queries that don't work or yield no results, note that the `reportedBy` field is case-sensitive. For example, valid values include `rapid7`, `tenable`, etc.

## Next steps

- [Overview of attack paths](work-attack-paths-overview.md)
