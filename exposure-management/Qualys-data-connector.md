---
title: Integrate Qualys data connector in Microsoft Security Exposure Management
description: Learn how to the Qualys data connector in Microsoft Security Exposure Management.
ms.author: dlanger
author: dlanger
manager: rayne-wiselman
ms.topic: overview
ms.service: exposure-management
ms.date: 09/24/2024
---

# Qualys data connector

To integrate with Qualys, you have to provide basic credentials for a Qualys user with **Manager** role or a **Reader** role with full scope.

## Qualys configuration

1. Get Qualys API URL
2. To set up the Qualys integration, you need the API_URL of your Qualys instance, such as “qualysapi.qg1.apps.qualys.co.uk”. You can find it [here](https://www.qualys.com/platform-identification/). .
   1. If you can't find it:
      1. Log in to your Qualys account.
      2. Go to **Help** → **About**.
      3. You'll see the required information under **Security Operations Center** (SOC).
3. Make sure the user intended to be used in the login credentials for connector has the necessary permissions:
4. Create the **Read** **Asset** role:
   1. Log in to Qualys.
   2. Go to **Administration** area.
   3. Go to the **Role Management** section.
   4. Select New Role.
   5. Fill in role name.
   6. Fill in the role permissions.
   7. Make sure to check API Access.
   8. From the **Modules** drop down, choose Asset View.
   9. To limit the permissions, choose the **Change** option within the **Asset View** selected module.
   10. Make sure to enable, at least, **Read Asset** under **Asset Management Permissions**.
5. Add the newly created role to the user you intend to authenticate with in the Exposure Management Qualys Connector.
   1. Under **Administration** go to **User** **Management**.
   2. Select the user you onboarded with the Exposure Management Qualys Connector and choose **Edit**.
6. Under **Roles and Scopes**, add the Read Asset role created in previous sections to the user assigned roles.
7. Allow full scope by checking the **Allow user view access to all objects** option.

## Establish Qualys connection in Exposure Management

To establish a connection with Qualys in Exposure Management, follow these steps:

1. Open the [Data Connectors](https://security.microsoft.com/exposure-data-connectors) from the Exposure Management navigation and select **Connect** in the Qualys tile.
1. Enter your Qualys API URL and authentication credentials and select **Connect**.

## Retrieved Qualys data

[QualysAssetInfoAdditionalData.json - Repos (azure.com)](https://dev.azure.com/msazure/CESEC/_git/XSPM-Orion-IngestionClientContracts?path=/src/EnterpriseGraphDataModel/DataModelDefinitions/AdditionalData/QualysAssetInfoAdditionalData.json&version=GBmain&_a=contents)

**Assets/devices**

- Gateway address
- FQDN
- IP address
- mac Address
- OS information
- Qualys criticality data

**Vulnerability findings: only CVEs.**

## Troubleshooting the Qualys data connector

Some common issues that may come up when configuring the Qualys connector.

### Temporary connection error or temporary connectivity issues (401 or 409) upon trying to connect

Elad Iwanir - what is the action here? Check permissions? TBD -- share the curl commands to run to check permissions/ access

### Connection error (409) upon trying to connect

Elad Iwanir - Do we reflect that Knowledge_base_api access fails? Link to the steps to fix this

### Not seeing my assets or the vulnerabilities reported by Qualys in the ingested data

See [Retrieved Qualys data](#retrieved-qualys-data) for a description of the expected data to be retrieved by the Qualys connector.
If there is still missing data, please contact Support.

### Configure Qualys allowed IPs to enable Exposure Management connectors to access Qualys

Read how to add the set of IPs to add to your allowlist here:[Allowlist IP addresses](configure-data-connectors.md#allowlist-ip-addresses).

## Next steps

[Getting value from your data connectors](value-data-connectors.md).
