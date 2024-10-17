---
title:  Managing exclusions reference
description: This aritcle describes various ways to manage exclusions for Defender for Endpoint and Microsoft Defender Antivirus
author: denisebmsft
ms.author: deniseb
ms.reviewer: joshbregman
ms.service: defender-endpoint
ms.subservice: onboard
ms.topic: how-to
ms.localizationpriority: medium
ms.date: 10/17/2024
search.appverid: met150
ms.custom: 
- partner-contribution
ms.collection: 
- m365-security
- tier2
---

# Managing Exclusions Reference

Each version of Defender for Endpoint provides management of exclusions via the supported management tools.  

## Managing Exclusions for Windows

### Defender portal

Many exclusions can be managed from the [Microsoft Defender portal](https://security.microsoft.com).

| Exclusion Type | Instructions |
|-----|----|
| Custom antivirus exclusions | 1. In the [Microsoft Defender portal](https://security.microsoft.com), go to **Endpoints** > **Configuration Management** > **Endpoint security policies** > **Windows policies**. <br/> 2. Select **Create New Policy**. <br.> 3. For **Platform**, select **Windows 10, Windows 11, and Windows Server**. <br/>4. Select a template. Both **Microsoft Defender Antivirus exclusions** and **Microsoft Defender Antivirus** support custom antivirus exclusions. |
| Attack surface reduction only exclusions | 1. In the [Microsoft Defender portal](https://security.microsoft.com), go to **Endpoints** > **Configuration Management** > **Endpoint security policies** > **Windows policies**. <br/> 2. Select **Create New Policy** <br/> 3. For **Platform**, select **Windows 10, Windows 11, and Windows Server**. <br/> 4. Select the **Attack Surface Reduction Rules** template. |
| Attack surface reduction rule per rule exclusion | Not supported in the [Microsoft Defender portal](https://security.microsoft.com).  |
| Automatic antivirus exclusions | Not supported in the [Microsoft Defender portal](https://security.microsoft.com). |

> [!NOTE]
> `IP Address Exclusions` cannot be configured from the [Microsoft Defender portal](https://security.microsoft.com).

**Learn More**:

- [Use Microsoft Defender for Endpoint Security Settings Management to manage Microsoft Defender Antivirus](/defender-endpoint/mde-security-settings-management)

### Intune

Many exclusions can be managed in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).

| Exclusion Type | Instructions |
|-----           | ----     |
| Custom antivirus exclusion  | 1. In the [Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Home** > **Endpoint security** > **Antivirus**. <br/> 2. Select **Create Policy**. <br/> 3. For **Platform**, select **Windows**. <br/> 4. Select a template. Both **Microsoft Defender Antivirus exclusions** and **Microsoft Defender Antivirus** support custom antivirus exclusions |
| Attack surface reduction rule only exclusions | 1. In the [Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Home** > **Endpoint security** > **Attack surface reduction**. <br/> 2. Select **Create Policy**. <br/> 3. For **Platform**, select **Windows**. <br/> 4. For **Profile**, select **Attack surface reduction rules**. <br/>5. Under **Configuration Settings**, scroll down to **Attack Surface Reduction Only Exclusions**. |
| Attack surface reduction per-rule exclusions | 1. In the [Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Home** > **Endpoint security** > **Attack surface reduction**. <br/> 2. Select **Create Policy**. <br/> 3. For **Platform**, select **Windows**. <br/> 4. For **Profile**, select **Attack surface reduction rules**. <br/> 5. Under **Configuration Settings**, scroll down to the rule to create an exclusion. <br/> 6. Change it from `Not configured` to `Block`,`Audit`, or `Warn`. <br/>7. Select **Add** to enter the path to be excluded. |
| Automatic antivirus exclusions | Not supported in the [Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).|

**Learn More**:

- [Create a new antivirus policy with exclusions in Intune](/defender-endpoint/configure-exclusions-microsoft-defender-antivirus#create-a-new-antivirus-policy-with-exclusions-in-intune)
- [Manage antivirus exclusions in Intune (for existing policies)](/defender-endpoint/configure-exclusions-microsoft-defender-antivirus#manage-antivirus-exclusions-in-intune-for-existing-policies)
- [Configure attack surface reduction per-rule exclusions](/defender-endpoint/attack-surface-reduction-rules-deployment-test#configure-attack-surface-reduction-per-rule-exclusions)


### MDM

| Exclusion type | OMA-URI | Description | 
|--|--|--|
| Custom antivirus exclusion | `./Device/Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses` | [ExcludedProcesses](/windows/client-management/mdm/policy-csp-defender#excludedprocesses) |
| Custom antivirus exclusion | `./Device/Vendor/MSFT/Policy/Config/Defender/ExcludedPaths` | [ExcludedPaths](/windows/client-management/mdm/policy-csp-defender#excludedpaths)
| Custom antivirus exclusion | `./Device/Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions` | [ExcludedExtensions](/windows/client-management/mdm/policy-csp-defender#excludedextensions) |
| Attack surface reduction only exclusions | `./Device/Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions` | [AttackSurfaceReductionOnlyExclusions](/windows/client-management/mdm/policy-csp-defender#attacksurfacereductiononlyexclusions) |


**Learn more**:

- [Defender CSP](/windows/client-management/mdm/defender-csp)
- [Defender Policy CSP](/windows/client-management/mdm/policy-csp-defender)
- [Use custom settings for Windows client devices in Intune](/mem/intune/configuration/custom-settings-windows-10)

### Powershell

Use `Set-MpPreference` or `Get-MpPreference` from the [Defender Powershell Module](/powershell/module/defender/?view=windowsserver2022-ps) 

| Exclusion type | Flag | Description |
|---|---|---|
| Custom antivirus exclusion | `ExclusionIpAddress` | [IP addresses to exclude from scheduled and real-time scanning](/powershell/module/defender/set-mppreference?view=windowsserver2022-ps&preserve-view=true#-exclusionipaddress) |
| Custom antivirus exclusion | `ExclusionPath` | [File paths to exclude from scheduled and real-time scanning](/powershell/module/defender/set-mppreference?view=windowsserver2022-ps&preserve-view=true#-exclusionpath) |
| Custom antivirus exclusion | `ExclusionProcess` | [Files opened by these processes are excluded from scheduled and real-time scanning](/powershell/module/defender/set-mppreference?view=windowsserver2022-ps&preserve-view=true#-exclusionprocess) |
| Custom antivirus exclusion | `ExclusionExtension` | [File name extensions, such as obj or lib, to exclude from scheduled, custom, and real-time scanning](/powershell/module/defender/set-mppreference?view=windowsserver2022-ps&preserve-view=true#-exclusionextension) |
| Attack surface reduction only exclusion | `AttackSurfaceReductionOnlyExclusions` | [Specifies the files and paths to exclude](/powershell/module/defender/set-mppreference?view=windowsserver2022-ps&preserve-view=true#-attacksurfacereductiononlyexclusions) | 
| Attack surface reduction per-rule exclusion | N/A | Not supported |
| Automatic antivirus exclusions <br/>(*Only available on Windows Server 2016 and later*) | `DisableAutoExclusions` | [Disable automatic antivirus exclusions](/powershell/module/defender/set-mppreference?view=windowsserver2022-ps&preserve-view=true#-disableautoexclusions) |


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
- [Add exclusions to network protection](/defender-endpoint/troubleshoot-np#add-exclusions)
- [Important points about exclusions](/defender-endpoint/configure-exclusions-microsoft-defender-antivirus#important-points-about-exclusions)
