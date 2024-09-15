---
title: Microsoft Defender portal overview
description: Learn about the Microsoft Defender portal
search.appverid: met150
ms.service: defender-xdr
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

Microsoft's unified security platform combines services in the [Microsoft Defender portal](https://security.microsoft.com). In the Defender portal, you can monitor and manage pre-breach and post-breach security across your organization's on-premises and multicloud assets and workloads.

In the Defender portal, you can visualize and monitor security state across the entire company. You can reduce risk by improving security posture and reducing attack surfaces. You can continuously detect, investigate, and respond to cybersecurity threats. The Defender portal provides quick and centralized access to security status, and consolidates security information and context for easy viewing and deep analysis. Microsoft services in the Defender portal include.

**Service** | **Details**
--- | ---
**[Microsoft Defender XDR](microsoft-365-defender.md)** | Provides a coordinated threat protection solution that integrating key services and capabilities, including Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Microsoft Defender for Cloud Apps, and Microsoft Defender for Identity.
**[Defender for Office 365](/defender-office-365/mdo-about)** | Helps secure organizations with a set of prevention, detection, investigation and hunting features to protect email, and Office 365 resources.
**[Defender for Endpoint](/defender-endpoint/)** | Delivers preventative protection, post-breach detection, automated investigation, and response for devices in the organization.
**[Defender for Identity](/defender-for-identity/what-is) | Provides a cloud-based security solution that uses on-premises Active Directory signals to identify, detect, and investigate advanced threats, compromised identities, and malicious insider actions directed at your organization.
**[Defender for Cloud Apps](defender-cloud-apps/what-is-defender-for-cloud-apps)** | Provides a comprehensive cross-SaaS and PaaS solution that brings deep visibility, strong data controls, and enhanced threat protection to your cloud apps.
**[Microsoft Sentinel](/azure/sentinel/overview)** Microsoft Sentinel is a cloud services that enables security information and event management (SIEM) and Provides in the Defender portal, Microsoft Sentinel integrates with Defender XDR to provide threat protection in the unified security operations platform. Microsoft Sentinel is a a cloud-native security information and event management (SIEM) solution and security orchestration automation response. Sentinel integrates with Defender XDR to provided a unified security platform for threat detection, investigation, hunting, and response.
**[Microsoft Defender for Cloud](/azure/defender-for-cloud/defender-for-cloud-introduction)** | Defender for Cloud improves multicloud and on-premises security posture, and protect cloud workloads against security threats. Defender for Cloud integrates into the Defender portal. Security teams can access Defender for Cloud alerts in the portal, providing a single location with added rich context for security investigations.
**[Microsoft Security Exposure Management](../../exposure-management/microsoft-security-exposure-management)** | Provides a unified view of security posture across organizational assets. With Security Exposure Management, you can assess the security state of assets, and identify and remediate security risk to reduce attack surfaces.
**[Microsoft Defender for IoT](../../defender-for-iot/microsoft-defender-iot)** | Integrates into the Defender portal to identify and protect OT/IT resources by extending Defender XDR protection to OT environments.


> [!NOTE]
> When you open the portal, you see only the security services included in your subscriptions. For example, if you have Defender for Office 365 but not Defender for Endpoint, you see features and capabilities for Defender for Office 365, but not for device protection. 

Watch this short video to learn more about the Defender portal.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWBKau]

## Portal permissions

Access to the Defender portal is configured with Microsoft Entra global roles, or using custom roles.

For Microsoft Sentinel, after you connect Microsoft Sentinel to the Defender portal, your existing Azure role-based access control (RBAC) permissions allow you to work with the Microsoft Sentinel features that you have access to. Continue to manage roles and permissions for your Microsoft Sentinel users from the Azure portal. Any Azure RBAC changes are reflected in the Defender portal.


:::image type="content" source="/defender/media/microsoft-365-defender-portal/defender-portal-permissions.png" alt-text="Screenshot of the permissions page in the Microsoft Defender portal" lightbox="/defender/media/microsoft-365-defender-portal/defender-portal-permissions.png":::

### Learn more 

- Learn how to [manage access](../m365d-permissions.md).
- Learn how to [create custom roles](../custom-roles.md).
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


## Investigate incidents and alerts

Centralizing security information creates a single place to investigate security incidents across your entire organization and all its components including:

- Hybrid identities
- Endpoints
- Cloud apps
- Business apps
- Email and docs
- IoT
- Network
- Business applications
- Operational technology (OT)
- Infrastructure and cloud workloads

A primary example is **Incidents** under **Incidents & alerts**.

:::image type="content" source="/defender/media/incidents-queue/incidents-ss-incidents.png" alt-text="The Incidents page in the Microsoft Defender portal." lightbox="/defender/media/incidents-queue/incidents-ss-incidents.png":::

Selecting an incident name displays a page that demonstrates the value of centralizing security information as you get better insights into the full extend of a threat, from email, to identity, to endpoints.

:::image type="content" source="/defender/media/incidents-overview/incidents-ss-incident-summary.png" alt-text="Screenshot that shows the attack story page for an incident in the Microsoft Defender portal." lightbox="/defender/media/incidents-overview/incidents-ss-incident-summary.png":::

Take the time to review the incidents in your environment, drill down into each alert, and practice building an understanding of how to access the information and determine next steps in your analysis.

Learn more about [incidents in the Defender portal](incidents-overview.md), and [managing incidents and alerts](manage-incidents.md).

## Hunt for threats

You can build custom detection rules and hunt for specific threats in your environment. **Hunting** uses a query-based threat hunting tool that lets you proactively inspect events in your organization to locate threat indicators and entities. These rules run automatically to check for, and then respond to, suspected breach activity, misconfigured machines, and other findings.

Learn about [proactive threat hunting](advanced-hunting-overview.md), and [hunting for threats across devices, emails, apps, and identities](./advanced-hunting-query-emails-devices.md).


## Respond to emerging threats

Threat analytics is the Microsoft threat intelligence solution from expert Microsoft security researchers.In the portal, track and respond to emerging threats with these threat analytics:

- Active threat actors and their campaigns
- Popular and new attack techniques
- Critical vulnerabilities
- Common attack surfaces
- Prevalent malware

Learn about [tracking and responding to emerging threats with threat analytics](threat-analytics.md).

## Partner catalog

The Defender portal has a couple of kinds of partner integration:

- Third-party integrations to help secure users with effective threat protection, detection, investigation, and response in various security fields of endpoints, vulnerability management, email, identities, and cloud apps.
- Professional services where organizations can enhance the detection, investigation, and threat intelligence capabilities of the platform.

## Send us your feedback

We need your feedback. If there's something you'd like to see, [watch this video to find out how you can trust us to read your feedback](https://www.microsoft.com/videoplayer/embed/RE4K5Ci).


