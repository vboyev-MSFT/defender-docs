---
title: Incidents and alerts in the Microsoft Defender portal - an overview
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

# Incidents and alerts in the Microsoft Defender portal: an overview

In the Microsoft Defender portal, ***alerts*** are signals from a collection of sources that result from various threat detection activities. These signals indicate the occurrence of malicious or suspicious events in your environment. While you can investigate and mitigate the threats that alerts bring to your attention, by themselves these threats are isolated occurrences that don't tell you anything about a broader, complex attack story. You could search for, research, investigate, and correlate groups of alerts that belong together in a single attack story, but that will cost you lots of time, effort, and energy. Instead, Microsoft's unified security operations platform in the Defender portal aggregates and correlates related alerts together to form ***incidents*** that represent these attack stories.

***Incidents*** tell the full story of an attack and provide the complete picture. The correlation engines and algorithms in the Microsoft Defender portal automatically correlate signals (alerts) from all Microsoft security and compliance solutions, as well as from vast numbers of external solutions through Microsoft Sentinel and Microsoft Defender for Cloud. Defender identifies multiple signals as belonging to the same attack story, using AI to continually monitor its telemetry sources and add more evidence to already open incidents. Incidents contain all the alerts deemed to be related to each other and to the overall attack story, and present the story in various forms: a timeline of alerts; lists of all the involved and impacted users, devices, and other resources; a visual representation of how all the players in the story interact, 

Incidents also function as "case files," providing you with a unified security operations platform for managing and documenting your investigations. For more information about incidents' functionality in this regard, see [Incident response in the Microsoft Defender portal](/defender-xdr/incidents-overview).

[!INCLUDE [unified-soc-preview](../includes/unified-soc-preview.md)]

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

Alerts in the Microsoft Defender portal come from many sources. These sources include the many services that are part of Microsoft Defender XDR, as well as other services with varying degrees of integration with the Microsoft Defender portal. Within each of these sources, there are one or more threat detection mechanisms that produce alerts based on the rules defined in each mechanism.

The following table shows the detection methods that produce alerts for each service in the Microsoft Defender portal:

| Service | Detection source |
| ------- | ---------------- |
| Microsoft Defender for Identity | <li>Microsoft Defender for Identity<li>Defender XDR |
| Microsoft Defender for Cloud Apps | <li>Microsoft Defender for Cloud Apps<li>Defender XDR |
| Microsoft Defender for Endpoint |  <li>Automated investigation<li>Microsoft Defender Experts<li>Custom detection<li>Defender XDR<li>Custom threat intelligence<li>Third party<li>SmartScreen<li>Antivirus<li>EDR |
| Microsoft Defender XDR | <li>Microsoft Defender Experts<li>Custom detection<li>Defender XDR<li>Manual |
| Microsoft Defender for Office 365 | <li>Microsoft Defender for Office 365 |
| App governance | <li>App governance policy<li>App governance detection |
| Microsoft Entra ID Protection | <li>Microsoft Entra ID Protection |
| Microsoft Data Loss Prevention | <li>Microsoft Data Loss Prevention |
| Microsoft Defender for Cloud | <li>Microsoft Defender for Cloud<li>Microsoft Defender for IoT<li>Microsoft Defender for Servers<li>Microsoft Defender for Storage<li>Microsoft Defender for DNS<li>Microsoft Defender for Databases<li>Microsoft Defender for Containers<li>Microsoft Defender for Network<li>Microsoft Defender for App Service<li>Microsoft Defender for Key Vault<li>Microsoft Defender for Resource Manager<li>Microsoft Defender for API Management |
| Microsoft Sentinel | <li>Microsoft Sentinel<li>NRT rules<li>Scheduled detection<li>Threat intelligence<li>ML detection |

- Solutions that are part of Microsoft Defender XDR
  - Microsoft Defender for Endpoint
  - Microsoft Defender for Office 365
  - Microsoft Defender for Identity
  - Microsoft Defender for Cloud Apps
  - The app governance add-on for Microsoft Defender for Cloud Apps
  - Microsoft Entra ID Protection
  - Microsoft Data Loss Prevention

- Other services that have integrations with the Microsoft Defender security portal
  - Microsoft Sentinel
  - Non-Microsoft security solutions that pass their alerts to Microsoft Sentinel
  - Microsoft Defender for Cloud

Microsoft Defender XDR itself also creates alerts. With Microsoft Sentinel onboarded to the [unified security operations platform](/defender-xdr/microsoft-sentinel-onboard), Microsoft Defender XDR's correlation engine now has access to all the raw data ingested by Microsoft Sentinel. (You can find this data in **Advanced hunting** tables.) Defender XDR's unique correlation capabilities provide another layer of data analysis and threat detection for all the non-Microsoft solutions in your digital estate. These detections produce Defender XDR alerts, in addition to the alerts already provided by Microsoft Sentinel's analytics rules.



================================================================================


An *incident* in the Microsoft Defender portal is a collection of related alerts and associated data that make up the story of an attack. It's also a case file that your SOC can use to investigate that attack and manage, implement, and document the response to it.

The Microsoft Sentinel and Microsoft Defender services create alerts when they detect a suspicious or malicious event or activity. Individual alerts provide valuable evidence of a completed or ongoing attack. However, increasingly prevalent and sophisticated attacks typically employ a variety of techniques and vectors against different types of asset entities, such as devices, users, and mailboxes. The result is multiple alerts, from multiple sources, for multiple asset entities in your digital estate.

Because individual alerts each tell only part of the story, and because manually grouping individual alerts together to gain insight into an attack can be challenging and time-consuming, the unified security operations platform automatically identifies alerts that are related&mdash;from both Microsoft Sentinel and Microsoft Defender XDR&mdash;and aggregates them and their associated information into an incident.

:::image type="content" source="/defender/media/incidents-overview/incidents.png" alt-text="How Microsoft Defender XDR correlates events from entities into an incident." lightbox="/defender/media/incidents-overview/incidents.png":::

Grouping related alerts into an incident gives you a comprehensive view of an attack. For example, you can see:

- Where the attack started.
- What tactics were used.
- How far the attack has gone into your digital estate.
- The scope of the attack, such as how many devices, users, and mailboxes were impacted.
- All of the data associated with the attack.

The unified security operations platform in the Microsoft Defender portal includes methods to automate and assist in the triage, investigation, and resolution of incidents.

- [Microsoft Copilot in Defender](/defender-xdr/security-copilot-in-microsoft-365-defender) harnesses AI to support analysts with complex and time-consuming daily workflows, including end-to-end incident investigation and response with clearly described attack stories, step-by-step actionable remediation guidance and incident activity summarized reports, natural language KQL hunting, and expert code analysis&mdash;optimizing on SOC efficiency across Microsoft Sentinel and Defender XDR data.

    This capability is in addition to the other AI-based functionality that Microsoft Sentinel brings to the unified platform, in the areas of user and entity behavior analytics, anomaly detection, multi-stage threat detection, and more.

- Automated attack disruption uses high-confidence signals collected from Microsoft Defender XDR and Microsoft Sentinel to automatically disrupt active attacks at machine speed, containing the threat and limiting the impact.

- If [enabled](/defender-xdr/m365d-enable), Microsoft Defender XDR can [automatically investigate and resolve](/defender-xdr/m365d-autoir) alerts from Microsoft 365 and Entra ID sources through automation and artificial intelligence. You can also perform additional remediation steps to resolve the attack.

- Microsoft Sentinel [automation rules](/azure/sentinel/automate-incident-handling-with-automation-rules) can automate triage, assignment, and management of incidents, regardless of their source. They can apply tags to incidents based on their content, suppress noisy (false positive) incidents, and close resolved incidents that meet the appropriate criteria, specifying a reason and adding comments.

<a name='incidents-and-alerts-in-the-microsoft-365-defender-portal'></a>

[!INCLUDE [unified-soc-preview](../includes/unified-soc-preview.md)]

## Incidents and alerts in the Microsoft Defender portal

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
> If you see an *Unsupported alert type* alert status, it means that automated investigation capabilities cannot pick up that alert to run an automated investigation. However, you can [investigate these alerts manually](/defender-xdr/investigate-incidents.md#alerts).

<a name='example-incident-response-workflow-for-microsoft-365-defender'></a>

## Incident response workflow example in the Microsoft Defender portal

Here's a workflow example for responding to incidents in Microsoft 365 with the Microsoft Defender portal.

:::image type="content" source="/defender/media/incidents-overview/incidents-example-workflow.png" alt-text="An example of an incident response workflow for the Microsoft Defender portal." lightbox="/defender/media/incidents-overview/incidents-example-workflow.png":::

On an ongoing basis, identify the highest priority incidents for analysis and resolution in the incident queue and get them ready for response. This is a combination of:

- [Triaging](/defender-xdr/incident-queue) to determining the highest priority incidents through filtering and sorting of the incident queue.
- [Managing](/defender-xdr/manage-incidents) incidents by modifying their title, assigning them to an analyst, and adding tags and comments.

You can use Microsoft Sentinel automation rules to automatically triage and manage (and even respond to) some incidents as they're created, removing the easiest-to-handle incidents from taking up space in your queue.

Consider these steps for your own incident response workflow:

| Stage | Steps |
| ----- | ----- |
| For each incident, begin an [attack and alert investigation and analysis](/defender-xdr/investigate-incidents). | <ol><li> View the attack story of the incident to understand its scope, severity, detection source, and which asset entities are affected.<li>Begin analyzing the alerts to understand their origin, scope, and severity with the alert story within the incident.<li>As needed, gather information on impacted devices, users, and mailboxes with the graph. Select any entity to open a flyout with all the details. Follow through to the entity page for more insights.<li>See how Microsoft Defender XDR has [automatically resolved some alerts](/defender-xdr/m365d-autoir) with the **Investigations** tab.<li>As needed, use information in the data set for the incident for more information with the **Evidence and Response** tab. |
| After or during your analysis, perform containment to reduce any additional impact of the attack and eradication of the security threat. | For example,<li>Disable compromised users<li>Isolate impacted devices<li>Block hostile IP addresses. |
| As much as possible, recover from the attack by restoring your tenant resources to the state they were in before the incident.||
| [Resolve](/defender-xdr/manage-incidents.md#resolve-an-incident) the incident and document your findings. | Take time for post-incident learning to: <li>Understand the type of the attack and its impact.<li>Research the attack in [Threat Analytics](/defender-xdr/threat-analytics) and the security community for a security attack trend.<li>Recall the workflow you used to resolve the incident and update your standard workflows, processes, policies, and playbooks as needed.<li>Determine whether changes in your security configuration are needed and implement them. |

If you're new to security analysis, see the [introduction to responding to your first incident](/defender-xdr/incidents-overview) for additional information and to step through an example incident.

For more information about incident response across Microsoft products, see [this article](/security/operations/incident-response-overview).

<a name='example-security-operations-for-microsoft-365-defender'></a>

## Integrating security operations in the Microsoft Defender portal

Here's an example of integrating security operations (SecOps) processes in the Microsoft Defender portal.

:::image type="content" source="/defender/media/incidents-overview/incidents-example-operations.png" alt-text="An example of security operations for Microsoft Defender XDR" lightbox="/defender/media/incidents-overview/incidents-example-operations.png":::

Daily tasks can include:

- [Managing](/defender-xdr/manage-incidents) incidents
- Reviewing [automated investigation and response (AIR)](/defender-xdr/m365d-action-center) actions in the Action center
- Reviewing the latest [Threat Analytics](/defender-xdr/threat-analytics)
- [Responding](/defender-xdr/investigate-incidents) to incidents

Monthly tasks can include:

- Reviewing [AIR settings](/defender-xdr/m365d-configure-auto-investigation-response)
- Reviewing [Secure Score](/defender-xdr/microsoft-secure-score-improvement-actions) and [Microsoft Defender Vulnerability Management](/defender-vulnerability-management/defender-vulnerability-management)
- Reporting to your IT security management chain

Quarterly tasks can include a report and briefing of security results to the Chief Information Security Officer (CISO).

Annual tasks can include conducting a major incident or breach exercise to test your staff, systems, and processes.

Daily, monthly, quarterly, and annual tasks can be used to update or refine processes, policies, and security configurations.

See [Integrating Microsoft Defender XDR into your security operations](/defender-xdr/integrate-microsoft-365-defender-secops) for more details.

### SecOps resources across Microsoft products

For more information about SecOps across Microsoft's products, see these resources:

- [Capabilities](/security/compass/security-operations-capabilities)
- [Best practices](/azure/cloud-adoption-framework/secure/security-operations)
- [Videos and slides](/security/operations/security-operations-videos-and-decks)

## Incident notifications by email

You can set up the Microsoft Defender portal to notify your staff with an email about new incidents or updates to existing incidents. You can choose to get notifications based on:

- Alert severity
- Alert sources
- Device group

To set up email notifications for incidents, see [get email notifications on incidents](/defender-xdr/m365d-notifications-incidents).

## Training for security analysts

Use this learning module from Microsoft Learn to understand how to use Microsoft Defender XDR to manage incidents and alerts.

|Training:|Investigate incidents with Microsoft Defender XDR|
|---|---|
|![Investigate incidents with Microsoft Defender XDR training icon.](/defender/media/incidents-overview/m365-defender-address-security-investigation.svg)| Microsoft Defender XDR unifies threat data from multiple services and uses AI to combine them into incidents and alerts. Learn how to minimize the time between an incident and its management for subsequent response and resolution. <p> 27 min - 6 Units |

> [!div class="nextstepaction"]
> [Start >](/training/modules/defender-investigate-incidents/)

## Next steps

Use the listed steps based on your experience level or role on your security team.

### Experience level

Follow this table for your level of experience with security analysis and incident response.

| Level | Steps |
|:-------|:-----|
| **New** | <ol><li> See the [Respond to your first incident walkthrough](/defender-xdr/respond-first-incident-365-defender) to get a guided tour of a typical process of analysis, remediation, and post-incident review in the Microsoft Defender portal with an example attack. </li><li> See which incidents should be [prioritized](/defender-xdr/incident-queue) based on severity and other factors. </li><li> [Manage incidents](/defender-xdr/manage-incidents), which includes renaming, assigning, classifying, and adding tags and comments based on your incident management workflow.</li></ol> |
| **Experienced** | <ol><li> Get started with the incident queue from the **Incidents** page of the Microsoft Defender portal. From here you can: </li> <ul><li> See which incidents should be [prioritized](/defender-xdr/incident-queue) based on severity and other factors. </li><li> [Manage incidents](/defender-xdr/manage-incidents), which includes renaming, assigning, classifying, and adding tags and comments based on your incident management workflow. </li><li> Perform [investigations](/defender-xdr/investigate-incidents) of incidents. </li></ul> </li><li> Track and respond to emerging threats with [threat analytics](/defender-xdr/threat-analytics). </li><li>  Proactively hunt for threats with [advanced threat hunting](/defender-xdr/advanced-hunting-overview). </li><li> See these [incident response playbooks](/security/operations/incident-response-playbooks) for detailed guidance for phishing, password spray, and app consent grant attacks. </li></ol> |

### Security team role

Follow this table based on your security team role.

| Role | Steps |
|---|---|
| Incident responder (Tier 1) | Get started with the incident queue from the **Incidents** page of the Microsoft Defender portal. From here you can: <ul><li> See which incidents should be [prioritized](/defender-xdr/incident-queue) based on severity and other factors. </li><li> [Manage incidents](/defender-xdr/manage-incidents), which includes renaming, assigning, classifying, and adding tags and comments based on your incident management workflow. </li></ul> |
| Security investigator or analyst (Tier 2) | <ol><li> Perform [investigations](/defender-xdr/investigate-incidents) of incidents from the **Incidents** page of the Microsoft Defender portal. </li><li> See these [incident response playbooks](/security/operations/incident-response-playbooks) for detailed guidance for phishing, password spray, and app consent grant attacks. </li></ol> |
| Advanced security analyst or threat hunter (Tier 3) | <ol><li>Perform [investigations](/defender-xdr/investigate-incidents) of incidents from the **Incidents** page of the Microsoft Defender portal. </li><li> Track and respond to emerging threats with [threat analytics](/defender-xdr/threat-analytics). </li><li> Proactively hunt for threats with [advanced threat hunting](/defender-xdr/advanced-hunting-overview). </li><li> See these [incident response playbooks](/security/operations/incident-response-playbooks) for detailed guidance for phishing, password spray, and app consent grant attacks. |
| SOC manager | See how to [integrate Microsoft Defender XDR into your Security Operations Center (SOC)](/defender-xdr/integrate-microsoft-365-defender-secops). |

[!INCLUDE [Microsoft Defender XDR rebranding](../includes/defender-m3d-techcommunity.md)]
