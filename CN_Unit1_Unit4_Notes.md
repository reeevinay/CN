# 🔥 COMPUTER NETWORKS — UNIT 1 & UNIT 4 MASTER NOTES
### AKTU Exam-Ready | Optimized for 7-Mark & 2-Mark Answers

---

# ═══════════════════════════════════════════
# UNIT 1: INTRODUCTION TO COMPUTER NETWORKS
# ═══════════════════════════════════════════

## 1.1 Computer Network — Definition
> A computer network is a collection of interconnected devices (computers, servers, routers) that communicate and share resources using defined protocols over transmission media.

**Goals of Networking:** Resource Sharing, Reliability, Cost Reduction, Communication Medium, Scalability.

---

## 1.2 Types of Networks (2-Mark Favorite)

| Type | Range | Example | Speed |
|------|-------|---------|-------|
| **PAN** | ~10m | Bluetooth, USB | Low |
| **LAN** | Building/Campus | Ethernet, WiFi | 10Mbps–10Gbps |
| **MAN** | City | Cable TV Network | Moderate |
| **WAN** | Country/Globe | Internet | Varies |

---

## 1.3 Network Topologies ⭐ (7-Mark + Diagram)

### 🔸 Bus Topology
- All devices share single backbone cable
- **Advantage:** Simple, cheap installation
- **Disadvantage:** Single point of failure; if backbone breaks, entire network fails

### 🔸 Star Topology
- All devices connect to a central hub/switch
- **Advantage:** Easy to add/remove devices; failure of one device doesn't affect others
- **Disadvantage:** If central hub fails → entire network down

### 🔸 Ring Topology
- Each device connected to exactly two neighbors (circular)
- Data travels in one direction (unidirectional)
- **Advantage:** Equal access, no collision
- **Disadvantage:** Single device failure breaks the ring

### 🔸 Mesh Topology
- Every device connected to every other device
- **Formula:** Links = n(n-1)/2 (for full mesh)
- **Advantage:** Highly reliable, fault-tolerant
- **Disadvantage:** Expensive, complex wiring

### 🔸 Tree Topology
- Hierarchical — combination of Star + Bus
- Root node → branches → leaf nodes

### 🔸 Hybrid Topology
- Combination of two or more topologies

> **Mnemonic: "B-S-R-M-T-H"** → **B**us **S**tar **R**ing **M**esh **T**ree **H**ybrid

---

## 1.4 OSI Reference Model ⭐⭐⭐ (Most Asked — 7 Marks)

> **Mnemonic (Top→Down): "All People Seem To Need Data Processing"**
> **Mnemonic (Bottom→Up): "Please Do Not Throw Sausage Pizza Away"**

| # | Layer | PDU | Function | Devices | Protocols |
|---|-------|-----|----------|---------|-----------|
| 7 | **Application** | Data | User interface, network services | — | HTTP, FTP, SMTP, DNS |
| 6 | **Presentation** | Data | Encryption, Compression, Translation | — | SSL, JPEG, MPEG |
| 5 | **Session** | Data | Session management, synchronization | — | NetBIOS, RPC |
| 4 | **Transport** | Segment | End-to-end delivery, error recovery | — | TCP, UDP |
| 3 | **Network** | Packet | Routing, logical addressing | Router | IP, ICMP, ARP |
| 2 | **Data Link** | Frame | Framing, MAC addressing, error detect | Switch, Bridge | Ethernet, PPP |
| 1 | **Physical** | Bits | Physical transmission of raw bits | Hub, Repeater, Cable | RS-232, RJ-45 |

### Key Points for Exam:
- OSI has **7 layers** developed by **ISO**
- Each layer communicates with **peer layer** on receiving end
- Data encapsulation happens **top to bottom** at sender
- Data decapsulation happens **bottom to top** at receiver

---

## 1.5 TCP/IP Model ⭐⭐ (Always compared with OSI)

| # | TCP/IP Layer | Equivalent OSI Layers | Protocols |
|---|-------------|----------------------|-----------|
| 4 | **Application** | Application + Presentation + Session | HTTP, FTP, SMTP, DNS, Telnet |
| 3 | **Transport** | Transport | TCP, UDP |
| 2 | **Internet** | Network | IP, ICMP, ARP, RARP |
| 1 | **Network Access** | Data Link + Physical | Ethernet, WiFi, PPP |

### OSI vs TCP/IP — Comparison Table (7-Mark Standard)

| Feature | OSI Model | TCP/IP Model |
|---------|-----------|--------------|
| Layers | 7 | 4 |
| Developed by | ISO | DoD (DARPA) |
| Approach | Theoretical | Practical |
| Protocol dependent | No (generic) | Yes (protocol-based) |
| Session & Presentation | Separate layers | Merged in Application |
| Reliability | Conceptual reference | Actually implemented |
| Header size | Variable | Min 20 bytes (TCP) |

---

## 1.6 Network Devices (2-Mark / Short Note)

| Device | Layer | Function |
|--------|-------|----------|
| **Hub** | Physical (L1) | Broadcasts data to all ports; no intelligence |
| **Repeater** | Physical (L1) | Amplifies/regenerates signal |
| **Switch** | Data Link (L2) | Forwards frames using MAC address table |
| **Bridge** | Data Link (L2) | Connects two LANs; filters by MAC |
| **Router** | Network (L3) | Routes packets using IP address; connects different networks |
| **Gateway** | All Layers | Protocol converter between different network architectures |
| **Modem** | Physical (L1) | Modulation-Demodulation; converts digital↔analog |

---

## 1.7 Switching Techniques (7-Mark)

### 🔸 Circuit Switching
- Dedicated communication path established before data transfer
- Path remains reserved for entire duration
- **Example:** Telephone system
- **Phases:** Connection Setup → Data Transfer → Connection Release
- **Advantage:** Guaranteed bandwidth, no delay during transfer
- **Disadvantage:** Wasteful if channel is idle

### 🔸 Packet Switching
- Data broken into packets; each routed independently
- Two types:
  - **Datagram:** Each packet routed independently (connectionless)
  - **Virtual Circuit:** Path established first, then all packets follow same path (connection-oriented)
- **Advantage:** Efficient bandwidth usage
- **Disadvantage:** Variable delay, packets may arrive out of order

### 🔸 Message Switching
- Entire message stored at each intermediate node (store-and-forward)
- **Advantage:** No dedicated path needed
- **Disadvantage:** High delay, needs large storage

---

## 1.8 Multiplexing (2-Mark)

| Type | Method |
|------|--------|
| **FDM** (Frequency Division) | Bandwidth divided by frequency bands |
| **TDM** (Time Division) | Bandwidth divided by time slots |
| **WDM** (Wavelength Division) | Used in optical fiber; different wavelengths |
| **CDM** (Code Division) | Each user assigned unique code |

---

# ═══════════════════════════════════════════
# UNIT 4: TRANSPORT LAYER
# ═══════════════════════════════════════════

## 4.1 Transport Layer — Functions
1. **Segmentation & Reassembly** — Breaks data into segments
2. **End-to-End Delivery** — Source to destination process delivery
3. **Connection Control** — Connection-oriented (TCP) or connectionless (UDP)
4. **Flow Control** — Prevents sender from overwhelming receiver
5. **Error Control** — Ensures reliable delivery
6. **Multiplexing/Demultiplexing** — Multiple apps share single network connection

---

## 4.2 TCP vs UDP ⭐⭐⭐ (Most Repeated — 7 Marks)

| Feature | TCP | UDP |
|---------|-----|-----|
| Full Form | Transmission Control Protocol | User Datagram Protocol |
| Connection | Connection-oriented | Connectionless |
| Reliability | Reliable (ACK-based) | Unreliable (no ACK) |
| Ordering | Guaranteed order | No order guarantee |
| Speed | Slower (overhead) | Faster (minimal overhead) |
| Header Size | **20 bytes** (min) | **8 bytes** (fixed) |
| Flow Control | Yes (sliding window) | No |
| Error Control | Yes | Optional (checksum) |
| Congestion Control | Yes | No |
| Broadcasting | Not supported | Supported |
| Examples | HTTP, FTP, SMTP, Telnet | DNS, DHCP, VoIP, Video Streaming |
| PDU Name | Segment | Datagram |

---

## 4.3 TCP Header Format ⭐⭐⭐ (Numerical + Diagram — 7 Marks)

```
 0                   1                   2                   3
 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|         Source Port (16)      |      Destination Port (16)    |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                    Sequence Number (32)                        |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                 Acknowledgment Number (32)                     |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
| HLEN |Reserv|U|A|P|R|S|F|         Window Size (16)           |
| (4)  | (6)  |R|C|S|S|Y|I|                                    |
|      |      |G|K|H|T|N|N|                                    |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|        Checksum (16)          |      Urgent Pointer (16)      |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                    Options (variable)                          |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
```

### TCP Header Fields — Quick Reference:
| Field | Size | Purpose |
|-------|------|---------|
| Source Port | 16 bits | Sender's port number |
| Destination Port | 16 bits | Receiver's port number |
| Sequence Number | 32 bits | Byte number of first data byte |
| ACK Number | 32 bits | Next expected byte number |
| HLEN | 4 bits | Header length (in 32-bit words) |
| Reserved | 6 bits | Future use (set to 0) |
| Flags (URG,ACK,PSH,RST,SYN,FIN) | 6 bits | Control bits |
| Window Size | 16 bits | Receiver's buffer capacity |
| Checksum | 16 bits | Error detection |
| Urgent Pointer | 16 bits | Points to urgent data |

> **Total Minimum Header = 20 bytes (without options)**

### TCP Header Numerical Pattern:
**Q:** Given TCP header in hex, find source port, dest port, sequence number, ACK, HLEN.
**Method:** Convert hex to binary/decimal. First 16 bits = Source Port, Next 16 = Dest Port, Next 32 = Seq No., Next 32 = ACK No., Next 4 bits = HLEN.

---

## 4.4 UDP Header Format ⭐⭐

```
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|         Source Port (16)      |      Destination Port (16)    |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|         Length (16)            |         Checksum (16)         |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
```

> **Total Header = 8 bytes (fixed)**

---

## 4.5 Three-Way Handshake ⭐⭐⭐ (Draw Diagram!)

```
   Client                         Server
     |                               |
     |-------- SYN (seq=x) -------->|   Step 1: Client sends SYN
     |                               |
     |<--- SYN+ACK (seq=y,ack=x+1)--|   Step 2: Server sends SYN+ACK
     |                               |
     |-------- ACK (ack=y+1) ------>|   Step 3: Client sends ACK
     |                               |
     |===== CONNECTION ESTABLISHED ==|
```

### Connection Termination (Four-Way):
```
   Client                         Server
     |-------- FIN --------------->|   Step 1
     |<------- ACK ----------------|   Step 2
     |<------- FIN ----------------|   Step 3
     |-------- ACK --------------->|   Step 4
     |===== CONNECTION CLOSED =====|
```

---

## 4.6 Flow Control & Retransmission

### Flow Control:
- Technique to prevent sender from overwhelming receiver
- **Receiver advertises window size** → sender adjusts transmission rate
- Uses **Sliding Window Protocol**

### Retransmission:
- If sender does NOT receive ACK within timeout → retransmit the segment
- Lost/corrupted segments are buffered at receiver
- **Example:** Client sends seq 101-200, then 201-300. If 301-500 is lost, server sends ACK 301 again. Client retransmits 301-500. Server then combines buffer and sends ACK 601.

---

## 4.7 TCP Congestion Control ⭐⭐⭐ (7-Mark with Graph)

### Three Phases:

#### Phase 1: Slow Start
- Start with congestion window (cwnd) = 1 MSS
- **Exponential increase**: cwnd doubles each RTT (1→2→4→8→16...)
- Continues until **threshold (ssthresh)** is reached

#### Phase 2: Congestion Avoidance
- After reaching threshold → **Linear increase** (cwnd += 1 per RTT)
- Continues until congestion is detected (packet loss)

#### Phase 3: Congestion Detection
- **Case A — Timeout occurs:**
  - ssthresh = cwnd/2
  - cwnd = 1 MSS
  - Go back to **Slow Start Phase**
  
- **Case B — 3 Duplicate ACKs:**
  - ssthresh = cwnd/2
  - cwnd = ssthresh
  - Go back to **Congestion Avoidance Phase** (Fast Recovery)

### Graph Description (MUST DRAW):
```
cwnd ↑
     |        ___________  ← Max Capacity (Congestion Detected)
     |       /           \
     |      / Cong.Avoid  \
     |     / (linear +1)   \
     |----/← Threshold      \
     |   / Slow Start        \→ Back to Slow Start (timeout)
     |  / (exponential)       \  OR Cong. Avoidance (3 dup ACK)
     | /                       \
     |/________________________\________→ Time
```

---

## 4.8 Quality of Service (QoS)

| Parameter | Definition |
|-----------|-----------|
| **Reliability** | Guarantee of packet delivery without loss |
| **Delay** | Time taken from source to destination |
| **Jitter** | Variation in packet delay |
| **Bandwidth** | Number of bits sent per second |

### QoS Improvement Techniques:
1. **Over-provisioning** — Increase router capacity, buffer, bandwidth
2. **Buffering** — Store data at receiver before delivery (smooths jitter)
3. **Scheduling** — FIFO, Priority Queuing
4. **Traffic Shaping** — Leaky Bucket & Token Bucket algorithms

---

## 4.9 Multiplexing & Demultiplexing (Transport Layer)

- **Multiplexing (Sender side):** Collecting data from multiple application processes → adding headers → transmitting as single stream
- **Demultiplexing (Receiver side):** Receiving segments → delivering to correct application process using port numbers

### Types:
- **FDM** — Frequency-based division
- **TDM** — Time-based division  
- **CDM** — Code-based division

---

> [!TIP]
> **UNIT 4 EXAM STRATEGY:** Always draw the TCP header diagram, three-way handshake, and congestion control graph. These diagrams alone can earn you 3-4 marks in a 7-mark question even if theory is incomplete.
