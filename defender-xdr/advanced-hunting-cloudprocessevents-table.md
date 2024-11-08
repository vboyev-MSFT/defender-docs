---
title: CloudProcessEvents table in the advanced hunting schema
description: Learn about 
search.appverid: met150
ms.service: defender-xdr
ms.subservice: adv-hunting
f1.keywords:
  - NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: 
- m365-security
- tier3
ms.custom: 
- cx-ti
- cx-ah
ms.topic: reference
ms.date: 11/08/2024
---

# CloudProcessEvents

[!INCLUDE [Microsoft Defender XDR rebranding](../includes/microsoft-defender.md)]

**Applies to:**
- Microsoft Defender XDR

The `CloudProcessEvents` table in the [advanced hunting](advanced-hunting-overview.md) schema contains information about events involving accounts and objects in Office 365 and other [cloud apps and services](#apps-and-services-covered). Use this reference to construct queries that return information from this table.


For information on other tables in the advanced hunting schema, [see the advanced hunting reference](advanced-hunting-schema-tables.md).

| Column name | Data type | Description |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Date and time when the event was recorded |
| `ActionType` | `string` | Type of activity that triggered the event |
| `Application` | `string` | Application that performed the recorded action |
| `ApplicationId` | `int` | Unique identifier for the application |




## Apps and services covered

The __CloudAppEvents__ table contains enriched logs from all SaaS applications connected to Microsoft Defender for Cloud Apps, such as:
- Office 365 and Microsoft Applications, including:
   - Exchange Online
   - SharePoint Online
   - Microsoft Teams
   - Dynamics 365
   - Skype for Business
   - Viva Engage
   - Power Automate
   - Power BI
   - Dropbox
   - Salesforce
   - GitHub
   - Atlassian

Connect supported cloud apps for instant, out-of-the-box protection, deep visibility into the app's user and device activities, and more. For more information, see [Protect connected apps using cloud service provider APIs](/defender-cloud-apps/protect-connected-apps).

## Related topics

- [Advanced hunting overview](advanced-hunting-overview.md)
- [Learn the query language](advanced-hunting-query-language.md)
- [Use shared queries](advanced-hunting-shared-queries.md)
- [Hunt across devices, emails, apps, and identities](advanced-hunting-query-emails-devices.md)
- [Understand the schema](advanced-hunting-schema-tables.md)
- [Apply query best practices](advanced-hunting-best-practices.md)

