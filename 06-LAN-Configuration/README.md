
# 🌐 Lab 06: LAN Configuration & Network Devices

## 🎯 Objective

To understand Local Area Networks (LAN), network devices, Ethernet communication, MAC addressing, network topologies, and basic LAN configuration.

---

## 1. What is LAN?

LAN stands for Local Area Network.

A LAN connects computers and other devices within a limited geographical area, such as:

- Home
- Office
- School
- Computer laboratory

**Example:** Multiple computers connected to an office switch form a LAN.

---

## 2. Network Devices

### Router
- Connects different IP networks.
- Forwards packets using IP addresses.
- Acts as a default gateway for network clients.

### Switch
- Connects devices within a LAN.
- Forwards Ethernet frames using MAC addresses.
- Learns MAC addresses and maintains a MAC address table.

### Hub
- Connects multiple Ethernet devices.
- Repeats incoming signals to other ports.

### Modem
- Converts signals for communication over an ISP access connection.

### Access Point
- Provides wireless network connectivity.
- Connects wireless clients to a network.

### Firewall
- Controls network traffic according to security rules.

---

## 3. MAC Address

MAC stands for Media Access Control.

A MAC address is a link-layer address used for communication on a local network.

Example:

```text
00-1A-2B-3C-4D-5E
```

Uses:
- Identifying network interfaces
- Ethernet frame delivery
- Switch MAC address learning

---

## 4. LAN Topologies

### Star Topology
All devices connect to a central switch or hub.

### Bus Topology
Devices share a common communication cable.

### Ring Topology
Devices are connected in a circular arrangement.

### Mesh Topology
Devices have multiple interconnections for redundancy.

---

## 5. Basic LAN Configuration Example

Example network:

| Device | IP Address |
|---|---|
| Router | 192.168.1.1 |
| PC 1 | 192.168.1.10 |
| PC 2 | 192.168.1.11 |
| Printer | 192.168.1.20 |

Subnet Mask:

```text
255.255.255.0
```

Default Gateway:

```text
192.168.1.1
```

All devices belong to the same IPv4 subnet.

---

## 6. How a Switch Works

1. A device sends an Ethernet frame.
2. The switch examines the source MAC address.
3. The switch learns the source MAC address and its incoming port.
4. The switch checks its MAC address table for the destination.
5. If known, it forwards the frame through the appropriate port.
6. If unknown, it generally floods the frame within the same VLAN, excluding the incoming port.

---

## 7. Windows LAN Troubleshooting Commands

### Check IP Configuration

```cmd
ipconfig /all
```

### Check Default Gateway Connectivity

```cmd
ping 192.168.1.1
```

### View ARP Table

```cmd
arp -a
```

### View Routing Table

```cmd
route print
```

### Test Network Connectivity

```cmd
ping 192.168.1.10
```

### View Network Connections

```cmd
netstat -ano
```

---

## 8. Practical Troubleshooting Scenarios

| Problem | Possible Cause | Troubleshooting |
|---|---|---|
| PC cannot connect to LAN | Cable or adapter issue | Check cable and link status |
| PC cannot reach gateway | Incorrect IP or VLAN | Verify IP and network configuration |
| Printer unavailable | Connectivity issue | Check printer IP and network |
| Slow network | Congestion or faulty link | Check link speed and network usage |
| IP conflict | Duplicate IP address | Identify conflicting devices |
| Switch port inactive | Port or cable issue | Check port status and cabling |

---

## 9. Practical Lab Exercises

1. What is the full form of LAN?
2. What is the difference between a router and a switch?
3. What is a MAC address?
4. How does a switch learn MAC addresses?
5. What is a default gateway?
6. What is the difference between a hub and a switch?
7. What is a star topology?
8. What is the purpose of the ARP table?
9. Why should devices in the same subnet have unique IP addresses?
10. How would you troubleshoot a PC that cannot connect to the office LAN?

---

## 🎓 Learning Outcomes

- Understand LAN fundamentals.
- Identify common network devices.
- Understand MAC addressing.
- Learn Ethernet switching basics.
- Understand network topologies.
- Perform basic LAN troubleshooting.

---

## 👨‍💻 Author

**Md Adil Alam**

IT Executive | Desktop Support | Networking Enthusiast

GitHub: https://github.com/mdadilalam024

---

**Lab 06 – LAN Configuration & Network Devices**
