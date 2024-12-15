---
title: MDE agent deployment guide for OT discovery - Microsoft Defender for IoT
description: Learn how to deploy an MDE agent on your OT network sensors.
ms.date: 12/19/2024
ms.topic: how-to
---
<!-- This isnt really a how-to but a concept - is that correct? Limor-->
# MDE Agent Deployment Guide for OT Discovery

## How to properly place MDE agent to receive maximal value

This guide provides step-by-step instructions for deploying a Microsoft Defender for Endpoint (MDE) agent in the correct network location to ensure that it receives the relevant traffic. Proper placement enhances data quality and optimal performance within the network.

## MDE Discovery for OT Capabilities

MDE agents offer various discovery and security capabilities. Depending on the ability to use each functionality,<!-- Theo - what does this mean? --> the MDE agent should be placed accordingly in the network. The capabilities include:

- [Passive monitoring](#passive-monitoring)

- [Standard probing](#standard-probing)

## General Recommendations

General recommendations to set up the MDE agent as an OT discovery data source are:

- Minimum Requirement: an MDE <!-- Theo - what does this mean? -->in the LAN is the minimum requirement if Standard mode is enabled.

- Scanners per VLAN: at least five scanners per VLAN.

- Onboarding Devices: onboard any devices with a status of "Can Be Onboarded" that can be located, to increase visibility.

## Usage Ability

- Server 2019 and computers with Build Version 17763

- Lower operating system versions: Machines with lower operating system versions (e.g., Server 2016) can be onboarded to MDE but can't run SENSENDR.

## Passive Monitoring

Theo can we add an intro sentence here

- Requirement: MDE must be <!-- running on? Theo? not inside-->inside the LAN or subnet to be monitored.

- Network Traffic Type<!-- Theo - do these need to be capitalised, are they a name? --> required: the MDE agent needs to receive unicast traffic between the discovered OT devices and the device with the agent.<!-- Theo - what does this mean? -->

:::image type="content" source="media/mde-agent-deployment-guide/mde-agent-deployment-guide-1.png" alt-text="A diagram showing the passive monitoring of a subnet.":::

## Standard Probing

- Requirement: MDE needs to be <!-- running on? Theo? not inside-->inside the interesting LAN or subnet.

- Functionality: Broadcast packets cause<!-- ?? allow?  --> the MDE agent to create the device, <!-- Theo - what does this mean? create the device in the inventory? link to it?find it? identify it? -->though not necessarily with all the information needed for OT classification and CVEs. Based on the initial information discovered, the agent uses standard probing to complete the necessary information using appropriate protocols.

:::image type="content" source="media/mde-agent-deployment-guide/mde-agent-deployment-guide-2.png" alt-text="A diagram showing the standard probing discovery process.":::

These guidelines could ensure that the MDE agent is effectively deployed to maximize its value for OT discovery.
