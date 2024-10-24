---
title: Using submissions, suppressions, and exclusions with Microsoft Defender for Endpoint
description: Learn about suppressing alerts, submitting files for analysis, and defining exclusions and indicators for Defender for Endpoint.
ms.service: defender-endpoint
ms.subservice: ngp
ms.localizationpriority: medium
ms.topic: how-to
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/21/2024
ms.reviewer: joshbregman
manager: deniseb
ms.collection: 
- m365-security
- tier2
- mde-ngp
search.appverid: met150
---

# Alternatives to creating exclusions and allow indicators

[!INCLUDE [Microsoft Defender XDR rebranding](../includes/microsoft-defender.md)]

**Applies to:**

- Microsoft Defender Antivirus
- [Microsoft Defender for Endpoint Plan 1](microsoft-defender-endpoint.md)
- [Microsoft Defender for Endpoint Plan 2](microsoft-defender-endpoint.md)


Creating an exclusion or allow indicator create a protection gap.  These techniques should only be used after determining the root cause of the issue.  Until that determination is made, consider these alternatives.

For more information, see [Exclusions overview]  (navigate-defender-endpoint-antivirus-exclusions.md).


## Submitting files for analysis

If you have a file that you think is wrongly detected as malware (a false positive), or a file that you suspect might be malware even though it wasn't detected (a false negative), you can submit the file to Microsoft for analysis. Your submission is scanned immediately, and will then be reviewed by Microsoft security analysts. You're able to check the status of your submission on the [submission history page](https://www.microsoft.com/wdsi/submissionhistory).

Submitting files for analysis helps reduce false positives and false negatives for all customers. To learn more, see the following articles:

- [Submit files for analysis](/microsoft-365/security/intelligence/submission-guide) (available to all customers)
- [Submit files using the new unified submissions portal in Defender for Endpoint](admin-submissions-mde.md) (available to customers who have Defender for Endpoint Plan 2 or Microsoft Defender XDR)

## Suppressing alerts

If you're getting alerts in the Microsoft Defender portal for tools or processes that you know aren't actually a threat, you can suppress those alerts. To suppress an alert, you create a suppression rule, and specify what actions to take for that on other, identical alerts. You can create suppression rules for a specific alert on a single device, or for all alerts that have the same title across your organization.

To learn more, see the following articles:

- [Suppress alerts](manage-alerts.md#suppress-alerts)
- [Introducing the new alert suppression experience](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/introducing-the-new-alert-suppression-experience/ba-p/3562719) (for Defender for Endpoint)




[!INCLUDE [Microsoft Defender for Endpoint Tech Community](../includes/defender-mde-techcommunity.md)]
