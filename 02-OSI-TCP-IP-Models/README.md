
# 🌐 Lab 02: OSI Model & TCP/IP Model

## 🎯 Objective

To understand the OSI reference model, its seven layers, their functions, protocols, and the relationship between OSI and TCP/IP models.

---

## 1. What is the OSI Model?

OSI stands for Open Systems Interconnection.

It is a conceptual reference model that explains how data travels between devices over a network.

The OSI model consists of seven layers.

## 2. Seven Layers of the OSI Model

| Layer | Name | Main Function | Examples |
|---|---|---|---|
| 7 | Application | Network services for applications | HTTP, FTP, DNS, SMTP |
| 6 | Presentation | Data translation, encryption and compression | TLS/SSL, JPEG |
| 5 | Session | Establishes and manages communication sessions | RPC, NetBIOS |
| 4 | Transport | End-to-end data delivery | TCP, UDP |
| 3 | Network | Logical addressing and routing | IP, ICMP, Routers |
| 2 | Data Link | Frames and MAC addressing | Ethernet, Switches |
| 1 | Physical | Transmission of raw bits | Cables, Hubs, Signals |

---

## 3. Explanation of Each Layer

### Layer 7 – Application
- Provides network services to applications.
- Examples: HTTP, HTTPS, FTP, DNS, SMTP.

### Layer 6 – Presentation
- Handles data translation and formatting.
- Performs encryption and compression.
- Examples: TLS/SSL, JPEG.

### Layer 5 – Session
- Establishes and manages communication sessions.
- Controls session establishment and termination.

### Layer 4 – Transport
- Provides end-to-end communication.
- TCP provides reliable, connection-oriented delivery.
- UDP provides connectionless delivery.

### Layer 3 – Network
- Handles logical IP addressing and routing.
- Determines paths between networks.
- Example: IP, ICMP.

### Layer 2 – Data Link
- Handles frame delivery over a local link.
- Uses MAC addresses.
- Ethernet switches commonly operate at this layer.

### Layer 1 – Physical
- Transmits raw bits through physical media.
- Examples: Ethernet cables, fiber optics and radio signals.

---

## 4. TCP/IP Model

The TCP/IP model is commonly represented using four layers.

| TCP/IP Layer | Function | Examples |
|---|---|---|
| Application | Application and session-related services | HTTP, DNS, SMTP |
| Transport | End-to-end transport | TCP, UDP |
| Internet | Logical addressing and routing | IP, ICMP |
| Network Access | Local network communication and physical transmission | Ethernet, Wi-Fi |

---

## 5. OSI vs TCP/IP Model

| OSI Model | TCP/IP Model |
|---|---|
| 7 Layers | 4 Layers |
| Reference model | Practical protocol architecture |
| Developed by ISO | Developed through DARPA/DoD research |
| Separates Session and Presentation | Includes these functions in Application |
| Separate Physical and Data Link layers | Combined as Network Access |

---

## 6. Data Units (PDU)

| Layer | Data Unit |
|---|---|
| Application | Data |
| Presentation | Data |
| Session | Data |
| Transport | Segment (TCP) / Datagram (UDP) |
| Network | Packet |
| Data Link | Frame |
| Physical | Bits |

---

## 7. Practical Example

When opening a website:

1. Application: Browser creates an HTTP/HTTPS request.
2. Presentation: Data representation and encryption are handled.
3. Session: Communication session is managed.
4. Transport: TCP or another transport protocol carries data.
5. Network: IP handles addressing and routing.
6. Data Link: Ethernet or Wi-Fi frames data for the local link.
7. Physical: Bits travel through the network medium.

At the destination, the process is reversed.

---

## 8. Troubleshooting by OSI Layer

| Layer | Example Issue |
|---|---|
| Physical | Damaged cable or no link light |
| Data Link | VLAN or MAC-related issue |
| Network | Incorrect IP or gateway |
| Transport | Port blocked or connection failure |
| Session | Session establishment problem |
| Presentation | Encryption or certificate problem |
| Application | DNS or application service issue |

---

## 🎓 Learning Outcomes

- Understand all seven OSI layers.
- Explain the purpose of each layer.
- Understand TCP/IP architecture.
- Identify common networking protocols.
- Relate troubleshooting issues to OSI layers.

---

## 👨‍💻 Author

**Md Adil Alam**

IT Executive | Desktop Support | Networking Enthusiast

GitHub: https://github.com/mdadilalam024

---

**Lab 02 – OSI Model & TCP/IP Model**
