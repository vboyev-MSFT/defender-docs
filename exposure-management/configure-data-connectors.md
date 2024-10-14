---
title: Configuring the data connectors in Microsoft Security Exposure Management
description: Learn about configuring the data connectors in Microsoft Security Exposure Management.
ms.author: dlanger
author: dlanger
manager: rayne-wiselman
ms.topic: overview
ms.service: exposure-management
ms.date: 09/11/2024
---

# Configure your data connectors

To establish a connection with any of the supported external products, follow these steps:

1. Complete the applicable prerequisite steps for your external data connectors.
    1. Each of the connectors have explicit instructions for setting up valid credentials and creating the connection.
     - [ServiceNow CMDB](ServiceNow-data-connector.md)
     - [Qualys VM](Qualys-data-connector.md)
     - [Rapid7 VM](Rapid7-data-connector.md)
     - [Tenable](Tenable-data-connector.md)
     - Wiz (coming soon)
     - Palo Alto (coming soon)
     
1. Go to **Data Connectors** in the Exposure Management navigation.
1. Select **Connect** on the selected data connector from the external connectors catalog.
1. A side pane opens with the relevant connectivity details. Fill in the required fields and select **Connect**.
1. The data connector is now connected and will start ingesting data from the external source.

> **Note:** It may take up to an hour for data to start flowing after the data connector is configured.

## Allowlist IP addresses

To ensure successful connections between your external products and our system, you may need to allowlist specific IP addresses. Follow these steps to allowlist IP addresses for your external products:

1. **Identify the IP Addresses**:
   - Obtain the list of IP addresses that need to be allowlisted. 
2. **Access the External Product's Configuration Settings**:
   - Log in to the external product's administration or configuration portal.
   - Navigate to the section where you can manage network settings or security settings.
3. **Add the IP Addresses to the Allowlist**:
   - Locate the allowlist.
   - Enter the IP addresses that you obtained in step 1.
   - Save the changes to update the allowlist.
4. **Verify the Connection**:
   - After updating the allowlist, verify that the connection between the external product and our system is successful.
   - Check for any error messages or connection issues and ensure that the allowlisted IP addresses are correctly configured.
5. **Troubleshooting**:
   - If you encounter any issues, double-check the IP addresses and ensure they are correctly entered.
   - Refer to the external product's documentation for additional troubleshooting steps or contact their support team for assistance.

For specific instructions on allowlisting IP addresses for each external product, please refer to their respective documentation or support resources.

## Next steps

Select the external data connector you want to configure and follow the steps to connect it to Exposure Management.

- [CMDB data connectors](ServiceNow-data-connector.md)
- [Vulnerability management data connectors](Qualys-data-connector.md)
- Cloud security data connectors (coming soon)
