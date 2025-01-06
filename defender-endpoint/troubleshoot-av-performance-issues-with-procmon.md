---
# Required metadata
# For more information, see https://review.learn.microsoft.com/en-us/help/platform/learn-editor-add-metadata?branch=main
# For valid values of ms.service, ms.prod, and ms.topic, see https://review.learn.microsoft.com/en-us/help/platform/metadata-taxonomies?branch=main

title:       # Add a title for the browser tab
description: # Add a meaningful description for search results
author:      YongRhee-MSFT # GitHub alias
ms.author:   yongrhee # Microsoft alias
ms.service:  # Add the ms.service or ms.prod value
# ms.prod:   # To use ms.prod, uncomment it and delete ms.service
ms.topic:    # Add the ms.topic value
ms.date:     01/06/2025
---

# Troubleshoot Microsoft Defender Antivirus performance issues with Process Monitor

## Capture process logs using Process Monitor

Process Monitor (ProcMon) is an advanced monitoring tool that can show real-time processes. You can use this tool to capture the performance issue (e.g. high cpu) as it is occurring.

This is also especially useful when troubleshooting various application compatibility scenarios.

There are two ways to capture a Process Monitor (ProcMon) trace:

1. Using the MDE Client Analyzer

1. Manually

### Using the MDE Client Analyzer

1. Download the [MDE Client Analyzer ](/defender-endpoint/download-client-analyzer)

1. Run the MDE Client Analyzer using [Live Response or locally ](/defender-endpoint/run-analyzer-windows)

> [!TIP]
> Before starting the trace, please make sure that the issue is reproducing.  And have as many apps closed that do not contribute to the repro.

3. Run the MDE Client Analyzer with the -c and -v switches


```powershell
C:\Work\tools\MDEClientAnalyzer\MDEClientAnalyzer.cmd -c -v
```

### Manually

1. Download [Process Monitor v3.89](/sysinternals/downloads/procmon) to a folder like `C:\temp`.

1. To remove the file's mark of the web:

   1. Right-click **ProcessMonitor.zip** and select **Properties**.
      
   1. Under the *General* tab, look for *Security*.
      
   1. Check the box beside **Unblock**.
      
   1. Select **Apply**.
      
![Screenshot showing the Remove MOTW page.](media/procmon-motw.png)

1. Unzip the file in `C:\temp` so that the folder path is `C:\temp\ProcessMonitor`.

1. Copy **ProcMon.exe** to the Windows client or Windows server you're troubleshooting.

1. Before running ProcMon, make sure all other applications not related to the high CPU usage issue are closed. Taking this step helps to minimize the number of processes to check.

1. You can launch ProcMon in two ways.

   1. Right-click **ProcMon.exe** and select **Run as administrator**.
      
      Since logging starts automatically, select the magnifying glass icon to stop the current capture or use the keyboard shortcut **Ctrl+E**.
      
      ![Screenshot showing the magnifying glass icon.](media/procmon-magglass.png)
      
      To verify that you've stopped the capture, check if the magnifying glass icon now appears with a red X.
      
      ![Screenshot showing a red slash.](media/procmon-magglass-stop.png)
      
      Next, to clear the earlier capture, select the eraser icon.
      
      ![Screenshot showing the clear icon](media/procmon-eraser-clear.png)
      
      Or use the keyboard shortcut **Ctrl+X**.
      
   1. The second way is to run the **command line** as admin, then from the Process Monitor path, run:
      
      ![Screenshot showing the cmd procmon.](media/cmd-procmon.png)
      
      ConsoleEdit development language
      
      
      ```
       Procmon.exe /AcceptEula /Noconnect /Profiling
      ```
      
      **Tip**
      
      Make the ProcMon window as small as possible when capturing data so you can easily start and stop the trace.
      
      ![Screenshot showing the page with Procmon minimized.](media/procmon-minimize.png)
      
1. After following one of the procedures in step 6, you'll next see an option to set filters. Select **OK**. You can always filter the results after the capture is completed.

![Screenshot showing the page where System Exclude is chosen as the Filter out Process Name.](media/procmon-filter-options.png)

1. To start the capture, select the magnifying glass icon again.

1. Reproduce the problem.

**Tip**

Wait for the problem to be fully reproduced, then take note of the timestamp when the trace started.

1. Once you have two to four minutes of process activity during the high CPU usage condition, stop the capture by selecting the magnifying glass icon.

1. To save the capture with a unique name and with the `.pml` format, select **File** then select **Save...**. Make sure to select the radio buttons **All events** and **Native Process Monitor Format (PML)**.

![Screenshot showing the save settings page](media/procmon-savesettings1.png)

1. For better tracking, change the default path from `C:\temp\ProcessMonitor\LogFile.PML` to `C:\temp\ProcessMonitor\%ComputerName%_LogFile_MMDDYEAR_Repro_of_issue.PML` where:

  - `%ComputerName%` is the device name
  - `MMDDYEAR` is the month, day, and year
  - `Repro_of_issue` is the name of the issue you're trying to reproduce
    
**Tip**

If you have a working system, you might want to get a sample log to compare.

1. Zip the `.pml` file and submit it to Microsoft support.

