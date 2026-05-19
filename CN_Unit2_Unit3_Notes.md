# 🔥 COMPUTER NETWORKS — UNIT 2 & UNIT 3 MASTER NOTES
### AKTU Exam-Ready | Numerical-Heavy Units

---

# ═══════════════════════════════════════════
# UNIT 2: DATA LINK LAYER
# ═══════════════════════════════════════════

## 2.1 Data Link Layer — Functions
1. **Framing** — Dividing bit stream into frames
2. **Physical Addressing** — Adding MAC address in header
3. **Error Control** — Detect & correct errors (CRC, Hamming)
4. **Flow Control** — Match sender/receiver speed
5. **Access Control** — Determine which device controls the channel (MAC sublayer)

### Two Sublayers:
- **LLC (Logical Link Control)** — Error control, flow control
- **MAC (Media Access Control)** — Multiple access protocols, physical addressing

---

## 2.2 Framing Techniques (2-Mark)

| Method | How it works |
|--------|-------------|
| **Character Count** | Header field specifies number of characters in frame |
| **Byte Stuffing** | Special flag byte (e.g., 01111110) marks start/end; escape bytes added if flag appears in data |
| **Bit Stuffing** | Flag = 01111110; after every 5 consecutive 1s in data, a 0 is inserted |

### Bit Stuffing Example:
- **Data:** 011111110
- **After stuffing:** 0111110110 (0 inserted after five 1s)

---

## 2.3 Error Detection Methods ⭐⭐⭐

### A. Parity Check
- **Single Parity:** Add 1 parity bit to make total 1s even (even parity) or odd (odd parity)
- Can detect **single-bit errors** only
- **Example:** Data = 1011001 → Even parity bit = 0 → Send: 10110010

### B. Two-Dimensional Parity
- Arrange data in matrix → add parity for each row AND column
- Can detect **single, double, and some triple-bit errors**
- Can also **correct single-bit errors** (intersection of failed row & column)

### C. Checksum
1. Divide data into equal segments (usually 16 bits)
2. Add all segments using 1's complement addition
3. Take 1's complement of sum → **Checksum**
4. Receiver adds all segments + checksum → result should be all 1s

### D. CRC (Cyclic Redundancy Check) ⭐⭐⭐ (MUST DO — Numerical)

**Steps for CRC Calculation:**
1. Given: Data (D) and Generator/Divisor (G)
2. Count bits in G → say `n` bits → append `(n-1)` zeros to data
3. Perform **binary division** (XOR) of augmented data by G
4. Remainder = CRC bits (must be n-1 bits)
5. **Transmitted data** = Original data + CRC remainder

**CRC Numerical Example:**
```
Data:        1101011011
Generator:   10011 (5 bits → append 4 zeros)
Augmented:   11010110110000

Perform XOR division:
11010110110000 ÷ 10011

Step-by-step XOR:
11010 ⊕ 10011 = 01001
 10011 → bring down → 10011
 10011 ⊕ 10011 = 00000
  00001 → bring down → 00010
  ... continue until end

Remainder (4 bits): 1110
Transmitted data: 1101011011|1110
```

**At Receiver:**
- Divide received data by same generator
- If remainder = 0 → No error
- If remainder ≠ 0 → Error detected

> [!IMPORTANT]
> **CRC Key Rule:** XOR division — when first bit is 1, XOR with divisor; when first bit is 0, XOR with all zeros (same length as divisor).

---

## 2.4 Hamming Code ⭐⭐⭐ (Error Detection + Correction)

### Step-by-Step Method:

**Step 1:** Find number of parity bits (r) using: **2^r ≥ m + r + 1**
- m = number of data bits

**Step 2:** Place parity bits at positions that are powers of 2 (1, 2, 4, 8, 16...)

**Step 3:** Fill data bits in remaining positions (from left/MSB)

**Step 4:** Calculate each parity bit:
- P1 checks positions: 1,3,5,7,9,11... (binary has 1 in LSB)
- P2 checks positions: 2,3,6,7,10,11... (binary has 1 in 2nd bit)
- P4 checks positions: 4,5,6,7,12,13... (binary has 1 in 3rd bit)
- P8 checks positions: 8,9,10,11,12,13... (binary has 1 in 4th bit)

**Step 5:** Set parity bit = 0 or 1 to make total 1s even (for even parity)

### Hamming Code Example:
**Q: Data = 1011, construct 7-bit even parity Hamming code**

```
m = 4, r = 3 (since 2³=8 ≥ 4+3+1=8 ✓)

Position:  1   2   3   4   5   6   7
Type:      P1  P2  D1  P4  D2  D3  D4
Data fill: P1  P2  1   P4  0   1   1

Calculate parity bits:
P1 → positions 1,3,5,7 → data: ?,1,0,1 → need P1=0 (even: 1+0+1=2, already even)
P2 → positions 2,3,6,7 → data: ?,1,1,1 → need P2=1 (1+1+1=3, add 1 to make 4)
P4 → positions 4,5,6,7 → data: ?,0,1,1 → need P4=0 (0+1+1=2, already even)

Final code: 0 1 1 0 0 1 1
```

### Error Detection with Hamming Code:
**Q: Received code = 1100101 (7-bit). Find and correct error.**

```
Check P1 (pos 1,3,5,7): 1,0,1,1 = 3 ones → ODD → P1=1
Check P2 (pos 2,3,6,7): 1,0,0,1 = 2 ones → EVEN → P2=0
Check P4 (pos 4,5,6,7): 0,1,0,1 = 2 ones → EVEN → P4=0

Error position = P4·P2·P1 = 0·0·1 = 001₂ = position 1
→ but if result = 0, no error

Actual: Read syndrome bits from P4,P2,P1 → write in order: P4 P2 P1
If = 110₂ = 6 → Error at position 6 → flip bit at position 6
```

---

## 2.5 Flow Control Protocols ⭐⭐

### A. Noiseless Channel Protocols:

**1. Simplest Protocol:**
- Unidirectional, no flow/error control
- Sender continuously sends; no ACK needed
- Example: Keyboard to computer

**2. Stop-and-Wait Protocol:**
- Send 1 frame → Wait for ACK → Send next frame
- Simple but **slow** (high waiting time)

### B. Noisy Channel Protocols:

**3. Stop-and-Wait ARQ:**
- Send frame → Start timer → Wait for ACK
- If ACK received → Send next
- If timeout → Retransmit same frame

**4. Go-Back-N ARQ:** ⭐
- **Sender window size = N**, Receiver window = 1
- Can send N frames without ACK
- If one frame is corrupted → **all N frames retransmitted**
- Receiver discards out-of-order frames

**5. Selective Repeat ARQ:** ⭐
- **Sender window = Receiver window = N**
- Only the **lost/corrupted frame** is retransmitted
- Receiver buffers out-of-order frames
- Receiver sends **NACK** for corrupted frames

### Go-Back-N vs Selective Repeat:

| Feature | Go-Back-N | Selective Repeat |
|---------|-----------|-----------------|
| Sender Window | N | N |
| Receiver Window | 1 | N |
| Retransmission | All frames from lost one | Only lost frame |
| Receiver buffer | Not needed | Required |
| Efficiency | Lower | Higher |
| Complexity | Simpler | More complex |

### Stop-and-Wait Efficiency Formula ⭐⭐ (Numerical):
```
η = 1 / (1 + 2a)

where a = Propagation Time / Transmission Time
      Propagation Time = Distance / Propagation Speed
      Transmission Time = Frame Size / Bandwidth

With Fault:
η = 1 / (1 + 2a + Fault_delay/Transmission_Time)

Decrease in efficiency = (η_max - η_fault) / η_max × 100%
```

### Numerical Example (from PYQ 2018-19, 10 marks):
```
Given: Bandwidth = 20 Kbps, Frame = 4500 bits
       Distance = 30000 km, Speed = 2.8 × 10⁸ m/s
       Fault delay = 0.25 sec

Propagation Time = (30000 × 10³) / (2.8 × 10⁸) = 0.107 sec
Transmission Time = 4500 / (20 × 10³) = 0.225 sec
a = 0.107 / 0.225 = 0.47

Max Efficiency = 1/(1 + 2×0.47) = 1/1.94 = 51.5%

With fault: η = 1/(1 + 2(0.47) + 0.25/0.225) = 1/(1 + 0.94 + 1.11) = 32.7%
Decrease = (51.5 - 32.7)/51.5 × 100 = 36.5%
```

---

## 2.6 Multiple Access Protocols ⭐⭐ (7-Mark)

### Classification (DRAW THIS FLOWCHART):
```
Multiple Access Protocols
├── Random Access
│   ├── ALOHA (Pure & Slotted)
│   ├── CSMA
│   ├── CSMA/CD (Collision Detection)
│   └── CSMA/CA (Collision Avoidance)
├── Controlled Access
│   ├── Reservation
│   ├── Polling
│   └── Token Passing
└── Channelization
    ├── FDMA
    ├── TDMA
    └── CDMA
```

### A. ALOHA:

| Feature | Pure ALOHA | Slotted ALOHA |
|---------|-----------|---------------|
| Transmission | Anytime | Only at slot beginning |
| Collision type | Partial + Total | Total only |
| Vulnerable time | 2 × Tfr | Tfr |
| Max efficiency | **18.4%** | **36.8%** |

### B. CSMA (Carrier Sense Multiple Access):
- **Listen before transmitting**
- **1-Persistent:** Continuously sense; transmit immediately when idle
- **Non-Persistent:** If busy → wait random time → check again
- **P-Persistent:** If idle → transmit with probability P; wait with probability (1-P)

### C. CSMA/CD (used in Ethernet):
- Listen + Detect collision **during** transmission
- If collision → send **Jam Signal** → wait random backoff time → retry

### D. CSMA/CA (used in WiFi):
- **Avoid** collision using RTS/CTS mechanism
- Sender → RTS → Access Point → CTS → Data → ACK
- Uses **IFS (Inter-Frame Spacing)** wait time

### E. Token Passing:
- Stations in ring topology; token circulates
- Station with token can transmit
- After transmission → pass token to next station

### F. Polling:
- Primary (controller) polls each secondary station
- Station sends data or NAK (negative acknowledgment)

---

## 2.7 LAN Standards (2-Mark)

### IEEE 802.3 (Ethernet):
- Uses CSMA/CD, Bus/Star topology
- Frame: Preamble(7B) + SFD(1B) + DA(6B) + SA(6B) + Length(2B) + Data(46-1500B) + FCS(4B)
- **Max frame = 1518 bytes**

### IEEE 802.5 (Token Ring):
- Uses Token Passing, Ring topology
- Uses Differential Manchester Encoding

---

# ═══════════════════════════════════════════
# UNIT 3: NETWORK LAYER
# ═══════════════════════════════════════════

## 3.1 Network Layer — Functions
1. **Logical Addressing** (IP addressing)
2. **Routing** (finding best path)
3. **Packetizing** (encapsulation into packets)
4. **Fragmentation & Reassembly**
5. **Error Handling & Diagnostics** (ICMP)

---

## 3.2 IP Addressing — Classful ⭐⭐⭐

| Class | First Octet Range | Default Mask | Network/Host | Max Networks | Max Hosts |
|-------|-------------------|-------------|-------------|-------------|-----------|
| **A** | 1 – 126 | 255.0.0.0 (/8) | N.H.H.H | 126 | 16,777,214 |
| **B** | 128 – 191 | 255.255.0.0 (/16) | N.N.H.H | 16,384 | 65,534 |
| **C** | 192 – 223 | 255.255.255.0 (/24) | N.N.N.H | 2,097,152 | 254 |
| **D** | 224 – 239 | — | Multicast | — | — |
| **E** | 240 – 255 | — | Reserved/Experimental | — | — |

> **Mnemonic for ranges:** "**1**-126 **A**, 1**28**-191 **B**, 1**92**-223 **C**"

### Special Addresses:
- **127.0.0.1** — Loopback (localhost)
- **0.0.0.0** — Default route
- **255.255.255.255** — Limited broadcast
- Host bits all 0 → **Network Address**
- Host bits all 1 → **Broadcast Address**

---

## 3.3 Subnetting ⭐⭐⭐ (MOST IMPORTANT NUMERICAL)

### Key Formulas:
```
Number of subnets = 2^n  (n = subnet bits borrowed)
Hosts per subnet = 2^h - 2  (h = remaining host bits; -2 for network & broadcast)
Block size = 256 - subnet mask value (in relevant octet)
```

### Subnetting Example:
**Q: Subnet 192.168.1.0/24 into 4 subnets. Find subnet addresses, ranges, broadcasts.**

```
Need 4 subnets → 2^n = 4 → n = 2 bits borrowed
New mask: /24 + 2 = /26 → 255.255.255.192
Host bits remaining: 32 - 26 = 6 → Hosts per subnet = 2⁶ - 2 = 62
Block size: 256 - 192 = 64

Subnet 1: 192.168.1.0/26    | Range: .1 to .62    | Broadcast: .63
Subnet 2: 192.168.1.64/26   | Range: .65 to .126  | Broadcast: .127
Subnet 3: 192.168.1.128/26  | Range: .129 to .190 | Broadcast: .191
Subnet 4: 192.168.1.192/26  | Range: .193 to .254 | Broadcast: .255
```

### VLSM (Variable Length Subnet Masking):
- Different subnets can have **different mask lengths**
- Allocate largest subnet first → then smaller ones
- Avoids wasting IP addresses

---

## 3.4 IPv4 Header Format (2-Mark / 7-Mark)

| Field | Size | Purpose |
|-------|------|---------|
| Version | 4 bits | IPv4 = 4 |
| IHL (Header Length) | 4 bits | Header length in 32-bit words (min 5 = 20 bytes) |
| TOS | 8 bits | Type of Service / QoS |
| Total Length | 16 bits | Total packet size (header + data) |
| Identification | 16 bits | Fragment identification |
| Flags | 3 bits | DF (Don't Fragment), MF (More Fragments) |
| Fragment Offset | 13 bits | Position of fragment in original datagram |
| TTL | 8 bits | Max hops before discard |
| Protocol | 8 bits | Upper layer protocol (TCP=6, UDP=17, ICMP=1) |
| Header Checksum | 16 bits | Error checking for header |
| Source IP | 32 bits | Sender's IP |
| Destination IP | 32 bits | Receiver's IP |

---

## 3.5 Routing Algorithms ⭐⭐

### A. Distance Vector Routing (DVR) — Bellman-Ford ⭐⭐

**How it works:**
1. Each router maintains a **routing table** with: (Destination, Cost, Next Hop)
2. Periodically, each router **shares its table** with direct neighbors
3. On receiving neighbor's table → update own table using:
   **D(x,y) = min { C(x,v) + D(v,y) }** for all neighbors v
4. Process repeats until **convergence** (no more changes)

**Problems:**
- **Count to Infinity** — Bad news travels slowly
- **Solution:** Split Horizon, Poison Reverse

**DVR Table Example:**
```
Router A's initial table:     After receiving B's table:
Dest | Cost | Via             Dest | Cost | Via
B    |  1   | B               B   |  1   | B
C    |  ∞   | -               C   |  3   | B  (1+2, via B)
D    |  4   | D               D   |  4   | D
```

### B. Link State Routing (Dijkstra's Algorithm):
1. Each router discovers neighbors and **cost to each**
2. Builds **Link State Packet (LSP)** and floods it to all routers
3. Each router builds **complete network topology map**
4. Runs **Dijkstra's shortest path** algorithm
5. Builds routing table from shortest path tree

### DVR vs Link State:

| Feature | Distance Vector | Link State |
|---------|----------------|------------|
| Algorithm | Bellman-Ford | Dijkstra |
| Knowledge | Neighbors only | Full topology |
| Updates | Periodic, full table | Event-driven, LSPs |
| Convergence | Slow | Fast |
| Bandwidth | Less | More (flooding) |
| Example | RIP | OSPF |
| Loop problem | Count to infinity | No loops |

---

## 3.6 ARP, RARP, ICMP (2-Mark)

| Protocol | Full Form | Function |
|----------|----------|----------|
| **ARP** | Address Resolution Protocol | IP address → MAC address |
| **RARP** | Reverse ARP | MAC address → IP address |
| **ICMP** | Internet Control Message Protocol | Error reporting & diagnostics (ping, traceroute) |

### ARP Process:
1. Host A wants to send to Host B (knows IP, needs MAC)
2. A broadcasts **ARP Request** ("Who has IP 192.168.1.5?")
3. Host B responds with **ARP Reply** containing its MAC address
4. A caches the MAC in its **ARP Table**

---

## 3.7 IPv4 vs IPv6 (2-Mark)

| Feature | IPv4 | IPv6 |
|---------|------|------|
| Address Size | 32 bits | 128 bits |
| Notation | Dotted decimal (192.168.1.1) | Hexadecimal colon (2001:0db8::1) |
| Header Size | 20-60 bytes | 40 bytes (fixed) |
| Address Space | ~4.3 billion | ~3.4 × 10³⁸ |
| Checksum | Yes | No (removed for speed) |
| Fragmentation | Router + Sender | Sender only |
| Security | Optional (IPSec) | Built-in IPSec |

---

## 3.8 Leaky Bucket & Token Bucket (Traffic Shaping) ⭐

### Leaky Bucket:
- Packets enter bucket at variable rate
- Bucket leaks (transmits) at **constant rate**
- If bucket full → packets dropped
- **Smooths bursty traffic** into uniform output

### Token Bucket:
- Tokens added at constant rate
- Each packet needs one token to transmit
- If tokens available → transmit immediately
- If no tokens → wait
- **Allows controlled bursts** (up to bucket size)

| Feature | Leaky Bucket | Token Bucket |
|---------|-------------|-------------|
| Output rate | Constant | Variable (allows bursts) |
| Bursty traffic | Not allowed | Allowed (limited) |
| Flexibility | Rigid | More flexible |

---

> [!TIP]
> **UNIT 2 & 3 EXAM STRATEGY:** For CRC/Hamming numericals, write every XOR step clearly — examiners give marks for working. For subnetting, always show: subnet mask, block size, network address, first usable, last usable, broadcast address in a clean table format.
