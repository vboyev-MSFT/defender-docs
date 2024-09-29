---
title: Integrate Wiz data connector in Microsoft Security Exposure Management
description: Learn how to integrate the Wiz data connector in Microsoft Security Exposure Management.
ms.author: dlanger
author: dlanger
manager: rayne-wiselman
ms.topic: overview
ms.service: exposure-management
ms.date: 09/29/2024
---

# Wiz data connector (Preview)

To integrate with Wiz, you need the Wiz URL, Client ID, and Client Secret. This article provides instructions on how to obtain these details and establish a connection between Wiz and Microsoft Security Exposure Management.

## Wiz configuration

To obtain the Wiz URL, navigate to your user profile and copy the API Endpoint URL.

Follow these steps to get the Wiz Client ID and Client Secret:

1. Go to **Settings** > **Service Accounts**.
1. Select **Add Service Account**.
1. Provide a name for the new service account.
1. Choose the permission read: resources and select **Add Service Account**.
1. Copy the **Client Secret** immediately, since it's not possible later.
1. Copy the **Client ID** from the Service Accounts page.

## Establish Wiz Connection in Exposure Management

To establish a connection between Wiz and Exposure Management, follow these steps:

1. Open the [Data connectors](https://security.microsoft.com/exposure-data-connectors) from the Exposure Management navigation and select **Connect** in the Wiz tile.
1. Enter your Wiz API URL, Client ID, and Client secret details and select **Connect**.

## Next steps

[Getting value from your data connectors](leverage-data-connectors.md).
