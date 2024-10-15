---
# Required metadata
# For more information, see https://review.learn.microsoft.com/en-us/help/platform/learn-editor-add-metadata?branch=main
# For valid values of ms.service, ms.prod, and ms.topic, see https://review.learn.microsoft.com/en-us/help/platform/metadata-taxonomies?branch=main

title: Managing exclusions
description: Information about how to manage exclusions in MDE
author:      j0shbregman # GitHub alias
ms.author:   joshbregman # Microsoft alias
ms.service: defender-endpoint
ms.topic: reference
ms.date:     10/15/2024
ms.subservice: reference
---

# Managing Exclusions

Each version of Defender for Endpoint provides management of exclusions via the supported management tools.  

## Managing Exclusions for Windows

### Defender Portal

Use the `Microsoft Defender Antivirus exclusions` [Endpoint security policy](/defender-endpoint/manage-security-policies?toc=%2Fmem%2Fintune%2Ftoc.json&bc=%2Fmem%2Fbreadcrumb%2Ftoc.json) to manage defender antivirus exclusions

### Intune

[Create new exclusions](https://learn.microsoft.com/en-us/defender-endpoint/configure-exclusions-microsoft-defender-antivirus#create-a-new-antivirus-policy-with-exclusions-in-intune) or [manage existing exclusions](https://learn.microsoft.com/en-us/defender-endpoint/configure-exclusions-microsoft-defender-antivirus#manage-antivirus-exclusions-in-intune-for-existing-policies) from Intune.

### Powershell

Use `Set-MpPreference` or `Get-MpPreference` from the [Defender Powershell Module](/powershell/module/defender/?view=windowsserver2022-ps) 

### Configuration Manager

Use configuration manager to configure [antivirus exclusions](/defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus).

### Group Policy Object (GPO)

Use group policy to configure [antivirus exclusions.](/defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus)

### Windows Management Instrumentation (WMI)

Use WMI to configure [antivirus exclusions.](/defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus)

## Managing Exclusions for macOS

## Managing Exclusions for Linux

