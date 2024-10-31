---
title: Run the client analyzer on macOS
description: Learn how to use the MDE Client Analyzer on Mac to identify health or performance issue causes.
author: denisebmsft
ms.author: deniseb
manager: deniseb
ms.reviewer: yongrhee
ms.service: defender-endpoint
ms.subservice: macos
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

# Run the client analyzer on macOS

If you're experiencing reliability or device health issues with Microsoft Defender for Endpoint on macOS, you can use the XMDE Client Analyzer to diagnose these issues. This article describes two ways to use the client analyzer tool:

- [Use the binary version of the client analyzer](#use-the-binary-version-of-the-client-analyzer)
- 

1. Using a binary version (no external Python dependency)
2. Using a Python-based solution

## Use the binary version of the client analyzer

1. Download the [XMDE Client Analyzer Binary](https://aka.ms/XMDEClientAnalyzerBinary) tool to the macOS machine you need to investigate. 

   If you're using a terminal, download the tool by running the following command:

   ```bash
   wget --quiet -O XMDEClientAnalyzerBinary.zip https://aka.ms/XMDEClientAnalyzerBinary
   ```

2. Verify the download.

   ```bash
   echo '2A9BF0A6183831BE43C7BCB7917A40D772D226301B4CDA8EE4F258D00B6E4E97  XMDEClientAnalyzerBinary.zip' | shasum -a 256 -c
   ```

2. Extract the contents of `XMDEClientAnalyzerBinary.zip` on the machine. 

   If you're using a terminal, extract the files by running the following command:

   ```bash
   unzip -q XMDEClientAnalyzerBinary.zip -d XMDEClientAnalyzerBinary
   ```

3. Change to the tool's directory by running the following command:

   ```bash
   cd XMDEClientAnalyzerBinary
   ```

4. Notice that the following two zipped files are produced:

   - `SupportToolLinuxBinary.zip`: For all Linux devices
   - `SupportToolMacOSBinary.zip`: For Mac devices

5. Depending on the machine you're investigating, unzip the appropriate file. 

   | OS type | Terminal command |
   |---|---|
   | Linux | `unzip -q SupportToolLinuxBinary.zip` |
   | Mac | `unzip -q SupportToolMacOSBinary.zip` |

6. Run the tool as root to generate your diagnostic package:

   ```bash
   sudo ./MDESupportTool -d
   ```

## Use the Python-based client analyzer

The client analyzer depends on few extra PIP packages (`decorator`, `sh`, `distro`, `lxml`, and `psutil`) that are installed in the operating system when in root mode to produce the result output. If not installed, the analyzer attempts to fetch it from the [official repository for Python packages](https://pypi.org/search/?q=lxml).

The tool currently requires Python version 3 or later to be installed on your device. If your device is behind a proxy, then you can simply pass the proxy server as an environment variable to the `mde_support_tool.sh` script. For example: `https_proxy=https://myproxy.contoso.com:8080 ./mde_support_tool.sh"`.

> [!WARNING]
> Running the Python-based client analyzer requires the installation of PIP packages which could cause some issues in your environment. To avoid issues from occurring, it is recommended that you install the packages into a user PIP environment.

1. Download the [XMDE Client Analyzer](https://aka.ms/XMDEClientAnalyzer) tool to the Mac or Linux machine you're investigating.

   If you're using a terminal, download the tool by running the following command:

   ```bash
   wget --quiet -O XMDEClientAnalyzer.zip https://aka.ms/XMDEClientAnalyzer
   ```

2. Verify the download. 

   | OS | Command |
   |--|--|
   | Linux | `echo '84C9718FF3D29DA0EEE650FB2FC0625549A05CD1228AC253DBB92C8B1D9F1D11 XMDEClientAnalyzer.zip' | sha256sum -c` |
   | macOS | `echo '84C9718FF3D29DA0EEE650FB2FC0625549A05CD1228AC253DBB92C8B1D9F1D11  XMDEClientAnalyzer.zip' | shasum -a 256 -c` |

3. Extract the contents of `XMDEClientAnalyzer.zip` on the machine. 

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

#### Use OS trace (for macOS only)

Use OS tracing facilities to record Defender for Endpoint performance traces.

> [!NOTE]
> This functionality exists in the Python solution only.

```console
-h, --help       show this help message and exit
--length LENGTH  Length of time to record the trace (in seconds).
--mask MASK      Mask to select with event to trace. Defaults to all
```

On running this command for the first time, it installs a Profile configuration.

Follow this to approve profile installation: [Apple Support Guide](https://support.apple.com/guide/mac-help/configuration-profiles-standardize-settings-mh35561/mac#:~:text=Install%20a%20configuration%20profile%20you%E2%80%99ve%20received).

Usage example `./mde_support_tool.sh trace --length 5`

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
> This functionality skips faulty rules. The faulty rule then needs to be further identified and fixed.

## Result package contents on macOS and Linux

| File | Description |
|---|---|
| `report.html` | The main HTML output file that contains the findings and guidance from running the client analyzer tool on the device. This file is only generated when running the Python-based version of the client analyzer tool. |
| `mde_diagnostic.zip` | Same diagnostic output that gets generated when running `mdatp diagnostic create` on either [macOS](mac-resources.md#collecting-diagnostic-information) or [Linux](linux-resources.md#collect-diagnostic-information). |
| `mde.xml` | XML output that is generated while running and is used to build the html report file. |
| `Processes_information.txt` | Contains the details of the running Microsoft Defender for Endpoint related processes on the system. |
| `Log.txt` | Contains the same log messages written on screen during the data collection. |
| `Health.txt` | The same basic health output that is shown when running *mdatp health* command. |
| `Events.xml` | Additional XML file used by the analyzer when building the HTML report. |
| `Audited_info.txt` | Details on audited service and related components for [Linux](linux-resources.md) OS. |
| `perf_benchmark.tar.gz` | The performance test reports. You'll see this only if you're using the performance parameter. |

[!INCLUDE [Microsoft Defender for Endpoint Tech Community](../includes/defender-mde-techcommunity.md)]
