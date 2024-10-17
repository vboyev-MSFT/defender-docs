---
title: Microsoft Defender portal overview
description: Learn about the Microsoft Defender portal
search.appverid: met150
ms.service: unified-secops-platform
ms.author: cwatson
author: cwatson-cat
ms.localizationpriority: medium
ms.date: 07/16/2024
audience: ITPro
ms.collection:
- M365-security-compliance
- tier1
- usx-security
ms.topic: conceptual
---

# Defender portal

Microsoft's unified security platform combines services in the [Microsoft Defender portal](https://security.microsoft.com). Use the Defender portal to monitor and manage pre-breach and post-breach security across on-premises and multicloud assets and workloads. The portal provides quick, centralized access to the state of security across the organization, consolidating security data and context for easy viewing and deep analysis. 

Microsoft services in the Defender portal include.

- Visualize and monitor security state across the entire company.
- Reduce risk by improving security posture and reducing attack surfaces.
- Continuously detect, investigate, and respond to cybersecurity threats. 


## Portal services

The Defender portal combines a number of Microsoft security services in a single location.

Service | Details
--- | ---
**[Microsoft Defender XDR](defender-xdr-portal.md)** | In the Defender portal, protect against security threats to assets and resources across the organization, including devices, email and collaboration tools, SaaS cloud apps, Entra ID threats, cloud and on-premises workloads, and OT/IT resources. Get integrated incidents and alerts, threat hunting, and threat protection services and capabilities included in Defender XDR.
**[Microsoft Defender Threat Intelligence](/defender/threat-intelligence/what-is-microsoft-defender-threat-intelligence-defender-ti)** | From the Defender portal, conduct threat infrastructure analysis, and gather threat intelligence.
**[Microsoft Security Exposure Management](/security-exposure-management/microsoft-security-exposure-management)** | In the Defender portal, get a unified view of security posture across organizational assets. Assess the security state of assets, and identify and remediate security risk to reduce attack surfaces.
**[Microsoft Defender for Cloud](/defender-xdr/microsoft-365-security-center-defender-cloud)** | Defender for Cloud improves multicloud and on-premises security posture, and protect cloud workloads against security threats. It integrates into the Defender portal so that security teams can access Defender for Cloud alerts in the portal, providing a single location with added rich context for security investigations.
**[Microsoft Defender for IoT](/defender-for-iot/microsoft-defender-iot)** | Defender for IoT integrates into the Defender portal to identify and protect OT/IT resources by extending Defender XDR protection to OT environments.

> [!NOTE]
> When you open the portal, you see only the security services included in your subscriptions. For example, if you have Defender for Office 365 but not Defender for Endpoint, you see features and capabilities for Defender for Office 365, but not for device protection. 

Watch this short video to learn more about the Defender portal.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWBKau]

## Portal permissions

Access to the Defender portal is configured with Microsoft Entra global roles, or using custom roles.

For Microsoft Sentinel, after you connect Microsoft Sentinel to the Defender portal, your existing Azure role-based access control (RBAC) permissions allow you to work with the Microsoft Sentinel features that you have access to. Continue to manage roles and permissions for your Microsoft Sentinel users from the Azure portal. Any Azure RBAC changes are reflected in the Defender portal.


:::image type="content" source="/defender/media/microsoft-365-defender-portal/defender-portal-permissions.png" alt-text="Screenshot of the permissions page in the Microsoft Defender portal" lightbox="/defender/media/microsoft-365-defender-portal/defender-portal-permissions.png":::

### Learn more 

- Learn how to [manage access](/defender-xdr/m365d-permissions).
- Learn how to [create custom roles](/defender-xdr/custom-roles).
- Learn about [roles and permissions in Microsoft Sentinel](/azure/sentinel/roles)
- [Manage access to Microsoft Sentinel data by resource](/azure/sentinel/resource-context-rbac)


## Working with the portal

The Defender portal helps you to investigate and respond to attacks by bringing in signals from different workloads into a set of unified experiences for:

- Incidents & alerts
- Hunting
- Actions & submissions
- Threat analytics
- Secure score
- Trials
- Partner catalog


## Quickly view your environment

The **Home** page shows many of the common cards that security teams need. The composition of cards and data is dependent on the user role. Because the Defender portal uses role-based access control, different roles see cards that are more meaningful to their day to day jobs.

This at-a-glance information helps you keep up with the latest activities in your organization. Microsoft Defender XDR brings together signals from different sources to present a holistic view of your Microsoft 365 environment.

You can add and remove different cards depending on your needs.

## Get notifications

Notifications are messages that inform you about important events or updates in the Defender portal. They help you stay on top of your security tasks and alerts.

:::image type="content" source="/defender/media/microsoft-365-defender-portal/notifications-panel.png" alt-text="Screenshot of the notifications icon in the Microsoft Defender portal." lightbox="/defender/media/microsoft-365-defender-portal/notifications-panel.png":::

Notifications are in the top bar of the portal's user interface. You can access them by clicking on the notification icon, which looks like a bell. A number on the icon indicates that you have that number of unread notifications.

Notifications can tell you about various types of events or updates:

- Success: when an action or task has been completed successfully like scanning a device or applying a policy.
- Ongoing: when an action is in progress.
- Information: when there is some information that you might find useful.
- Warning: when there is a potential issue or risk that you should be aware of like a device that is out of compliance or a policy that needs to be updated.
- Error: when there is an error or failure that requires your attention like an incident is deleted or merged, a scan that failed, or a policy that could not be applied.

Each notification has a title and content that provides relevant information about the event or update. Each notification also has a timestamp that shows when the notification was generated.

You can hide notifications from your view. You can dismiss a single notification by clicking on the *x* icon on the right side of the notification. You can also dismiss all notifications in the list with a single click by using *dismiss all* at the top of the notification panel.

Dismissing a notification does not delete it from the portal. You can always view your dismissed notifications by selecting  *show dismissed* at the bottom of the notification panel.

Notifications are sorted by their generated time in the notification panel, with the most recent ones displayed first. You can scroll through the list of notifications to see older ones.


## Get reports

In the portal, you can start with a general security report, and branch into specific reports about endpoints, email & collaboration. The links are dynamically generated based upon workload configuration.


## Search the portal

> [!IMPORTANT]
> Some information relates to prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here. The search bar is located at the top of the page. As you type, suggestions are provided so that it's easier to find entities. The enhanced search results page centralizes the results from all entities.

The Microsoft Defender portal's search function is located at the top of the page. As you type, suggestions are provided so that it's easier to find entities. The enhanced search results page centralizes the results from all entities.

:::image type="content" source="/defender/media/microsoft-365-defender-portal/search-panel.png" alt-text="Screenshot of the search bar in the Microsoft Defender portal." lightbox="/defender/media/microsoft-365-defender-portal/search-panel.png":::

Search results are categorized by sections related to your search terms. You can search across the following entities in the Microsoft Defender portal:

- **Devices** - supported for Defender for Endpoint, Defender for Identity, Defender for Cloud, and Microsoft Sentinel (Preview).
- **Users** - supported for Defender for Endpoint, Defender for Identity, Defender for Cloud Apps, and Microsoft Sentinel (Preview).
- **Files, IPs, and URLs** - same capabilities as in Defender for Endpoint.

  > [!NOTE]
  > IP and URL searches are exact match and don't appear in the search results page – they lead directly to the entity page.

- **Defender Vulnerability Management** - same capabilities as in Defender for Endpoint (vulnerabilities, software, and recommendations).

Search also provides results from relevant links in the Microsoft Tech Community portal, relevant documentation in Microsoft Learn, navigation items within the portal, and a link where you can provide feedback. Search history is stored in your browser and is accessible for the next 30 days.

## Partner catalog

The Defender portal has a couple of kinds of partner integration:

- Third-party integrations to help secure users with effective threat protection, detection, investigation, and response in various security fields of endpoints, vulnerability management, email, identities, and cloud apps.
- Professional services where organizations can enhance the detection, investigation, and threat intelligence capabilities of the platform.

## Send us your feedback

We need your feedback. If there's something you'd like to see, [watch this video to find out how you can trust us to read your feedback](https://www.microsoft.com/videoplayer/embed/RE4K5Ci).


