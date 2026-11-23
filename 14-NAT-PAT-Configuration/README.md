
# Lab 14: NAT and PAT Configuration in Cisco Packet Tracer

## Objective
Configure Static NAT, Dynamic NAT, and PAT (Port Address Translation) on a Cisco router to translate private IP addresses into public IP addresses.

## Tools Required
- Cisco Packet Tracer
- 1 Router
- 2 Switches
- 2 PCs
- 1 Server (representing an external network)
- Ethernet cables

## Network Topology

```text
PC0 ----\
         Switch ---- Router ---- External Network ---- Server
PC1 ----/
```

## IP Addressing Scheme

### Inside Network

| Device | Interface | IP Address |
|---|---|---|
| Router | G0/0 | 192.168.1.1/24 |
| PC0 | FastEthernet0 | 192.168.1.10/24 |
| PC1 | FastEthernet0 | 192.168.1.20/24 |

### Outside Network

| Device | Interface | IP Address |
|---|---|---|
| Router | G0/1 | 203.0.113.1/24 |
| Server | FastEthernet0 | 203.0.113.10/24 |

PC default gateway: `192.168.1.1`

Server default gateway: `203.0.113.1`

Note: The public-side addresses use the documentation-only TEST-NET-3 range, not real internet-routable addresses.

## Step 1: Configure Router Interfaces

```text
enable
configure terminal

interface gigabitEthernet 0/0
ip address 192.168.1.1 255.255.255.0
ip nat inside
no shutdown
exit

interface gigabitEthernet 0/1
ip address 203.0.113.1 255.255.255.0
ip nat outside
no shutdown
exit
```

## Step 2: Configure Static NAT

Static NAT maps one private IP address to one public IP address.

Example: Map PC0's private IP to a public-side address.

```text
ip nat inside source static 192.168.1.10 203.0.113.100
```

Verify:

```text
show ip nat translations
show ip nat statistics
```

## Step 3: Configure Dynamic NAT

Dynamic NAT maps private IP addresses to available addresses from a public IP pool.

Remove the static mapping before testing this separate example:

```text
no ip nat inside source static 192.168.1.10 203.0.113.100

access-list 1 permit 192.168.1.0 0.0.0.255

ip nat pool PUBLIC_POOL 203.0.113.100 203.0.113.110 netmask 255.255.255.0

ip nat inside source list 1 pool PUBLIC_POOL
```

Note: Dynamic NAT needs enough available pool addresses for simultaneous translations.

## Step 4: Configure PAT (NAT Overload)

PAT allows multiple private devices to share one public IP address by using different port numbers.

Remove the Dynamic NAT rule before testing PAT:

```text
no ip nat inside source list 1 pool PUBLIC_POOL

ip nat inside source list 1 interface gigabitEthernet 0/1 overload
```

## Step 5: Test Connectivity

From PC0 and PC1:

```text
ping 203.0.113.10
```

Generate traffic from both PCs and check the router:

```text
show ip nat translations
show ip nat statistics
```

Check whether translations are created.

## Understanding NAT

NAT stands for Network Address Translation.

### Types of NAT

1. Static NAT: One-to-one mapping between private and public IP addresses.
2. Dynamic NAT: Maps private addresses to addresses from a public IP pool.
3. PAT: Allows multiple private devices to share a public IP using port numbers.

## Important NAT Commands

```text
show ip nat translations
show ip nat statistics
show running-config
clear ip nat translation *
```

## Troubleshooting

If NAT is not working:

- Verify inside and outside interface configuration.
- Check interface IP addresses.
- Verify the NAT access list.
- Check NAT pool configuration.
- Confirm the overload command for PAT.
- Verify default gateways.
- Generate traffic before checking translations.
- Check interface status using `show ip interface brief`.

## What I Learned

- Network Address Translation.
- Static NAT.
- Dynamic NAT.
- Port Address Translation.
- NAT inside and outside interfaces.
- NAT translation table verification.
- Basic NAT troubleshooting.

## Practical Evidence

Add your own screenshots after completing the lab:

- Network topology.
- Router NAT configuration.
- `show ip nat translations` output.
- `show ip nat statistics` output.
- Successful connectivity test.

## Author
Md Adil Alam

GitHub: https://github.com/mdadilalam024
