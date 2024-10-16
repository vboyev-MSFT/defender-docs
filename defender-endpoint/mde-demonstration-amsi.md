---
title: AMSI demonstrations with Microsoft Defender for Endpoint
description: Demonstration of AMSI detection by Microsoft Defender for Endpoint
author: denisebmsft
ms.author: deniseb
ms.reviewer: yongrhee
ms.service: defender-endpoint
ms.topic: how-to
ms.date: 10/16/2024
ms.subservice: ngp
---

# AMSI demonstrations with Microsoft Defender for Endpoint

**Applies to:**

- [Microsoft Defender for Endpoint Plan 2](microsoft-defender-endpoint.md)
- [Microsoft Defender for Business](https://www.microsoft.com/security/business/endpoint-security/microsoft-defender-business)
- [Microsoft Defender for Endpoint Plan 1](microsoft-defender-endpoint.md)

- [Microsoft Defender Antivirus](microsoft-defender-antivirus-windows.md)

Microsoft Defender for Endpoint utilizes the [Antimalware Scan Interface (AMSI)](/defender-endpoint/amsi-on-mdav) to enhance protection against fileless malware, dynamic script-based attacks, and other nontraditional cyber threats.  In this article, we describe how to test the AMSI engine with a benign sample.

## Scenario requirements and setup

- Windows 10 or newer
- Windows Server 2016, or newer
- Microsoft Defender Antivirus (as primary) and these need to be enabled:
  - Real-Time Protection (RTP) 
  - Behavior Monitoring (BM)  
  - Turn on script scanning
    

## Testing AMSI with Defender for Endpoint

In this demonstration page, you have three engine choices to test AMSI:

- PowerShell
- VBScript

### Test AMSI with PowerShell

1. Save the following PowerShell script as `AMSI_PoSh_script.ps1`:

   :::image type="content" source="media/mde-demonstrations-amsi/test-amsi-powershell-save-script.png" alt-text="Screenshot showing PowerShell script to save as AMSI_PoSh_script.ps1":::

2. On your device, open PowerShell as an administrator.

3. Type `Powershell -ExecutionPolicy Bypass AMSI_PoSh_script.ps1`, and then press **Enter**.

   The result should be as follows:

   ```console

   Invoke-Expression : At line:1 char:1

   + AMSI Test Sample: 7e72c3ce-861b-4339-8740-0ac1484c1386

   + ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

   This script contains malicious content and has been blocked by your antivirus software.

   At C:\Users\Admin\Desktop\AMSI_PoSh_script.ps1:3 char:1

   + Invoke-Expression $testString

   + ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    + CategoryInfo          : ParserError: (:) [Invoke-Expression], ParseException

    + FullyQualifiedErrorId : ScriptContainedMaliciousContent,Microsoft.PowerShell.Commands.InvokeExpressionCommand
    
    ```


### Testing AMSI with VBScript

1. Save the following VBScript as `AMSI_vbscript.vbs`:

   :::image type="content" source="media/mde-demonstrations-amsi/test-amsi-vbscript-save-script.png" alt-text="Screenshot showing VBScript to save as AMSI_vbscript.vbs":::

2. On your Windows Device, open Command Prompt as an administrator.

2. Type `wscript AMSI_vbscript.js`, and then press **Enter**.

   The result should be as follows:

   ```console

   Windows Script Host

   Script: C:\Users\Admin\Desktop\AMSI_vbscript.vbs

   Line: 3

   Char: 1

   Error: This script contains malicious content and has been blocked by your antivirus software.: 'eval'

   Code: 800A802D

   Source: Microsoft VBScript runtime error

   ```

### Verifying the test results

In your protection history, you should be able to see the following information:

```console

Threat blocked

Detected: Virus: Win32/MpTest!amsi

Status: Cleaned

This threat or app was cleaned or quarantined before it became active on your device.

Details: This program is dangerous and replicates by infecting other files.

Affected items:

amsi: \Device\HarddiskVolume3\Windows\System32\WindowsPowershell\v1.0\powershell.exe or amsi: C:\Users\Admin\Desktop\AMSI_vbscript.vbs

```

You might also see the following information:

```console

Threat blocked

Detected: Virus: Win32/MpTest!amsi

Status: Cleaned

This threat or app was cleaned or quarantined before it became active on your device.

Details: This program is dangerous and replicates by infecting other files

Affected items:

```

### Get the list of Microsoft Defender Antivirus threats

You can view detected threats by using the Event log or PowerShell.

#### Use the Event log

1. Go to **Start**, and search for `EventVwr.msc`. Open Event Viewer in the list of results.

2. Go to **Applications and Services Logs** > **Microsoft** > **Windows** > **Windows Defender operational events**.

3. Look for `event ID 1116`. You should see the following information:

   ```console

   Microsoft Defender Antivirus has detected malware or other potentially unwanted software.

   For more information please see the following: https://go.microsoft.com/fwlink/?linkid=37020&name=Virus:Win32/MpTest!amsi&threatid=2147694217&enterprise=0

   Name: Virus:Win32/MpTest!amsi

   ID: 2147694217

   Severity: Severe

   Category: Virus

   Path: _\Device\HarddiskVolume3\Windows\System32\WindowsPowerShell\v1.0\powershell.exe or _C:\Users\Admin\Desktop\AMSI_jscript.js;   file: _C:\Users\Admin\Desktop\AMSI_jscript.js->[Eval] or _C:\Users\Admin\Desktop\AMSI_vbscript.vbs

   Detection Origin: Local machine or Unknown

   Detection Type: Concrete

   Detection Source: System

   User: NT AUTHORITY\SYSTEM

   Process Name: C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe or C:\Windows\System32\cscript.exe or C:\Windows\System32\wscript.exe or Unknown 

   Security intelligence Version: AV: 1.419.221.0, AS: 1.419.221.0, NIS: 1.419.221.0

   Engine Version: AM: 1.1.24080.9, NIS: 1.1.24080.9

   ```

##### Use PowerShell

Open PowerShell, and then type the following command: `Get-MpThreat`.

You might see the following results:

```console

CategoryID       : 42

DidThreatExecute : True

IsActive         : True

Resources        :

RollupStatus     : 97

SchemaVersion    : 1.0.0.0

SeverityID       : 5

ThreatID         : 2147694217

ThreatName       : Virus:Win32/MpTest!amsi

TypeID           : 0

PSComputerName   :

```

## See also

[Microsoft Defender for Endpoint - demonstration scenarios](defender-endpoint-demonstrations.md)

[!INCLUDE [Microsoft Defender for Endpoint Tech Community](../includes/defender-mde-techcommunity.md)]