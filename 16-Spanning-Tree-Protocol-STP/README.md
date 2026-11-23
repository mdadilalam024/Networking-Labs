
# Lab 16: Spanning Tree Protocol (STP)

## Objective
Understand and configure Spanning Tree Protocol (STP) on Cisco switches to prevent Layer 2 switching loops.

## Tools Required
- Cisco Packet Tracer
- 3 Cisco 2960 Switches
- 3 PCs
- Copper Straight-Through Cables

## Network Topology

```text
             Switch0
             /     \
            /       \
       Switch1 ----- Switch2
          |             |
         PC0           PC1
```

The three switches form a redundant triangle topology.

## Step 1: Create the Topology

1. Open Cisco Packet Tracer.
2. Add three Cisco 2960 switches.
3. Connect the switches in a triangle.
4. Connect PC0 to Switch1.
5. Connect PC1 to Switch2.
6. Wait for STP to converge.

## Step 2: Understand STP

STP stands for Spanning Tree Protocol.

It prevents Layer 2 switching loops by logically blocking redundant paths.

Without STP, switching loops can cause:
- Broadcast storms.
- Multiple frame copies.
- MAC address table instability.
- Network performance problems.

## Step 3: Verify STP Configuration

Open the switch CLI and run:

```text
enable
show spanning-tree
```

Check the following:
- Root Bridge ID.
- Root Port.
- Designated Port.
- Blocking or alternate port status.
- Port roles and states.

## Step 4: Configure Switch Hostnames

On Switch0:

```text
enable
configure terminal
hostname SW1
exit
```

On Switch1:

```text
enable
configure terminal
hostname SW2
exit
```

On Switch2:

```text
enable
configure terminal
hostname SW3
exit
```

## Step 5: Configure the Root Bridge

Choose SW1 as the Root Bridge.

On SW1:

```text
enable
configure terminal
spanning-tree vlan 1 root primary
end
```

Verify:

```text
show spanning-tree
```

## Step 6: Configure a Backup Root Bridge

On SW2:

```text
enable
configure terminal
spanning-tree vlan 1 root secondary
end
```

This makes SW2 a preferred backup root bridge if the primary root bridge becomes unavailable.

## Step 7: Verify STP

On all switches, run:

```text
show spanning-tree
show spanning-tree vlan 1
show spanning-tree summary
```

Check whether:
- SW1 is the Root Bridge.
- One redundant path is logically blocked.
- The network has a loop-free forwarding topology.

## Step 8: Test Connectivity

Configure both PCs in the same subnet.

| Device | IP Address | Subnet Mask |
|---|---|---|
| PC0 | 192.168.1.2 | 255.255.255.0 |
| PC1 | 192.168.1.3 | 255.255.255.0 |

From PC0:

```text
ping 192.168.1.3
```

The ping should succeed if the topology and PC configurations are correct.

## Important STP Concepts

- Root Bridge: The central reference switch selected by STP.
- Root Port: The best path from a non-root switch toward the Root Bridge.
- Designated Port: The forwarding port selected for a network segment.
- Blocking/Alternate Port: A redundant path that does not forward normal user traffic.
- Bridge ID: Used in Root Bridge election.
- Path Cost: Used to select the best path.

## Important STP Commands

```text
show spanning-tree
show spanning-tree vlan 1
show spanning-tree summary
show spanning-tree root
```

## Troubleshooting

If STP is not working as expected:

- Verify switch-to-switch connections.
- Check STP status using `show spanning-tree`.
- Confirm the Root Bridge election.
- Check port roles and states.
- Wait for STP convergence.
- Verify that PCs have correct IP addresses.

## What I Learned

- Spanning Tree Protocol.
- Layer 2 switching loops.
- Broadcast storms.
- Root Bridge election.
- Root and Designated Ports.
- Redundant link management.
- STP verification and troubleshooting.

## Practical Evidence

Add your own screenshots after completing the lab:

- Triangle switch topology.
- `show spanning-tree` output.
- Root Bridge identification.
- Blocked or alternate port.
- Successful PC-to-PC ping test.

## Author
Md Adil Alam

GitHub: https://github.com/mdadilalam024
