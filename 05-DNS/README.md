
# 🌐 Lab 05: DNS Configuration & Troubleshooting

## 🎯 Objective

To understand Domain Name System (DNS), DNS resolution, DNS records, DNS servers, and practical DNS troubleshooting.

---

## 1. What is DNS?

DNS stands for Domain Name System.

DNS translates human-readable domain names into IP addresses so that computers can locate services on a network.

Example:

```text
google.com → IP Address
```

Instead of remembering an IP address, users can access websites using domain names.

---

## 2. How DNS Works

When a user enters a website address in a browser:

1. The client checks its local DNS cache.
2. It checks other applicable local name-resolution sources.
3. If necessary, it sends a query to a configured DNS resolver.
4. The resolver finds the required DNS information.
5. The resolver returns the result to the client.
6. The browser uses the resolved IP address to connect to the website.

---

## 3. Types of DNS Servers

### DNS Resolver
Receives DNS queries from clients and obtains answers.

### Root DNS Server
Directs queries towards the appropriate Top-Level Domain servers.

### TLD DNS Server
Provides information about authoritative name servers for a domain.

### Authoritative DNS Server
Provides DNS records for the domain it manages.

---

## 4. Common DNS Records

| Record | Purpose |
|---|---|
| A | Maps domain to IPv4 address |
| AAAA | Maps domain to IPv6 address |
| CNAME | Creates a canonical name alias |
| MX | Identifies mail servers |
| NS | Identifies authoritative name servers |
| PTR | Maps IP address to hostname |
| TXT | Stores text information |
| SOA | Contains zone authority information |

---

## 5. DNS Port Numbers

| Protocol | Port | Purpose |
|---|---|---|
| UDP | 53 | Most standard DNS queries |
| TCP | 53 | DNS zone transfers and other DNS operations |

DNS can use both UDP and TCP on port 53.

---

## 6. Public DNS Servers

Examples of public DNS resolver addresses:

| Provider | Primary DNS | Secondary DNS |
|---|---|---|
| Google | 8.8.8.8 | 8.8.4.4 |
| Cloudflare | 1.1.1.1 | 1.0.0.1 |
| Quad9 | 9.9.9.9 | 149.112.112.112 |

---

## 7. Windows DNS Commands

### 1. Check DNS Resolution

```cmd
nslookup google.com
```

Purpose: Queries DNS to obtain domain information.

### 2. Display DNS Cache

```cmd
ipconfig /displaydns
```

Purpose: Displays cached DNS resolver records.

### 3. Clear DNS Cache

```cmd
ipconfig /flushdns
```

Purpose: Clears the local DNS resolver cache.

### 4. Renew IP Configuration

```cmd
ipconfig /renew
```

Purpose: Requests renewed DHCP configuration.

### 5. Test Network Connectivity

```cmd
ping 8.8.8.8
```

Purpose: Tests IP connectivity to the destination.

### 6. Trace Network Route

```cmd
tracert google.com
```

Purpose: Displays the route towards the resolved destination.

---

## 8. DNS Troubleshooting

| Problem | Possible Cause | Troubleshooting |
|---|---|---|
| Website not opening | DNS resolution issue | Run nslookup |
| Domain not resolving | Incorrect DNS server | Verify DNS settings |
| Old IP returned | Cached DNS record | Flush DNS cache |
| Internal website unavailable | Internal DNS issue | Check internal DNS server |
| IP works but domain fails | Possible DNS issue | Compare IP connectivity and name resolution |

---

## 9. Practical Troubleshooting Scenario

**Scenario:**

A user can access websites using IP addresses but cannot open websites using domain names.

Possible cause: DNS resolution problem.

Troubleshooting steps:

1. Check network connectivity.
2. Run `ipconfig /all`.
3. Identify the configured DNS server.
4. Run `nslookup google.com`.
5. Check whether DNS queries return an answer.
6. Verify DNS server reachability.
7. Run `ipconfig /flushdns`.
8. Test DNS resolution again.

Note: Successful IP connectivity with failed name resolution suggests a DNS problem, but proxy, firewall and other configuration issues should also be considered.

---

## 10. Practical Lab Exercises

1. What is the full form of DNS?
2. What is the purpose of DNS?
3. What is the difference between A and AAAA records?
4. What is a CNAME record?
5. Which port does DNS use?
6. What is an authoritative DNS server?
7. What is DNS caching?
8. What does `ipconfig /flushdns` do?
9. What is the difference between DNS and DHCP?
10. Why can a user access an IP address but not a domain name?

---

## 🎓 Learning Outcomes

- Understand DNS fundamentals.
- Learn DNS resolution.
- Identify common DNS records.
- Understand DNS server types.
- Practice Windows DNS commands.
- Troubleshoot domain resolution problems.

---

## 👨‍💻 Author

**Md Adil Alam**

IT Executive | Desktop Support | Networking Enthusiast

GitHub: https://github.com/mdadilalam024

---

**Lab 05 – DNS Configuration & Troubleshooting**
