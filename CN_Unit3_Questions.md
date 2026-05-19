# UNIT 3 — NETWORK LAYER
## 30 × 2-Mark Questions + 15 × 7-Mark Questions

---

# 📝 2-MARK QUESTIONS (30)

---

### Q1. What are the functions of the Network Layer?
Logical addressing (IP), Routing (finding best path), Packetizing (encapsulation), Fragmentation & Reassembly, Error handling (ICMP). It provides host-to-host delivery across multiple networks.

---

### Q2. What is an IP Address?
An IP address is a 32-bit (IPv4) logical address assigned to each device on a network. It uniquely identifies a device and has two parts: Network ID and Host ID. Written in dotted decimal notation (e.g., 192.168.1.1).

---

### Q3. What are the five classes of IP addresses?
| Class | Range | Default Mask | Use |
|-------|-------|-------------|-----|
| A | 1–126 | /8 (255.0.0.0) | Large networks |
| B | 128–191 | /16 (255.255.0.0) | Medium networks |
| C | 192–223 | /24 (255.255.255.0) | Small networks |
| D | 224–239 | — | Multicast |
| E | 240–255 | — | Reserved/Experimental |

---

### Q4. What is a Subnet Mask?
A subnet mask is a 32-bit number that separates the network portion from the host portion of an IP address. It uses 1s for network bits and 0s for host bits. Example: 255.255.255.0 means first 24 bits = network, last 8 = host.

---

### Q5. What is the loopback address?
The loopback address is **127.0.0.1**. It is used to test the TCP/IP stack on the local machine. Packets sent to this address never leave the device — they are looped back internally.

---

### Q6. Differentiate between Network Address and Broadcast Address.
| Feature | Network Address | Broadcast Address |
|---------|----------------|-------------------|
| Host bits | All 0s | All 1s |
| Purpose | Identifies the network | Sends to all hosts in network |
| Example (192.168.1.0/24) | 192.168.1.0 | 192.168.1.255 |
| Assignable | No | No |

---

### Q7. What is ARP?
ARP (Address Resolution Protocol) resolves a known **IP address to a MAC address**. The sender broadcasts an ARP Request on the LAN; the device with the matching IP responds with an ARP Reply containing its MAC address.

---

### Q8. What is RARP?
RARP (Reverse Address Resolution Protocol) resolves a known **MAC address to an IP address**. Used by diskless workstations at boot time to discover their IP address from a RARP server.

---

### Q9. What is ICMP?
ICMP (Internet Control Message Protocol) is used for **error reporting and diagnostics** at the network layer. It does not carry user data. Common uses: `ping` (echo request/reply), `traceroute`, destination unreachable messages.

---

### Q10. What is the TTL field in IPv4 header?
TTL (Time To Live) is an 8-bit field that specifies the maximum number of hops a packet can traverse. Each router decrements TTL by 1. When TTL reaches 0, the packet is discarded and an ICMP "Time Exceeded" message is sent back.

---

### Q11. What is Subnetting?
Subnetting is the process of dividing a large network into smaller sub-networks (subnets) by borrowing bits from the host portion. It improves security, reduces broadcast traffic, and optimizes IP address usage.

---

### Q12. What is VLSM?
VLSM (Variable Length Subnet Masking) allows subnets of different sizes within the same network by using different subnet mask lengths. This minimizes IP address waste. Allocate the largest subnet first.

---

### Q13. What is the difference between Static and Dynamic Routing?
| Feature | Static Routing | Dynamic Routing |
|---------|---------------|-----------------|
| Configuration | Manual by admin | Automatic via protocols |
| Adaptability | Cannot adapt to changes | Adapts automatically |
| Overhead | No protocol overhead | Protocol overhead (RIP, OSPF) |
| Best for | Small networks | Large, complex networks |

---

### Q14. What is a Default Gateway?
A default gateway is the IP address of the router that a host uses to send packets to devices outside its own network/subnet. If a destination IP is not in the local subnet, the packet is forwarded to the default gateway.

---

### Q15. What is a Routing Table?
A routing table is a data structure stored in a router that lists the available routes to network destinations. Each entry typically contains: Destination Network, Subnet Mask, Next Hop, Interface, and Metric (cost).

---

### Q16. What is the Bellman-Ford equation used in DVR?
**D(x,y) = min { C(x,v) + D(v,y) }** for all neighbors v of x. Where D(x,y) = least cost from x to y, C(x,v) = direct cost from x to neighbor v, D(v,y) = neighbor v's reported cost to y.

---

### Q17. What is the Count-to-Infinity problem?
Count-to-Infinity occurs in Distance Vector Routing when a link goes down but routers keep incrementing the cost in a loop because bad news travels slowly. Solutions: Split Horizon, Poison Reverse, Hold-down timer.

---

### Q18. Differentiate between Unicast, Broadcast, and Multicast.
| Type | Definition | Example |
|------|-----------|---------|
| **Unicast** | One sender → one receiver | HTTP request |
| **Broadcast** | One sender → all devices in network | ARP Request |
| **Multicast** | One sender → group of receivers | Video streaming (Class D) |

---

### Q19. What is NAT (Network Address Translation)?
NAT translates private IP addresses to public IP addresses (and vice versa) at the router. It allows multiple devices on a LAN to share a single public IP for internet access, conserving IPv4 addresses.

---

### Q20. What is the difference between IPv4 and IPv6 address size?
IPv4 uses **32-bit** addresses (≈4.3 billion addresses, dotted decimal: 192.168.1.1). IPv6 uses **128-bit** addresses (≈3.4×10³⁸ addresses, hexadecimal colon: 2001:0db8::1).

---

### Q21. What is Fragmentation?
Fragmentation is the process of breaking a large IP packet into smaller fragments when it exceeds the MTU (Maximum Transmission Unit) of the next-hop link. Reassembly occurs at the destination.

---

### Q22. What is MTU?
MTU (Maximum Transmission Unit) is the largest packet size (in bytes) that a network link can transmit. If a packet exceeds MTU, it must be fragmented. Standard Ethernet MTU = 1500 bytes.

---

### Q23. What is a Leaky Bucket Algorithm?
Leaky Bucket is a traffic shaping algorithm where packets enter a bucket at variable rate but leave (transmit) at a **constant rate**. If the bucket is full, incoming packets are dropped. It smooths bursty traffic.

---

### Q24. What is a Token Bucket Algorithm?
Token Bucket allows controlled bursts. Tokens are added at a constant rate. Each packet needs a token to transmit. If tokens available → transmit immediately. If no tokens → wait. More flexible than Leaky Bucket.

---

### Q25. What are the flags in IPv4 header?
The Flags field is 3 bits:
- **Bit 0:** Reserved (always 0)
- **Bit 1 (DF):** Don't Fragment — if set, router must not fragment
- **Bit 2 (MF):** More Fragments — if set, more fragments follow; 0 means last/only fragment

---

### Q26. What is CIDR?
CIDR (Classless Inter-Domain Routing) eliminates fixed class boundaries and uses variable-length prefixes (e.g., /18, /22). It allows flexible allocation of IP addresses and reduces routing table sizes. Notation: 192.168.0.0/20.

---

### Q27. What is the Protocol field in IPv4 header?
The Protocol field (8 bits) identifies the upper-layer protocol to which the packet should be delivered. Common values: TCP = 6, UDP = 17, ICMP = 1.

---

### Q28. What is Split Horizon?
Split Horizon is a technique to prevent routing loops in Distance Vector Routing. Rule: A router does NOT advertise a route back to the neighbor from which it learned that route. This prevents count-to-infinity.

---

### Q29. What is Supernetting?
Supernetting (route aggregation) is the opposite of subnetting — it combines multiple smaller networks into a single larger network by reducing the network prefix. Example: Four /24 networks → one /22 supernet.

---

### Q30. What is the difference between RIP and OSPF?
| Feature | RIP | OSPF |
|---------|-----|------|
| Algorithm | Distance Vector (Bellman-Ford) | Link State (Dijkstra) |
| Metric | Hop count (max 15) | Cost (bandwidth-based) |
| Convergence | Slow | Fast |
| Updates | Periodic (every 30 sec) | Event-driven |
| Network size | Small | Large |

---

---

# 📝 7-MARK QUESTIONS (15)

---

### Q1. Explain Classful IP Addressing with all five classes. ⭐⭐⭐
**Answer:**
1. IP address = 32 bits = Network ID + Host ID
2. Table for all 5 classes:

| Class | First Bits | Range | Default Mask | Networks | Hosts/Network |
|-------|-----------|-------|-------------|----------|---------------|
| A | 0xxxxxxx | 1–126 | 255.0.0.0 | 126 | 16,777,214 |
| B | 10xxxxxx | 128–191 | 255.255.0.0 | 16,384 | 65,534 |
| C | 110xxxxx | 192–223 | 255.255.255.0 | 2,097,152 | 254 |
| D | 1110xxxx | 224–239 | — | Multicast | — |
| E | 1111xxxx | 240–255 | — | Experimental | — |

3. Special addresses: 127.x.x.x (loopback), 0.0.0.0 (default), 255.255.255.255 (broadcast)
4. Diagram showing bit allocation for each class
5. Limitations: Wasteful allocation → need for subnetting/CIDR

---

### Q2. Solve a Subnetting problem. ⭐⭐⭐
**Q: Subnet 192.168.10.0/24 into 8 subnets. Find all subnet addresses, ranges, and broadcasts.**

**Answer:**
```
Need 8 subnets → 2^n = 8 → n = 3 bits borrowed
New mask: /24 + 3 = /27 → 255.255.255.224
Host bits: 32 - 27 = 5 → Hosts/subnet = 2⁵ - 2 = 30
Block size: 256 - 224 = 32

| Subnet # | Network Address    | First Usable    | Last Usable      | Broadcast       |
|----------|-------------------|-----------------|-----------------|-----------------|
| 1        | 192.168.10.0/27   | 192.168.10.1    | 192.168.10.30   | 192.168.10.31   |
| 2        | 192.168.10.32/27  | 192.168.10.33   | 192.168.10.62   | 192.168.10.63   |
| 3        | 192.168.10.64/27  | 192.168.10.65   | 192.168.10.94   | 192.168.10.95   |
| 4        | 192.168.10.96/27  | 192.168.10.97   | 192.168.10.126  | 192.168.10.127  |
| 5        | 192.168.10.128/27 | 192.168.10.129  | 192.168.10.158  | 192.168.10.159  |
| 6        | 192.168.10.160/27 | 192.168.10.161  | 192.168.10.190  | 192.168.10.191  |
| 7        | 192.168.10.192/27 | 192.168.10.193  | 192.168.10.222  | 192.168.10.223  |
| 8        | 192.168.10.224/27 | 192.168.10.225  | 192.168.10.254  | 192.168.10.255  |
```

---

### Q3. Explain Distance Vector Routing algorithm with example. ⭐⭐⭐
**Answer:**
1. Define DVR: Each router shares routing table with neighbors periodically
2. Bellman-Ford equation: D(x,y) = min{C(x,v) + D(v,y)}
3. **Example with 4 routers (A, B, C, D):**
   - Show initial routing tables
   - Exchange tables with neighbors
   - Update using Bellman-Ford
   - Show updated tables after iteration 1, 2
   - Show convergence
4. Problems: Count-to-Infinity, Slow convergence
5. Solutions: Split Horizon, Poison Reverse

---

### Q4. Compare Distance Vector and Link State Routing. ⭐⭐
**Answer:**

| Feature | Distance Vector | Link State |
|---------|----------------|------------|
| Algorithm | Bellman-Ford | Dijkstra |
| Knowledge | Only neighbors | Full topology |
| Shared info | Entire routing table | Link State Packets (LSPs) |
| Sharing with | Direct neighbors only | All routers (flooding) |
| Updates | Periodic | Event-driven |
| Convergence | Slow | Fast |
| Loop problem | Count-to-Infinity | No loops |
| Memory | Low | High (stores topology) |
| CPU | Low | High (runs Dijkstra) |
| Bandwidth | Less (small tables) | More (flooding) |
| Scalability | Small networks | Large networks |
| Protocol example | RIP | OSPF |

---

### Q5. Explain IPv4 Header format with diagram. ⭐⭐
**Answer:**
1. Draw the IPv4 header (20 bytes minimum, 32-bit rows)
2. Explain each field:
   - Version (4b): IPv4=4
   - IHL (4b): Header length in 32-bit words
   - TOS (8b): Type of Service
   - Total Length (16b): Entire packet size
   - Identification (16b): Fragment ID
   - Flags (3b): DF, MF
   - Fragment Offset (13b): Position of fragment
   - TTL (8b): Max hops
   - Protocol (8b): TCP=6, UDP=17, ICMP=1
   - Header Checksum (16b): Error check
   - Source IP (32b), Destination IP (32b)
3. Optional: Options field (variable)

---

### Q6. Differentiate between IPv4 and IPv6. ⭐⭐
**Answer:**

| Feature | IPv4 | IPv6 |
|---------|------|------|
| Address size | 32 bits | 128 bits |
| Address space | ~4.3 billion | ~3.4 × 10³⁸ |
| Notation | Dotted decimal | Hexadecimal colon |
| Header size | 20–60 bytes (variable) | 40 bytes (fixed) |
| Header fields | 12 fields | 8 fields (simplified) |
| Checksum | Present | Removed |
| Fragmentation | Routers + Sender | Sender only |
| Security | IPSec optional | IPSec built-in |
| Broadcasting | Supported | Replaced by Multicast |
| Configuration | Manual/DHCP | Auto-configuration (SLAAC) |
| NAT | Required | Not needed |

---

### Q7. Explain ARP and RARP with working and diagrams. ⭐⭐
**Answer:**
1. **ARP (IP → MAC):**
   - Host A knows B's IP but needs MAC
   - A broadcasts ARP Request: "Who has 192.168.1.5?"
   - B replies with ARP Reply: "My MAC is AA:BB:CC:DD:EE:FF"
   - A caches in ARP table
   - Diagram: A →(broadcast)→ all → B →(unicast reply)→ A
2. **RARP (MAC → IP):**
   - Diskless machine knows its MAC but needs IP
   - Broadcasts RARP Request with its MAC
   - RARP Server replies with IP
   - Diagram showing the process
3. ARP table/cache explanation

---

### Q8. Explain Leaky Bucket and Token Bucket algorithms with diagrams. ⭐⭐
**Answer:**
1. **Leaky Bucket:**
   - Packets enter at variable rate
   - Bucket leaks at constant rate
   - Overflow → packets dropped
   - Smooths bursty traffic into constant output
   - Diagram: Variable input → Bucket → Constant output
2. **Token Bucket:**
   - Tokens added at constant rate
   - Packet needs token to transmit
   - Allows controlled bursts (up to bucket capacity)
   - Diagram: Token source → Bucket → Packets + Tokens → Output
3. Comparison table

---

### Q9. Explain Subnetting and VLSM. When is VLSM preferred? ⭐⭐
**Answer:**
1. **Subnetting:** Divide large network into equal-sized subnets. Same mask for all.
2. **VLSM:** Variable masks → different-sized subnets. More efficient.
3. **When VLSM preferred:** When subnets need different numbers of hosts
4. **VLSM Example:**
   - Network: 192.168.1.0/24
   - Subnet A needs 100 hosts → /25 (126 hosts)
   - Subnet B needs 50 hosts → /26 (62 hosts)
   - Subnet C needs 10 hosts → /28 (14 hosts)
   - Allocate largest first
5. Comparison: Fixed subnetting vs VLSM

---

### Q10. What is Routing? Explain types of routing algorithms. ⭐⭐
**Answer:**
1. Define routing: Process of selecting best path for packets
2. **Classification:**
   - **Static vs Dynamic**
   - **Adaptive vs Non-Adaptive**
   - **Distance Vector vs Link State vs Path Vector**
3. **Distance Vector:** Share table with neighbors, Bellman-Ford, RIP
4. **Link State:** Flood LSPs, Dijkstra, OSPF
5. **Path Vector:** Share full path info, BGP (used in inter-domain)
6. Comparison table

---

### Q11. Explain ICMP protocol. What are its message types? ⭐
**Answer:**
1. Define ICMP: Error reporting & diagnostics at Network Layer
2. Encapsulated in IP datagram
3. **Error Messages:**
   - Destination Unreachable
   - Time Exceeded (TTL=0)
   - Source Quench (congestion)
   - Redirect
   - Parameter Problem
4. **Query Messages:**
   - Echo Request/Reply (ping)
   - Timestamp Request/Reply
   - Address Mask Request/Reply
5. ICMP is NOT used to carry user data
6. Applications: ping, traceroute

---

### Q12. Explain IP packet fragmentation with example. ⭐
**Answer:**
1. Why fragmentation? Packet > MTU of next link
2. Fields used: Identification, Flags (DF, MF), Fragment Offset
3. **Example:** Packet = 4000 bytes, MTU = 1500 bytes
   - Fragment 1: 0–1479 (1480 data + 20 header), MF=1, Offset=0
   - Fragment 2: 1480–2959 (1480 data + 20 header), MF=1, Offset=185
   - Fragment 3: 2960–3979 (1020 data + 20 header), MF=0, Offset=370
   - Offset = byte position / 8
4. Reassembly at destination using Identification + Offset
5. Diagram showing original packet → fragments

---

### Q13. What is Quality of Service (QoS)? Explain its parameters and improvement techniques. ⭐
**Answer:**
1. Define QoS: Overall performance measure of network
2. **Parameters:**
   - Reliability, Delay, Jitter, Bandwidth
3. **Application requirements table:**
   - Email: High reliability, Low delay requirement
   - Video: High bandwidth, Low jitter
   - VoIP: Low delay, Low jitter
4. **Improvement Techniques:**
   - Over-provisioning, Buffering, Scheduling (FIFO, Priority), Traffic Shaping (Leaky/Token Bucket)

---

### Q14. Explain Network Address Translation (NAT). ⭐
**Answer:**
1. Define NAT: Translates private IP ↔ public IP at router
2. Why needed: IPv4 address shortage
3. **Types:**
   - Static NAT: One-to-one mapping
   - Dynamic NAT: Pool of public IPs
   - PAT (Port Address Translation): Many-to-one using port numbers
4. **Working:** Internal host (10.0.0.5) → Router translates to public IP (203.0.113.1) → Internet
5. Diagram showing inside-outside translation
6. Advantages & disadvantages

---

### Q15. Solve: Given IP 172.16.5.130/20, find the Network Address, Broadcast Address, First and Last usable host, and Total hosts. ⭐⭐
**Answer:**
```
IP: 172.16.5.130/20
Mask: 255.255.240.0 (20 network bits)

Third octet: 5 in binary = 00000101
Mask 3rd octet: 240 = 11110000
AND: 00000101 AND 11110000 = 00000000 = 0

Network Address: 172.16.0.0
Block size: 256 - 240 = 16 (in 3rd octet)
Next network: 172.16.16.0

Broadcast: 172.16.15.255
First usable: 172.16.0.1
Last usable: 172.16.15.254
Host bits: 32 - 20 = 12
Total hosts: 2¹² - 2 = 4094
```
