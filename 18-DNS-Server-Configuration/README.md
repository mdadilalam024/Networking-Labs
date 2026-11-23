
# Lab 18: DNS Server Configuration in Cisco Packet Tracer

## Objective
Configure a DNS server in Cisco Packet Tracer to resolve domain names into IP addresses.

## Tools Required
- Cisco Packet Tracer
- 1 Router
- 1 Switch
- 1 Server
- 2 PCs
- Ethernet cables

## Network Topology

```text
PC0 --------\
             \
              Switch -------- Router
             /
PC1 --------/ 
             |
           Server
```

## IP Addressing Scheme

| Device | IP Address | Subnet Mask |
|---|---|---|
| Router G0/0 | 192.168.1.1 | 255.255.255.0 |
| DNS Server | 192.168.1.10 | 255.255.255.0 |
| PC0 | 192.168.1.20 | 255.255.255.0 |
| PC1 | 192.168.1.21 | 255.255.255.0 |

Default Gateway: `192.168.1.1`

DNS Server: `192.168.1.10`

## Step 1: Create the Topology

1. Open Cisco Packet Tracer.
2. Add one router.
3. Add one switch.
4. Add one server.
5. Add two PCs.
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

## Step 3: Configure DNS Server IP

Open Server → Desktop → IP Configuration.

Configure:

- IP Address: `192.168.1.10`
- Subnet Mask: `255.255.255.0`
- Default Gateway: `192.168.1.1`
- DNS Server: `192.168.1.10`

## Step 4: Enable DNS Service

1. Open Server.
2. Select Services.
3. Select DNS.
4. Turn DNS Service ON.

Add a DNS record:

| Field | Value |
|---|---|
| Name | www.example.com |
| Type | A Record |
| Address | 192.168.1.10 |

Click Add.

This maps the domain name to the DNS server's IP address for this lab.

## Step 5: Configure PC0

Open PC0 → Desktop → IP Configuration.

- IP Address: `192.168.1.20`
- Subnet Mask: `255.255.255.0`
- Default Gateway: `192.168.1.1`
- DNS Server: `192.168.1.10`

## Step 6: Configure PC1

Open PC1 → Desktop → IP Configuration.

- IP Address: `192.168.1.21`
- Subnet Mask: `255.255.255.0`
- Default Gateway: `192.168.1.1`
- DNS Server: `192.168.1.10`

## Step 7: Test DNS Resolution

Open PC0 → Desktop → Command Prompt.

Run:

```text
ping 192.168.1.10
nslookup www.example.com
ping www.example.com
```

Expected result:
- DNS server should respond to the IP connectivity test.
- `nslookup` should resolve `www.example.com` to `192.168.1.10`.
- Ping by domain name should resolve the name and reach the server.

Note: The exact `nslookup` output may vary depending on the Packet Tracer version.

## Understanding DNS

DNS stands for Domain Name System.

It translates human-readable domain names into IP addresses.

### Common DNS Records

| Record | Purpose |
|---|---|
| A | Maps a hostname to an IPv4 address |
| AAAA | Maps a hostname to an IPv6 address |
| CNAME | Creates an alias for another hostname |
| MX | Identifies mail servers |
| NS | Identifies authoritative name servers |
| PTR | Maps an IP address to a hostname |

### DNS Port Numbers

- UDP 53: Common DNS queries.
- TCP 53: DNS transfers and other DNS operations requiring TCP.

## Important DNS Concepts

- DNS Resolver: Receives DNS queries from clients.
- DNS Server: Provides DNS information.
- DNS Record: Stores information about a domain.
- DNS Cache: Stores previously resolved results.
- DNS Resolution: Process of converting a hostname into an IP address.

## Troubleshooting

If DNS resolution fails:

- Verify the DNS server IP address.
- Ensure DNS service is ON.
- Check that the DNS record is correctly added.
- Verify the PC's DNS server setting.
- Test connectivity using `ping 192.168.1.10`.
- Check IP addresses and subnet masks.

## What I Learned

- DNS server configuration.
- DNS name resolution.
- A records.
- DNS client configuration.
- nslookup command.
- DNS troubleshooting.

## Practical Evidence

Add your own screenshots after completing the lab:

- Complete Packet Tracer topology.
- DNS service configuration.
- DNS A record.
- PC DNS configuration.
- Successful nslookup output.
- Successful ping using domain name.

## Author
Md Adil Alam

GitHub: https://github.com/mdadilalam024
