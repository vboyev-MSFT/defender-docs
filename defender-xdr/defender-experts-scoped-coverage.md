---
title: Scoped coverage in Microsoft Defender Experts for XDR
ms.reviewer:
description: Defender Experts scoped coverage covers a specific section of the organization where SOC support is limited.
ms.service: defender-experts
ms.subservice: dex-xdr
ms.author: vpattnaik
author: vpattnai
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
  - m365-security
  - tier1
ms.topic: conceptual
ms.custom: 
- cx-ti
- cx-dex
search.appverid: met150
ms.date: 12/19/2024
---

# Scoped coverage in Microsoft Defender Experts for XDR

**Applies to:**

- [Microsoft Defender XDR](microsoft-365-defender.md)

Microsoft Defender Experts for XDR offers scoped coverage for customers who wish to have Defender Experts cover only a section of their organization (for example, specific geography, subsidiary, or function) that requires security operations center (SOC) support or where their security support is limited.

You can define a specific set of devices and/or users for which Defender Experts will offer support. Any incident that impacts any of the defined set of devices and users will be considered in scope, and our experts will provide the necessary response actions to mitigate the threat.

Devices and users that are out of scope won't be supported by Defender Experts. If they're part of an incident where at least one device or user in scope is impacted, we'll keep you informed about the out-of-scope assets but won't take any response actions or offer guidance.

## Using Defender Experts scoped coverage

Defender Experts would create a pre-defined device and user group to which you can add devices and users which would then be considered as the set of assets that are in scope for this service.

Currently, we do not offer support to rename this group nor have the option to support nested groups. The devices and users would have to be added individually to the groups created.

> [!IMPORTANT]
> The device group must also be in the highest order of priority for the devices under it to be considered in scope. This is a known product limitation.

To set up scoped coverage, in the Microsoft Defender XDR portal, go to **System** > **Settings** > **Defender Experts** > (Missing info here. Where exactly)

You can also set up this service as part of your onboarding. [Learn more about getting started with Microsoft Defender Experts for XDR](get-started-xdr.md)


## Frequently asked questions

1. **What actions are covered in this service?**
   - This service doesn't change our pricing structure. You still pay for Defender Experts service based on E5 (and servers, Microsoft Defender for Cloud, and Open XDR) for your desired user base.
   - This service doesn't scope according to individual Microsoft Defender products and services (such as Microsoft Defender for Endpoint, Microsoft Defender for Office 365, or Microsoft Defender for Cloud). That is, the minimum baseline for scoped coverage will continue to be E5 license. 
   - There's no change in permissions for analysts in Defender Experts for XDR. Defender Experts analysts will still have access to your entire tenant and not just the scoped assets.

2. **Can I change the scoped assets later?**

   You're allowed to change the scoped assets based on your needs. Keep in mind that the changes you make might take some time to take effect in our service. We recommend that you take into account your organization's rhythm of business for incidents before and after the changes are made.

3. **What type of response actions does this service provide?**

   There's no changes to existing response actions that are in scope. Read our [FAQs related to Microsoft Defender Experts for XDR Managed response](../defender-xdr/frequently-asked-questions.md) to learn more.