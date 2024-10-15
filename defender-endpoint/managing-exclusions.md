---
# Required metadata
# For more information, see https://review.learn.microsoft.com/en-us/help/platform/learn-editor-add-metadata?branch=main
# For valid values of ms.service, ms.prod, and ms.topic, see https://review.learn.microsoft.com/en-us/help/platform/metadata-taxonomies?branch=main

title:       # Add a title for the browser tab
description: # Add a meaningful description for search results
author:      j0shbregman # GitHub alias
ms.author:   joshbregman # Microsoft alias
ms.service:  # Add the ms.service or ms.prod value
# ms.prod:   # To use ms.prod, uncomment it and delete ms.service
ms.topic:    # Add the ms.topic value
ms.date:     10/15/2024
---

# Managing Exclusions Reference

Each version of Defender for Endpoint provides management of exclusions via the supported management tools.  

## Managing Exclusions for Windows

### Endpoint Security Policy

|Exclusion Type | Reference |
| -------- | -------- |
| Antivirus exclusions   | `Microsoft Defender Antivirus exclusions` [Endpoint security policy](/defender-endpoint/manage-security-policies?toc=%2Fmem%2Fintune%2Ftoc.json&bc=%2Fmem%2Fbreadcrumb%2Ftoc.json)   |
| Attack Surface Reduction rule exclusions   | `Attack Surface Reduction` [Endpoint security policy](/defender-endpoint/enable-attack-surface-reduction#endpoint-security-policy) |


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

