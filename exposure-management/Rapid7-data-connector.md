---
title: Integrate Rapid7 data connector in Microsoft Security Exposure Management
description: Learn how to the Rapid7 data connector in Microsoft Security Exposure Management.
ms.author: dlanger
author: dlanger
manager: rayne-wiselman
ms.topic: overview
ms.service: exposure-management
ms.date: 09/24/2024
---

# Rapid7 data connector 

To set up the Rapid7 integration, you need the endpoint of your server, such as “us.api.insight.rapid7.com”. The connector authenticates with API Key Auth using an Endpoint and API Key.

## Rapid7 configuration

1. **Endpoint** - Find your Rapid7 endpoint. Follow the instructions [here](https://docs.rapid7.com/insight/navigate-the-insight-platform/#check-your-data-region).

2. **API Key** – This integration needs a user API key for a user that has permissions to fetch assets. To generate an API key, see details at [this link.](https://docs.rapid7.com/insight/managing-platform-api-keys/#api-keys-based-on-your-insight-account-role)

   > **Note:** *We have found that connecting with an organization key has been more successful than connecting with a user key. We recommend you opt for an organization key to increase the likelihood of a successful connection.*

## Establish ServiceNow connection in Exposure Management

1. Open the [Data Connectors](https://security.microsoft.com/exposure-data-connectors) from the Exposure Management navigation and select **Connect** in the Rapid7 tile.
1. Enter your Rapid7 Endpoint and API key details and select **Connect**.

## Next steps

[Getting value from your data connectors](leverage-data-connectors.md).
