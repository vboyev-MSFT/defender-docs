---
title: Integrate Tenable data connector in Microsoft Security Exposure Management
description: Learn how to the Tenable data connector in Microsoft Security Exposure Management.
ms.author: dlanger
author: dlanger
manager: rayne-wiselman
ms.topic: overview
ms.service: exposure-management
ms.date: 09/24/2024
---

# Tenable data connector

To integrate with Tenable, you need Tenable Vulnerability Management API access and secret keys for authentication. To generate the secret keys, you must have  Basic, Scan Operator, Standard, Scan Manager, or Administrator user roles in Tenable Vulnerability Management.

## Tenable configuration

Instructions for generating API keys for Tenable Vulnerability Management can be found [here](https://docs.tenable.com/vulnerability-management/Content/Settings/my-account/GenerateAPIKey.htm).

1. To generate API keys for your own account, access the My Account page.
2. Click the API Keys tab to view the API Keys section.
3. Select Generate, and note that the **Generate API Keys** window appears with a warning that Any existing API keys are replaced when you click the Generate button
4. Select **Generate.** Tenable Vulnerability Management generates new access and secret keys, and displays the new keys in the **Custom API Keys** section of the page.
5. Copy the new access and secret keys to a safe location.

> [!CAUTION]
>
> Be sure to copy the access and secret keys before you close the API Keys tab. After you close this tab, you cannot retrieve the keys from Tenable Vulnerability Management.

 6. If you have an Administrator account, you can generate API keys for any user account.

### For more information

To understand the Tenable API authorization model, see: [Authorization (tenable.com)](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdeveloper.tenable.com%2Fdocs%2Fauthorization&data=05|02|dlanger@microsoft.com|2f15f56aca59477d800108dcfdb761d8|72f988bf86f141af91ab2d7cd011db47|1|0|638664211268030543|Unknown|TWFpbGZsb3d8eyJFbXB0eU1hcGkiOnRydWUsIlYiOiIwLjAuMDAwMCIsIlAiOiJXaW4zMiIsIkFOIjoiTWFpbCIsIldUIjoyfQ%3D%3D|0|||&sdata=HMJD9P0Nqfot0ghZx9ZC7mmremd58oPuuKkVqGDmf1A%3D&reserved=0)

## Establish Tenable connection in Exposure Management

To establish a connection with Tenable in Exposure Management, follow these steps:

1. Open the [Data Connectors](https://security.microsoft.com/exposure-data-connectors) from the Exposure Management navigation and select **Connect** in the Tenable tile.
1. Enter your Tenable Access key and Secret key details and select **Connect**.

## Retrieved data

Exposure Management retrieves data on compute devices from Tenable, including machines and virtual machines. It also retrieves some networking data to identify those devices.

Only devices that were modified in the last 90 days are retrieved, based on assessing the "updated_at" field in the Tenable asset.

Exposure Management also retrieves vulnerability findings from Tenable on those assets.

The vulnerability data retrieved for Tenable is applicable to CVEs only, and not other types of vulnerabilities or misconfigurations. Tenable shows total vulnerability counts that include other non-CVE misconfigurations as well, so these counts are not applicable to the numbers of vulnerabilities ingested to Exposure Management.

### Assets/devices

| Category         | Properties                                                                 |
|------------------|----------------------------------------------------------------------------|
| **Assets/devices** | - biosUuid<br>- Net Bios names<br>- Operating systems<br>- Cloud Provider ID (e.g. Azure VM ID)<br>- System Types<br>- Tenable Criticality<br>- Network interfaces (see below) |
| **Network interface** | - IP information<br>- Mac address<br>- FQDNs |

> [!NOTE]
>
> To retrieve the data on criticality of your Tenable assets (Tenable [Asset Criticality Rating](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.tenable.com%2Fvulnerability-management%2FContent%2FLumin%2FLuminMetrics.htm%23ACR&data=05|02|dlanger@microsoft.com|2f15f56aca59477d800108dcfdb761d8|72f988bf86f141af91ab2d7cd011db47|1|0|638664211268041890|Unknown|TWFpbGZsb3d8eyJFbXB0eU1hcGkiOnRydWUsIlYiOiIwLjAuMDAwMCIsIlAiOiJXaW4zMiIsIkFOIjoiTWFpbCIsIldUIjoyfQ%3D%3D|0|||&sdata=vvsho76yIUdOqtQjjHLFvz8wyZ%2BD5Z694b6USengAso%3D&reserved=0)), you must have a [Tenable Lumin license](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.tenable.com%2Fvulnerability-management%2FContent%2FLumin%2FLuminGetStarted.htm&data=05|02|dlanger@microsoft.com|2f15f56aca59477d800108dcfdb761d8|72f988bf86f141af91ab2d7cd011db47|1|0|638664211268053146|Unknown|TWFpbGZsb3d8eyJFbXB0eU1hcGkiOnRydWUsIlYiOiIwLjAuMDAwMCIsIlAiOiJXaW4zMiIsIkFOIjoiTWFpbCIsIldUIjoyfQ%3D%3D|0|||&sdata=Jn%2FcNYVEFw4RdsRkHK4hF6f9%2FR9NPiSf9GQxAaz8zFQ%3D&reserved=0) with Tenable. See details here. Criticality on devices is used by Exposure Management to discover attack paths to the most critical devices in your environment.

## Troubleshooting the connector

Some common issues that might come up when configuring the Tenable connector.

### Temporary connection error (409) upon trying to connect

Elad Iwanir - what is the action here? Check permissions?

### Too many requests error (429) upon trying to connect

Elad Iwanir - what is the action here? Throttling? What to do?

### Unauthorized (401) or another permissions-related connection error when trying to connect

1. Make sure your Tenable.io account has Tenable Administrator role permissions
2. Try recreating your Access Key and Secret Key, following the instructions [here](https://docs.tenable.com/vulnerability-management/Content/Settings/my-account/GenerateAPIKey.htm)

### Not seeing my assets or the vulnerabilities reported by Tenable in the ingested data

See [Retrieved data](#retrieved-data) for a description of the data expected to be retrieved by the Tenable connector.

If there's still missing data, please contact Support.

### Seeing only vulnerability management data imported, not data from other Tenable products

The Tenable connector currently supports only vulnerability data from Tenable Vulnerability Management. If you're interested in other types of data, please enter a request through the **Request new connectors** feedback option on the **Data Connectors** page.

### Not seeing any Tenable data ingested

1. Ensure you Tenable connector is properly connected and not in an error state.
2. Run queries on the Exposure Graph via Advanced Hunting (as described in [Getting value from your data connectors](value-data-connectors.md)) to check for the Tenable sourced data.
3. If you're still not seeing any data ingested, please contact Support.

### Configure Tenable allowed IPs to enable Exposure Management connectors to access Tenable

Read how to add the set of IPs to add to your allowlist here:[Allowlist IP addresses](configure-data-connectors.md#allowlist-ip-addresses)

### I'm using Tenable Security Center (the on-premises version), can I connect to that via the Tenable connector?

We currently support only Tenable Vulnerability Management and don't support Tenable SC. We're working to add Tenable.sc in the future.

## Next steps

[Getting value from your data connectors](value-data-connectors.md).
