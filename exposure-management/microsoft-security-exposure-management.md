---
title: What is Microsoft Security Exposure Management?
description: Learn how Microsoft Security Exposure Management enhances and extends security posture management.
author: dlanger
ms.author: dlanger
manager: rayne-wiselman
ms.topic: overview
ms.service: exposure-management
ms.date: 08/20/2024
---


# What is Microsoft Security Exposure Management?

Microsoft Security Exposure Management is a security solution that provides a unified view of security posture across company assets and workloads. Security Exposure Management enriches asset information with security context that helps you to proactively manage attack surfaces, protect critical assets, and explore and mitigate exposure risk.

Security Exposure Management is currently in public preview.

[!INCLUDE [prerelease](../includes//prerelease.md)]

## Who uses Security Exposure Management?

Security Exposure Management is aimed at:

- Security and compliance admins responsible for maintaining and improving organizational security posture.
- Security operations (SecOps) and partner teams who need visibility into data and workloads across organizational silos to effectively detect, investigate, and mitigate security threats.
- Security architects responsible for solving systematic issues in overall security posture.
- Chief Security Information Officers (CISOs) and security decision makers who need insights into organizational attack surfaces and exposure in order to understand security risk within organizational risk frameworks.

## What can I do with Security Exposure Management?

With Security Exposure Management you can:

- **Get a unified view across the organization**: Security Exposure Management continuously discovers assets and workloads, and gathers discovered data into a unified and up-to-date view of your inventory and attack surface.
- **Manage and investigate attack surfaces**: Visualize, analyze, and manage cross-workload attack surfaces.
  - The enterprise exposure graph gathers information to provide a comprehensive view of security posture and exposure across the business.
  - Graph schemas provide contextual information about specific organizational entities such as devices, identities, machines, and storage.
  - Query the enterprise exposure graph to explore assets, assess risk, and hunt for threats across on-premises, hybrid, and multicloud environments.
  - Visualize your environment and graph queries with the attack surface map.

- **Discover and safeguard critical assets**: Security Exposure Management marks predefined assets and assets you customize, as critical. This enables you to focus and prioritize on those critical assets to ensure security and business continuity.

- **Manage exposure**: Security Exposure Management provides tools to manage security exposure, and mitigate exposure risk.
  - Exposure insights aggregate security posture data, and provide rich context around the security posture state of your asset inventory.
  - You leverage these insights to prioritize security efforts and investments.
  - Insights include security events, recommendations, metrics, and security initiatives.
  - As you manage exposure risk, attack paths show you how an attacker might breach your attack surface.
    - Security Exposure Management generates attack paths based on data collected across assets and workloads. It simulates attack scenarios, and identifies weaknesses that an attacker could exploit.
    - You can use the enterprise exposure graph and attack surface map to visualize and understand potential threats.
    - You can also focus on choke points through which many attack paths flow.
    - Actionable recommendations help you to mitigate identified attack paths.

## What's integrated into Security Exposure Management?

Currently, Security Exposure Management consolidates security posture information and insights from workloads that include:

- Microsoft Defender for Endpoint
- Microsoft Defender for Identity
- Microsoft Defender for Cloud Apps
- Microsoft Defender for Office
- Microsoft Defender for IoT
- Microsoft Secure Score  
- Microsoft Defender Vulnerability Management  
- Microsoft Defender for Cloud
- Microsoft Entra ID  
- Microsoft Defender External Attack Surface Management (EASM)

In addition to Microsoft services, Security Exposure Management will connect to non-Microsoft data sources over time.

## How to get Microsoft Security Exposure Management

Exposure Management is available in the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com/)

Access to the exposure management blade and features in the Microsoft Defender portal is available with any of the following licenses:

- Microsoft 365 E5 or A5
- Microsoft 365 E3
- Microsoft 365 E3 with the Microsoft Enterprise Mobility + Security E5 add-on
- Microsoft 365 A3 with the Microsoft 365 A5 security add-on
- Microsoft Enterprise Mobility + Security E5 or A5
- Microsoft Defender for Endpoint (Plan 1 and 2)
- Microsoft Defender for Identity
- Microsoft Defender for Cloud Apps
- Microsoft Defender for Office 365 (Plans 1 and 2)
- Microsoft Defender Vulnerability Management  

Integration of data from the above tools, as well as other Microsoft security tools like Microsoft Defender for Cloud, Microsoft Defender Cloud Security Posture Management, and Microsoft Defender External Attack Surface Management, is available with these licenses.

## Next steps

Review [prerequisites](prerequisites.md) to get started with Security Exposure Management.