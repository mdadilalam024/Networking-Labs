
# Lab 12: OSPF Routing Configuration (Area 0)

## Objective
Configure Open Shortest Path First (OSPF) on Cisco routers to establish dynamic routing between multiple LAN networks.

## Tools Required
- Cisco Packet Tracer
- 3 Routers
- 3 Switches
- 3 PCs
- Ethernet cables

## Network Topology

```text
PC0 -- SW0 -- R1 -------- R2 -------- R3 -- SW2 -- PC2
                       |
                      SW1
                       |
                      PC1
```

## IP Addressing Scheme

### LAN Networks

| Device | Interface | IP Address |
|---|---|---|
| R1 | G0/0 | 192.168.1.1/24 |
| R2 | G0/0 | 192.168.2.1/24 |
| R3 | G0/0 | 192.168.3.1/24 |

### Router-to-Router Links

| Connection | Interface | IP Address |
|---|---|---|
| R1 - R2 | R1 G0/1 | 10.0.12.1/30 |
| R1 - R2 | R2 G0/1 | 10.0.12.2/30 |
| R2 - R3 | R2 G0/2 | 10.0.23.1/30 |
| R2 - R3 | R3 G0/1 | 10.0.23.2/30 |

## PC IP Configuration

| PC | IP Address | Subnet Mask | Default Gateway |
|---|---|---|---|
| PC0 | 192.168.1.2 | 255.255.255.0 | 192.168.1.1 |
| PC1 | 192.168.2.2 | 255.255.255.0 | 192.168.2.1 |
| PC2 | 192.168.3.2 | 255.255.255.0 | 192.168.3.1 |

## Step 1: Configure Router Interfaces

Configure the IP addresses on each router interface according to the addressing table.

### Router R1

```text
enable
configure terminal

interface gigabitEthernet 0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit

interface gigabitEthernet 0/1
ip address 10.0.12.1 255.255.255.252
no shutdown
exit
```

### Router R2

```text
enable
configure terminal

interface gigabitEthernet 0/0
ip address 192.168.2.1 255.255.255.0
no shutdown
exit

interface gigabitEthernet 0/1
ip address 10.0.12.2 255.255.255.252
no shutdown
exit

interface gigabitEthernet 0/2
ip address 10.0.23.1 255.255.255.252
no shutdown
exit
```

### Router R3

```text
enable
configure terminal

interface gigabitEthernet 0/0
ip address 192.168.3.1 255.255.255.0
no shutdown
exit

interface gigabitEthernet 0/1
ip address 10.0.23.2 255.255.255.252
no shutdown
exit
```

## Step 2: Configure OSPF on R1

```text
router ospf 1
router-id 1.1.1.1
network 192.168.1.0 0.0.0.255 area 0
network 10.0.12.0 0.0.0.3 area 0
exit
```

## Step 3: Configure OSPF on R2

```text
router ospf 1
router-id 2.2.2.2
network 192.168.2.0 0.0.0.255 area 0
network 10.0.12.0 0.0.0.3 area 0
network 10.0.23.0 0.0.0.3 area 0
exit
```

## Step 4: Configure OSPF on R3

```text
router ospf 1
router-id 3.3.3.3
network 192.168.3.0 0.0.0.255 area 0
network 10.0.23.0 0.0.0.3 area 0
exit
```

## Step 5: Verify OSPF Neighbors

Run on each router:

```text
show ip ospf neighbor
```

Check whether neighboring routers have established an OSPF adjacency.

## Step 6: Verify Routing Table

```text
show ip route
show ip route ospf
```

OSPF-learned routes are marked with the letter `O`.

## Step 7: Test Connectivity

From PC0:

```text
ping 192.168.2.2
ping 192.168.3.2
```

From PC2:

```text
ping 192.168.1.2
```

Successful replies confirm end-to-end connectivity.

## Understanding OSPF

- OSPF stands for Open Shortest Path First.
- It is a link-state routing protocol.
- Uses the SPF (Dijkstra) algorithm.
- Uses cost as its routing metric.
- OSPF uses IP protocol number 89.
- Area 0 is the backbone area.
- Router ID uniquely identifies an OSPF router.

## Important OSPF Commands

```text
show ip ospf
show ip ospf neighbor
show ip ospf interface brief
show ip route ospf
show running-config
```

## Troubleshooting

If OSPF is not working:

- Check interface status using `show ip interface brief`.
- Verify IP addresses and subnet masks.
- Check OSPF network statements and wildcard masks.
- Confirm routers are in the same area on shared links.
- Check OSPF neighbor status.
- Verify that router IDs are unique.
- Check physical connections.

## What I Learned

- OSPF dynamic routing.
- OSPF Area 0.
- Router ID configuration.
- Wildcard masks.
- OSPF neighbor relationships.
- Routing table verification.
- Network connectivity testing.

## Practical Evidence

Add your own screenshots after completing the lab:

- Complete Packet Tracer topology.
- OSPF configuration on all routers.
- `show ip ospf neighbor` output.
- `show ip route` showing OSPF routes.
- Successful PC-to-PC ping test.

## Author
Md Adil Alam

GitHub: https://github.com/mdadilalam024
