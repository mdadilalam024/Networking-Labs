
# Lab 10: Static Routing in Cisco Packet Tracer

## Objective
Configure static routing between two routers to enable communication between two different LAN networks.

## Tools Required
- Cisco Packet Tracer
- 2 Routers
- 2 Switches
- 2 PCs
- Copper Straight-Through Cables
- Router-to-Router connection (Ethernet)

## Network Topology

```text
PC0 --- Switch0 --- Router0 ===== Router1 --- Switch1 --- PC1
```

## IP Addressing Scheme

### LAN 1

| Device | Interface | IP Address | Subnet Mask |
|---|---|---|---|
| PC0 | FastEthernet0 | 192.168.1.2 | 255.255.255.0 |
| Router0 | G0/0 | 192.168.1.1 | 255.255.255.0 |

### Router-to-Router Link

| Device | Interface | IP Address | Subnet Mask |
|---|---|---|---|
| Router0 | G0/1 | 10.0.0.1 | 255.255.255.252 |
| Router1 | G0/1 | 10.0.0.2 | 255.255.255.252 |

### LAN 2

| Device | Interface | IP Address | Subnet Mask |
|---|---|---|---|
| Router1 | G0/0 | 192.168.2.1 | 255.255.255.0 |
| PC1 | FastEthernet0 | 192.168.2.2 | 255.255.255.0 |

## Step 1: Configure Router0

```text
enable
configure terminal

interface gigabitEthernet 0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit

interface gigabitEthernet 0/1
ip address 10.0.0.1 255.255.255.252
no shutdown
exit

ip route 192.168.2.0 255.255.255.0 10.0.0.2

end
```

## Step 2: Configure Router1

```text
enable
configure terminal

interface gigabitEthernet 0/0
ip address 192.168.2.1 255.255.255.0
no shutdown
exit

interface gigabitEthernet 0/1
ip address 10.0.0.2 255.255.255.252
no shutdown
exit

ip route 192.168.1.0 255.255.255.0 10.0.0.1

end
```

## Step 3: Configure PC0

Desktop → IP Configuration

- IP Address: `192.168.1.2`
- Subnet Mask: `255.255.255.0`
- Default Gateway: `192.168.1.1`

## Step 4: Configure PC1

Desktop → IP Configuration

- IP Address: `192.168.2.2`
- Subnet Mask: `255.255.255.0`
- Default Gateway: `192.168.2.1`

## Step 5: Verify Routing Tables

On Router0 and Router1, run:

```text
show ip route
```

Look for the static route marked with `S`.

## Step 6: Test Connectivity

From PC0:

```text
ping 192.168.1.1
ping 10.0.0.2
ping 192.168.2.2
```

From PC1:

```text
ping 192.168.1.2
```

Successful replies confirm end-to-end connectivity.

## Understanding Static Routing

Static routing is a method in which an administrator manually configures routes to remote networks.

Command syntax:

```text
ip route destination-network subnet-mask next-hop-address
```

Example:

```text
ip route 192.168.2.0 255.255.255.0 10.0.0.2
```

## Troubleshooting

If ping fails:

- Check physical cable connections.
- Verify interface IP addresses.
- Ensure router interfaces are enabled using `no shutdown`.
- Check the next-hop IP address.
- Verify static routes using `show ip route`.
- Check PC default gateways.
- Test router-to-router connectivity first.

## What I Learned

- Static routing configuration.
- Router interface configuration.
- Next-hop address.
- Routing table verification.
- Communication between different LAN networks.
- Basic routing troubleshooting.

## Practical Evidence

Add your own screenshots after completing the lab:

- Complete network topology.
- Router0 configuration.
- Router1 configuration.
- `show ip route` output.
- Successful PC-to-PC ping test.

## Author
Md Adil Alam

GitHub: https://github.com/mdadilalam024
