---
title: Investigate and respond to container threats in the Microsoft Defender portal
description: Investigate and respond to container attacks and threats with cloud investigation and response capabilities in the Microsoft Defender portal.
ms.service: defender-xdr
f1.keywords: 
  - NOCSH
ms.author: diannegali
author: diannegali
ms.localizationpriority: medium
manager: deniseb
audience: ITPro
ms.collection: 
  - m365-security
  - tier1
ms.topic: conceptual
search.appverid: 
  - MOE150
  - MET150
ms.date: 11/18/2024
appliesto:
- Microsoft Defender XDR
---
# Investigate and respond to container threats in the Microsoft Defender portal

[!INCLUDE [Microsoft Defender XDR rebranding](../includes/microsoft-defender.md)]

> [!IMPORTANT]
> Some information in this article relates to a prereleased product, which may be substantially modified before it’s commercially released. Microsoft makes no warranties expressed or implied, with respect to the information provided here

Security operations can now investigate and respond to container-related alerts in near real-time in the Microsoft Defender portal with the integration of cloud-native response actions and investigation logs to hunt for related activities. The availability of attack paths can also help analysts immediately investigate and address critical security issues to prevent a potential breach.

Organizations often use containers to support their microservices, DevOps, and hybrid cloud setup. However, containers can also be targeted by threat actors and used for malicious purposes.

Security operations center (SOC) analysts can now easily track container threats with near real-time alerts and immediately respond to these threats by isolating or terminating container pods. This integration allows analysts to instantly mitigate a container attack from their environment in a click.

Analysts can then investigate the full scope of the attack with the ability to hunt for related activities within the incident graph. They can also further apply preventive actions with the availability of potential attack paths in the incident graph. Using the information from the attack paths allows security teams to inspect the paths and prevent possible breaches. In addition, Threat analytics reports specific to container threats and attacks are available for analysts to gain more information and apply recommendations for container attack response and prevention.

## Prerequisites

The following licenses are required to view and resolve container-related alerts in the Defender portal:

- [Microsoft Defender for Containers enabled](/azure/defender-for-cloud/defender-for-containers-introduction)
- Microsoft Defender XDR

> [!Note]
> The **isolate pod** response action requires a network policy enforcer. Check whether your Kubernetes cluster has a network policy installed.

Users on the [Microsoft Defender for Cloud Security Posture Management](/azure/defender-for-cloud/concept-cloud-security-posture-management) plan can view attack paths in the incident graph.

Users with provisioned access to Microsoft Security Copilot can also take advantage of the guided responses delivered in the Microsoft Defender portal to investigate and remediate container threats.

## Permissions

To perform any of the response actions, users must have the following permissions for Microsoft Defender for Cloud in the Microsoft Defender XDR unified role-based access control:

|Permission name|Level|
|:---:|:---:|
|Alerts|Manage|
|Response|Manage|

For more information on these permissions, see [Permissions in Microsoft Defender XDR Unified role-based access control (RBAC)](custom-permissions-details.md).
