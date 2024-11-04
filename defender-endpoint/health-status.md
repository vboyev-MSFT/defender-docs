---
title: Investigate agent health issues
description: Learn about the values returned when running the mdatp health command
ms.service: defender-endpoint
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: deniseb
audience: ITPro
ms.collection: 
- m365-security
- tier3
ms.topic: conceptual
ms.subservice: onboard
search.appverid: met150
ms.date: 11/04/2024
---

# Investigate agent health issues

[!INCLUDE [Microsoft Defender XDR rebranding](../includes/microsoft-defender.md)]

- [Microsoft Defender for Endpoint Plan 1](microsoft-defender-endpoint.md)
- [Microsoft Defender for Endpoint Plan 2](microsoft-defender-endpoint.md)
- [Microsoft Defender XDR](/defender-xdr)

The following table provides information about the values that are returned when you run the `mdatp health` command and their corresponding descriptions.

| Value | Description |
|---|---|
| `app_version` | Displays Microsoft Defender application version.|
|`automatic_definition_update_enabled`|`True` if automatic antivirus definition updates are enabled; otherwise, `false`.|
|`behavior_monitoring`|Feature to detect real time threats and prevention by monitoring the behavior of applications, services, and files.<br/><br/>Can be one of the following: <br/>- **disabled** - default <br/>- **enabled** |
|`cloud_automatic_sample_submission_consent`|Current sample submission level. <br/><br/>Can be one of the following values: <br/>- **None**: No suspicious samples are submitted to Microsoft.<br/>- **safe**: Only suspicious samples that don't contain personally identifiable information (PII) are submitted automatically. This is the default value for this setting.<br/>- **All**: All suspicious samples are submitted to Microsoft.|
|`cloud_diagnostic_enabled`|`True` if optional diagnostic data collection is enabled; otherwise, `false`. <br/><br/>For more information related to Defender for Endpoint and other products and services like Microsoft Defender Antivirus and Windows, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=827576).|
|`cloud_enabled`|`True` if cloud-delivered protection is enabled; otherwise, `false`.|
|`conflicting_applications`|List of applications that are possibly conflicting with Microsoft Defender for Endpoint. This list includes, but isn't limited to, other security products and other applications known to cause compatibility issues.|
|definitions_status|Status of antivirus definitions. Can be one of the following: <br/>- **up_to_date**<br/>- **updating**<br/>- **unavailable**|
|definitions_updated|Date and time of last antivirus definition update.|
|definitions_updated_minutes_ago|Number of minutes since last antivirus definition update.|
|definitions_version|Antivirus definition version.|
|edr_client_version|Version of the EDR client running on the device.|
|edr_configuration_version|EDR configuration version.|
|edr_device_tags|List of tags associated with the device.|
|edr_early_preview_enabled|Setting of edr early preview. Can be one of the following: <ul><li>**disabled**</li><li>**enabled**</li></ul>|
|edr_group_ids|Group ID that the device is associated with.|
|edr_machine_id|Device identifier used in Microsoft Defender XDR.|
|engine_load_status|Status of antivirus engine whether its running. Can be one of the following: <ul><li>**Engine not loaded** - AV engine process is down</li><li>**Engine load succeeded** - AV engine process is up and running</li></ul>|
|engine_version|Version of the antivirus engine.|
|healthy|True if the product is healthy, false otherwise.|
|health_issues|Lists health issues if any.|
|licensed|True if the device is onboarded to a tenant, false otherwise.|
|log_level|Current log level for the product. Can be one of the following values: <ul><li>**info**</li><li>**debug**</li></ul>|
|machine_guid|Unique machine identifier used by the antivirus component.|
|network_protection_enforcement_level|Mode of network protection. Can be one of the following: <ul><li>**disabled** - all components associated with network protection are disabled</li><li>**block** - network protection prevents connection to malicious websites</li><li>**audit** - Check how blocks occur</li></ul>|
|network_protection_status|Status of the network protection component (macOS only). Can be one of the following values: <ul><li>**starting** - Network protection is starting</li><li>**failed_to_start** - Network protection couldn't be started due to an error</li><li>**started** - Network protection is running on the device</li><li>**restarting** - Network protection is restarting</li><li>**stopping** - Network protection is stopping</li><li>**stopped** - Network protection isn't running</li></ul>|
|org_id|Organization that the device is onboarded to. If the device isn't yet onboarded to any organization, this prints unavailable. For more information on onboarding, see [Onboard to Microsoft Defender for Endpoint](onboarding.md).|
|passive_mode_enabled|True if the antivirus component is set to run in passive mode, false otherwise.|
|product_expiration|Date and time when the current product version reaches end of support.|
|real_time_protection_available|True if the real-time protection component is healthy, false otherwise.|
|real_time_protection_enabled|True if real-time antivirus protection is enabled, false otherwise.|
|real_time_protection_subsystem|Subsystem used to serve real-time protection. If real-time protection isn't operating as expected, this prints unavailable.|
|release_ring|Release ring. For more information, see [Deployment rings](onboarding.md).|
|supplementary_events_subsystem|Subsystem that provides supplementary event data. Can be one of the following values: <ul><li>**ebpf** - Default from app version: 101.2408.0000</li><li>**auditd**</li></ul>|

## Component specific health

You can get more detailed health information for different Defender's features with `mdatp health --details <feature>`. For example:

```bash
mdatp health --details edr

mdatp health --details definitions

mdatp health --details help

```

You can run `mdatp health --help` on recent versions to list all supported features.

[!INCLUDE [Microsoft Defender for Endpoint Tech Community](../includes/defender-mde-techcommunity.md)]
