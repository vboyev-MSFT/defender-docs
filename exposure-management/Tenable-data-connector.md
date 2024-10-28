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

To integrate with Tenable, you need to create an Access Key and Secret Key on Tenable.io. You additionally need to have a Tenable.io account with the role of Tenable Administrator to successfully set up the integration.

## Tenable configuration

For more information on generating your access and secret keys, see [here](https://docs.tenable.com/tenableio/Content/Platform/Settings/MyAccount/GenerateAPIKey.htm).

## Establish Tenable connection in Exposure Management

To establish a connection with Tenable in Exposure Management, follow these steps:

1. Open the [Data Connectors](https://security.microsoft.com/exposure-data-connectors) from the Exposure Management navigation and select **Connect** in the Tenable tile.
1. Enter your Tenable Secret key and Access key details and select **Connect**.

## Retrieved data

Exposure Management currently retrieves data on devices and vulnerabilities from Tenable.

The following fields are ingested via the connector: [TenableAssetInfoAdditionalData.json - Repos (azure.com)](https://dev.azure.com/msazure/CESEC/_git/XSPM-Orion-IngestionClientContracts?path=/src/EnterpriseGraphDataModel/DataModelDefinitions/AdditionalData/TenableAssetInfoAdditionalData.json&version=GBmain&_a=contents)

**Assets/devices**
- IP info
- FQDN

**Network adapter**
- Mac address
- OS
- Hostnames

**Vulnerability findings**
- CVEs

## Troubleshooting the connector

Some common issues that might come up when configuring the Tenable connector.

### Temporary connection error (409) upon trying to connect

Elad Iwanir - what is the action here? Check permissions?

###  Too many requests error (429) upon trying to connect

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
