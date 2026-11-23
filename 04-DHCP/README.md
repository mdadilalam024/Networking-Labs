
# 🌐 Lab 04: DHCP Configuration & Troubleshooting

## 🎯 Objective

To understand Dynamic Host Configuration Protocol (DHCP), its working process, DORA mechanism, IP address allocation, DHCP configuration, and troubleshooting.

---

## 1. What is DHCP?

DHCP stands for Dynamic Host Configuration Protocol.

It is a network management protocol that automatically assigns IP configuration to devices connected to a network.

DHCP can provide:

- IP Address
- Subnet Mask
- Default Gateway
- DNS Server
- Lease Duration

**Example:**

When a laptop connects to a Wi-Fi network, the DHCP server can automatically assign an IP address without manual configuration.

---

## 2. How DHCP Works

DHCP uses UDP at the transport layer.

| Component | Port |
|---|---|
| DHCP Server | UDP 67 |
| DHCP Client | UDP 68 |

A DHCP client initially uses broadcast communication to discover available DHCP servers on its local network.

---

## 3. DHCP DORA Process

DORA represents the four main steps of the DHCP address allocation process.

### 1. Discover

The client broadcasts a DHCP Discover message to find available DHCP servers.

### 2. Offer

The DHCP server responds with a DHCP Offer containing an available IP address and configuration information.

### 3. Request

The client sends a DHCP Request indicating the offered address it wants to use.

### 4. Acknowledgement

The DHCP server sends a DHCP ACK confirming the IP address lease and configuration.

### DORA Summary

| Step | Message | Description |
|---|---|---|
| 1 | Discover | Client searches for DHCP server |
| 2 | Offer | Server offers IP configuration |
| 3 | Request | Client requests offered configuration |
| 4 | ACK | Server confirms the lease |

---

## 4. DHCP Components

### DHCP Server
Assigns IP configuration to clients.

### DHCP Client
A device that requests network configuration.

### DHCP Scope
Defines the range of IP addresses available for allocation.

### DHCP Lease
Defines how long a client can use an assigned IP address.

### DHCP Reservation
Associates a specific IP address with a client's identifier, commonly its MAC address.

### DHCP Exclusion
Prevents specified addresses within a scope from being dynamically allocated.

---

## 5. Example DHCP Configuration

Example network:

| Setting | Value |
|---|---|
| Network | 192.168.1.0/24 |
| DHCP Range | 192.168.1.100–192.168.1.200 |
| Subnet Mask | 255.255.255.0 |
| Default Gateway | 192.168.1.1 |
| DNS Server | 8.8.8.8 |
| DHCP Server | 192.168.1.2 |

A client connecting to this network may automatically receive an available IP address from the DHCP scope.

---

## 6. DHCP on Windows Server 2022

Basic DHCP server configuration steps:

1. Open Server Manager.
2. Select Add Roles and Features.
3. Choose Role-based or feature-based installation.
4. Select the target server.
5. Select DHCP Server.
6. Install the role.
7. Complete DHCP post-installation configuration.
8. Open DHCP management console.
9. Create a new IPv4 scope.
10. Configure the IP address range.
11. Configure exclusions if required.
12. Configure subnet mask and lease duration.
13. Configure default gateway and DNS options.
14. Activate the scope.

**Note:** The DHCP server should have an appropriate static IP configuration. In a production domain environment, DHCP authorization may also be required.

---

## 7. Windows DHCP Client Commands

### Display IP Configuration

```cmd
ipconfig
```

### Display Detailed Configuration

```cmd
ipconfig /all
```

### Release DHCP IPv4 Address

```cmd
ipconfig /release
```

### Renew DHCP IPv4 Address

```cmd
ipconfig /renew
```

### Clear DNS Cache

```cmd
ipconfig /flushdns
```

---

## 8. DHCP Troubleshooting

| Problem | Possible Cause | Troubleshooting |
|---|---|---|
| No IP address | DHCP unavailable | Check DHCP server |
| 169.254.x.x address | DHCP configuration unavailable | Check connectivity and DHCP |
| Unable to renew IP | DHCP server unreachable | Check network and DHCP service |
| Incorrect gateway | Wrong DHCP scope option | Verify scope configuration |
| Incorrect DNS | Wrong DNS option | Verify DHCP DNS settings |
| IP conflict | Duplicate address assignment | Check reservations and static IPs |

### What is APIPA?

APIPA stands for Automatic Private IP Addressing.

When a Windows DHCP client cannot obtain an IPv4 address automatically, it may assign itself an address from:

```text
169.254.0.0/16
```

An APIPA address generally indicates that DHCP configuration was not obtained.

It normally allows local-link communication only, not ordinary communication with remote networks.

---

## 9. Practical Troubleshooting Scenario

**Scenario:**

A user reports that their computer is connected to the office LAN but cannot access the internet.

Troubleshooting steps:

1. Check physical network connectivity.
2. Run `ipconfig /all`.
3. Verify the IPv4 address.
4. Check subnet mask and default gateway.
5. Check whether the address is APIPA.
6. Verify DHCP server information.
7. Run `ipconfig /release`.
8. Run `ipconfig /renew`.
9. Test gateway connectivity using `ping`.
10. Check DNS resolution using `nslookup`.

**Important:** These steps help isolate the issue. A failed renewal can indicate a DHCP or connectivity problem, but does not by itself prove the DHCP server is faulty.

---

## 10. Practical Lab Exercises

Try these exercises:

1. What is the full form of DHCP?
2. What are the four stages of DORA?
3. Which UDP port does a DHCP server use?
4. Which UDP port does a DHCP client use?
5. What is a DHCP scope?
6. What is a DHCP reservation?
7. What is APIPA?
8. Why does a computer receive a 169.254.x.x address?
9. What is the purpose of `ipconfig /renew`?
10. What is the difference between static and dynamic IP addressing?

---

## 🎓 Learning Outcomes

After completing this lab, I aim to understand:

- DHCP fundamentals
- DORA communication process
- DHCP server and client roles
- DHCP scope and lease configuration
- Windows Server 2022 DHCP installation
- IP address assignment
- DHCP troubleshooting

---

## 👨‍💻 Author

**Md Adil Alam**

IT Executive | Desktop Support | Networking Enthusiast

GitHub: https://github.com/mdadilalam024

---

**Lab 04 – DHCP Configuration & Troubleshooting**
