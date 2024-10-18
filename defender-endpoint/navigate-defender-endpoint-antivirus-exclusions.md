---
title: Exclusions overview
description: Learn how to navigate exclusions for Defender for Endpoint and Microsoft Defender Antivirus.
ms.service: defender-endpoint
ms.subservice: ngp
ms.localizationpriority: medium
ms.topic: how-to
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2024
ms.reviewer: joshbregman
manager: deniseb
ms.collection: 
- m365-security
- tier2
- mde-ngp
search.appverid: met150
---

# Exclusions overview 

[!INCLUDE [Microsoft Defender XDR rebranding](../includes/microsoft-defender.md)]

**Applies to:**

- Microsoft Defender Antivirus
- [Microsoft Defender for Endpoint Plan 1 or 2](microsoft-defender-endpoint.md)
- Microsoft Defender for Servers (for Windows Server and Linux Server)

> [!NOTE]
> To onboard servers to Defender for Endpoint, you need another license, such as [Microsoft Defender for Servers Plan 1 or 2](/azure/defender-for-cloud/defender-for-servers-introduction). To learn more, see [Defender for Endpoint onboarding Windows Server](onboard-windows-server.md). 
> If you're a small or medium-sized business using [Microsoft Defender for Business](/defender-business/mdb-overview), you can get [Microsoft Defender for Business servers](/defender-business/get-defender-business#how-to-get-microsoft-defender-for-business-servers).

[Microsoft Defender for Endpoint](microsoft-defender-endpoint.md) includes a wide range of capabilities to prevent, detect, investigate, and respond to advanced cyberthreats. These capabilities include [Next-generation protection](next-generation-protection.md) (which includes Microsoft Defender Antivirus). 

Microsoft preconfigures the product to perform well on the operating system that it's installed. No other changes should be needed. Despite preconfigured settings, sometimes unexpected behaviors occur. Here are some examples:

- **False positives**: Files, folders, or processes that aren't actually a threat can be detected as malicious by Defender for Endpoint or Microsoft Defender Antivirus. These entities can be blocked or sent to quarantine, even though they're not really a threat. 

- **Performance issues**: Systems experience an unexpected performance impact when running with Defender for Endpoint

- **Application compatibility issues**: Applications experience unexpected behavior when running with Defender for Endpoint 

This article explains the various types of exclusions that you can define, how exclusions are evaluated, and what to expect if policy conflicts occur. For how-to information, see the following articles:

- [Address common false-positive scenarios with exclusions](address-common-false-positives-exclusions.md)
- [Address false positives/negatives in Microsoft Defender for Endpoint](defender-endpoint-false-positives-negatives.md)
- [Managing exclusions reference](managing-exclusions.md)

## Types of exclusions

The following table summarizes the different exclusion types and capabilities in Defender for Endpoint and Microsoft Defender Antivirus. Select each type to see more information about it. 

### Custom exclusions

Microsoft Defender for Endpoint allows you to configure custom exclusions to optimize performance and avoid false positives. The types of exclusions you can set vary by Defender for Endpoint capabilities and by operating systems. 

The following table summarizes types of custom exclusions that you can define. Note the scope for each exclusion type. 

| Exclusion types | Scope |Use When|
|---| ----| -------- |
|[Custom Defender for Endpoint exclusions](#custom-exclusions) | Microsoft Defender Antivirus<br/>Microsoft Defender for Endpoint<br/>Attack surface reduction rules<br/>Network Protection |A file, folder, or process is identified as malicious, even though it's not a threat.<br/><br/> An application encounters unexpected performance or application compatibility issue when running with Defender for Endpoint|
|[Defender for Endpoint attack surface reduction exclusions](#attack-surface-reduction-exclusions) | Attack surface reduction rules|An attack surface reduction rule causes unexpected behavior|
|[Defender for Endpoint File and Certificate Allow Indicators](/defender-endpoint/indicator-certificates)| Microsoft Defender Antivirus<br/>Attack surface reduction rules<br/>Controlled folder access |A file or process signed by a certificate is identified as malicious even through it's not.|
|[Defender for Endpoint Domain/URL and IP address Indicators](/defender-endpoint/indicator-ip-domain) |SmartScreen<br/>Web Content Filtering<br/>Network Protection |SmartScreen false positive (FP) or to override a Web Content Filtering (WFC) block on a specific site.|
|[Defender for Endpoint controlled folder access exclusions](#controlled-folder-access-exclusions) | Controlled folder access|Controlled folder access blocks an application from accessing a protected folder.|
|[Defender for Endpoint automation folder exclusions](#automation-folder-exclusions) |Automated investigation and response|Automated investigation and remediation takes action on a file, extension, or directory that should be done manually.|


> [!NOTE]
> Network Protection is directly impacted by process exclusions on all platforms. A process exclusion on any OS (Windows, MacOS, Linux) results in preventing Network Protection from inspecting traffic or enforcing rules for that specific process.

The following sections describe exclusion types for the macOS, Linux, and Windows operating systems.

#### Exclusions on Mac

For macOS, you can define exclusions that apply to on-demand scans, real-time protection, and monitoring. The supported exclusion types include:

- **File extension**: Exclude all files with a specific extension.
- **File**: Exclude a specific file identified by its full path.
- **Folder**: Exclude all files under a specified folder recursively.
- **Process**: Exclude a specific process and all files opened by it.

For more information, see the [Microsoft Defender for Endpoint on macOS documentation](/defender-endpoint/mac-exclusions).

#### Exclusions on Linux

On Linux, you can configure both antivirus and global exclusions.

- **Antivirus exclusions**: Apply to on-demand scans, real-time protection (RTP), and behavior monitoring (BM).
- **Global exclusions**: Apply to real-time protection (RTP), behavior monitoring (BM), and endpoint detection and response (EDR), stopping all associated antivirus detections and EDR alerts.

For more information, see the [Microsoft Defender for Endpoint on Linux documentation](/defender-endpoint/linux-exclusions)

#### Exclusions on Windows

Microsoft Defender Antivirus can be configured to exclude combinations of processes, files, and extensions from scheduled scans, on-demdand scans and real-time protection. See [Configure custom exclusions for Microsoft Defender Antivirus](/defender-endpoint/configure-exclusions-microsoft-defender-antivirus).

For more granular control that helps minimize protection gaps, consider using [Contextual file and process exclusions](/defender-endpoint/configure-contextual-file-folder-exclusions-microsoft-defender-antivirus).  

### Antivirus preconfigured exclusions

These exclusion types are preconfigured in Microsoft Defender for Endpoint for Microsoft Defender Antivirus. 

| Exclusion types | Configuration | Description |
|---|----|----|
| [Automatic Microsoft Defender Antivirus exclusions](#automatic-server-role-exclusions) | Automatic | Automatic Exclusions for server roles and features in Windows Server. When you install a role on Windows Server 2016 or later, Microsoft Defender Antivirus includes automatic exclusions for the server role and any files that are added while installing the role. <br/> These exclusions are only for active roles on Windows Server 2016 and later. |
| [Built-in Microsoft Defender Antivirus exclusions](#built-in-exclusions) | Automatic |Microsoft Defender Antivirus includes built-in exclusions for operating system files on all versions of Windows.|

#### Automatic server role exclusions

[Automatic server role exclusions](configure-server-exclusions-microsoft-defender-antivirus.md#automatic-server-role-exclusions) include exclusions for server roles and features in Windows Server 2016 and later. These exclusions aren't scanned by [real-time protection](configure-protection-features-microsoft-defender-antivirus.md) but are still subject to [quick, full, or on-demand antivirus scans](schedule-antivirus-scans.md#comparing-the-quick-scan-full-scan-and-custom-scan). 

Here are some examples of automatic server role exclusions: 

- File Replication Service (FRS)
- Hyper-V
- SYSVOL
- Active Directory
- DNS Server
- Print Server
- Web Server
- Windows Server Update Services
- ...and more.

> [!NOTE]
> Automatic exclusions for server roles aren't supported on Windows Server 2012 R2. For servers running Windows Server 2012 R2 with the Active Directory Domain Services (AD DS) server role installed, exclusions for domain controllers must be specified manually. See [Active Directory exclusions](configure-server-exclusions-microsoft-defender-antivirus.md#active-directory-exclusions). 

For more information, see [Automatic server role exclusions](configure-server-exclusions-microsoft-defender-antivirus.md#automatic-server-role-exclusions).

#### Built-in exclusions

[Built-in exclusions](configure-server-exclusions-microsoft-defender-antivirus.md#built-in-exclusions) include certain operating system files that are excluded by Microsoft Defender Antivirus on all versions of Windows (including Windows 10, Windows 11, and Windows Server). 

Examples include:

- `%windir%\SoftwareDistribution\Datastore\*\Datastore.edb` 
- `%allusersprofile%\NTUser.pol`
- Windows Update files
- Windows Security files 
- ... and more.

The list of built-in exclusions in Windows is kept up to date as the threat landscape changes. To learn more about these exclusions, see [Microsoft Defender Antivirus exclusions on Windows Server: Built-in exclusions](configure-server-exclusions-microsoft-defender-antivirus.md#built-in-exclusions).

### Attack surface reduction exclusions

[Attack surface reduction rules](attack-surface-reduction.md) (also known as ASR rules) target certain software behaviors, such as:

- Launching executable files and scripts that attempt to download or run files
- Running scripts that seem to be obfuscated or otherwise suspicious
- Performing behaviors that apps don't usually initiate during normal day-to-day work

Sometimes, legitimate applications exhibit software behaviors that could be blocked by attack surface reduction rules. If that's occurring in your organization, you can define exclusions for certain files and folders. Such exclusions are applied to all attack surface reduction rules. See [Enable attack surface reduction rules](attack-surface-reduction-rules-deployment-implement.md#exclude-files-and-folders).

> [!NOTE]
> Attack surface reduction rules honor process exclusions, but not all attack surface reduction rules honor Microsoft Defender Antivirus exclusions. See [Attack surface reduction rules reference - Microsoft Defender Antivirus exclusions and ASR rules](attack-surface-reduction-rules-reference.md#microsoft-defender-antivirus-exclusions-and-asr-rules). 

### Custom remediation actions

When Microsoft Defender Antivirus detects a potential threat while running a scan, it attempts to remediate or remove the detected threat. You can define custom remediation actions to configure how Microsoft Defender Antivirus should address certain threats, whether a restore point should be created before remediating, and when threats should be removed. 

For more information, see [Configure remediation actions for Microsoft Defender Antivirus detections](configure-remediation-microsoft-defender-antivirus.md).



### Controlled folder access exclusions

[Controlled folder access](controlled-folders.md) monitors apps for activities that are detected as malicious and protects the contents of certain (protected) folders on Windows devices. Controlled folder access allows only trusted apps to access protected folders, such as common system folders (including boot sectors) and other folders that you specify. You can allow certain apps or signed executables to access protected folders by defining exclusions. 

For more information, See [Customize controlled folder access](customize-controlled-folders.md).

### Automation folder exclusions

Automation folder exclusions apply to [automated investigation and remediation](automated-investigations.md) in Defender for Endpoint, which is designed to examine alerts and take immediate action to resolve detected breaches. As alerts are triggered, and an automated investigation runs, a verdict (Malicious, Suspicious, or No threats found) is reached for each piece of evidence investigated. Depending on the [automation level](automation-levels.md) and other security settings, remediation actions can occur automatically or only upon approval by your security operations team.

You can specify folders, file extensions in a specific directory, and file names to be excluded from automated investigation and remediation capabilities. Such automation folder exclusions apply to all devices onboarded to Defender for Endpoint. These exclusions are still subject to antivirus scans. 

For more information, see [Manage automation folder exclusions](manage-automation-folder-exclusions.md).

## How exclusions and indicators are evaluated

Most organizations have several different types of exclusions and indicators to determine whether users should be able to access and use a file or process. Exclusions and indicators are processed in a particular order so that [policy conflicts are handled systematically](indicator-file.md#policy-conflict-handling).

Here's how it works:

1. If a detected file/process isn't allowed by Windows Defender Application Control and AppLocker, it's blocked. Otherwise, it proceeds to Microsoft Defender Antivirus.

2. If the detected file/process isn't part of an exclusion for Microsoft Defender Antivirus, it's blocked. Otherwise, Defender for Endpoint checks for a custom indicator for the file/process.

3. If the detected file/process has a Block or Warn indicator, that action is taken. Otherwise, the file/process is allowed, and proceeds to evaluation by attack surface reduction rules, controlled folder access, and SmartScreen protection.

4. If the detected file/process isn't blocked by attack surface reduction rules, controlled folder access, or SmartScreen protection, it proceeds to Microsoft Defender Antivirus.

5. If the detected file/process isn't allowed by Microsoft Defender Antivirus, it's checked for an action based on its threat ID.

## How policy conflicts are handled

In cases where Defender for Endpoint indicators conflict, here's what to expect:

- If there are conflicting file indicators, the indicator that uses the most secure hash is applied. For example, SHA256 takes precedence over SHA-1, which takes precedence over MD5.

- If there are conflicting URL indicators, the more strict indicator is used. For [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview), an indicator that uses the longest URL path is applied. For example, `www.dom.ain/admin/` takes precedence over `www.dom.ain`. ([Network protection](network-protection.md) applies to domains, rather than subpages within a domain.)

- If there are similar indicators for a file or process that have different actions, the indicator that is scoped to a specific device group takes precedence over an indicator that targets all devices.

## How automated investigation and remediation works with indicators

[Automated investigation and remediation capabilities](automated-investigations.md) in Defender for Endpoint first determine a verdict for each piece of evidence, and then take an action depending on Defender for Endpoint indicators. Thus, a file/process could get a verdict of "good" (which means no threats were found) and still be blocked if there's an indicator with that action. Similarly, an entity could get a verdict of "bad" (which means it's determined to be malicious) and still be allowed if there's an indicator with that action.

For more information, see [automated investigation and remediation works with indicators](indicators-overview.md#automated-investigation-and-remediation-engine).

## Other server workloads and exclusions

If your organization is using other server workloads, such as Exchange Server, SharePoint Server, or SQL Server, be aware that only built-in server roles (that could be prerequisites for software you install later) on Windows Server are excluded by [automatic exclusions](#automatic-exclusions) feature (and only when using their default installation location). You'll likely need to define antivirus exclusions for these other workloads, or for all workloads if you disable automatic exclusions.

Here are some examples of technical documentation to identify and implement the exclusions you need:

- [Running antivirus software on Exchange Server](/exchange/antispam-and-antimalware/windows-antivirus-software?view=exchserver-2019&preserve-view=true)
- [Folders to exclude from antivirus scans on SharePoint Server](https://support.microsoft.com/office/certain-folders-may-have-to-be-excluded-from-antivirus-scanning-when-you-use-file-level-antivirus-software-in-sharepoint-01cbc532-a24e-4bba-8d67-0b1ed733a3d9)
- [Choosing antivirus software for SQL Server](https://support.microsoft.com/topic/how-to-choose-antivirus-software-to-run-on-computers-that-are-running-sql-server-feda079b-3e24-186b-945a-3051f6f3a95b)

Depending on what you're using, you might need to refer to the documentation for that server workload.

## See also

- [Submissions, suppressions, and exclusions](submissions-suppressions-exclusions.md)
- [Address common false-positive scenarios with exclusions](address-common-false-positives-exclusions.md)
- [Important points about exclusions](configure-exclusions-microsoft-defender-antivirus.md#important-points-about-exclusions)
- [Common mistakes to avoid when defining exclusions](common-exclusion-mistakes-microsoft-defender-antivirus.md)
- [Overview of indicators in Microsoft Defender for Endpoint](indicators-overview.md)

[!INCLUDE [Microsoft Defender for Endpoint Tech Community](../includes/defender-mde-techcommunity.md)]
