---
title: Microsoft Defender for Endpoint on Linux for ARM devices (preview)
description: Defender for Endpoint on Linux now supports ARM devices. Read this article to learn more.            
author: denisebmsft
ms.author: deniseb
manager: deniseb 
ms.date: 12/06/2024
ms.topic: how-to
ms.service: defender-endpoint
ms.subservice: linux
ms.localizationpriority: medium 
ms.collection: 
- m365-security
- tier3
- mde-linux
ms.custom: 
- partner-contribution
ms.reviewer: meghapriya
search.appverid: MET150
f1.keywords: NOCSH 
audience: ITPro
ai-usage: human-only
---

# Microosft Defender for Endpoint on Linux for ARM devices (preview)

Now in [preview](/defender-xdr/preview), Microsoft Defender for Endpoint on Linux supports ARM64-based Linux servers. Read this article to get an overview of this new capability, how to deploy it on ARM64-based Linux servers, and how to troubleshoot issues that you might encounter.

## Overview of Defender for Endpoint on Linux for ARM devices

[Microsoft Defender for Endpoint on Linux](microsoft-defender-endpoint-linux.md) is a unified endpoint security solution that helps you protect your server devices from advanced threats. Currently in preview, Defender for Endpoint on Linux now supports ARM64-based Linux servers with the same capabilities that are supported on x64-based Linux servers (including Intel and AMD 64-bit platform): 

- Microsoft Defender Antivirus
- Endpoint detection and response (EDR)
- Live response
- Device isolation
- Advanced hunting
- Vulnerability management
- Centralized policy configuration using security settings management

Initially, the following Linux distributions are supported in preview:

- Ubuntu 20.04 ARM64
- Ubuntu 22.04 ARM64
- Amazon Linux 2 ARM64
- Amazon Linux 2023 ARM64

> [!NOTE]
> Support for more Linux distributions is planned as part of this preview program.

## Deploy Defender for Endpoint on Linux for ARM devices

You can choose from several methods to deploy Defender for Endpoint on Linux on your ARM64-based device:

- Installer script
- Ansible
- Puppet
- Saltstack
- Microsoft Defender for Cloud

### Before you begin

- Make sure to meet the prerequisites for Defender for Endpoint on Linux: [Prerequisites](microsoft-defender-endpoint-linux.md#prerequisites)

- To onboard servers to Defender for Endpoint, server licenses are required. You can choose from these options:
   - Microsoft Defender for Servers Plan 1 or Plan 2 (as part of the [Defender for Cloud](/azure/defender-for-cloud/defender-for-cloud-introduction)) offering
   - Microsoft Defender for Endpoint for Servers

   [Learn more about Defender for Endpoint licensing](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-defender-for-endpoint).

- Make sure to install the agent version `101.24102.0002` from the insiders-slow channel on the ARM device. (See [What's new in Microsoft Defender for Endpoint on Linux](linux-whatsnew.md).) 

### Deploy using the installer script

1. In the [Microsoft Defender portal](https://security.microsoft.com), go to to **Settings** > **Endpoints** > **Device management** > **Onboarding**.

2. In the onboarding screen, select the following options:

   1. In the **Select operating system to start onboarding process** list, select **Linux Server**.

   2. In the **Connectivity type** list, select **Streamlined**. Or, if necessary, you can select **Standard**. (For more information, see [Onboarding devices using streamlined connectivity for Microsoft Defender for Endpoint](configure-device-connectivity.md).)

   3. In the **Deployment method** list, select **Local Sript (Python)**.

   4. Select **Download onboarding package**.

3. In a new browser window, download the [Defender for Endpoint installer bash script](https://github.com/microsoft/mdatp-xplat/blob/master/linux/installation/mde_installer.sh).

4. Use the following command to grant the necessary permissions for the script:

   `$chmod +x /mde_installer.sh`

5. Run the following command to execute the installer script:

   `$sudo ~/mde_installer.sh --install --channel insiders-slow --onboard ~/MicrosoftDefenderATPOnboardingLinuxServer.py`

6. Validate the deployment by following these steps:

   1. In the [Microsoft Defender portal](https://security.microsoft.cm), under **Assets** > **Devices**, look for the Linux device you just onboarded. 
   
      It can take approximately 20 minutes for the device to show up in the portal.

   2. On the device, run the following command to check the health status. A return value of `true` denotes that the product is functioning as expected:

      `$ mdatp health --field healthy`

7. If you run into an issue, see [Troubleshoot deploymemt issues](#troubleshoot-deploymemt-issues) (in this article).
 

## Troubleshoot deploymemt issues

## See also

[Microsoft Defender for Endpoint on Linux](microsoft-defender-endpoint-linux.md)

[Supported Microsoft Defender for Endpoint capabilities by platform](supported-capabilities-by-platform.md)