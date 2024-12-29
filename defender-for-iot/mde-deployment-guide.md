---
title: MDE agent deployment guide for OT discovery - Microsoft Defender for IoT
description: Learn how to deploy an MDE agent on your OT network sensors.
ms.date: 12/19/2024
ms.topic: how-to
author: limwainstein
ms.author: lwainstein
---
<!-- This isnt really a how-to but a concept - is that correct? Limor-->
# MDE Agent Deployment Guide for OT Discovery

## Placement of an MDE agent to receive maximum network value

This guide provides step-by-step instructions for deploying a Microsoft Defender for Endpoint (MDE) agent in the correct network location to ensure that it receives the relevant traffic. Proper placement enhances data quality and optimal performance within the network.

## MDE Discovery for OT Capabilities

MDE agents offer various discovery and security capabilities, such as passive monitoring or standard probing. The MDE agent should be placed according to the capability type that your network needs. The capabilities include:

- [Passive monitoring](#passive-monitoring)

- [Standard probing](#standard-probing)

## General Recommendations

General recommendations to set up the MDE agent as an OT discovery data source are:

- Minimum Requirement: an MDE agent running in the subnet, if Standard mode is enabled<!-- Is this last part needed? is there something else if the mode is off? -->.

- Scanners per VLAN: at least five scanners per VLAN.

- Onboarding Devices: onboard any devices with the "Can Be Onboarded" status in order to increase visibility.

## Usage Ability

- Server 2019 and computers with Build Version 17763

- Lower operating system versions: Machines with lower operating system versions (e.g., Server 2016) can be onboarded to MDE <!-- does this mean: can be onboarded to an MDE agent OR can still have an MDE agent onboarded to it-->but can't run SENSENDR.

## Passive Monitoring

Passive monitoring involves silently analyzing network traffic using known endpoints and traffic patterns, for example, MDE passively monitors network traffic to discover OT devices.

- Requirement: An MDE agent must be running on the LAN or subnet to be monitored.

- Network traffic type required: the MDE agent needs to receive unicast traffic between<!-- from ...  to the --> the discovered OT devices and the device with the agent.<!-- Theo - what does this mean? -->

:::image type="content" source="media/mde-agent-deployment-guide/mde-agent-deployment-guide-1.png" alt-text="A diagram showing the passive monitoring of a subnet." lightbox="media/mde-agent-deployment-guide/mde-agent-deployment-guide-1.png":::

## Standard Probing

Standard probing involves actively probing observed devices in the network to enrich collected data.

This mode leverages common discovery protocols that use multicast queries in the network to identify other devices not located using passive monitoring. For example, MDE can use standard probing to actively find devices in your network, which helps build a reliable and coherent device inventory.<!-- this doesnt show and example for this type of probing?-->

- Requirement: An MDE agent must be running on the LAN or subnet to be monitored.

- Functionality: Broadcast packets allow the MDE agent to create the device, <!-- Theo - what does this mean? create the device in the inventory? link to it?find it? identify it? -->though not necessarily with all the information needed for OT classification and CVEs. Based on the initial information discovered, the agent uses standard probing to complete the necessary information using appropriate protocols.

:::image type="content" source="media/mde-agent-deployment-guide/mde-agent-deployment-guide-2.png" alt-text="A diagram showing the standard probing discovery process." lightbox="media/mde-agent-deployment-guide/mde-agent-deployment-guide-2.png":::

These guidelines could ensure that the MDE agent is effectively deployed to maximize its value for OT discovery.
