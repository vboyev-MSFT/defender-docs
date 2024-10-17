---
title: Address common false-positive scenarios with exclusions            
description: Learn how to address common false-positive scenarios using antivirus exclusions or Defender for Endpoint indicators.            
author: denisebmsft
ms.author: deniseb
manager: deniseb 
ms.date: 10/17/2024
ms.topic: how-to
ms.service: defender-endpoint
ms.subservice: onboard
ms.localizationpriority: medium 
ms.reviewer: joshbregman
search.appverid: MET150
f1.keywords: NOCSH 
audience: ITPro
ms.custom: 
- partner-contribution
ms.collection: 
- m365-security
- tier2
---

# Address common false-positive scenarios with exclusions

A false positive is when an entity, such as a file or a process, was detected and identified as malicious, even though the entity isn't a threat. This article describes common false-positive scenarios you might encounter, and how you can address them with exclusions. For more information about exclusions, see [Exclusions overview](navigate-defender-endpoint-antivirus-exclusions.md).

## An app is detected by Microsoft Defender Antivirus when the application runs

In this scenario, whenever a user runs an application, the application is detected by Microsoft Defender Antivirus as a potential threat. 

**How to observe**: CONTENT NEEDED

**How to address**: Create "allow" indicators for Microsoft Defender for Endpoint. For example, you can create an "allow" indicator for a file, such as an executable. See [Create indicators for files](indicator-file.md). 

## A custom, self-signed app is detected by Microsoft Defender Antivirus when the application runs 

In this scenario, whenever a custom app that is periodically updated run, it's detected by Microsoft Defender Antivirus as a potential threat, even though it's signed.

**How to address**: Create "allow" indicators for certificates or files. See the following articles:

- [Create indicators based on certificates](indicator-certificates.md)
- [Create indicators for files](indicator-file.md)

## A custom app accesses a set of file types that is detected as malicious when the application runs

In this scenario, a custom app accesses a set file types, and the set is detected as malicious by Microsoft Defender Antivirus whenever the application runs. 

**How to observe**: When the application is running, it's detected by Microsoft Defender Antivirus as a behavior monitoring detection.

**How to address**: Define exclusions for Microsoft Defender Antivirus, such as a file or path exclusion that might include wildcards. Or define a custom file path exclusion. See the following articles:

- [Address false positives/negatives in Microsoft Defender for Endpoint](defender-endpoint-false-positives-negatives.md)
- [Configure and validate exclusions based on file extension and folder location](configure-extension-file-exclusions-microsoft-defender-antivirus.md)

## An application is detected by Microsoft Defender Antivirus as a “behavior” detection 

In this scenario, an application is detected by Microsoft Defender Antivirus because of certain behavior, even though the application is not a threat. 

**How to address**: Define a process exclusion. See the following articles:

- [Configure and validate exclusions based on file extension and folder location](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Configure exclusions for files opened by processes](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

## A non-malicious PowerShell script file is incorrectly detected by Microsoft Defender Antivirus

In this scenario, a user copies a non-malicious PowerShell script file onto an endpoint, and the script file is incorrectly detected by Microsoft Defender Antivirus.   

**How to observe**: AMSI detection in the Operational logs 

**How to address**: Define a path exclusion with limitations. See [Configure and validate exclusions based on file extension and folder location](configure-extension-file-exclusions-microsoft-defender-antivirus.md). 

## An app is considered a potentially unwanted application (PUA)

In this scenario, an app is detected as PUA, and you want to allow it to run. 

**How to address**: Define an exclusion for the app. See the following articles:

- [Exclude files from PUA protection](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md#exclude-files-from-pua-protection)
- [Configure and validate exclusions based on file extension and folder location](configure-extension-file-exclusions-microsoft-defender-antivirus.md)

## An app is blocked from writing to a protected folder

In this scenario, a legitimate app is blocked from writing to folders that are protected by controlled folder access.

**How to address**: Define an "allow" indicator for files or certificates, and define a path exclusion. See the following articles:

- [Create indicators for files](indicator-file.md)
- [Create indicators based on certificates](indicator-certificates.md)
- [Configure and validate exclusions based on file extension and folder location](configure-extension-file-exclusions-microsoft-defender-antivirus.md)

## A third-party app is detected as malicious by Microsoft Defender Antivirus

In this scenario, a third-party app that is not a threat is detected and identified as malicious by Microsoft Defender Antivirus.

**How to address**: Submit the app to Microsoft for analysis. See [How to submit a file to Microsoft for analysis](/defender-xdr/submission-guide#how-do-i-submit-a-file-to-microsoft-for-analysis).

## A custom app is incorrectly detected and identified as malicious by Defender for Endpoint

In this scenario, a custom, legitimate app that is not a threat is detected and identified as malicious by an attack surface reduction rule in Defender for Endpoint. Whenever a user uses the app, 

Customer app launches downloaded content and is blocked  by Microsoft Defender ASR rule “Block JavaScript or VBScript from launching downloaded executable content”. 

**How to observe**: CONTENT NEEDED

**How to address**:

Point customers to ASR report in the MDATP portal and use that to add ASR exclusions – strongly recommended 

## Word templates that contain macros that launch other apps are blocked

In this scenario, whenever a user opens documents that were created by using Microsoft Word templates that contain macros and those macros launch other applications, the attack surface reduction rule [Block Win32 API calls from Office macros](/defender-endpoint/attack-surface-reduction-rules-reference#block-win32-api-calls-from-office-macros) blocks Microsoft Word. 

**How to observe**: CONTENT NEEDED

**How to address**: PLEASE VERIFY THESE STEPS

1. In the [Microsoft Defender portal](https://security.microsoft.com), go to **Reports**. Under **Reports**, select **Security report**.

2. Scroll down to devices to find your attack surface reduction cards. For more information, see [attack surface reduction rules report](attack-surface-reduction-rules-report.md).

3. Use the information to identify the files and folder locations to be excluded.

4. Add exclusions. See [Configure and validate exclusions based on file extension and folder location](configure-extension-file-exclusions-microsoft-defender-antivirus.md). 

## When a user runs a custom app from a USB drive, the app is blocked

In this scenario, whenever a user runs a custom created application from an USB drive, the app is blocked by the “Block apps running from USB drive” configuration. 

**How to observe**: CONTENT NEEDED

**How to address**: CONTENT NEEDED. Add a AV path exclusion does not work as the USB may get mapped to a different drive name and ASR does not respect wildcards in AV path exclusions 

## See also

- [Exclusions overview](navigate-defender-endpoint-antivirus-exclusions.md)
- [Managing exclusions reference](managing-exclusions.md)