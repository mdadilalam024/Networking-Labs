
# Lab 15: Switch Port Security Configuration

## Objective
Configure Port Security on a Cisco switch to control which devices can connect to specific switch ports using MAC address restrictions.

## Tools Required
- Cisco Packet Tracer
- 1 Cisco 2960 Switch
- 3 PCs
- Copper Straight-Through Cables

## Network Topology

```text
PC0 -------- Fa0/1
PC1 -------- Fa0/2
              |
           Switch
              |
PC2 -------- Fa0/3
```

## IP Addressing Scheme

| Device | Switch Port | IP Address |
|---|---|---|
| PC0 | Fa0/1 | 192.168.1.2 |
| PC1 | Fa0/2 | 192.168.1.3 |
| PC2 | Fa0/3 | 192.168.1.4 |

Subnet Mask: `255.255.255.0`

## Step 1: Create the Topology

1. Open Cisco Packet Tracer.
2. Add one Cisco 2960 switch.
3. Add three PCs.
4. Connect each PC to the switch.
5. Configure IP addresses on all PCs.

## Step 2: Configure Switch Port Security

Open the switch CLI:

```text
enable
configure terminal

interface fastEthernet 0/1
switchport mode access
switchport port-security
switchport port-security maximum 1
switchport port-security mac-address sticky
switchport port-security violation shutdown
exit
```

## Step 3: Verify Port Security

Run:

```text
show port-security
show port-security interface fastEthernet 0/1
show port-security address
```

Check the secure MAC address and violation mode.

## Step 4: Understand Port Security Violation Modes

### 1. Protect
- Drops traffic from unauthorized MAC addresses.
- Does not generate a violation notification through the usual violation counter.

### 2. Restrict
- Drops traffic from unauthorized MAC addresses.
- Increments the violation counter.
- Can generate a syslog or SNMP notification.

### 3. Shutdown
- Places the port into the error-disabled state after a violation.
- This is the default violation mode when port security is enabled.

## Step 5: Test Port Security

1. Keep PC0 connected to Fa0/1.
2. Generate traffic from PC0.
3. Check the learned sticky MAC address.
4. Disconnect PC0.
5. Connect a different PC to Fa0/1.
6. Generate traffic and observe the port-security violation.

Note: The violation is triggered when the switch receives traffic from an unauthorized MAC address, not merely when a cable is connected.

## Step 6: Recover a Shutdown Port

After removing the unauthorized device, manually recover the port:

```text
enable
configure terminal

interface fastEthernet 0/1
shutdown
no shutdown
exit
```

Verify:

```text
show interfaces status
show port-security interface fastEthernet 0/1
```

## Important Port Security Commands

```text
show port-security
show port-security address
show port-security interface fastEthernet 0/1
show running-config
```

## Understanding Sticky MAC Address

Sticky MAC learning allows a switch to dynamically learn a connected device's MAC address and add it to the running configuration as a secure sticky address.

## Troubleshooting

If Port Security is not working:

- Verify that the port is configured as an access port.
- Check whether Port Security is enabled.
- Verify the maximum secure MAC address limit.
- Check the violation mode.
- Inspect the learned MAC addresses.
- Check whether the port is error-disabled.
- Remove unauthorized devices before recovering the port.

## What I Learned

- Switch Port Security.
- Secure MAC address learning.
- Sticky MAC configuration.
- Maximum MAC address limits.
- Port security violation modes.
- Error-disabled port recovery.
- Basic switch security troubleshooting.

## Practical Evidence

Add your own screenshots after completing the lab:

- Packet Tracer topology.
- Port Security configuration.
- `show port-security` output.
- Sticky MAC address table.
- Port security violation test.
- Port recovery verification.

## Author
Md Adil Alam

GitHub: https://github.com/mdadilalam024
