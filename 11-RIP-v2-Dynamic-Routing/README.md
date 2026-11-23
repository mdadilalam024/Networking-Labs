
# Lab 11: Dynamic Routing Using RIP v2

## Objective
Configure RIP version 2 on Cisco routers to exchange routing information dynamically and enable communication between different LAN networks.

## Tools Required
- Cisco Packet Tracer
- 3 Routers
- 3 Switches
- 3 PCs
- Copper Straight-Through Cables

## Network Topology

```text
PC0 -- Switch0 -- R1 -------- R2 -------- R3 -- Switch2 -- PC2
                              |
                            Switch1
                              |
                             PC1
```

For a simple linear topology, connect each router to the next router using Ethernet interfaces.

## IP Addressing Scheme

### LAN Networks

| Network | Router Interface | IP Address |
|---|---|---|
| LAN 1 | R1 G0/0 | 192.168.1.1/24 |
| LAN 2 | R2 G0/0 | 192.168.2.1/24 |
| LAN 3 | R3 G0/0 | 192.168.3.1/24 |

### Router-to-Router Links

| Connection | First Interface | Second Interface |
|---|---|---|
| R1 - R2 | R1 G0/1: 10.0.12.1/30 | R2 G0/1: 10.0.12.2/30 |
| R2 - R3 | R2 G0/2: 10.0.23.1/30 | R3 G0/1: 10.0.23.2/30 |

## PC Configuration

| PC | IP Address | Subnet Mask | Default Gateway |
|---|---|---|---|
| PC0 | 192.168.1.2 | 255.255.255.0 | 192.168.1.1 |
| PC1 | 192.168.2.2 | 255.255.255.0 | 192.168.2.1 |
| PC2 | 192.168.3.2 | 255.255.255.0 | 192.168.3.1 |

## Step 1: Configure Router Interfaces

Configure the interfaces according to the IP addressing table.

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

## Step 2: Configure RIP v2 on R1

```text
router rip
version 2
no auto-summary
network 192.168.1.0
network 10.0.0.0
exit
```

## Step 3: Configure RIP v2 on R2

```text
router rip
version 2
no auto-summary
network 192.168.2.0
network 10.0.0.0
exit
```

## Step 4: Configure RIP v2 on R3

```text
router rip
version 2
no auto-summary
network 192.168.3.0
network 10.0.0.0
exit
```

Note: Cisco RIP network commands identify the major classful network. The `10.0.0.0` statement enables RIP on the 10.0.12.0/30 and 10.0.23.0/30 interfaces.

## Step 5: Verify RIP Configuration

Run on each router:

```text
show ip protocols
show ip route
show ip route rip
```

RIP-learned routes are marked with `R` in the routing table.

## Step 6: Test Connectivity

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

## Understanding RIP v2

RIP stands for Routing Information Protocol.

- It is a distance-vector routing protocol.
- Uses hop count as its routing metric.
- Maximum usable hop count is 15.
- A metric of 16 means the destination is unreachable.
- RIP v2 supports classless routing and VLSM.
- Uses UDP port 520.
- Sends periodic routing updates approximately every 30 seconds.

## Troubleshooting

If connectivity fails:

- Check router interface status using `show ip interface brief`.
- Verify IP addresses and subnet masks.
- Check RIP configuration using `show ip protocols`.
- Verify routes using `show ip route`.
- Ensure all required networks are included in RIP.
- Check physical connections between routers.
- Verify PC default gateways.

## What I Learned

- Dynamic routing concepts.
- RIP version 2 configuration.
- Distance-vector routing.
- Routing table verification.
- Hop-count metric.
- Network connectivity testing.

## Practical Evidence

Add your own screenshots after completing the lab:

- Complete Packet Tracer topology.
- RIP v2 configuration on all routers.
- `show ip protocols` output.
- `show ip route` showing RIP routes.
- Successful ping between PCs on different LANs.

## Author
Md Adil Alam

GitHub: https://github.com/mdadilalam024
