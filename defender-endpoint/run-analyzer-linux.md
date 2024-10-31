---
title: Run the client analyzer on Linux
description: Run the Defender for Endpoint client analyzer on Linux
uthor: denisebmsft
ms.author: deniseb
manager: deniseb
ms.reviewer: yongrhee
ms.service: defender-endpoint
ms.subservice: linux
ms.localizationpriority: medium
ms.topic: troubleshooting-general
ms.date: 10/31/2024
ms.custom: partner-contribution
ms.collection:
- m365-security
- tier3
- mde-macos
search.appverid: met150
audience: ITPro
f1.keywords: NOCSH 
---

# Run the client analyzer on Linux

# 

**Applies to:**
- [Microsoft Defender for Endpoint Plan 2](microsoft-defender-endpoint.md)
- [Microsoft Defender XDR](/defender-xdr)

> Want to experience Defender for Endpoint? [Sign up for a free trial.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

When contacting support, you might be asked to provide the output package of the Microsoft Defender for Endpoint Client Analyzer tool.

The XMDEClientAnalyzer is used for diagnosing Microsoft Defender for Endpoint health or reliability issues on onboarded devices running Linux.

There are two different ways to run the client analyzer tool using live response or locally:

1. Using a binary version (no external Python dependency)
1. Using a Python-based solution

## Collect support logs in Microsoft Defender for Endpoint using live response

This section provides instructions on how to run the tool via Live Response on Linux machines.

## Linux

The XMDE Client Analyzer tool can be downloaded as a [binary](https://aka.ms/XMDEClientAnalyzerBinary) or [Python](https://aka.ms/XMDEClientAnalyzer) package that can be extracted and executed on Linux machines. Both versions of the XMDE Client Analyzer can be executed during a Live Response session.

### Prerequisites

- For installation the `unzip` package is required.

- For execution the `acl` package is required.

> [!IMPORTANT]
> Window uses the Carriage Return and Line Feed invisible characters to represent the end of one line and beginning of a new line in a file, but Linux systems uses only the Line Feed invisible character at the end of its file lines. When using the following scripts, if done on Windows, this difference can result in errors and failures of the scripts to run. A potential solution to this is to utilize the Windows Subsystem for Linux and the `dos2unix` package to reformat the script so it aligns with the Unix and Linux format standard.

### Installing the XMDE Client Analyzer

Both versions of XMDE Client Analyzer, binary and Python, a self-contained package that must be downloaded and extracted before executing, and the complete set of steps for this process can be found:

- [Running the Binary version of the Client Analyzer](/defender-endpoint/run-analyzer-macos-linux)

- [Running the Python version of the Client Analyzer](/defender-endpoint/run-analyzer-macos-linux)

Due to the limited commands available in Live Response the steps detailed must be executed in a bash script, and by splitting the installation and execution portion of these commands it's possible to run the install script once, while running the execution script multiple times.

> [!IMPORTANT]
> The example scripts assume the machine has direct internet access and can retrieve the XMDE Client Analyzer from Microsoft. If the machine does not have direct internet access then the installation scripts will need to be updated to fetch the XMDE Client Analyzer from a location the machines can access successfully.

#### Binary Client Analyzer Install Script

The following script performs the first six steps of the [Running the Binary version of the Client Analyzer](/defender-endpoint/run-analyzer-macos-linux). When complete, the XMDE Client Analyzer binary is available from the `/tmp/XMDEClientAnalyzerBinary/ClientAnalyzer` directory.

1. Create a bash file `InstallXMDEClientAnalyzer.sh` and paste the following content into it.

   ```bash
   #! /usr/bin/bash

   echo "Starting Client Analyzer Script. Running As:"
   whoami

   echo "Getting XMDEClientAnalyzerBinary"
   wget --quiet -O /tmp/XMDEClientAnalyzerBinary.zip https://aka.ms/XMDEClientAnalyzerBinary
   echo '9D0552DBBD1693D2E2ED55F36147019CFECFDC009E76BAC4186CF03CD691B469 /tmp/XMDEClientAnalyzerBinary.zip' | sha256sum -c

   echo "Unzipping XMDEClientAnalyzerBinary.zip"
   unzip -q /tmp/XMDEClientAnalyzerBinary.zip -d /tmp/XMDEClientAnalyzerBinary

   echo "Unzipping SupportToolLinuxBinary.zip"
   unzip -q /tmp/XMDEClientAnalyzerBinary/SupportToolLinuxBinary.zip -d /tmp/XMDEClientAnalyzerBinary/ClientAnalyzer

   echo "MDESupportTool installed at /tmp/XMDEClientAnalyzerBinary/ClientAnalyzer"

   ```

#### Python Client Analyzer Install Script

The following script performs the first six steps of the [Running the Python version of the Client Analyzer](/defender-endpoint/run-analyzer-macos-linux). When complete, the XMDE Client Analyzer Python scripts are available from the `/tmp/XMDEClientAnalyzer` directory.

1. Create a bash file `InstallXMDEClientAnalyzer.sh` and paste the following content into it.

   ```bash
   #! /usr/bin/bash

   echo "Starting Client Analyzer Install Script. Running As:"
   whoami
  
   echo "Getting XMDEClientAnalyzer.zip"
   wget --quiet -O XMDEClientAnalyzer.zip https://aka.ms/XMDEClientAnalyzer 
   echo '36C2B13AE657456119F3DC2A898FD9D354499A33F65015670CE2CD8A937F3C66 XMDEClientAnalyzer.zip' | sha256sum -c  

   echo "Unzipping XMDEClientAnalyzer.zip"
   unzip -q XMDEClientAnalyzer.zip -d /tmp/XMDEClientAnalyzer  

   echo "Setting execute permissions on mde_support_tool.sh script"
   cd /tmp/XMDEClientAnalyzer 
   chmod a+x mde_support_tool.sh  

   echo "Performing final support tool setup"
   ./mde_support_tool.sh

   ```

#### Running the Client Analyzer Install Scripts

1. Initiate a [Live Response session](live-response.md#initiate-a-live-response-session-on-a-device) on the machine you need to investigate.

2. Select **Upload file to library**.

3. Select **Choose file**.

4. Select the downloaded file named `InstallXMDEClientAnalyzer.sh`, and then select **Confirm**.

5. While still in the LiveResponse session, use the following commands to install the analyzer:

   ```console
   run InstallXMDEClientAnalyzer.sh
   ```

### Running the XMDE Client Analyzer

Live Response doesn't support running the XMDE Client Analyzer or Python directly, so an execution script is necessary.

> [!IMPORTANT]
> The following scripts assume the XMDE Client Analyzer was installed using the same locations from the scripts mentioned earlier. If your organization has chosen to install the scripts into a different location, then the following scripts need to be updated to align with your organization's chosen installation location.

#### Binary Client Analyzer Run Script

The Binary Client Analyzer accepts command line parameters to perform different analysis tests. To provide similar capabilities during Live Response the execution script takes advantage of the `$@` bash variable to pass all input parameters provided to the script to the XMDE Client Analyzer.

1. Create a bash file `MDESupportTool.sh` and paste the following content into it.

   ```bash
   #! /usr/bin/bash

   echo "cd /tmp/XMDEClientAnalyzerBinary/ClientAnalyzer"
   cd /tmp/XMDEClientAnalyzerBinary/ClientAnalyzer

   echo "Running MDESupportTool"
   ./MDESupportTool $@

   ```

#### Python Client Analyzer Run Script

The Python Client Analyzer accepts command line parameters to perform different analysis tests. To provide similar capabilities during Live Response the execution script takes advantage of the `$@` bash variable to pass all input parameters provided to the script to the XMDE Client Analyzer.

1. Create a bash file `MDESupportTool.sh` and paste the following content into it.

   ```bash
   #! /usr/bin/bash  

   echo "cd /tmp/XMDEClientAnalyzer"
   cd /tmp/XMDEClientAnalyzer 

   echo "Running mde_support_tool"
   ./mde_support_tool.sh $@

   ```

#### Running the Client Analyzer Script

> [!NOTE]
> If you have an active Live Response session you can skip Step 1.

1. Initiate a [Live Response session](live-response.md#initiate-a-live-response-session-on-a-device) on the machine you need to investigate. 

2. Select **Upload file to library**.

3. Select **Choose file**.

4. Select the downloaded file named `MDESupportTool.sh`, and then select **Confirm**.

1. While still in the Live Response session, use the following commands to run the analyzer and collect the resulting file.

   ```
   run MDESupportTool.sh -parameters "--bypass-disclaimer -d"
   GetFile "/tmp/your_archive_file_name_here.zip"
   ```
   
## Collect Microsoft Defender for Endpoint support logs locally

This section provides instructions on how to run the tool locally on the Linux machines.

## Running the binary version of the client analyzer

1. Download the [XMDE Client Analyzer Binary](https://aka.ms/XMDEClientAnalyzerBinary) tool to the Linux machine you need to investigate.  
If you're using a terminal, download the tool by entering the following command:

```
   ```bash
wget --quiet -O XMDEClientAnalyzerBinary.zip https://aka.ms/XMDEClientAnalyzerBinary
```
```1. Verify the download.

- Linux

       ```bash
    echo '2A9BF0A6183831BE43C7BCB7917A40D772D226301B4CDA8EE4F258D00B6E4E97 XMDEClientAnalyzerBinary.zip' | sha256sum -c
    ```

2. Extract the contents of _XMDEClientAnalyzerBinary.zip_ on the machine.

    If you're using a terminal, extract the files by entering the following command:

    ```bash
    unzip -q XMDEClientAnalyzerBinary.zip -d XMDEClientAnalyzerBinary
    ```

3. Change to the tool's directory by entering the following command:

    ```bash
    cd XMDEClientAnalyzerBinary
    ```

4. Two new zip files are produced:

   - **SupportToolLinuxBinary.zip** : For all Linux devices
   - **SupportToolMacOSBinary.zip** : For Mac devices

5. Unzip one of the above 2 zip files based on the machine you need to investigate.

   When using a terminal, unzip the file by entering one of the following commands based on OS type:

   - Linux

     ```bash
     unzip -q SupportToolLinuxBinary.zip
     ```

   - Mac

     ```bash
     unzip -q SupportToolMacOSBinary.zip
     ```

6. Run the tool as _root_ to generate diagnostic package:

   ```bash
   sudo ./MDESupportTool -d
   ```

## Running the Python-based client analyzer

> [!NOTE]
> - The analyzer depends on few extra PIP packages (`decorator`, `sh`, `distro`, `lxml`, and `psutil`) which are installed in the operating system when in root to produce the result output. If not installed, the analyzer attempts to fetch it from the [official repository for Python packages](https://pypi.org/search/?q=lxml).
> - In addition, the tool currently requires Python version 3 or later to be installed on your device.
> - If your device is behind a proxy, then you can simply pass the proxy server as an environment variable to the `mde_support_tool.sh` script. For example: `https_proxy=https://myproxy.contoso.com:8080 ./mde_support_tool.sh"`.

> [!WARNING]
> Running the Python-based client analyzer requires the installation of PIP packages which may cause some issues in your environment. To avoid issues from occurring, it is recommended that you install the packages into a user PIP environment.

1. Download the [XMDE Client Analyzer](https://aka.ms/XMDEClientAnalyzer) tool to the macOS or Linux machine you need to investigate.

    If you're using a terminal, download the tool by running the following command:

    ```bash
    wget --quiet -O XMDEClientAnalyzer.zip https://aka.ms/XMDEClientAnalyzer
    ```

1. Verify the download

- Linux

       ```bash
    echo '84C9718FF3D29DA0EEE650FB2FC0625549A05CD1228AC253DBB92C8B1D9F1D11 XMDEClientAnalyzer.zip' | sha256sum -c
    ```

3. Extract the contents of XMDEClientAnalyzer.zip on the machine.
    If you're using a terminal, extract the files by using the following command:

    ```bash
    unzip -q XMDEClientAnalyzer.zip -d XMDEClientAnalyzer
    ```

4. Change directory to the extracted location.

    ```bash
    cd XMDEClientAnalyzer
    ```

5. Give the tool executable permission:

    ```bash
    chmod a+x mde_support_tool.sh
    ```

6. Run as a non-root user to install required dependencies:

    ```bash
    ./mde_support_tool.sh
    ```

7. To collect actual diagnostic package and generate the result archive file, run again as root:

    ```bash
    sudo ./mde_support_tool.sh -d
    ```

## Command line options

### Primary command lines

Use the following command to get the machine diagnostic.

```console
-h, --help            show this help message and exit
--output OUTPUT, -o OUTPUT
                      Output path to export report
--outdir OUTDIR       Directory where diagnostics file will be generated
--no-zip, -nz         If set a directory will be created instead of an archive file
--force, -f           Will overwrite if output directory exists
--diagnostic, -d      Collect extensive machine diagnostic information
--bypass-disclaimer   Do not display disclaimer banner
--interactive, -i     Interactive diagnostic
--delay DELAY, -dd DELAY
                      Set MDATP log level. If you use interactive or delay mode, the log level will set to debug automatically, and reset after 48h.
--mdatp-log {info,debug,verbose,error,trace,warning}
                      Set MDATP log level
--max-log-size MAX_LOG_SIZE
                      Maximum log file size in MB before rotating(Will restart mdatp)
```

Usage example: `sudo ./MDESupportTool -d`

NOTE: The log level auto-reset feature only available in 2405 or newer client version.

### Positional arguments

#### Collect performance info

Collect extensive machine performance tracing for analysis of a performance scenario that can be reproduced on demand.

```console
-h, --help            show this help message and exit
--frequency FREQUENCY
                      profile at this frequency
--length LENGTH       length of time to collect (in seconds)
```

Usage example: `sudo ./MDESupportTool performance --frequency 2`

#### Exclude mode

Add exclusions for audit-d monitoring.

> [!NOTE]
> This functionality exists for Linux only.

```console
  -h, --help            show this help message and exit
  -e <executable>, --exe <executable>
                        exclude by executable name, i.e: bash
  -p <process id>, --pid <process id>
                        exclude by process id, i.e: 911
  -d <directory>, --dir <directory>
                        exclude by target path, i.e: /var/foo/bar
  -x <executable> <directory>, --exe_dir <executable> <directory>
                        exclude by executable path and target path, i.e: /bin/bash /var/foo/bar
  -q <q_size>, --queue <q_size>
                        set dispatcher q_depth size
  -r, --remove          remove exclusion file
  -s, --stat            get statistics about common executables
  -l, --list            list auditd rules
  -o, --override        Override the existing auditd exclusion rules file for mdatp
  -c <syscall number>, --syscall <syscall number>
                        exclude all process of the given syscall
```

Usage example: `sudo ./MDESupportTool exclude -d /var/foo/bar`

### AuditD Rate Limiter

Syntax that can be used to limit the number of events being reported by the auditD plugin. This option sets the rate limit globally for AuditD causing a drop in all the audit events. When the limiter is enabled the number of auditd events are limited to 2500 events/sec. This option can be used in cases where we see high CPU usage from AuditD side.

> [!NOTE]
> This functionality exists for Linux only.

```console
-h, --help                                  show this help message and exit
-e <true/false>, --enable <true/false>      enable/disable the rate limit with default values
```

Usage example: `sudo ./mde_support_tool.sh ratelimit -e true`

> [!NOTE]
> This functionality should be carefully used as limits the number of events being reported by the auditd subsystem as a whole. This could reduces the number of events for other subscribers as well.

### AuditD Skip Faulty Rules

This option enables you to skip the faulty rules added in the auditd rules file while loading them. This option allows the auditd subsystem to continue loading rules even if there's a faulty rule. This option summarizes the results of loading the rules. In the background, this option runs the auditctl with the -c option.

> [!NOTE]
> This functionality is only available on Linux.

```console
-h, --help                                  show this help message and exit
-e <true/false>, --enable <true/false>      enable/disable the option to skip the faulty rules. In case no argumanet is passed, the option will be true by default.
```

Usage example: `sudo ./mde_support_tool.sh skipfaultyrules -e true`

> [!NOTE]
> This functionality will be skipping the faulty rules. The faulty rule then needs to be further identified and fixed.

## Result package contents on Linux

- report.html

  Description: The main HTML output file that contains the findings and guidance from running the client analyzer tool on the device. This file is only generated when running the Python-based version of the client analyzer tool.
  
- mde_diagnostic.zip

  Description: Same diagnostic output that gets generated when running *mdatp diagnostic create* on [Linux](linux-resources.md#collect-diagnostic-information).
  
- mde.xml

  Description: XML output that is generated while running and is used to build the html report file.
  
- Processes_information.txt

  Description: contains the details of the running Microsoft Defender for Endpoint related processes on the system.
  
- Log.txt

  Description: contains the same log messages written on screen during the data collection.
  
- Health.txt

  Description: The same basic health output that is shown when running *mdatp health* command.
  
- Events.xml

  Description: Additional XML file used by the analyzer when building the HTML report.
  
- Audited_info.txt

  Description: details on audited service and related components for [Linux](linux-resources.md) OS.
  
- perf_benchmark.tar.gz

  Description: The performance test reports. You'll see this only if you're using the performance parameter.
See also

- [Client analyzer overview](overview-client-analyzer.md)

- [Download and run the client analyzer](download-client-analyzer.md)

- [Run the client analyzer on Windows](run-analyzer-windows.md)

- [Run the client analyzer on macOS or Linux](run-analyzer-macos-linux.md)

- [Data collection for advanced troubleshooting on Windows](data-collection-analyzer.md)

- [Understand the analyzer HTML report](analyzer-report.md)

[!INCLUDE [Microsoft Defender for Endpoint Tech Community](../includes/defender-mde-techcommunity.md)]




