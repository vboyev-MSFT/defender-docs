---
title: How to subscribe to Microsoft Defender Experts for Hunting
ms.reviewer:
description: If you're new to Microsoft Defender XDR and Defender Experts for Hunting, this is how you onboard, receive, and set up Defender experts notifications.
ms.service: defender-experts-for-hunting
ms.author: vpattnaik
author: vpattnai
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
  - m365-security
  - tier1
  - essentials-get-started
ms.topic: conceptual
ms.custom: 
- cx-ti
- cx-ean
search.appverid: met150
ms.date: 01/06/2025
---

# General information on Defender Experts for Hunting service

**Applies to:**

- [Microsoft Defender XDR](microsoft-365-defender.md)

The following section lists down questions your SOC team might have regarding the Microsoft Defender Experts for Hunting service:

| Questions | Answers |
|---------|---------|
| **What is Microsoft Defender Experts for Hunting service?** | Microsoft Defender Experts for Hunting provides proactive threat hunting service to proactively find threats. Please note that Defender Experts for XDR also includes the proactive threat hunting offered by Defender Experts for Hunting.|
|**Does Defender Experts for Hunting either use or need Sentinel or a SIEM?**|No. Defender Experts does not use any third-party data ingested via either Microsoft Sentinel or any other SIEM.|
|**What products does Defender Experts for Hunting operate on?**|This service relies on event signals from Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Microsoft Defender for Cloud Apps, and Microsoft Defender for Identity, along with proprietary Microsoft Threat Intelligence sources. Any event definitions that is not written by Microsoft Defender products that is, third-party authored event or detection, is not within the scope of Defender Experts for Hunting.|
|**Does Defender Experts for Hunting replace my threat hunting team?**|Defender Experts for Hunting does not replace your internal hunting team but instead augments their capabilities. The Defender Experts for Hunting focuses on novel emerging threat landscape, where there might be knowledge gaps in the industry in the best ways to identify them.|
|**What is the role of Defender Experts for Hunting in the context of a Purple Team exercise?**|Defender Experts for Hunting is part of the blue team in a purple team exercise (Red Team and Blue Team coordinated work stream). Defender Experts for Hunting complements your internal hunting team by enhancing their capabilities rather than replacing them.|
|**What actions can your experts take during a hunting investigation that results in a Defender Experts Hunting Notification?**|During threat hunting investigations, our analysts refrain from taking direct actions on customer assets. Instead, they provide detailed information, including threat summary, hunting queries that show the timeline of events for the identified attack and remediation action recommendations. Defender Experts Notifications will provide guidance on how to review and address the novel threat.|
|**What types of incidents can your experts investigate?**|The Defender Experts for Hunting focuses on novel emerging threat landscape, where there might be knowledge gaps in the industry in the best ways to identify them. This service does not prioritize well-established threats that are adequately addressed by Defender Products . However, when a well-known tactic is employed to generate a novel attack, Defender Experts will diligently identify both the novel and existing attack tactics. Please see review our Defender Experts Blogs on Novel attacks.|
|**Can your experts help me improve my security posture?**|The scope of the posture change recommendation is limited to the scope of the Defender Experts Notification scope and is limited to preventing the attack identified in the context of the notification.|
|**Can Defender Experts for Hunting help with an active compromise or vulnerability?**|No, Defender Experts currently don't provide incident response services.Contact your Microsoft representative or fill out the Experiencing a Cybersecurity Incident? form to engage Microsoft Incident Response for incident response assistance.|
|**How can my organization participate in the Defender Experts for Hunting service?**|Contact your Microsoft representative to express interest in Defender Experts for Hunting|
|**Does Defender Experts for Hunting Cover Cloud Servers that have Defender for Endpoint deployed on them.**|Defender Experts for Hunting also covers servers—whether on premises or on a hyperscale cloud service provider—that have Defender for Endpoint deployed on them with a Microsoft Defender for Endpoint for Servers license. For Defender Experts coverage, a server is considered as a user seat for billing. The service doesn't cover Microsoft Defender for Cloud. Learn more about specific hardware and software requirements|
|**Once I see a Defender Experts Notification, if I have questions, how do I communicate with the Defender Experts for Hunting Team?**|We provide an “Ask Defender Experts” inside the Microsoft 365 security portal to get swift and accurate responses to all your threat hunting question. Please note that the scope of questions is limited to Defender Experts for Hunting questions only.|
|**What kinds of inquiries could I submit in the Ask Defender Experts capability?**|Ask Defender Experts is intended to provide a better understanding of complex threats affecting your organization – focused on products included in Microsoft Defender XDR i.e. Defender for Endpoint, Defender for Office, Defender for Cloud Apps, and Defender for Identify. Please note that inquiries related to custom detections in the above products (i.e., non-Defender XDR and third-party cybersecurity products), bugs in your product experience in the Defender XDR portal, and those related to security incident response services cannot be handled by Ask Defender Experts. See sample and more details in this article – Collaborate with experts on demand.|
|**What Certifications do the Defender Experts Services have?**|Defender Experts for Hunting is certified for HIPAA and ISO.|
|**How is customer data protected?**|Please review the section on data retention and protection.|
|**Does the Hunting Service offer Real time Threat remediation with boots on ground?**|No, the hunting service does not cover this type of service. Despite this, Microsoft provides professional on-site service through our Microsoft Incident Response Team. This service requires a separate contract. We prioritize our customers’ needs and have a swift turnaround time. Please contact your Customer Service Account Manager or CSAM for further assistance.|
|**Is there a graph API to fetch the Defender Experts Notifications content?**|Yes. Please review this section in the documentation.|