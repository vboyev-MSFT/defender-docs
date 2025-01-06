---
title: Troubleshoot Microsoft Defender Antivirus performance issues with WPRUI
description: Troubleshoot Microsoft Defender Antivirus performance issues with WPRUI
author: emmwalshh
ms.author: emmwalsh
ms.reviewer: yongrhee
ms.service: defender-endpoint
ms.topic: troubleshooting-general
ms.date: 01/06/2025
ms.subservice: ngp
manager: deniseb
ms.localizationpriority: medium 
f1.keywords: NOCSH 
audience: ITPro
ai-usage: human-only
---

# Troubleshoot Microsoft Defender Antivirus performance issues with WPRUI

## Capture performance logs using Windows Performance Recorder

You can use Windows Performance Recorder (WPR) to include additional information in your submission to Microsoft support. WPR is a powerful recording tool that creates Event Tracing for Windows recordings.

WPR is part of the Windows Assessment and Deployment Kit (Windows ADK) and can be downloaded from [Download and install the Windows ADK](/windows-hardware/get-started/adk-install). You can also download it as part of the Windows 10 Software Development Kit at [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/).

You can use the WPR user interface by following the steps in [Capture performance logs using the WPR UI](/editor/MicrosoftDocs/defender-docs-pr/defender-endpoint%2Ftroubleshoot-performance-issues.md/main/ae28f1cf-14bc-fb9c-5f0c-873a683e907c/?branch=main&branchFallbackFrom=main%2C).

Alternatively, you can also use the command-line tool *wpr.exe*, which is available in Windows 8 and later versions by following the steps in [Capture performance logs using the WPR CLI](/editor/MicrosoftDocs/defender-docs-pr/defender-endpoint%2Ftroubleshoot-performance-issues.md/main/ae28f1cf-14bc-fb9c-5f0c-873a683e907c/?branch=main&branchFallbackFrom=main%2C).

### Capture performance logs using the WPR UI

> [!TIP]
> If multiple devices are experiencing this issue, use the one which has the most RAM.

1. Download and install WPR.

2. Under *Windows Kits*, right-click **Windows Performance Recorder**.

   ![Screenshow showing the Start menu](media/wpr-01.png)

Select **More**. Select **Run as administrator**.

3. When the User Account Control dialog box appears, select **Yes**.

   ![Screenshot showing the UAC page.](media/wpt-yes.png)

4. Next, download the [Microsoft Defender for Endpoint analysis](https://github.com/YongRhee-MDE/Scripts/blob/master/MDAV.wprp) profile and save as `MDAV.wprp` to a folder like `C:\temp`.

5. On the WPR dialog box, select **More options**.

   ![Screenshot showing the page where you can select more options](media/wpr-03.png)

6. Select **Add Profiles...** and browse to the path of the `MDAV.wprp` file.

7. After that, you should see a new profile set under *Custom measurements* named *Microsoft Defender for Endpoint analysis* underneath it.

   ![Screenshot showing the in-file.](media/wpr-infile.png)

   > [!WARNING]
   > If your Windows Server has 64 GB of RAM or more, use the custom measurement `Microsoft Defender for Endpoint analysis for large servers` instead of `Microsoft Defender for Endpoint analysis`. Otherwise, your system could consume a high amount of non-paged pool memory or buffers which can lead to system instability. You can choose which profiles to add by expanding **Resource Analysis**.
   > This custom profile provides the necessary context for in-depth performance analysis.

8. To use the custom measurement Microsoft Defender for Endpoint verbose analysis profile in the WPR UI:

   1. Ensure no profiles are selected under the *First-level triage*, *Resource Analysis* and *Scenario Analysis* groups.

   2. Select **Custom measurements**.

   3. Select **Microsoft Defender for Endpoint analysis**.

   4. Select **Verbose** under *Detail* level.

   5. Select **File** or **Memory** under Logging mode.

   > [!IMPORTANT]
   > You should select *File* to use the file logging mode if the performance issue can be reproduced directly by the user. Most issues fall under this category. However, if the user cannot directly reproduce the issue but can easily notice it once the issue occurs, the user should select *Memory* to use the memory logging mode. This ensures that the trace log will not inflate excessively due to the long run time.

9. Now you're ready to collect data. Exit all the applications that aren't relevant to reproducing the performance issue. You can select **Hide options** to keep the space occupied by the WPR window small.

   ![Screenshot showing the Hide options.](media/wpr-08.png)

10. Select **Start**.

   ![Screenshot showing the Record system information page.](media/wpr-09.png)

11. Reproduce the issue.

   > [!TIP]
   > Keep the data collection to no more than five minutes. Two to three minutes is a good range since a lot of data is being collected.

12. Select **Save**.

   ![Screenshot showing the Save option.](media/wpr-10.png)

13. Fill up **Type in a detailed description of the problem:** with information about the problem and how you reproduced the issue.

   ![Screenshot showing the pane in which you fill.](media/wpr-12.png)

1. Select **File Name:** to determine where your trace file is saved. By default, it's saved to `%user%\Documents\WPR Files\`.

   1. Select **Save**.

14. Wait while the trace is being merged.

   ![Screenshot showing the WPR gathering general trace.](media/wpr-13.png)

15. Once the trace is saved, select **Open folder**.

   ![Screenshot that displays the notification that WPR trace has been saved.](media/wpr-14.png)

   Include both the file and the folder in your submission to Microsoft Support.

   ![Screenshot showing the details of the file and the folder.](media/wpr-15.png)

### Capture performance logs using the WPR CLI

The command-line tool *wpr.exe* is part of the operating system starting with Windows 8. To collect a WPR trace using the command-line tool wpr.exe:

1. Download **[Microsoft Defender for Endpoint analysis](https://github.com/YongRhee-MDE/Scripts/blob/master/MDAV.wprp)** profile for performance traces to a file named `MDAV.wprp` in a local directory such as `C:\traces`.

2. Right-click the **Start Menu** icon and select **Windows PowerShell (Admin)** or **Command Prompt (Admin)** to open an Admin command prompt window.

3. When the User Account Control dialog box appears, select **Yes**.

4. At the elevated prompt, run the following command to start a Microsoft Defender for Endpoint performance trace:

   ```console
   
   wpr.exe -start C:\traces\MDAV.wprp!WD.Verbose -filemode
  
   ```

   > [!WARNING]
   > If your Windows Server has 64 GB or RAM or more, use profiles `WDForLargeServers.Light` and `WDForLargeServers.Verbose` instead of profiles `WD.Light` and `WD.Verbose`, respectively. Otherwise, your system could consume a high amount of non-paged pool memory or buffers which can lead to system instability.

5. Reproduce the issue.

   > [!TIP]
   > Keep the data collection no to more than five minutes. Depending on the scenario, two to three minutes is a good range since a lot of data is being collected.

6. At the elevated prompt, run the following command to stop the performance trace, making sure to provide information about the problem and how you reproduced the issue:

   ```console
   wpr.exe -stop merged.etl "Timestamp when the issue was reproduced, in HH:MM:SS format" "Description of the issue" "Any error that popped up"
   ```

7. Wait until the trace is merged.

8. Include both the file and the folder in your submission to Microsoft support.

## See also

- [Collect Microsoft Defender Antivirus diagnostic data](collect-diagnostic-data.md)
- [Configure and validate exclusions for Microsoft Defender Antivirus scans](configure-exclusions-microsoft-defender-antivirus.md)
- [Performance analyzer for Microsoft Defender Antivirus](tune-performance-defender-antivirus.md)

[!INCLUDE [Microsoft Defender for Endpoint Tech Community](../includes/defender-mde-techcommunity.md)]
