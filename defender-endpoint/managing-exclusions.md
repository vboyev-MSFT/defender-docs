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
| Attack Surface reduction rule file and folder exclusions   | `Attack Surface Reduction` [Endpoint security policy](/defender-endpoint/enable-attack-surface-reduction#endpoint-security-policy) |
| Attack surface reduction rule per rule exclusion | |


### Intune


|Exclusion Type | Reference |
| -------- | -------- |
| Antivirus exclusions |  [Create new exclusions](https://learn.microsoft.com/en-us/defender-endpoint/configure-exclusions-microsoft-defender-antivirus#create-a-new-antivirus-policy-with-exclusions-in-intune)<BR>[manage existing exclusions](https://learn.microsoft.com/en-us/defender-endpoint/configure-exclusions-microsoft-defender-antivirus#manage-antivirus-exclusions-in-intune-for-existing-policies)
| Attack surface reduction rule file and folder exclusions | [Create exclusion for attack surface reduction rule](https://learn.microsoft.com/en-us/defender-endpoint/enable-attack-surface-reduction#custom-profile-in-intune)
| Attack surface reduction rule per rule exclusion | |

### Powershell

Use `Set-MpPreference` or `Get-MpPreference` from the [Defender Powershell Module](/powershell/module/defender/?view=windowsserver2022-ps) 

<table>
  <thead>
    <tr>
      <th>Exclusion Type</th>
      <th>Flag</th>
      <th>Description</th>
    </tr>
  </thead>
  <tr>
    <td rowspan="4">Antivirus exclusion</td><td><code>-ExclusionIpAddress<code></td><td><a href="https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference?view=windowsserver2022-ps#-exclusionipaddress">IP addresses to exclude from scheduled and real-time scanning</a></td>
  </tr>
  <tr>
    <td><code>-ExclusionPath</code></td><td><a href="https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference?view=windowsserver2022-ps#-exclusionpath">file paths to exclude from scheduled and real-time scanning</a></td>
  </tr>
  <tr>
    <td><code>-ExclusionProcess</td><td><a href="https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference?view=windowsserver2022-ps#-exclusionprocess">Files opened by these processes are excluded from scheduled and real-time scanning.</a></td>
  </tr>
  <tr>
    <td><code>-ExclusionExtension</code></td><td><a href="https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference?view=windowsserver2022-ps#-exclusionextension">File name extensions, such as obj or lib, to exclude from scheduled, custom, and real-time scanning</a></td>
  </tr>
  <tr>
    <td>Attack surface reduction rule file and folder exclusion</td><td><code>-AttackSurfaceReductionOnlyExclusions</code></td><td><a href="https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference?view=windowsserver2022-ps#-attacksurfacereductiononlyexclusions">Specifies the files and paths to exclude</a></td>
  </tr>
  <tr>
    <td>Attack surface reduction per rule exclusions</td><td colspan="2">Not supported</td>
  </tr>
</table>


### Configuration Manager

Use configuration manager to configure [antivirus exclusions](/defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus).

### Group Policy Object (GPO)

Use group policy to configure [antivirus exclusions.](/defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus)

### Windows Management Instrumentation (WMI)

Use WMI to configure [antivirus exclusions.](/defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus)

## Managing Exclusions for macOS

## Managing Exclusions for Linux

