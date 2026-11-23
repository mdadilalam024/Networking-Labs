
# Lab 20: Complete Network Troubleshooting Project

## Objective

Design and configure a small office network using Cisco Packet Tracer. Configure IP addressing, DHCP, DNS and default gateway settings, then perform network troubleshooting and connectivity testing.

## Tools Required

- Cisco Packet Tracer
- 1 Router
- 1 Cisco 2960 Switch
- 1 Server
- 3 PCs
- Ethernet cables

## Network Topology

```text
             Router
                |
              Switch
          _____|_____
         |      |    |
       Server  PC0  PC1
                |
               PC2
```

## Network Addressing Scheme

Network: 192.168.10.0/24

| Device | IP Address | Subnet Mask |
|---|---|---|
| Router G0/0 | 192.168.10.1 | 255.255.255.0 |
| Server | 192.168.10.10 | 255.255.255.0 |
| PC0 | DHCP | DHCP |
| PC1 | DHCP | DHCP |
| PC2 | DHCP | DHCP |

Default Gateway: 192.168.10.1

DNS Server: 192.168.10.10

## Step 1: Create Network Topology

1. Open Cisco Packet Tracer.
2. Add one router.
3. Add one Cisco 2960 switch.
4. Add one server.
5. Add three PCs.
6. Connect all devices to the switch.
7. Connect the router to the switch.

## Step 2: Configure Router

Open Router CLI:

```text
enable
configure terminal

interface gigabitEthernet 0/0
ip address 192.168.10.1 255.255.255.0
no shutdown
exit

end
```

Verify:

```text
show ip interface brief
```

## Step 3: Configure Server

Open Server → Desktop → IP Configuration.

Configure:

- IP Address: 192.168.10.10
- Subnet Mask: 255.255.255.0
- Default Gateway: 192.168.10.1
- DNS Server: 192.168.10.10

## Step 4: Configure DHCP Service

Open Server → Services → DHCP.

Turn DHCP service ON.

Configure the following pool:

| Setting | Value |
|---|---|
| Pool Name | OFFICE_LAN |
| Default Gateway | 192.168.10.1 |
| DNS Server | 192.168.10.10 |
| Start IP Address | 192.168.10.100 |
| Subnet Mask | 255.255.255.0 |
| Maximum Users | 50 |

Click Add or Save.

## Step 5: Configure DNS Service

Open Server → Services → DNS.

1. Turn DNS Service ON.
2. Add the following A record:

| Field | Value |
|---|---|
| Name | intranet.adil.lab |
| Type | A Record |
| Address | 192.168.10.10 |

Click Add.

## Step 6: Configure HTTP Service

Open Server → Services → HTTP.

Turn HTTP Service ON.

This will allow the server to host a basic webpage for testing.

## Step 7: Configure PCs

For PC0, PC1 and PC2:

1. Open Desktop.
2. Select IP Configuration.
3. Click DHCP.
4. Wait for the network configuration.

Expected configuration:

- IP address from 192.168.10.100 onwards.
- Subnet mask: 255.255.255.0
- Default gateway: 192.168.10.1
- DNS server: 192.168.10.10

## Step 8: Perform Connectivity Testing

From PC0, open Command Prompt.

Test gateway:

```text
ping 192.168.10.1
```

Test server:

```text
ping 192.168.10.10
```

Test another PC using its assigned IP address:

```text
ping 192.168.10.101
```

Use the actual IP address assigned to PC1.

## Step 9: Perform DNS Testing

From PC0:

```text
nslookup intranet.adil.lab
```

Expected result:

The hostname should resolve to:

192.168.10.10

Then test:

```text
ping intranet.adil.lab
```

You can also open the PC Web Browser and enter:

```text
http://intranet.adil.lab
```

The server webpage should open if DNS and HTTP are configured correctly.

## Step 10: Network Troubleshooting Scenarios

### Scenario 1: PC Not Receiving IP Address

Problem:
A PC is not receiving an IP address automatically.

Troubleshooting:

- Check physical cable connections.
- Verify DHCP service is ON.
- Check DHCP pool configuration.
- Check the available IP address range.
- Verify that the PC is configured for DHCP.

Useful command:

```text
ipconfig
```

### Scenario 2: Cannot Reach Default Gateway

Problem:
PC cannot communicate with the router.

Troubleshooting:

- Verify the PC IP address.
- Check subnet mask.
- Verify the default gateway.
- Check router interface status.
- Check switch connections.

Useful commands:

```text
ipconfig /all
ping 192.168.10.1
```

### Scenario 3: DNS Name Not Resolving

Problem:
PC can reach the server using its IP address but cannot resolve its hostname.

Troubleshooting:

- Check DNS server IP on the PC.
- Verify DNS service is ON.
- Check the DNS A record.
- Verify DNS server connectivity.

Useful command:

```text
nslookup intranet.adil.lab
```

### Scenario 4: Website Not Opening

Problem:
The server webpage is not opening.

Troubleshooting:

- Verify server IP configuration.
- Check HTTP service status.
- Test connectivity to the server.
- Verify DNS resolution.
- Check the URL.

Useful command:

```text
ping 192.168.10.10
```

## Step 11: Important Troubleshooting Commands

| Command | Purpose |
|---|---|
| ipconfig | Display IP configuration |
| ipconfig /all | Display detailed network information |
| ipconfig /release | Release DHCP address |
| ipconfig /renew | Request a new DHCP address |
| ping | Test network connectivity |
| tracert | Trace network path |
| nslookup | Test DNS resolution |
| arp -a | Display ARP cache |
| netstat -an | Display network connections |
| hostname | Display computer name |

## Step 12: Final Verification Checklist

- [ ] Router interface is up.
- [ ] Server has a static IP address.
- [ ] DHCP service is working.
- [ ] All PCs receive IP addresses automatically.
- [ ] PCs can reach the default gateway.
- [ ] PCs can communicate with the server.
- [ ] DNS resolution works.
- [ ] HTTP webpage opens using the hostname.
- [ ] Network troubleshooting tests are documented.

## What I Learned

- Network topology design.
- IPv4 addressing.
- DHCP configuration.
- DNS configuration.
- Default gateway configuration.
- Network connectivity testing.
- Basic HTTP server configuration.
- Network troubleshooting methodology.
- Common Windows networking commands.

## Practical Evidence

Add your own screenshots after completing the project:

1. Complete network topology.
2. Router interface configuration.
3. Server IP configuration.
4. DHCP service and pool configuration.
5. DNS A record configuration.
6. PC DHCP configuration.
7. Successful ping tests.
8. Successful nslookup output.
9. Website opened using hostname.
10. Troubleshooting results.

## Author

Md Adil Alam

GitHub: https://github.com/mdadilalam024
