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

### ServiceNow configuration

1. Create a New ServiceNow user:
   1. Follow the steps [here](https://docs.servicenow.com/en-US/bundle/vancouver-platform-administration/page/administer/users-and-groups/task/t_CreateAUser.html) to create a new user.
   2. Keep the **username (User Id) and password** you provided for future use.
   3. If there’s no password field, submit the form to create the user. Afterwards, when you select on the new user, you receive the **Set Password** option.
   4. Check the **Web service access only** box.
2. Assign a **cmdb_read** role to the user you have created. Detailed instructions can be found [here](https://docs.servicenow.com/bundle/vancouver-platform-administration/page/administer/users-and-groups/task/t_AssignARoleToAUser.html).

### Establish ServiceNow connection in Exposure Management

To establish a connection with ServiceNow in Exposure Management, follow these steps:

1. Open the [Data Connectors](https://security.microsoft.com/exposure-data-connectors) from the Exposure Management navigation and select **Connect** in the ServiceNow CMDB tile.
1. Enter your ServiceNow instance **details** (created in the ServiceNow configuration) and select **Connect**.

### Next steps

[Getting value from your data connectors](value-data-connectors.md).
