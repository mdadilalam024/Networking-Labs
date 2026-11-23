
# 🌐 Lab 03: IP Addressing & Subnetting

## 🎯 Objective

To understand IPv4 addressing, subnet masks, network IDs, host IDs, private and public IP addresses, default gateways, and basic subnetting concepts.

---

## 1. What is an IP Address?

An IP (Internet Protocol) address is a logical address assigned to a device on an IP network.

It helps identify devices and enables communication between networks.

Example:

```text
192.168.1.10
```

## 2. Types of IP Addresses

### IPv4

- Uses 32 bits.
- Divided into four octets.
- Each octet ranges from 0 to 255.
- Written in dotted-decimal format.

Example:

```text
192.168.1.100
```

### IPv6

- Uses 128 bits.
- Written in hexadecimal notation.
- Provides a much larger address space.

Example:

```text
2001:db8::1
```

---

## 3. IPv4 Address Structure

An IPv4 address contains 32 bits.

Example:

```text
192.168.1.10
```

Binary representation:

```text
11000000.10101000.00000001.00001010
```

Each octet contains 8 bits.

---

## 4. IP Address Classes

| Class | First Octet Range | Default Mask |
|---|---|---|
| A | 1–126 | 255.0.0.0 |
| B | 128–191 | 255.255.0.0 |
| C | 192–223 | 255.255.255.0 |
| D | 224–239 | Multicast |
| E | 240–255 | Experimental |

Note: Classful addressing is historical. Modern networks primarily use CIDR.

---

## 5. Private IP Address Ranges

Private IP addresses are used inside local networks and are not directly routed on the public internet.

| Class | Private IP Range |
|---|---|
| A | 10.0.0.0 – 10.255.255.255 |
| B | 172.16.0.0 – 172.31.255.255 |
| C | 192.168.0.0 – 192.168.255.255 |

Public IP addresses are globally routable addresses assigned through internet service providers or other authorized address allocations.

---

## 6. What is a Subnet Mask?

A subnet mask identifies the network and host portions of an IPv4 address.

Example:

```text
IP Address:  192.168.1.10
Subnet Mask: 255.255.255.0
CIDR:        /24
```

In this example:

- Network Address: 192.168.1.0
- Host Address: 192.168.1.10
- Broadcast Address: 192.168.1.255
- Usable Host Range: 192.168.1.1 – 192.168.1.254

---

## 7. What is CIDR?

CIDR stands for Classless Inter-Domain Routing.

It represents the number of network bits in an IP address.

Examples:

| CIDR | Subnet Mask | Total Addresses |
|---|---|---|
| /8 | 255.0.0.0 | 16,777,216 |
| /16 | 255.255.0.0 | 65,536 |
| /24 | 255.255.255.0 | 256 |
| /25 | 255.255.255.128 | 128 |
| /26 | 255.255.255.192 | 64 |
| /27 | 255.255.255.224 | 32 |
| /28 | 255.255.255.240 | 16 |
| /30 | 255.255.255.252 | 4 |

For ordinary IPv4 subnets, usable host addresses are generally total addresses minus 2. Special-purpose subnets have exceptions.

---

## 8. What is a Default Gateway?

A default gateway is the router or Layer 3 device a host uses to reach destinations outside its local subnet.

Example:

```text
IP Address:      192.168.1.10
Subnet Mask:     255.255.255.0
Default Gateway: 192.168.1.1
DNS Server:      8.8.8.8
```

---

## 9. What is Subnetting?

Subnetting is the process of dividing a larger IP network into smaller networks.

Benefits:

- Efficient IP address utilization
- Better network organization
- Reduced broadcast domains
- Easier network management
- Improved network segmentation

### Subnetting Formula

For conventional IPv4 subnets:

Total Addresses = 2^h

Usable Hosts = 2^h - 2

Where h is the number of host bits.

---

## 10. Practical Subnetting Example

Given:

```text
Network: 192.168.1.0/24
Required Subnets: 2
```

Divide the network into two /25 subnets.

| Detail | Subnet 1 | Subnet 2 |
|---|---|---|
| Network | 192.168.1.0 | 192.168.1.128 |
| First Host | 192.168.1.1 | 192.168.1.129 |
| Last Host | 192.168.1.126 | 192.168.1.254 |
| Broadcast | 192.168.1.127 | 192.168.1.255 |
| Usable Hosts | 126 | 126 |

---

## 11. Windows Commands for IP Configuration

### Display IP Configuration

```cmd
ipconfig
```

### Display Detailed Configuration

```cmd
ipconfig /all
```

### Display Routing Table

```cmd
route print
```

### Display ARP Cache

```cmd
arp -a
```

### Test Connectivity

```cmd
ping 192.168.1.1
```

---

## 12. Practical Exercises

Try solving these questions:

1. What is the subnet mask of /24?
2. How many total IP addresses are in a /26 subnet?
3. How many usable host addresses are in a /26 subnet?
4. What is the network address of 192.168.10.25/24?
5. What is the broadcast address of 192.168.10.25/24?
6. What is the difference between a private and public IP?
7. What is the purpose of a default gateway?

---

## 🎓 Learning Outcomes

- Understand IPv4 and IPv6.
- Identify private and public IP addresses.
- Understand subnet masks and CIDR.
- Calculate network and broadcast addresses.
- Understand basic subnetting.
- Use Windows IP configuration commands.

---

## 👨‍💻 Author

**Md Adil Alam**

IT Executive | Desktop Support | Networking Enthusiast

GitHub: https://github.com/mdadilalam024

---

**Lab 03 – IP Addressing & Subnetting**
