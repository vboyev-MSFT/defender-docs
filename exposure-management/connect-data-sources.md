---
title: Overview of connecting data sources in Microsoft Security Exposure Management
description: Learn about connecting data sources in Microsoft Security Exposure Management.
ms.author: dlanger
author: dlanger
manager: rayne-wiselman
ms.topic: overview
ms.service: exposure-management
ms.date: 09/09/2024
---

# Overview

[Microsoft Security Exposure Management](microsoft-security-exposure-management.md) consolidates security posture data from all your digital assets enabling you to map your attack surface and focus your security efforts on areas at greatest risk. The data from Microsoft products gets ingested automatically once connected to Exposure Management, and you can add more connectors from external data sources.

To provide coverage of all your assets and security signals, Exposure Management provides data connectors that ingest data from other security or asset management products deployed in your environment.
This means you're able to seamlessly integrate with existing security solutions to:

- Ingest data from external data sources
- Consolidate all your asset and security posture data in Exposure Management

The support for external solutions helps to further streamline, integrate, and orchestrate defenses from other vendors with Exposure Management; enabling security teams to effectively manage their posture and exposure across the entire attack surface.

Integration with the following solutions is currently supported:

- ServiceNow CMDB
- Qualys VM
- Rapid7 VM
- Tenable
- Wiz

:::image type="content" source="media/connect-data-sources/data-connectors.png" alt-text="Screenshot of data connectors in MSEM" lightbox="media/connect-data-sources/data-connectors.png":::

Security Exposure Management is currently in public preview.

[!INCLUDE [prerelease](../includes//prerelease.md)]

## Prerequisites

The following prerequisites are required to connect data sources to Microsoft Security Exposure Management.

### Environmental requirements

- Implemented Microsoft Security Exposure Management.
- Supported external data sources to ingest data from these asset inventory or vulnerability management products:
    - ServiceNow CMDB
    - Qualys VM
    - Rapid7 VM
    - Tenable
    - Wiz

### Roles & permissions

For full access, you need one of the following Microsoft Entra ID roles:

- Global Admin (read and write permissions)
- Global Reader (read permissions)
- Security Admin (read and write permissions)
- Security Operator (read and limited write permissions)
- Security Reader (read permissions)

You can find more details about the permission levels here, [Prerequisites, and support](prerequisites.md).

### Cloud support

- MSEM is available in Commercial Clouds (Azure, AWS, and GCP).
- Nation/Sovereign Clouds: MSEM isn't available in US Gov, China Gov, or Other Gov clouds.

## Next steps

[Understanding your data connectors](understand-data-connectors.md).
