
# 🖥️ Lab 01: Basic Networking Commands

## 🎯 Objective

To understand and practice essential Windows networking commands used in IT Support, Desktop Support, and Network Troubleshooting.

## 🛠️ Environment

- Operating System: Windows 10 / 11
- Tool: Command Prompt (CMD)

---

## 1. IP Configuration

**Command:**
```cmd
ipconfig
```

**Purpose:** Displays the basic IP configuration of network adapters.

**Uses:**
- Check IPv4 address
- Check subnet mask
- Check default gateway

---

## 2. Detailed IP Configuration

**Command:**
```cmd
ipconfig /all
```

**Purpose:** Displays detailed network adapter information.

**Uses:**
- MAC address
- DHCP status
- DNS servers
- DHCP server
- Network adapter details

---

## 3. Release IP Address

**Command:**
```cmd
ipconfig /release
```

**Purpose:** Releases the current DHCP-assigned IPv4 configuration.

**IT Support Use:** Used when troubleshooting DHCP address assignment issues.

---

## 4. Renew IP Address

**Command:**
```cmd
ipconfig /renew
```

**Purpose:** Requests a new IP configuration from the DHCP server.

---

## 5. Test Network Connectivity

**Command:**
```cmd
ping 8.8.8.8
```

**Purpose:** Tests connectivity using ICMP Echo Requests.

**Uses:**
- Check network reachability
- Observe response time
- Identify packet loss

---

## 6. Trace Network Route

**Command:**
```cmd
tracert google.com
```

**Purpose:** Displays the route taken by packets to a destination.

**Uses:**
- Identify network hops
- Investigate routing problems
- Observe timeouts

---

## 7. DNS Lookup

**Command:**
```cmd
nslookup google.com
```

**Purpose:** Queries DNS to resolve a domain name.

**Uses:**
- Check DNS resolution
- Identify DNS server
- Troubleshoot name resolution

---

## 8. Display Computer Name

**Command:**
```cmd
hostname
```

**Purpose:** Displays the computer's hostname.

---

## 9. Network Statistics

**Command:**
```cmd
netstat -ano
```

**Purpose:** Displays network connections, listening ports and associated process IDs.

---

## 📊 Lab Summary

| Command | Function |
|---|---|
| ipconfig | Basic IP information |
| ipconfig /all | Detailed network configuration |
| ipconfig /release | Release DHCP IPv4 configuration |
| ipconfig /renew | Renew DHCP IPv4 configuration |
| ping | Test connectivity |
| tracert | Trace network route |
| nslookup | DNS lookup |
| hostname | Display computer name |
| netstat -ano | Network connections and PIDs |

---

## 🎓 Learning Outcomes

- Understanding IP configuration
- Learning DHCP operations
- Testing network connectivity
- Understanding DNS resolution
- Basic network troubleshooting
- Using Windows CMD networking tools

---

## 👨‍💻 Author

**Md Adil Alam**

IT Executive | Desktop Support | Networking Enthusiast

GitHub: https://github.com/mdadilalam024

---

**Lab 01 – Basic Networking Commands**
