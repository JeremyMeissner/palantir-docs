---
source_url: "https://www.palantir.com/docs/foundry/peer-manager/establish-mpx-connection/"
title: "Documentation | Create and update a peer connection > Establish a Multipass exchanger connection"
---
# Establish a Multipass exchanger connection

A Multipass exchanger (MPX) connection enables **Enrollment administrators** to create a secure communication channel between two enrollments across a network as a prerequisite to [creating a peer connection](/docs/foundry/peer-manager/create-a-peer-connection/). Before you establish an MPX connection, contact Palantir Support for help configuring the network setup required between the [enrollments](/docs/foundry/administration/enrollments-and-organizations/) you will connect, including firewall rules, certificate trust, and any other network configuration needed for the enrollments to communicate.

The instructions in the sections below outline actions an **Enrollment administrator** on *each* enrollment must take to establish the connection, such as generating an invite code, sharing the code with the other **Enrollment administrator**, and pasting the invite code in the **Network connections** tab in Peer Manager.

:::callout{theme="neutral"}
Use an MPX connection when a network connection is available between the two enrollments. If no network connection is available, contact Palantir Support to establish a data relay connection as an alternative to an MPX connection. A data relay connection establishes peering over an enrollment's existing cross-domain solution.
:::

## Coordinate the connection direction

Before you generate an invite code by selecting **New MPX invite** in the **Network connections** tab of Peer Manager, coordinate with the other enrollment's administrator so that each side selects the matching direction when generating their invite code:

* **Bidirectional connection**: To create a bidirectional connection where network traffic is sent in both directions, *both* administrators select **Bidirectional**.
* **Unidirectional connection from `Enrollment A` to `Enrollment B`:** To create a unidirectional connection where `Enrollment A` initiates network requests to `Enrollment B`:
  * The administrator on `Enrollment A` selects **Egress only**.
  * The administrator on `Enrollment B` selects **Ingress only**.
## Create a new MPX invite code

After you determine the connection's direction alongside the other **Enrollment administrator**, select from the options listed under **New MPX invite** to generate an invite code to share:

* **Bidirectional**: Both systems can initiate network requests to each other. Use this option if both enrollments have stable IPs.
* **Egress only**: Only your enrollment will initiate network requests. Choose this option if your system does not have a stable IP.
* **Ingress only**: Only the remote enrollment will initiate network requests. Choose this option if the remote enrollment does not have a stable IP.

After you select a direction, Peer Manager displays the **New MPX invite** dialog, where you can copy the invite code to share with the other **Enrollment administrator**.
## Enter an MPX invite code

After you receive an invite code from the **Enrollment administrator** on the other enrollment, follow the steps below to enter the code on your enrollment and complete your side of the connection:

1. Select **Enter code** next to **New MPX invite**.
2. Paste the invite code in the **Enter MPX invite code** dialog. Peer Manager validates the code and routes you to the MPX connection creation page.
3. Provide a **Name** for the MPX connection.
4. Confirm that a [network egress policy](/docs/foundry/administration/configure-egress/) is configured for your enrollment, as noted in the **Before you proceed** section.
5. Select **Create connection**.

Both administrators must [create their own](#create-a-new-mpx-invite-code) and [enter the enrollment's](#enter-an-mpx-invite-code) MPX invite codes. After the MPX connection is established on both enrollments, you can return to Peer Manager to [create a peer connection](/docs/foundry/peer-manager/create-a-peer-connection/) that uses the MPX connection.
