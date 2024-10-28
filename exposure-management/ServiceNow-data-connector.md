---
title: Integrate ServiceNow data connector in Microsoft Security Exposure Management
description: Learn how to the ServiceNow data connector in Microsoft Security Exposure Management.
ms.author: dlanger
author: dlanger
manager: rayne-wiselman
ms.topic: overview
ms.service: exposure-management
ms.date: 09/24/2024
---

# ServiceNow data connector

To set up the ServiceNow integration, you need the hostname of your ServiceNow instance, such as “msft-xspm.service-now.com”. The connector authenticates with Basic Auth using username and password for read only access.

## ServiceNow configuration

1. Create a New ServiceNow user:
   1. Follow the steps [here](https://docs.servicenow.com/en-US/bundle/vancouver-platform-administration/page/administer/users-and-groups/task/t_CreateAUser.html) to create a new user.
   2. Keep the **username (User Id) and password** you provided for future use.
   3. If there’s no password field, submit the form to create the user. Afterwards, when you select on the new user, you receive the **Set Password** option.
   4. Check the **Web service access only** box.
2. Assign a **cmdb_read** role to the user you have created. Detailed instructions can be found [here](https://docs.servicenow.com/bundle/vancouver-platform-administration/page/administer/users-and-groups/task/t_AssignARoleToAUser.html).

> **Note:** The ServiceNow connector only supports Basic Authentication. OAuth authentication will be made available at a later time.


## Establish ServiceNow connection in Exposure Management

To establish a connection with ServiceNow in Exposure Management, follow these steps:

1. Open the [Data Connectors](https://security.microsoft.com/exposure-data-connectors) from the Exposure Management navigation and select **Connect** in the ServiceNow CMDB tile.
1. Enter your ServiceNow instance **details** (created in the ServiceNow configuration) and select **Connect**.

## Retreived data

## Troublehsooting the connector

Some common issues that may come up when configuring the ServiceNow CMDB connector:

Q: I'm getting a 'Bad URL' error  upon trying to connect
A: Double-check your ServiceNow Instance hostname. Learn more about authentication to ServiceNow here: [Authentication (servicenow.com)](https://docs.servicenow.com/bundle/vancouver-platform-security/page/integrate/single-sign-on/concept/c_Authentication.html)
 
Q: My ServiceNow connector shows a 'Temporary disconnected' or 'Temporary failure' error
A: **@Elad Iwanir - what should be the customer action here?**

Q: I'm not seeing some of my ServiceNow CMDB CIs in the ingested data.
A: See below for a description of the expected data to be retrieved by the ServiceNow CMDB connector.
   If there is still missing data, please contact Support.

Q: How can I configure my ServiceNow allowed IPs to enable Exposure Management connectors to access ServiceNow?
A: See how to add the set of IPs to add to your allowlist here:[Allowlist IP addresses](configure-data-connectors.md#allowlist-ip-addresses)

## Next steps

[Getting value from your data connectors](value-data-connectors.md).