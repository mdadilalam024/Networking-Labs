
# Lab 13: Access Control Lists (ACL) Configuration

## Objective
Configure Standard and Extended Access Control Lists (ACLs) on a Cisco router to control network traffic.

## Tools Required
- Cisco Packet Tracer
- 1 Router
- 2 Switches
- 3 PCs
- Ethernet cables

## Network Topology

```text
PC0 -------- Switch0 -------- Router -------- Switch1 -------- PC1
                                                   |
                                                  PC2
```

## IP Addressing Scheme

| Device | IP Address | Subnet Mask | Gateway |
|---|---|---|---|
| Router G0/0 | 192.168.1.1 | 255.255.255.0 | - |
| Router G0/1 | 192.168.2.1 | 255.255.255.0 | - |
| PC0 | 192.168.1.2 | 255.255.255.0 | 192.168.1.1 |
| PC1 | 192.168.2.2 | 255.255.255.0 | 192.168.2.1 |
| PC2 | 192.168.2.3 | 255.255.255.0 | 192.168.2.1 |

## Step 1: Configure Router Interfaces

```text
enable
configure terminal

interface gigabitEthernet 0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit

interface gigabitEthernet 0/1
ip address 192.168.2.1 255.255.255.0
no shutdown
exit
```

## Step 2: Configure Standard ACL

Standard ACL filters traffic based on the source IP address.

Our objective is to block PC0 (192.168.1.2) from reaching the 192.168.2.0 network.

```text
access-list 10 deny host 192.168.1.2
access-list 10 permit any

interface gigabitEthernet 0/1
ip access-group 10 out
exit
```

## Step 3: Verify Standard ACL

Run:

```text
show access-lists
show ip interface gigabitEthernet 0/1
show running-config
```

## Step 4: Test Connectivity

From PC0:

```text
ping 192.168.2.2
```

Expected: Ping should fail because PC0 is denied by ACL 10.

From PC1:

```text
ping 192.168.1.2
```

Expected: Ping should succeed because traffic from PC1 is not denied by this ACL.

## Step 5: Configure Extended ACL

Extended ACL can filter traffic using source IP, destination IP, and protocol.

For this example, remove the previous ACL and configure a new ACL that blocks PC0 from accessing PC1 while allowing other IP traffic.

```text
configure terminal

interface gigabitEthernet 0/1
no ip access-group 10 out
exit

no access-list 10

access-list 110 deny ip host 192.168.1.2 host 192.168.2.2
access-list 110 permit ip any any

interface gigabitEthernet 0/0
ip access-group 110 in
exit
```

## Step 6: Test Extended ACL

From PC0:

```text
ping 192.168.2.2
```

Expected: Ping should fail.

From PC0:

```text
ping 192.168.2.3
```

Expected: Ping should succeed.

## Important ACL Concepts

- Standard ACL: Filters based on source IP address.
- Extended ACL: Filters using source, destination, protocol and ports.
- Permit: Allows matching traffic.
- Deny: Blocks matching traffic.
- Implicit Deny: Traffic not explicitly permitted or denied is denied at the end of an ACL.
- ACLs are processed from top to bottom.

## Important ACL Commands

```text
show access-lists
show ip access-lists
show ip interface
show running-config
```

## Troubleshooting

If ACL is not working:

- Verify the ACL configuration.
- Check the interface where ACL is applied.
- Verify inbound or outbound direction.
- Check ACL rule order.
- Remember the implicit deny at the end.
- Check source and destination IP addresses.
- Use `show access-lists` to inspect match counters.

## What I Learned

- Access Control Lists.
- Standard ACL configuration.
- Extended ACL configuration.
- Permit and deny rules.
- Inbound and outbound ACL application.
- Network traffic filtering.
- ACL troubleshooting.

## Practical Evidence

Add your own screenshots after completing the lab:

- Network topology.
- Standard ACL configuration.
- Extended ACL configuration.
- `show access-lists` output.
- Successful and blocked ping tests.

## Author
Md Adil Alam

GitHub: https://github.com/mdadilalam024
