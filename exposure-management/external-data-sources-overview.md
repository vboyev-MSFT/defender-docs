---
title: Overview of external data sources in Microsoft Security Exposure Management
description: Learn how to connect external data sources in Microsoft Security Exposure Management.
ms.author: dlanger
author: dlanger
manager: rayne-wiselman
ms.topic: overview
ms.service: exposure-management
ms.date: 09/02/2024
---

# Overview - External data sources

[Microsoft Security Exposure Management](microsoft-security-exposure-management.md) consolidates security posture data from all your digital assets enabling you to map your attack surface and focus your security efforts on areas at greatest risk.

To provide coverage of all your assets and security signals, MSEM provides data connectors that ingest data from other security or asset management products deployed in your environment. 
This means you will be able to seamlessly integrate with existing security solutions to:
-Ingest data from external data sources
-Consolidate all your asset and security posture data in MSEM

The support for third-party solutions helps to further streamline, integrate, and orchestrate defenses from other vendors with MSEM; enabling security teams to effectively manage their posture and exposure across the entire attack surface.
Integration is currently supported for the following solutions:
- ServiceNow CMDB
- Qualys VM
- Rapid7 VM
- Tenable
- Wiz

Security Exposure Management is currently in public preview.

[!INCLUDE [prerelease](../includes//prerelease.md)]

## Prerequisites

### Required environmental requirements

* You need to use Microsoft Security Exposure Management.
* Supported external data sources: You can integrate MSEM with ServiceNow CMDB, Qualys VM, or Rapid7 VM to ingest data from these asset inventory or vulnerability management products.

### Required roles & permissions

For full access, you need one of the following Microsoft Entra ID roles:

* Global Admin (read and write permissions)
* Global Reader (read permissions)
* Security Admin (read and write permissions)
* Security Operator (read and limited write permissions)
* Security Reader (read permissions)

You can find more details about MSEM permission levels [here](https://learn.microsoft.com/en-us/security-exposure-management/prerequisites#permissions).

### Cloud support

·     MSEM is available in Commercial Clouds (Azure, AWS, and GCP).

·     Nation/Sovereign Clouds: MSEM is not available in US Gov, China Gov, or Other Gov clouds.

## Next steps

- 
- 
