---
title: Defender Experts scoped coverage
ms.reviewer:
description: Defender Experts scoped coverage covers a specific section of the organization where SOC support is limited
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

# Defender Experts Scoped coverage

**Applies to:**

- [Microsoft Defender XDR](microsoft-365-defender.md)

Defender experts scoped coverage for XDR is for customers who wish to have Defender Experts cover only a section of their organization (e.g., specific geo, subsidiary or function) that requires SOC support or where their SOC support is limited.

## Assets to be customized

You can define a specific set of devices and/or users for which Defender Experts would offer support. Any incident that impacts any of these defined set of devices and users would be considered in scope and would be offered the necessary response actions to mitigate the threat.

## How to use scoped coverage by Microsoft Defender Experts for XDR

Defender Experts would create a pre-defined device and user group to which you can add devices and users which would then be considered as the set of assets that are in scope for this service. Currently, we do not offer support to rename this group nor have the option to support nested groups. The devices and users would have to be added individually to the groups created. 

<[!NOTE]
> The device group must also be in the highest order of priority for the devices under that group to be considered in scope. (This is a known product limitation).

## How to initiate scoped coverage

You have the option to do this as part of onboarding or later via **Defender Experts** > **Settings** in the Microsoft Defender XDR portal.

## What happens to assets that are out of scope

Devices and users that are out of scope are not supported by Defender Experts. However, if they are part of an incident where at least one user or device in scope is impacted, we would keep you informed about the out-of-scope assets, and not take any response actions or offer guidance.

## Frequently asked questions

1. **What actions are not in scope for this service**

- Our pricing structure will not change. Customers would still pay for DEX based on E5 (and servers, MDC, OpenXDR) for their desired userbase.
- We won't support scoping by Defender products i.e. more granular pricing and coverage for individual Defender products like MDE, MDO or MDC. Our min baseline will continue to be E5.
- In Defender Experts for XDR, there is no change in permissions for analysts. Defender Experts Analysts will still have access to the entire tenant and not just the scoped assets.

2.**Will customers be allowed to change the scoped assets later?**

You are allowed to change the scoped assets based on your needs. Keep in mind that there will be some delay that we'd need to account for once the change is made. The rhythm of business for incidents before and after the changes are made would need to account for these changes getting propagated.

3.**What type of response actions would be provided?**

There will be no changes to existing response actions that are in scope, which are already defined at [FAQs related to Microsoft Defender Experts for XDR Managed response]()