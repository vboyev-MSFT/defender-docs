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

### Defender portal

Many exclusions can be managed from [Defender portal](https://security.microsoft.com)

| Exclusion Type | Instructions |
|-----           | ----     |
| Custom antivirus exclusions | 1. Navigate to `Endpoints > Configuration Management > Endpoint security policies > Windows policies` <BR> 2. Click on `Create New Policy` <BR> 3. Select Platform `Windows 10, Windows 11, and Windows Server` 4.  Select a template. Both `Microsoft Defender Antivirus exclusions` and `Microsoft Defender Antivirus` support custom antivirus exclusions |
| Attack Surface Reduction only exclusions | 1. Navigate to `Endpoints > Configuration Management > Endpoint security policies > Windows policies` <BR> 2. Click on `Create New Policy` <BR> 3. Select Platform `Windows 10, Windows 11, and Windows Server` 4. Select the `Attack Surface Reduction Rules` template |
| Attack surface reduction rule per rule exclusion | Not supported |
| Automatic antivirus exclusions | Not supported |

> [!NOTE]
> `IP Address Exclusions` cannot be configured from the Defender portal.

Learn More
- [Use Microsoft Defender for Endpoint Security Settings Management to manage Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/mde-security-settings-management)



### Intune

Many exclusions can be managed from [Intune portal](https://endpoint.microsoft.com)

| Exclusion Type | Instructions |
|-----           | ----     |
| Custom antivirus exclusion  | 1. Navigate to ` Home > Endpoint security > Antivirus` <BR> 2. Click on `Create Policy` <BR> 3. Select `Windows` as the platform <BR> 4. Both `Microsoft Defender Antivirus exclusions` and `Microsoft Defender Antivirus` support custom antivirus exclusions |
| Attack Surface Reduction only exclusions | 1. Navigate to ` Home > Endpoint security > Attack surface reduction` <BR> 2. Click on `Create Policy` <BR> 3. Select `Windows` as the platform <BR> 4. Select `Attack surface reduction rules` profile. <br>5. Under `Configuration Settings`, scroll down to `Attack Surface Reduction Only Exclusions` |
| Attack surface reduction per rule exclusion | 1. Navigate to ` Home > Endpoint security > Attack surface reduction` <BR> 2. Click on `Create Policy` <BR> 3. Select `Windows` as the platform <BR> 4. Select `Attack surface reduction rules` profile. <br>5. Under `Configuration Settings`, scroll down to the rule to create an exclusion.  <br>6.  Change it from `Not configured` to `Block`,`Audit`, or `Warn`. <br>7. Click on `Add` to enter the path to be excluded. |
| Automatic antivirus exclusions | Not supported |

Learn More
- [Create a new antivirus policy with exclusions in Intune](https://learn.microsoft.com/en-us/defender-endpoint/configure-exclusions-microsoft-defender-antivirus#create-a-new-antivirus-policy-with-exclusions-in-intune)
- [Manage antivirus exclusions in Intune (for existing policies)](https://learn.microsoft.com/en-us/defender-endpoint/configure-exclusions-microsoft-defender-antivirus#manage-antivirus-exclusions-in-intune-for-existing-policies)
- [Configure attack surface reduction per-rule exclusions](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment-test#configure-attack-surface-reduction-per-rule-exclusions)


### MDM

<table>
  <thead>
    <tr>
      <th>Exclusion Type</th>
      <th>OMA-URI</th>
      <th>Description</th>
    </tr>
  </thead>
  <tr>
    <td rowspan=3>Custom antivirus exclusion</td><td>./Device/Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses</td><td><a href="https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-defender#excludedprocesses">ExcludedProcesses</a></td>
  </tr>
  <tr>
    <td>./Device/Vendor/MSFT/Policy/Config/Defender/ExcludedPaths</td><td><a href="https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-defender#excludedpaths">ExcludedPaths</a></td>
  </tr>
  <tr><td>./Device/Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions</td><td><a href="https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-defender#excludedextensions">ExcludedExtensions</a><td></tr>
  <tr>
    <td>Attack Surface Reduction only exclusions</td><td>./Device/Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions</td><td><a href="https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-defender#attacksurfacereductiononlyexclusions">AttackSurfaceReductionOnlyExclusions</a></td><tr>
  <tr>
</table>

Learn more
- [Defender CSP](https://learn.microsoft.com/en-us/windows/client-management/mdm/defender-csp)
- [Defender Policy CSP](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-defender)
- [Use custom settings for Windows client devices in Intune](https://learn.microsoft.com/en-us/mem/intune/configuration/custom-settings-windows-10)

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
    <td rowspan="4">Custom antivirus exclusion</td><td><code>-ExclusionIpAddress<code></td><td><a href="https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference?view=windowsserver2022-ps#-exclusionipaddress">IP addresses to exclude from scheduled and real-time scanning</a></td>
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
    <td>Attack Surface Reduction only exclusions</td><td><code>-AttackSurfaceReductionOnlyExclusions</code></td><td><a href="https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference?view=windowsserver2022-ps#-attacksurfacereductiononlyexclusions">Specifies the files and paths to exclude</a></td>
  </tr>
  <tr>
    <td>Attack surface reduction per rule exclusions</td><td colspan="2">Not supported</td>
  </tr>
  <tr>
    <td>Automatic antivirus exclusions</td><td><code>-DisableAutoExclusions</code></td><td><a href="https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference?view=windowsserver2022-ps#-disableautoexclusions">Disable automatic antivirus exclusions<a/></td>
  </tr>
</table>

> [!NOTE]
> `Automatic antivirus exclusions` are only available on Windows Server 2016 or later

### Configuration Manager

|Exclusion Type | Reference |
| -------- | -------- |
| Custom antivirus exclusion | Use configuration manager to configure [antivirus exclusions](/defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus).|
| Attack Surface Reduction only exclusions ||
| Attack surface reduction rule per rule exclusion | Not supported |
| Automatic antivirus exclusions ||


### Group Policy Object (GPO)

|Exclusion Type | Reference |
| -------- | -------- |
| Custom antivirus exclusion | Use group policy to configure [antivirus exclusions.](/defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus) |
| Attack Surface Reduction only exclusions ||
| Attack surface reduction rule per rule exclusion | Not supported |
| Automatic antivirus exclusions ||



### Windows Management Instrumentation (WMI)

|Exclusion Type | Reference |
| -------- | -------- |
| Custom antivirus exclusion | Use WMI to configure [antivirus exclusions.](/defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus)|
| Attack Surface Reduction only exclusions ||
| Attack surface reduction rule per rule exclusion | Not supported |
| Automatic antivirus exclusions ||



## Managing Exclusions for macOS

## Managing Exclusions for Linux

## Managing Exclusions for Network Protection

> [!NOTE]
> A process exclusion on any platform causes network protection to be unable to inspect traffic or enforce rules for that specific process.

Learn More
- [Add exclusions to network protection](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-np#add-exclusions)
- [Important points about exclusions](https://learn.microsoft.com/en-us/defender-endpoint/configure-exclusions-microsoft-defender-antivirus#important-points-about-exclusions)
