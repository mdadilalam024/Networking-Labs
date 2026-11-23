
# Lab 08: VLAN Configuration in Cisco Packet Tracer

## Objective
Create VLANs on a Cisco switch and assign PCs to different VLANs.

## Tools Required
- Cisco Packet Tracer
- 1 Cisco Switch (2960)
- 4 PCs
- Copper Straight-Through Cables

## Network Topology

```text
PC0 -------- Switch -------- PC2
             |
PC1 ---------|
             |
PC3 ---------|
```

## VLAN Configuration Plan

| Device | Switch Port | VLAN | IP Address |
|---|---|---|---|
| PC0 | Fa0/1 | VLAN 10 | 192.168.10.2 |
| PC1 | Fa0/2 | VLAN 10 | 192.168.10.3 |
| PC2 | Fa0/3 | VLAN 20 | 192.168.20.2 |
| PC3 | Fa0/4 | VLAN 20 | 192.168.20.3 |

Subnet Mask: `255.255.255.0`

## Step 1: Create the Topology

1. Open Cisco Packet Tracer.
2. Add one Cisco 2960 switch.
3. Add four PCs.
4. Connect each PC to the switch using Copper Straight-Through cables.

## Step 2: Create VLANs

Open Switch CLI:

```text
enable
configure terminal

vlan 10
name HR
exit

vlan 20
name IT
exit
```

## Step 3: Assign Ports to VLAN 10

```text
interface range fastEthernet 0/1-2
switchport mode access
switchport access vlan 10
exit
```

## Step 4: Assign Ports to VLAN 20

```text
interface range fastEthernet 0/3-4
switchport mode access
switchport access vlan 20
exit
```

## Step 5: Verify VLAN Configuration

Run:

```text
show vlan brief
```

Check that:
- Fa0/1 and Fa0/2 belong to VLAN 10.
- Fa0/3 and Fa0/4 belong to VLAN 20.

## Step 6: Configure IP Addresses

Configure IP addresses on each PC:

| PC | IP Address | Subnet Mask |
|---|---|---|
| PC0 | 192.168.10.2 | 255.255.255.0 |
| PC1 | 192.168.10.3 | 255.255.255.0 |
| PC2 | 192.168.20.2 | 255.255.255.0 |
| PC3 | 192.168.20.3 | 255.255.255.0 |

No default gateway is required for this same-switch VLAN connectivity test.

## Step 7: Test Connectivity

From PC0, open Command Prompt:

```text
ping 192.168.10.3
```

This should succeed because both PCs belong to VLAN 10.

Now test:

```text
ping 192.168.20.2
```

This should fail because PC0 and PC2 belong to different VLANs, and inter-VLAN routing has not been configured.

## Troubleshooting

If the ping test fails:
- Check cable connections.
- Verify IP addresses and subnet masks.
- Run `show vlan brief`.
- Confirm the correct switch ports are assigned to each VLAN.
- Check that the switch ports are operational.

## What I Learned

- What VLANs are.
- How to create VLANs on a Cisco switch.
- How to assign switch ports to VLANs.
- How VLANs separate broadcast domains.
- How to verify VLAN configuration.
- How to test connectivity between devices in different VLANs.

## Practical Evidence

Add your own screenshots after completing the lab:

- Packet Tracer topology.
- `show vlan brief` output.
- Successful ping between PCs in the same VLAN.
- Failed ping between PCs in different VLANs.

## Author
Md Adil Alam

GitHub: https://github.com/mdadilalam024
