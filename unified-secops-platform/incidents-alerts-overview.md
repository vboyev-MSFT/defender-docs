---
title: Overview of incidents and alerts in the Microsoft Defender portal
description: An introduction to incidents and alerts, and the differences between them, in the unified security operations platform in the Microsoft Defender portal.
ms.service: defender-xdr
f1.keywords:
  - NOCSH
ms.author: yelevin
author: yelevin
ms.localizationpriority: medium
manager: raynew
audience: ITPro
ms.collection:
  - m365-security
  - tier1
  - usx-security
  - sentinel-only
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
  - MOE150
  - MET150
ms.date: 06/05/2024
appliesto: 
- Microsoft Defender XDR
- Microsoft Sentinel in the Microsoft Defender portal
---

# Overview of incidents and alerts in the Microsoft Defender portal

The Microsoft Defender portal brings together a unified set of security services to reduce your exposure to security threats, improve your organizational security posture, detect security threats, and investigate and respond to breaches. These services collect and produce signals that are displayed in the portal. This article discusses two main kinds of signals&mdash;**alerts** and **incidents**, what they represent, and what you can do with them.

## What are alerts and incidents?

***Alerts*** are signals that result from various threat detection activities. These signals indicate the occurrence of malicious or suspicious events in your environment.

***Incidents*** are "case files" that contain collections of related alerts and tell the full story of an attack. The alerts come from all Microsoft security and compliance solutions, as well as from vast numbers of external solutions collected through Microsoft Sentinel and Microsoft Defender for Cloud.

## Why do we need incidents?

While you can investigate and mitigate the threats that individual alerts bring to your attention, by themselves these threats are isolated occurrences that don't tell you anything about a broader, complex attack story. You could search for, research, investigate, and correlate groups of alerts that belong together in a single attack story, but that will cost you lots of time, effort, and energy.

Instead, the correlation engines and algorithms in the Microsoft Defender portal automatically aggregate and correlate related alerts together to form ***incidents*** that represent these larger attack stories. Defender identifies multiple signals as belonging to the same attack story, using AI to continually monitor its telemetry sources and add more evidence to already open incidents. Incidents contain all the alerts deemed to be related to each other and to the overall attack story, and present the story in various forms:

- A timeline of alerts
- Lists of all the involved and impacted users, devices, and other resources
- A visual representation of how all the players in the story interact
- Logs of automatic investigation and response processes that Defender XDR initiated and completed
- Collections of evidence supporting the attack story: bad actors' user accounts and device information and address, malicious files and processes, relevant threat intelligence, and so on
- A textual summary of the attack story

Incidents also provide you with a framework for managing and documenting your investigations and threat response. For more information about incidents' functionality in this regard, see [Manage incidents in Microsoft Defender](manage-incidents.md).

<!-- INCLUDE THIS?
[!INCLUDE [unified-soc-preview](../includes/unified-soc-preview.md)]
-->

Here is a summary of the main attributes of incidents and alerts, and the differences between them:

**Incidents:**

- Are the main "unit of measure" of the work of the Security Operations Center (SOC).
- Display the broader context of an attack&mdash;the **attack story**.
- Represent "case files" containing all the information needed to investigate the threat and the findings of the investigation.
- Are created by Microsoft Defender XDR to contain at least one alert, and in many cases, to contain many alerts.
- Trigger automatic series of responses to the threat, using [automation rules](/azure/sentinel/automate-incident-handling-with-automation-rules?tabs=onboarded), [attack disruption](/defender-xdr/automatic-attack-disruption), and [playbooks](/azure/sentinel/automation/automate-responses-with-playbooks).
- Record all activity related to the threat and its investigation and resolution.

**Alerts:**

- Represent the individual pieces of the story that are essential to understanding and investigating the incident.
- Are created by many different sources both internal and external to the Defender portal.
- Can be analyzed by themselves to add value when deeper analysis is required.
- Can trigger [automatic investigations and responses](/defender-xdr/m365d-autoir) at the alert level, to minimize the potential threat impact.

## Alert sources and threat detection

Alerts in the Microsoft Defender portal come from many sources. These sources include the many services that are part of Microsoft Defender XDR, as well as other services with varying degrees of integration with the Microsoft Defender portal. 

- Solutions that are part of Microsoft Defender XDR
  - Microsoft Defender for Endpoint
  - Microsoft Defender for Office 365
  - Microsoft Defender for Identity
  - Microsoft Defender for Cloud Apps
  - The app governance add-on for Microsoft Defender for Cloud Apps
  - Microsoft Entra ID Protection
  - Microsoft Data Loss Prevention

- Other services that have integrations with the Microsoft Defender security portal
  - Microsoft Defender for Cloud
  - Microsoft Sentinel
  - Non-Microsoft security solutions that pass their alerts to Microsoft Sentinel  
    When Microsoft Sentinel is onboarded to the [unified security operations platform](/defender-xdr/microsoft-sentinel-onboard), the correlation engine in the Microsoft Defender portal has access to all the raw data ingested by Microsoft Sentinel. (You can find this data in **Advanced hunting** tables.) 

- Microsoft Defender XDR itself also creates alerts. Defender XDR's unique correlation capabilities provide another layer of data analysis and threat detection for all the non-Microsoft solutions in your digital estate. These detections produce Defender XDR alerts, in addition to the alerts already provided by Microsoft Sentinel's analytics rules.

Within each of these sources, there are one or more threat detection mechanisms that produce alerts based on the rules defined in each mechanism.

The following table shows the detection methods that produce alerts for each service in the Microsoft Defender portal:

| Service | Detection source |
| ------- | ---------------- |
| Microsoft Defender for Identity | <li>Microsoft Defender for Identity<li>Defender XDR |
| Microsoft Defender for Cloud Apps | <li>Microsoft Defender for Cloud Apps<li>Defender XDR |
| Microsoft Defender for Endpoint | <li>Automated investigation<li>Microsoft Defender Experts<li>Custom detection<li>Defender XDR<li>Custom threat intelligence<li>Third party<li>SmartScreen<li>Antivirus<li>EDR |
| Microsoft Defender XDR | <li>Microsoft Defender Experts<li>Custom detection<li>Defender XDR<li>Manual |
| Microsoft Defender for Office 365 | <li>Microsoft Defender for Office 365 |
| App governance | <li>App governance policy<li>App governance detection |
| Microsoft Entra ID Protection | <li>Microsoft Entra ID Protection |
| Microsoft Data Loss Prevention | <li>Microsoft Data Loss Prevention |
| Microsoft Defender for Cloud | <li>Microsoft Defender for Cloud<li>Microsoft Defender for IoT<li>Microsoft Defender for Servers<li>Microsoft Defender for Storage<li>Microsoft Defender for DNS<li>Microsoft Defender for Databases<li>Microsoft Defender for Containers<li>Microsoft Defender for Network<li>Microsoft Defender for App Service<li>Microsoft Defender for Key Vault<li>Microsoft Defender for Resource Manager<li>Microsoft Defender for API Management |
| Microsoft Sentinel | <li>Microsoft Sentinel<li>NRT rules<li>Scheduled detection<li>Threat intelligence<li>ML detection |

Grouping related alerts into an incident gives you a comprehensive view of an attack. For example, you can see:

- Where the attack started.
- What tactics were used.
- How far the attack has gone into your digital estate.
- The scope of the attack, such as how many devices, users, and mailboxes were impacted.
- All of the data associated with the attack.

The Microsoft Defender portal includes methods to automate and assist in the triage, investigation, and resolution of incidents.

- [Microsoft Copilot in Defender](/defender-xdr/security-copilot-in-microsoft-365-defender) harnesses AI to support analysts with complex and time-consuming daily workflows, including end-to-end incident investigation and response with clearly described attack stories, step-by-step actionable remediation guidance and incident activity summarized reports, natural language KQL hunting, and expert code analysis&mdash;optimizing on SOC efficiency across data from all sources.  
***CHANGE TO "SECURITY COPILOT"? "SECURITY COPILOT IN DEFENDER"?***

    This capability is in addition to the other AI-based functionality that Microsoft Sentinel brings to the unified platform, in the areas of user and entity behavior analytics, anomaly detection, multi-stage threat detection, and more.

- Automated attack disruption uses high-confidence signals collected from Microsoft Defender XDR and Microsoft Sentinel to automatically disrupt active attacks at machine speed, containing the threat and limiting the impact.

- If [enabled](/defender-xdr/m365d-enable) to do so, Microsoft Defender XDR can [automatically investigate and resolve](/defender-xdr/m365d-autoir) alerts from Microsoft 365 and Entra ID sources through automation and artificial intelligence. You can also perform additional remediation steps to resolve the attack.

- Microsoft Sentinel [automation rules](/azure/sentinel/automate-incident-handling-with-automation-rules) can automate triage, assignment, and management of incidents, regardless of their source. They can apply tags to incidents based on their content, suppress noisy (false positive) incidents, and close resolved incidents that meet the appropriate criteria, specifying a reason and adding comments.

<a name='incidents-and-alerts-in-the-microsoft-365-defender-portal'></a>

## Manage incidents and alerts in the Defender portal

You manage incidents from **Investigation & response > Incidents & alerts > Incidents** on the quick launch of the [Microsoft Defender portal](https://security.microsoft.com). Here's an example:

:::image type="content" source="/defender/media/incidents-overview/incidents-ss-incidents.png" alt-text="The Incidents page in the Microsoft Defender portal." lightbox="/defender/media/incidents-overview/incidents-ss-incidents.png":::

Selecting an incident name displays the incident page, starting with the entire **attack story** of the incident, including:

- **Alert page within incident**: The scope of alerts related to the incident and their information on the same tab.

- **Graph**: A visual representation of the attack that connects the different suspicious entities that are part of the attack with the asset entities that make up the attack's targets, such as users, devices, apps, and mailboxes.

You can view the asset and other entity details directly from the graph and act on them with response options such as like disabling an account, deleting a file, or isolating a device.

:::image type="content" source="/defender/media/incidents-overview/incident-summary.png" alt-text="Screenshot that shows the attack story page for an incident in the Microsoft Defender portal." lightbox="/defender/media/incidents-overview/incident-summary.png":::

The incident page consists of the following tabs:

- **Attack story**

  Mentioned above, this tab includes the timeline of the attack, including all the alerts, asset entities, and remediation actions taken.

- **Alerts**

  All the alerts related to the incident, their sources, and information.

- **Assets**

  All the assets (protected entities such as devices, users, mailboxes, apps, and cloud resources) that have been identified to be part of or related to the incident.

- **Investigations**

  All the [automated investigations](/defender-xdr/m365d-autoir) triggered by alerts in the incident, including the status of the investigations and their results.

- **Evidence and Response**

  All the suspicious entities in the alerts of the incident, which constitute evidence supporting the attack story. These entities can include IP addresses, files, processes, URLs, registry keys and values, and more.

- **Summary**

  A quick overview of the impacted assets associated with alerts.

> [!NOTE]
> If you see an *Unsupported alert type* alert status, it means that automated investigation capabilities cannot pick up that alert to run an automated investigation. However, you can [investigate these alerts manually](/defender-xdr/investigate-incidents#alerts).

## Related items

To learn more about alert correlation and incident merging in the Defender portal, see [Alerts, incidents, and correlation in Microsoft Defender XDR](/defender-xdr/alerts-incidents-correlation)
