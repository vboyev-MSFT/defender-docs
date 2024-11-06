---
title: Integrate Rapid7 data connector in Microsoft Security Exposure Management
description: Learn how to the Rapid7 data connector in Microsoft Security Exposure Management.
ms.author: dlanger
author: dlanger
manager: rayne-wiselman
ms.topic: overview
ms.service: exposure-management
ms.date: 11/06/2024
---

# Rapid7 data connector

To set up the Rapid7 integration, you need the endpoint of your Rapid7 Platform API, such as “us.api.insight.rapid7.com”. The connector authenticates with API Key Auth using an Endpoint and API Key.

## Rapid7 configuration

1. **Endpoint** - Find your Rapid7 endpoint. Follow the instructions [here](https://docs.rapid7.com/insight/api-overview#endpoint )
2. **API Key** – This integration needs a user API key for a user that has permissions to fetch assets. To generate an API key, see details at [this link.](https://docs.rapid7.com/insight/managing-platform-api-keys/#api-keys-based-on-your-insight-account-role)

   > **Note:** *We have found that connecting with an organization key has been more successful than connecting with a user key. We recommend you opt for an organization key to increase the likelihood of a successful connection.*

## Establish Rapid7 connection in Exposure Management

To establish a connection with Rapid7 in Exposure Management, follow these steps:

1. Open the [Data Connectors](https://security.microsoft.com/exposure-data-connectors) from the Exposure Management navigation and select **Connect** in the Rapid7 tile.
1. Enter your Rapid7 Endpoint and API key details and select **Connect**.

## Retrieved data

Exposure Management retrieves data on compute devices from Rapid7, including machines and virtual machines. It also retrieves vulnerabilities reported by Rapid7 on those devices.

Only devices that were actively scanned in the last 90 days are retrieved, based on assessing the "last_scan_end" field in the Rapid7 asset.

**Assets/devices, and data per each identifier**:

- Rapid7 ID
- Hostname
- IP address
- mac Address
- OS information
- Rapid7 risk score
- Tags
- Rapid7 criticality data
- Cloud platform

**Vulnerability findings**: Rapid7 retrieves CVE findings on the assets that it ingests.

## Troubleshooting the Rapid7 data connector

Some common issues that may come up when configuring the Rapid7 connector:

### “Temporary connectivity issues”, or 'The remote name couldn't be resolved' error upon trying to connect

Check the URL, make sure it aligns with instructions here [InsightVM Cloud Integrations API (rapid7.com)](https://nam06.safelinks.protection.outlook.com/?url=https:%2f%2fhelp.rapid7.com%2finsightvm%2fen-us%2fapi%2fintegrations.html&data=05|02|ronitr@microsoft.com|613676725a324b099c8508dcd8b812ae|72f988bf86f141af91ab2d7cd011db47|1|0|638623532338702698|Unknown|TWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D|0|||&sdata=YRvrsZ6xNm%2f1v1TvK2XeX0B7xWSjBaXHuf86yelRmTI%3D&reserved=0)

### Permissions-related connection error when trying to connect

Double check that your API Auth key has sufficient permissions for the connection. We have found that connecting with an organization key is more likely to enable establishing a connection successfully.

### Not seeing my assets or the vulnerabilities reported by Rapid7 in the ingested data

See [Retrieved data](#retrieved-data) for a description of the expected data to be retrieved by the Rapid7 connector.

If there's still missing data, please contact Support.

### Configure Rapid7 allowed IPs to enable Exposure Management connectors to access Rapid7

Read how to add the set of IPs to add to your allowlist here:[Allowlist IP addresses](configure-data-connectors.md#allowlist-ip-addresses).

## Next steps

[Getting value from your data connectors](value-data-connectors.md).
