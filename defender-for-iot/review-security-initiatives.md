---
title: Review security initiatives with Microsoft Defender for IoT in the Defender portal
description: This article describes how to review security initiatives with Microsoft Defender for IoT in the Defender portal.
ms.service: defender-for-iot
author: limwainstein
ms.author: lwainstein
ms.localizationpriority: medium
ms.date: 11/17/2024
ms.topic: how-to
---

# Review security initiatives

[Security initiatives](/security-exposure-management/exposure-insights-overview#security-initiatives) offer a focused, metric-driven way of tracking exposure in specific security areas using security initiatives.

Microsoft Defender for IoT in the Defender portal allows you to review security initiatives dedicated to OT and enterprise IoT device security.

In this article, you learn how to review security initiatives so that your security teams can prioritize, discover, and validate OT-related security findings across your sites.

Specifically, your security teams can use the **OT Security** and **Enterprise IoT Security** initiatives to:

- Identify unprotected devices.
- Harden posture across sites through vulnerability assessments, with actionable guidance to help remediate at-risk devices.

[!INCLUDE [defender-iot-preview](../includes//defender-for-iot-defender-public-preview.md)]

## Prerequisites

If you haven't yet onboarded Defender for IoT, in the security initiative, follow the steps under the **More data is required to support this initiative** section. For more information, see:

    - [Onboard Defender for IoT in the Defender portal](get-started.md)
    - [Set up sites](set-up-sites.md)

## Review initiatives

1. Follow the procedure to [open the Initiatives page and review an initiative](/security-exposure-management/initiatives#view-initiatives-page). In step 6, search for and select the initiative you want to review.
1. Review the data in the initiative page, including the initiative score, top metrics, and more (learn more about [initiatives](/security-exposure-management/exposure-insights-overview)). For example, this **OT Security** initiative page shows an initiative score of 87%, and shows that 30.87% of the detected OT devices are unprotected.

    :::image type="content" source="media/review-security-recommendations/ot-security-initiative.png" alt-text="Screenshot showing the OT Security initiative in Microsoft Defender for IoT in the Microsoft Defender portal.":::

1. Select the metric from the **Top metrics** area in the initiative page or from the **Related metrics** area in the small overview. 
    - Review the **General** tab to drill down into additional security data and recommendations. For example, the **Unprotected OT devices** metric  shows 66 affected items, and 3.77 score impact.

        :::image type="content" source="media/review-security-recommendations/unprotected-ot-devices.png" alt-text="Screenshot showing the Unprotected OT devices metric **General** tab in Microsoft Defender for IoT in the Microsoft Defender portal.":::

    - Review the recommendations in the **Security recommendations** tab. For example, for the **Site-linked devices using insecure protocols** metric, you're recommended to disable the Telnet administration protocol, and remove the SNMP V1 and SNMP V2 administration protocols.
    
        :::image type="content" source="media/review-security-recommendations/security-recommendations.png" alt-text="Screenshot showing the **Security recommendations** tab for a metric in Microsoft Defender for IoT in the Microsoft Defender portal.":::

    Learn more about [working with metrics](/security-exposure-management/exposure-insights-overview#working-with-metrics).

## Next steps

[Learn about vulnerabilities](discover-vulnerabilities-overview.md) or proceed to [investigate and remediate vulnerabilities](prioritize-vulnerabilities.md).