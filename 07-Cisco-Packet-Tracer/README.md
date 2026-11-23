
# Lab 07: Cisco Packet Tracer – Basic Network Topology

## Objective
Create a basic network topology using Cisco Packet Tracer and test connectivity between two PCs through a switch and router.

## Tools Required
- Cisco Packet Tracer
- 1 Router
- 1 Switch
- 2 PCs
- Copper Straight-Through Cables

## Network Topology

```text
PC0 --------\
             \
              Switch -------- Router
             /
PC1 --------/
```

## IP Addressing Scheme

| Device | Interface | IP Address | Subnet Mask |
|---|---|---|---|
| Router | G0/0 | 192.168.1.1 | 255.255.255.0 |
| PC0 | FastEthernet0 | 192.168.1.2 | 255.255.255.0 |
| PC1 | FastEthernet0 | 192.168.1.3 | 255.255.255.0 |

Default Gateway for both PCs: `192.168.1.1`

## Step 1: Create the Topology
1. Open Cisco Packet Tracer.
2. Add one router.
3. Add one switch.
4. Add two PCs.
5. Connect both PCs to the switch.
6. Connect the switch to the router.

## Step 2: Configure Router

Open the router CLI and enter:

```text
enable
configure terminal
interface gigabitEthernet 0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit
end
show ip interface brief
```

Note: If your router uses a different interface name, select the correct interface.

## Step 3: Configure PC0

Desktop → IP Configuration

- IP Address: `192.168.1.2`
- Subnet Mask: `255.255.255.0`
- Default Gateway: `192.168.1.1`

## Step 4: Configure PC1

Desktop → IP Configuration

- IP Address: `192.168.1.3`
- Subnet Mask: `255.255.255.0`
- Default Gateway: `192.168.1.1`

## Step 5: Test Connectivity

Open PC0 → Desktop → Command Prompt.

Run:

```text
ping 192.168.1.3
ping 192.168.1.1
```

Open PC1 and run:

```text
ping 192.168.1.2
```

## Expected Result

- Both PCs should communicate successfully.
- Router interface should show an up/up status.
- Ping should receive replies if the configuration and connections are correct.

## Troubleshooting

If ping fails, check:

- Physical cable connections.
- Correct IP addresses.
- Subnet masks.
- Default gateway.
- Router interface status.
- Whether the router interface is enabled using `no shutdown`.

## What I Learned

- Creating a basic network topology.
- Connecting PCs, switches, and routers.
- Configuring IPv4 addresses.
- Configuring a default gateway.
- Testing connectivity using the ping command.
- Basic network troubleshooting.

## Practical Evidence

Add your own screenshots here after completing the lab:

- Network topology screenshot.
- Router interface configuration.
- Successful ping test.

## Author
Md Adil Alam

GitHub: https://github.com/mdadilalam024
