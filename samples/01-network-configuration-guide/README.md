# Configuring VLAN Trunking on a Layer 3 Switch

**Document type:** Configuration Guide
**Audience:** Network administrators with basic CLI familiarity
**Why this sample:** Demonstrates procedural writing for enterprise networking hardware — prerequisites, numbered steps, verification, and troubleshooting, structured the way a Cisco-style config guide is structured.

---

## Overview

This guide explains how to configure VLAN trunking between two Layer 3 switches so that traffic from multiple VLANs can pass over a single physical link. Use this procedure when connecting switches in a multi-VLAN network, such as between a distribution switch and an access switch.

## Prerequisites

Before you begin, confirm the following:

- You have console or SSH access to both switches with administrative privileges.
- Both switches are running a compatible OS version (see the [Compatibility Matrix] for supported releases).
- The physical link between the switches is connected and the interface is active (`show interface status`).
- You know the VLAN IDs that need to travel over the trunk.

> **Note:** Changes in this procedure affect live traffic. Perform this configuration during a maintenance window.

## Configuration Steps

### Step 1: Identify the trunk interface

Determine which physical interface connects the two switches.

```
Switch1# show interface status
```

Confirm the interface is listed as `connected` before proceeding.

### Step 2: Set the interface to trunk mode

Enter interface configuration mode and set the switchport mode to trunk.

```
Switch1(config)# interface GigabitEthernet0/1
Switch1(config-if)# switchport mode trunk
```

### Step 3: Specify allowed VLANs

Restrict the trunk to only the VLANs required. This limits unnecessary broadcast traffic and reduces the security exposure of the link.

```
Switch1(config-if)# switchport trunk allowed vlan 10,20,30
```

> **Warning:** Omitting this step allows *all* VLANs across the trunk by default on most platforms. Always scope the trunk explicitly in production environments.

### Step 4: Set the native VLAN

Set a native VLAN that is not used for any tagged traffic, to reduce the risk of VLAN hopping attacks.

```
Switch1(config-if)# switchport trunk native vlan 999
```

### Step 5: Repeat on the peer switch

Repeat Steps 2–4 on the corresponding interface on the second switch, using matching VLAN and native VLAN values. A mismatch between the two sides is the most common cause of trunk failures.

## Verification

Confirm the trunk is operating correctly:

```
Switch1# show interface trunk
```

Check that:
- The interface appears in the trunk output
- The allowed VLAN list matches your configuration
- The status shows the port as `trunking`

## Troubleshooting

| Symptom | Likely Cause | Resolution |
|---|---|---|
| Trunk interface shows `not-trunking` | Mode mismatch between switches | Confirm both sides are set to `trunk`, not `dynamic` |
| Some VLANs not passing traffic | VLAN not in the allowed list | Re-check Step 3 on both switches |
| Native VLAN mismatch warning in logs | Native VLAN differs between switches | Set matching native VLAN on both interfaces |

## Related Documentation

- VLAN Design Best Practices
- Spanning Tree Configuration Guide
- Interface Security Hardening Guide
