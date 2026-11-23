
# Lab 17: DHCP Server Configuration in Cisco Packet Tracer

## Objective
Configure a DHCP server to automatically assign IP addresses and other network settings to client PCs.

## Tools Required
- Cisco Packet Tracer
- 1 Router
- 1 Switch
- 1 Server
- 3 PCs
- Ethernet cables

## Network Topology

```text
PC0 --------\
PC1 ---------- Switch -------- Router
PC2 --------/    |
                 |
               Server
```

## Network Addressing Scheme

| Device | IP Address | Subnet Mask |
|---|---|---|
| Router G0/0 | 192.168.1.1 | 255.255.255.0 |
| Server | 192.168.1.10 | 255.255.255.0 |
| PC0 | DHCP | DHCP |
| PC1 | DHCP | DHCP |
| PC2 | DHCP | DHCP |

Default Gateway: `192.168.1.1`

DNS Server: `192.168.1.10`

## Step 1: Create the Topology

1. Open Cisco Packet Tracer.
2. Add one router.
3. Add one switch.
4. Add one server.
5. Add three PCs.
6. Connect all devices to the switch.
7. Connect the router to the switch.

## Step 2: Configure Router Interface

Open Router CLI:

```text
enable
configure terminal

interface gigabitEthernet 0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit

end
```

## Step 3: Configure Server IP Address

Open Server → Desktop → IP Configuration.

Configure:

- IP Address: `192.168.1.10`
- Subnet Mask: `255.255.255.0`
- Default Gateway: `192.168.1.1`
- DNS Server: `192.168.1.10`

## Step 4: Enable DHCP Service

Open Server → Services → DHCP.

Turn DHCP service ON.

Create a DHCP pool with the following settings:

| Setting | Value |
|---|---|
| Pool Name | LAN_POOL |
| Default Gateway | 192.168.1.1 |
| DNS Server | 192.168.1.10 |
| Start IP Address | 192.168.1.100 |
| Subnet Mask | 255.255.255.0 |
| Maximum Users | 50 |

Click Add or Save, depending on the Packet Tracer version.

## Step 5: Configure PCs to Obtain IP Automatically

For each PC:

1. Open Desktop.
2. Select IP Configuration.
3. Click DHCP.
4. Wait for the IP configuration to be assigned.

Expected address range: `192.168.1.100` onwards.

## Step 6: Verify DHCP Configuration

On each PC, open Command Prompt:

```text
ipconfig
```

Check that the PC has received:

- An IP address from the DHCP pool.
- Correct subnet mask.
- Default gateway: `192.168.1.1`.
- DNS server: `192.168.1.10`.

## Step 7: Test Connectivity

From PC0:

```text
ping 192.168.1.1
ping 192.168.1.10
```

Test communication between PCs using their assigned IP addresses.

## Understanding DHCP

DHCP stands for Dynamic Host Configuration Protocol.

It automatically assigns network configuration to client devices.

### DHCP DORA Process

1. Discover – Client broadcasts a request for a DHCP server.
2. Offer – DHCP server offers an IP address.
3. Request – Client requests the offered IP address.
4. Acknowledgement – Server confirms the lease.

### DHCP Ports

- UDP 67: DHCP Server
- UDP 68: DHCP Client

## Important DHCP Concepts

- DHCP Scope: Range of IP addresses available for assignment.
- Lease: Period for which an IP address is assigned.
- Reservation: Assigns a specific IP address to a particular device.
- Exclusion: Prevents selected IP addresses from being assigned.
- Default Gateway: Router address used to reach other networks.

## Troubleshooting

If a PC does not receive an IP address:

- Check physical cable connections.
- Ensure DHCP service is ON.
- Verify the DHCP pool configuration.
- Check the available IP address range.
- Verify the server's static IP configuration.
- Check whether the DHCP server and client are on the same subnet.
- Renew the DHCP address if required.

## What I Learned

- DHCP server configuration.
- Automatic IP address assignment.
- DHCP DORA process.
- DHCP scope and lease.
- Default gateway and DNS configuration.
- DHCP troubleshooting.

## Practical Evidence

Add your own screenshots after completing the lab:

- Complete Packet Tracer topology.
- DHCP service configuration.
- DHCP pool settings.
- PC IP configuration showing DHCP.
- Successful ping test.

## Author
Md Adil Alam

GitHub: https://github.com/mdadilalam024
