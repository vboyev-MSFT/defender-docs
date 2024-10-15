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
ms.date: 10/17/2024
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

[Microsoft Defender for Endpoint](/defender-endpoint/microsoft-defender-endpoint) is part of the Microsoft Defender portal, delivering a unified experience for security teams to manage incidents and alerts, hunt for threats, and automate investigations and responses. The Microsoft Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) combines security capabilities that protect assets, and detect, investigate, and respond to threats.

Endpoints like laptops, phones, tablets, routers, and firewalls are the entry points to your network. Microsoft Defender for Endpoint helps you secure these endpoints by providing visibility into the activities on your network, and by detecting and responding to advanced threats.

This guide shows you what to expect when running Microsoft Defender for Endpoint in the Microsoft Defender portal.

## Know before you begin

To use Microsoft Defender for Endpoint in the Microsoft Defender portal, you need to have a Microsoft Defender for Endpoint license. For more information, see [Microsoft Defender for Endpoint licensing](/defender-endpoint/minimum-requirements#licensing-requirements).

## What to expect

### Exposure management

The Exposure management page shows you the devices in your organization that are exposed to threats. You can view onboarded and discovered devices, devices with critical and high vulnerabilities, attack surface map data for devices, critical assets, and more. You can also view the Microsoft Secure score for your organization, which is a measure of the security posture of your organization.

Data presented in the Exposure management page is delivered by Microsoft Security Exposure Management. For more information, see [Microsoft Security Exposure Management](/security-exposure-management/microsoft-security-exposure-management).

### Investigation and response

Investigation and response capabilities in the Microsoft Defender portal help you investigate and respond to incidents and alerts. Incidents are groups of alerts that are related to each other.

#### Incidents and alerts

Devices involved in incidents are shown in an incident's page [attack story](investigate-incidents.md#attack-story), incident graph, and [assets](investigate-incidents.md#assets) tab. You can view the details of the incident, including the devices involved, the alerts that triggered the incident, and the actions taken. You can apply actions to the incident, like isolating devices, collecting investigation packages, and more.

Individual alerts are shown in the Alerts page. You can view the details of the alert, including the devices involved, the incident that the alert is part of, and the actions taken. You can also apply actions to the alert in the alert page.

#### Hunting

Proactively search for threats, malware, and malicious activity across your endpoints, Office 365 mailboxes, and more by using [advanced hunting queries](advanced-hunting-overview.md). These powerful queries can be used to locate and review threat indicators and entities for both known and potential threats.

[Custom detection rules](custom-detection-rules.md) can be built from advanced hunting queries to help you proactively watch for events that might be indicative of breach activity and misconfigured devices.

#### Actions and submissions

The [Action center](m365d-action-center.md) shows you the investigations created by automated investigation and response capabilities. This automated, self-healing in the Microsoft Defender portal can help security teams by automatically responding to specific events. You can view actions applied to devices, the status of the actions, and approve or reject the automated actions.

You can submit files, email attachments, and URLs to Microsoft Defender for analysis in the [Submission portal](submission-guide.md). You can also view the status of the submissions and the results of the analysis.

### Assets

The Assets page contains the [device inventory](/defender-endpoint/machines-view-overview) page, which lists all the devices in your organization where alerts were generated. You can view the details of the devices, including the IP address, criticality level, device category, and device type.

### Endpoints

The Endpoints page contain the [Microsoft Defender Vulnerability Management](/defender-vulnerability-management/defender-vulnerability-management) data, including device exposure, Secure Score for devices, top vulnerable software, and top exposed devices in your organization. This page offers recommendations to help you improve the security posture of your organization, remediation actions, and more.

Security administrators can deploy endpoint security policies to devices in your organization under **Endpoints > Configuration management > Endpoint security policies**. Know more about [endpoint security policies](/defender-endpoint/manage-security-policies).

### Reports

You can view device health, vulnerable devices, monthly security summary, web protection, firewall, device control, and attack surface reduction rules reports in the **Reports** page.

### Device discovery

In the **Settings > Device discovery** page, you can configure device discovery settings, including the discovery method, exclusions, enabling Enterprise IOT (access dependent), and configure authenticated scan schedules. For more information, see [Device discovery](/defender-endpoint/device-discovery).

### General settings

Navigate to the **Settings > Endpoints** page to configure settings for Microsoft Defender for Endpoint, including advanced features, email notifications, permissions, and more.

#### Email notifications

You can create rules for specific devices, alert severities, and vulnerabilities to send email notifications to specific users or groups. For more information, see the following information:

- [Configure email notifications for alerts](configure-email-notifications.md)
- [Configure email notifications for vulnerabilities](/defender-endpoint/configure-vulnerability-email-notifications)

#### Permissions and roles

To manage roles, permissions, and device groups for endpoints, navigate to *Permissions* options under **Settings > Endpoints**. You can create and define role and assign permissions under *Roles* and create and organize devices into groups under *Device groups*.

Alternately, you can navigate to *Endpoints roles & groups* in the **System > Permissions** page.

#### APIs and MSSP

The Microsoft Defender XDR alerts API is the official API that enables customers to work with alerts across all Defender XDR products using a single integration. For more information, see [Migrate from the MDE SIEm API to the Microsoft Defender XDR alerts API](/defender-endpoint/configure-siem).

To authorize a managed security service provider (MSSP) to access receive alerts, you need to provide the application and tenant IDs of the MSSP. For more information, see [MSSP integration](/defender-endpoint/configure-mssp-support#mssp-integration).

#### Rules

You can create rules and policies to manage indicators, filter web content, manage automation uploads and automation folder exclusions, and more. To create these rules, navigate to *Rules* under **Settings > Endpoints**. More information on managing these rules can be found in the following links:

- [Manage indicators](/defender-endpoint/indicator-manage)
- [Manage automation uploads](/defender-endpoint/manage-automation-file-uploads)
- [Manage automation folder exclusions](/defender-endpoint/manage-automation-folder-exclusions)
- [Web content filtering](/defender-endpoint/web-content-filtering)

#### Configuration management

In **Settings > Endpoints > Configuration management > Enforcement scope**, you can allow Microsoft Intune security settings to be enforced by Microsoft Defender for Endpoint. For more information, see [Use Microsoft Intune to configure and manage Microsoft Defender Antivirus](/defender-endpoint/use-intune-config-manager-microsoft-defender-antivirus).

#### Device management

You can onboard or offboard devices and run a device detection test in the **Settings > Endpoints > Device management** page. See [Onboard to Microsoft Defender for Endpoint](/defender-endpoint/onboarding) to know the steps to onboard devices. To offboard devices, see [Offboard devices](/defender-endpoint/offboard-machines).

[!INCLUDE [Microsoft Defender XDR rebranding](../includes/defender-m3d-techcommunity.md)]
