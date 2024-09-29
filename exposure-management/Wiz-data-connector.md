---
title: Integrate Wiz data connector in Microsoft Security Exposure Management
description: Learn how to the Wiz data connector in Microsoft Security Exposure Management.
ms.author: dlanger
author: dlanger
manager: rayne-wiselman
ms.topic: overview
ms.service: exposure-management
ms.date: 09/19/2024
---

# Wiz data connector (Preview)

To integrate with Wiz, you need the Wiz URL, Client ID, and Client Secret.

## Wiz configuration

To obtain the Wiz URL, navigate to your user profile and copy the API Endpoint URL.

To get the Wiz Client ID and Client Secret:

1. Go to **Settings** > **Service Accounts**.
1. Select **Add Service Account**.
1. Provide a name for the new service account.
1. Choose the permission read: resources and select **Add Service Account**.
1. Copy the CLIENT SECRET immediately, as you won’t be able to do so later.
1. Copy the CLIENT ID from the Service Accounts page.

## Establish Wiz Connection in Exposure Management

1. Open the [Data Connectors](https://security.microsoft.com/exposure-data-connectors) from the Exposure Management navigation and select **Connect** in the Wiz tile.
1. Enter your Wiz API URL, Client ID, and Client secret details and select **Connect**.

## Next steps

[Getting value from your data connectors](leverage-data-connectors.md).
