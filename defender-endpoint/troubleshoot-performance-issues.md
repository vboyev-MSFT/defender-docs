---
title: Troubleshoot performance issues
description: Troubleshoot high CPU usage related to the real-time protection service in Microsoft Defender for Endpoint.
search.appverid: met150
ms.service: defender-endpoint
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dolmont
ms.date: 11/12/2024
audience: ITPro
ms.topic: troubleshooting
ms.subservice: ngp
ms.collection: 
- m365-security
- tier3
- mde-ngp
---

# Troubleshoot performance issues related to real-time protection


[!INCLUDE [Microsoft Defender XDR rebranding](../includes/microsoft-defender.md)]


**Applies to:**

- [Microsoft Defender for Endpoint Plan 2](microsoft-defender-endpoint.md)

- [Microsoft Defender for Endpoint Plan 1](microsoft-defender-endpoint.md)

- Microsoft Defender Antivirus

**Platforms**
- Windows

- Windows Server

If your system is having high CPU usage or performance issues related to the Microsoft Defender Antivirus (Antimalware Service Executable, MsMpEng.exe, Microsoft Defender Antivirus).

As an admin, you can also troubleshoot these issues on your own.

First, you might want to check if the issue is caused by other software. Read [Check with the vendor for known issues with antivirus exclusions](#check-with-the-vendor-for-known-issues-with-antivirus-products).

## Common reasons for higher cpu utilization by Microsoft Defender Antivirus:

|#|Common reason for higher cpu utilization|Information|Solution |
| -------- | -------- | -------- | -------- |
|1|Binaries not being signed (.exe’s, .dll’s, .ps1, etc…)  |Anytime that a binary (.exe’s, .dll’s, .ps1, etc…) are launched/started, if they are not digitally signed, we will go ahead and do a real-time protection (rtp) scan and/or scheduled scan and/or on-demand scan.|You all should consider signing (Extended code validation (EV) code signing or using internal PKI) the binaries.  And/or reaching out to the vendor so they could sign the binary (EV code signing).  We recommend that software vendors follow the various guidelines in [Partnering with the industry to minimize false positives](https://www.microsoft.com/en-us/security/blog/2018/08/16/partnering-with-the-industry-to-minimize-false-positives/). The vendor or if it’s an inhouse built application/service/script, the software can be submitted through the [Microsoft Security Intelligence portal](https://www.microsoft.com/wdsi/filesubmission?persona=SoftwareDeveloper). Work-around: 1) (Preferred) For .exe’s and dll’s use [Indicators – File hash - allow](/defender-endpoint/indicator-file) or [Indicators – Certificate - allow](/defender-endpoint/indicator-certificates) 2) (Alternative) 2) Add [AV exclusions (process+path)](/defender-endpoint/configure-exclusions-microsoft-defender-antivirus).  |
|2|Using HTA’s, CHM’s and different files as databases.|Anytime that MDAV needs to extract and/or scan complex file formats, higher cpu utilization can occur.|Look at using actual databases, if you need to save info and query it. Work-around: Add [AV exclusions (process+path)](/defender-endpoint/configure-exclusions-microsoft-defender-antivirus)|
|3|Using obfuscations on scripts|If you obfuscate scripts, MDAV in order to check if the script contains malicious payloads, it can use more cpu utilization while scanning.|Only use script obfuscation if really necessary.  Work-around: Add [AV exclusions (process+path)](/defender-endpoint/configure-exclusions-microsoft-defender-antivirus)|
|4|Not letting the MDAV cache finish before sealing the image.  |If you are creating a VDI image such as for a non-persistent image, make sure that the ‘cache maintenance’ completes before the image is sealed. |Review: [Configure Microsoft Defender Antivirus on a remote desktop or virtual desktop infrastructure environment](/defender-endpoint/deployment-vdi-microsoft-defender-antivirus)|
|5|Having the wrong path exclusion(s) due to misspelling|If you add misspelled exclusion paths, it can lead to performance issues.|Use MpCmdRun.exe -CheckExclusion -Path to validate path-based exclusions.|
|6|When a path exclusion is added, it works for scanning flows.  |Behavior Monitoring (BM) and Network Real-time Inspection (NRI) may still cause performance issues. |Work-around: 1) (Preferred) For .exe’s and dll’s use [Indicators – File hash - allow](/defender-endpoint/indicator-file) or [Indicators – Certificate - allow](/defender-endpoint/indicator-certificates) 2) (Alternative) 2) [Add AV exclusions (process+path)](/defender-endpoint/configure-exclusions-microsoft-defender-antivirus)|
|7|File hash computation|If you enable "File hash computation" which is used for Indicators - File hash - allow, there is an additional performance overhead which is [documented](/defender-endpoint/indicator-file).  For example, copying large files from a network share onto your local device, especially over a VPN connection, might have an effect on device performance. |This is where you, and your leadership team will have to make a decision, of having more security or less cpu utilization.  Solution would be to disable the File hash computation feature. Computer Configuration > Adminstrative Templates > Windows Components > Microsoft Defender Antivirus > MpEngine > Enable file hash computation features.|

### Narrowing it down to which Microsoft Defender Antivirus component could be contributing to the higher cpu utilization:

|Component|Information| Solution|
| -------- | -------- | -------- |
|Real-time protection (RTP) scanning|You can use [Troubleshooting mode](/defender-endpoint/enable-troubleshooting-mode) to turn off [Tamper Protection](/defender-endpoint/troubleshoot-problems-with-tamper-protection).  Once Tamper Protection is turned off, you could turn off the “Real-time protection” temporarily, in order to rule it out.|Please see above “Common reasons for higher cpu utilization by Microsoft Defender Antivirus”|
|Scheduled scanning|Check your default scheduled scan settings|A few things that you can do to lower the cpu utilization during a scheduled scan.  1) **General scheduled scan settings** •	1a) Configure low CPU priority for scheduled scans (Use low CPU priority for scheduled scans): The thread priority in Windows for Normal, has two values.  8 (lower) and 9 (higher).  By setting this to enabled, you are lowering the scheduled scan thread priority from 9 to 8.  Which provides the other application threads to run with a higher priority, thus getting more cpu time than MDAV.  •	1b) Specify the maximum percentage of CPU utilization during a scan (CPU usage limit per scan): 50 (default), you could lower it to 20 or 30%.  Note: If you have a change control window, by modifying the amount of cpu that can be used, causes the scan to take longer. •	1c) Start the scheduled scan only when computer is on but not in use (ScanOnlyIfIdle): Not configured (Enabled by default).  It requires the machine to be idle, meaning the cpu usage overall of the device has to be lower than 80%.  2) __Daily quick scan 2a) Specify the interval to run quick scans per day: Not configured (How many hours have elapsed, before the next quick scan runs - 0 to 24 hours) 2b) Specify the time for a daily quick scan (Run daily quick scan at): 12 PM.  3) Run a weekly scheduled scan (quick or full) 3a) Specify the scan type to use for a scheduled scan (Scan type): Not configured 3b) Specify the time of day to run a scheduled scan (Day of week to run scheduled scan): Not configured 3c) Specify the day of the week to run a scheduled scan (Time of day to run a scheduled scan): Not configured__|
|Scan after a security intelligence update.|By default, MDAV scans after a security intelligence update for optimal protection purposes.  Note: Customers that have scheduled scans enabled, might think that there are scans that are run outside of the schedule.|This is where you, and your leadership team will have to make a decision, of having more security or less cpu utilization. Work-around: In Group Policy (or other management such as MDM), Computer Configuration > Administrative Templates > Microsoft Defender Antivirus > Security Intelligence Updates > Turn on scan after security intelligence update > Disabled|
|Conflict with other security software|If you have a 3rd party security software such as antivirus, edr, dlp, endpoint privilege management, vpn, etc…|Add the 3rd party security software to the MDAV exclusions (path + processes) and vice-versa.  The list of the MDAV binaries are listed in the .xlsx here: [Configure your network environment to ensure connectivity with Defender for Endpoint service](/defender-endpoint/configure-environment)|
|Scanning a large number of files or folders|Having big file such as an .iso or .vhdx , etc…  sitting in your user profile (desktop, downloads, documents, etc…), and that profile is being redirected to network shares such as  via Offline Files (CSC) or onedrive (or similar products).  Since it has to scan via a network, where there is additional latency compared to sitting locally on the disk, the scans could take longer. |If you don’t need the .iso/.vhd/.vhdx, etc… sitting on your profile, move it to a different folder where it’s not sitting on a network share (mapped drive, unc share, smb share)|

## What’s triggering and causing the higher cpu utilization in Microsoft Defender Antivirus.

Now, if you have gone thru the proactive steps, next is to find what’s triggering and causing the higher cpu utilization:


| #|Tools to help narrow down what’s triggering the high cpu utilization|Comments|
| -------- | -------- | -------- |
|1   |[Collect Microsoft Defender Antivirus diagnostic data](/defender-endpoint/collect-diagnostic-data)|Microsoft Defender Antivirus diagnostic data that you want to include whenever troubleshooting an issue with MDAV.|
|2|[Performance analyzer for Microsoft Defender Antivirus](/defender-endpoint/tune-performance-defender-antivirus)|For performance-specific issues related to Microsoft Defender Antivirus, see Performance analyzer for Microsoft Defender Antivirus.  This allows you to run the data collection and parse the data, where it’s easy to understand. Note: Please make sure that the issue is reproducing when you collect this data.|
|3|[Troubleshoot Microsoft Defender Antivirus performance issues with Process Monitor](/defender-endpoint/troubleshoot-av-performance-issues-with-procmon)|If for some reason that the MDAV performance analyzer doesn’t provide with the details that you need to narrow down on what’s triggering the high cpu utilization, you can use Process Monitor (ProcMon). Tip: You can collect for 5-10 minutes. Note: Please make sure that the issue is reproducing when you collect this data.|
|4|[Troubleshoot Microsoft Defender Antivirus performance issues with WPRUI](Troubleshoot Microsoft Defender Antivirus performance issues with WPRUI)|In cases of a more advanced troubleshooting needed, you can use the Windows Performance Recorder UI (WPRUI) or Windows Performance Recorder (WPR).  Tip: Due to the verbosity of this trace, keep it to 3 to 5 minute max.  Note: Please make sure that the issue is reproducing when you collect this data.|

## Check with the vendor for known issues with antivirus products

If you can readily identify the software affecting system performance, go to the software vendor's knowledge base or support center. Check to see if there are any known issues with antivirus products. If necessary, you can open a support ticket with them and ask them to publish one.

We recommend that software vendors follow the various guidelines in [Partnering with the industry to minimize false positives](https://www.microsoft.com/security/blog/2018/08/16/partnering-with-the-industry-to-minimize-false-positives/). The vendor can submit their software through the [Microsoft Security Intelligence portal](https://www.microsoft.com/wdsi/filesubmission?persona=SoftwareDeveloper).

**Q**:  Should I use the “EstimatedImpact” in the Microsoft Protection Log C:\ProgramData\Microsoft\Windows Defender\Support\MPLog-xxxxxxxx-xxxxxx.log?

**A**: No, we do not support looking anything in the MPLog.log, please use the tools mentioned “What’s triggering and causing the higher cpu utilization in Microsoft Defender Antivirus.“

## What if I still have an issue?

You can submit a ticket to [Microsoft support](/defender-endpoint/contact-support).

Follow the steps in [Collect Microsoft Defender Antivirus diagnostic data](collect-diagnostic-data.md).  Follow the steps in [Collect Microsoft Defender Antivirus diagnostic data](collect-diagnostic-data.md).

## See also

- [Collect Microsoft Defender Antivirus diagnostic data](collect-diagnostic-data.md)
- [Configure and validate exclusions for Microsoft Defender Antivirus scans](configure-exclusions-microsoft-defender-antivirus.md)
- [Performance analyzer for Microsoft Defender Antivirus](tune-performance-defender-antivirus.md)

[!INCLUDE [Microsoft Defender for Endpoint Tech Community](../includes/defender-mde-techcommunity.md)]
