---
title: Troubleshoot Microsoft Defender Antivirus Security intelligence not getting updated
description: Learn how to troubleshoot Microsoft Defender Antivirus Security intelligence not getting updated.
author: denisebmsft
ms.author: deniseb
manager: deniseb 
ms.date: 01/10/2025
ms.topic: troubleshooting
ms.service: defender-endpoint
ms.subservice: ngp
ms.localizationpriority: medium 
ms.collection: # Useful for querying on a set of strategic or high-priority content.
ms.custom: 
- partner-contribution
ms.reviewer: yongrhee
search.appverid: MET150
f1.keywords: NOCSH
audience: ITPro
---

# Troubleshoot Microsoft Defender Antivirus Security intelligence not getting updated

**Applies to:**

- [Microsoft Defender XDR](/defender-xdr)
- [Microsoft Defender for Endpoint Plan 1 and 2](microsoft-defender-endpoint.md)
- [Microsoft Defender for Business](https://www.microsoft.com/security/business/endpoint-security/microsoft-defender-business)
- [Microsoft Defender for Individuals](https://www.microsoft.com/microsoft-365/microsoft-defender-for-individuals)
- Microsoft Defender Antivirus

## Symptom

When you try updating the Security intelligence for Microsoft Defender Antivirus, you might see an error about **Protection definition update failed**.

:::image type="content" source="media/protection-definition-update-failed.png" alt-text="Screenshot of Protection definition update failed.":::

You might see the following error codes:

- 0x8024402c 
- 0x80240022 
- 0X80004002 
- 0x80070422 
- 0x80072efd 
- 0x80070005 
- 0x80072f78 
- 0x80072ee2 
- 0x8007001B 

The following screenshot shows an error about **Signature Update failed**.

:::image type="content" source="media/signature-update-failed.png" alt-text="Screenshot showing signature update failed." lightbox="media/signature-update-failed.png":::

## Solution

1. Check the URLs required for the Security intelligence updates. You can get them via the firewall and/or proxy. See [Configure your network environment to ensure connectivity with Defender for Endpoint service](configure-environment.md).

2. Is Microsoft Defender Antivirus (MDAV) the primary antivirus? Is there a third-party antivirus installed, which uses the Windows Security Center (WSC) API, which disables MDAV? If MDAV is disabled, then no updates such as Security intelligence update can occur.

3. If MDAV is the primary antivirus and the services are running:

    1. Does updating the Security intelligence work if you manually download from [Latest security intelligence updates for Microsoft Defender Antivirus and other Microsoft antimalware?](https://www.microsoft.com/wdsi/defenderupdates)

    2. If it does, then you could try updating via Microsoft Malware Protection Center (MMPC).

       Run the following PowerShell command as an administrator.

       ```powershell
          & "${env:ProgramFiles}\Windows Defender\MpCmdRun.exe" -SignatureUpdate -MMPC
       ```

    3. If it works, then you could be having issues with the Security intelligence [Fallback order](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order) being set to a WSUS server that doesn't have the **Security intelligence** updates approved. Or if pointing to a UNC share, they might be stale or the Windows Update service might be having issues.
        1. To check the WSUS server that the machine goes to, review `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\WUServer (REG_SZ)`. Once you find the WUServer, check if that WSUS server has the MDAV security intelligence [(KB2267602 for MDAV and KB2461484 for SCEP)](microsoft-defender-antivirus-updates.md#security-intelligence-updates) approved.
        2. To check the UNC share, review [Manage how and where Microsoft Defender Antivirus receives updates](manage-protection-updates-microsoft-defender-antivirus.md#create-a-unc-share-for-security-intelligence-and-platform-updates).
        3. To check the status of the Windows Update service, review [Guidance for troubleshooting Windows Update issues](/troubleshoot/windows-client/installing-updates-features-roles/troubleshoot-windows-update-issues) and [Troubleshoot problems updating Windows](https://support.microsoft.com/windows/troubleshoot-problems-updating-windows-188c2b0f-10a7-d72f-65b8-32d177eb136c).