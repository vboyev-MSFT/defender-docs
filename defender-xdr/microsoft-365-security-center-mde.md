---
title: Microsoft Defender for Endpoint in the Microsoft Defender portal
description: Get an overview of what to expect when running Microsoft Defender for Endpoint in the Microsoft Defender portal
ms.service: defender-xdr
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dansimp
author: diannegali
manager: deniseb
ms.date: 09/20/2024
audience: ITPro
ms.topic: conceptual
search.appverid: 
- MOE150
- MET150
ms.collection: 
- m365-security 
- tier2
ms.custom: admindeeplinkDEFENDER
appliesto:
- Microsoft Defender XDR
- Microsoft Defender for Endpoint
---

# Microsoft Defender for Endpoint in the Microsoft Defender portal

[!INCLUDE [Microsoft Defender XDR rebranding](../includes/microsoft-defender.md)]

[Microsoft Defender for Endpoint](/defender-endpoint/microsoft-defender-endpoint) is part of the Microsoft Defender portal, delivering a unified experience for security teams to manage incidents and alerts, hunt for threats, and automate investigations and responses The Microsoft Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) combines security capabilities that protect assets, and detect, investigate, and respond to threats.

## What to expect

### Incidents and alerts

Devices involved in incidents are shown in the Incidents page. You can view the details of the incident, including the devices involved, the alerts that triggered the incident, and the actions taken. You can apply actions to the incident, like isolating devices, collecting investigation packages, and more. 

Individual alerts are shown in the Alerts page. You can view the details of the alert, including the devices involved, the incident that the alert is part of, and the actions taken. You can also apply actions to the alert in the alert page.

### Hunting

Proactively search for threats, malware, and malicious activity across your endpoints, Office 365 mailboxes, and more by using [advanced hunting queries](advanced-hunting-overview.md). These powerful queries can be used to locate and review threat indicators and entities for both known and potential threats.

[Custom detection rules](custom-detection-rules.md) can be built from advanced hunting queries to help you proactively watch for events that might be indicative of breach activity and misconfigured devices.

### Action center

Action center shows you the investigations created by automated investigation and response capabilities. This automated, self-healing in the Microsoft Defender portal can help security teams by automatically responding to specific events.

[Learn more about the Action center](m365d-action-center.md).

### Endpoints section

View and manage the security of endpoints in your organization. If you've used the Microsoft Defender Security Center, it will look familiar.

:::image type="content" source="/defender/media/converge-2-endpoints.png" alt-text="The Endpoints quick launch bar in the Microsoft Defender portal" lightbox="/defender/media/converge-2-endpoints.png":::

### Access and reports

View reports, change your settings, and modify user roles.

:::image type="content" source="/defender/media/converge-4-access-and-reporting-new.png" alt-text="The Access and Reporting quicklaunch bar in the Microsoft Defender portal" lightbox="/defender/media/converge-4-access-and-reporting-new.png":::

### SIEM API connections

If you use the [Defender for Endpoint SIEM API](/defender-endpoint/configure-siem), you can continue to do so. We've added new links on the API payload that point to the alert page or the incident page in the Microsoft 365 security portal. New API fields include LinkToMTP and IncidentLinkToMTP. For more information, see [Redirecting accounts from Microsoft Defender for Endpoint to The Microsoft Defender portal](microsoft-365-security-mde-redirection.md).

### Email alerts

You can continue to use email alerts for Defender for Endpoint. We've added new links in the emails that point to the alert page or the incident page in The Microsoft Defender portal. For more information, see [Redirecting accounts from Microsoft Defender for Endpoint to The Microsoft Defender portal](microsoft-365-security-mde-redirection.md).

### Managed Security Service Providers (MSSP)

Logging in to multiple tenants simultaneously in the same browsing session is currently not supported in the unified portal. You can opt out of the automatic redirection by [reverting to the former Microsoft Defender for Endpoint portal](microsoft-365-security-mde-redirection.md#can-i-go-back-to-using-the-former-portal), to maintain this functionality until the issue is resolved.

## Related information

- [Microsoft Defender XDR](microsoft-365-defender.md)
- [Microsoft Defender for Endpoint in The Microsoft Defender portal](microsoft-365-security-center-mde.md)
- [Redirecting accounts from Microsoft Defender for Endpoint to The Microsoft Defender portal](microsoft-365-security-mde-redirection.md)

[!INCLUDE [Microsoft Defender XDR rebranding](../includes/defender-m3d-techcommunity.md)]
