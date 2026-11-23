
# Lab 09: Inter-VLAN Routing Using Router-on-a-Stick

## Objective
Configure Inter-VLAN Routing using a Cisco router so that devices in different VLANs can communicate with each other.

## Tools Required
- Cisco Packet Tracer
- 1 Router (with a GigabitEthernet interface)
- 1 Cisco 2960 Switch
- 4 PCs
- Copper Straight-Through Cables

## Network Topology

```text
PC0 --------\
             \
PC1 ---------- Switch ===== Router
             /
PC2 --------/
             \
PC3 ----------/
```

The connection between the switch and router will be a trunk link.

## IP Addressing Scheme

| Device | VLAN | IP Address | Subnet Mask | Gateway |
|---|---|---|---|---|
| PC0 | 10 | 192.168.10.2 | 255.255.255.0 | 192.168.10.1 |
| PC1 | 10 | 192.168.10.3 | 255.255.255.0 | 192.168.10.1 |
| PC2 | 20 | 192.168.20.2 | 255.255.255.0 | 192.168.20.1 |
| PC3 | 20 | 192.168.20.3 | 255.255.255.0 | 192.168.20.1 |

## Step 1: Create VLANs on the Switch

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

## Step 2: Assign Access Ports

```text
interface range fastEthernet 0/1-2
switchport mode access
switchport access vlan 10
exit

interface range fastEthernet 0/3-4
switchport mode access
switchport access vlan 20
exit
```

## Step 3: Configure the Switch Trunk Port

Assuming the router is connected to switch port GigabitEthernet 0/1:

```text
interface gigabitEthernet 0/1
switchport mode trunk
exit
```

Verify:

```text
show interfaces trunk
```

## Step 4: Configure Router Subinterfaces

Assuming the router's connected interface is GigabitEthernet 0/0:

```text
enable
configure terminal

interface gigabitEthernet 0/0
no shutdown
exit

interface gigabitEthernet 0/0.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0
exit

interface gigabitEthernet 0/0.20
encapsulation dot1Q 20
ip address 192.168.20.1 255.255.255.0
exit

end
```

Note: Use the actual router interface connected to the switch. The physical interface must be enabled.

## Step 5: Configure PC IP Addresses

Configure each PC through Desktop → IP Configuration.

PC0:
- IP: 192.168.10.2
- Mask: 255.255.255.0
- Gateway: 192.168.10.1

PC1:
- IP: 192.168.10.3
- Mask: 255.255.255.0
- Gateway: 192.168.10.1

PC2:
- IP: 192.168.20.2
- Mask: 255.255.255.0
- Gateway: 192.168.20.1

PC3:
- IP: 192.168.20.3
- Mask: 255.255.255.0
- Gateway: 192.168.20.1

## Step 6: Verify Router Configuration

Run:

```text
show ip interface brief
show running-config
```

Check that the physical interface and both subinterfaces are operational.

## Step 7: Test Connectivity

From PC0:

```text
ping 192.168.10.3
ping 192.168.20.2
```

From PC2:

```text
ping 192.168.10.2
```

Successful replies confirm connectivity between VLANs.

## Troubleshooting

If communication fails:

- Verify VLAN assignments using `show vlan brief`.
- Verify trunk configuration using `show interfaces trunk`.
- Check router subinterface configuration.
- Check `encapsulation dot1Q` VLAN IDs.
- Verify IP addresses and default gateways.
- Ensure the router's physical interface is enabled.
- Confirm that the correct switch and router ports are connected.

## What I Learned

- Inter-VLAN Routing.
- Router-on-a-Stick architecture.
- Router subinterfaces.
- 802.1Q VLAN tagging.
- Switch trunk configuration.
- Default gateway configuration.
- Connectivity testing between VLANs.

## Practical Evidence

Add your own screenshots after completing the lab:

- Complete Packet Tracer topology.
- Switch VLAN configuration.
- Switch trunk configuration.
- Router subinterface configuration.
- Successful ping between VLAN 10 and VLAN 20.

## Author
Md Adil Alam

GitHub: https://github.com/mdadilalam024
