# 🚨 2024-25 PAPER ANALYSIS + UPDATED EXAM STRATEGY
## BCS603 — Computer Networks | Latest Paper Breakdown

---

# ═══════════════════════════════════════════
# PAPER STRUCTURE (2024-25)
# ═══════════════════════════════════════════

| Section | Format | Marks |
|---------|--------|-------|
| **Section A** | 7 compulsory short questions | 2 × 7 = **14** |
| **Section B** | Attempt 3 out of 5 | 7 × 3 = **21** |
| **Section C** | 5 questions (attempt 1 part each) | 7 × 5 = **35** |
| **Total** | | **70 marks** |

---

# ═══════════════════════════════════════════
# 🔴 NEW TOPICS SPOTTED (Not in Previous Papers!)
# ═══════════════════════════════════════════

> [!CAUTION]
> These topics appeared for the FIRST TIME in 2024-25. HIGH chance of repeat or variation tomorrow!

| # | NEW Topic | Section | Marks | Unit |
|---|-----------|---------|-------|------|
| 1 | **Signal Attenuation (dB calculation)** | A (Q1b) | 2 | 1 |
| 2 | **RPC Stub mechanism** | A (Q1g) | 2 | 5 |
| 3 | **Slotted ALOHA numerical** (channel load + throughput from idle%) | C (Q3a) | 7 | 2 |
| 4 | **Total Delay calculation** with multiple routers (processing + queuing) | C (Q3b) | 7 | 2 |
| 5 | **IPv6 Multiple Headers** concept | C (Q5a) | 7 | 3 |
| 6 | **VPN (Virtual Private Network)** | C (Q5b) | ~2 | 3 |
| 7 | **Silly Window Syndrome** + Nagle's + Clark's algorithm | C (Q6a) | 7 | 4 |
| 8 | **SMTP handling of multimedia** (MIME) | C (Q7a) | 7 | 5 |

---

# ═══════════════════════════════════════════
# FULL QUESTION-BY-QUESTION ANALYSIS + MODEL ANSWERS
# ═══════════════════════════════════════════

---

## SECTION A — All Compulsory (2 marks each)

---

### Q1a. Determine the number of links for a fully connected mesh with 10 nodes.
**Answer:**
```
Formula: Links = n(n-1)/2
n = 10
Links = 10 × 9 / 2 = 45 links
```
✅ Already covered in our notes.

---

### Q1b. 🔴 NEW — Signal with 2W power, attenuation -3 dB. Find received power.
**Answer:**
```
Attenuation in dB = 10 × log₁₀(P_out / P_in)
-3 = 10 × log₁₀(P_out / 2)
log₁₀(P_out / 2) = -0.3
P_out / 2 = 10^(-0.3) = 0.5
P_out = 2 × 0.5 = 1W

Received Power = 1 Watt
```
**Key Formula:** -3 dB always means **half the power**. +3 dB means double.

---

### Q1c. When are contention-based MAC protocols suitable?
**Answer:**
Contention-based (Random Access) MAC protocols are suitable when:
1. Number of stations is large and traffic is **bursty/unpredictable**
2. Stations transmit **infrequently** (low traffic load)
3. Centralized control is not feasible
4. Examples: ALOHA, CSMA/CD (Ethernet), CSMA/CA (WiFi)

---

### Q1d. Illustrate piggybacking.
**Answer:**
Piggybacking is a technique where the **acknowledgment (ACK) is attached to the next outgoing data frame** instead of sending a separate ACK. This improves efficiency by reducing the number of frames on the network.
```
Without Piggybacking:          With Piggybacking:
A → Data → B                  A → Data → B
A ← ACK  ← B                  A ← Data+ACK ← B (ACK embedded in data frame)
A → Data → B                  A → Data+ACK → B
A ← ACK  ← B
```

---

### Q1e. List functions of all OSI layers with diagram.
**Answer:** ✅ Fully covered in Unit 1 notes (OSI table + mnemonic).

---

### Q1f. List policies for congestion control.
**Answer:**
**Open Loop (Prevention):**
1. Retransmission Policy
2. Window Policy
3. ACK Policy
4. Discarding Policy
5. Admission Policy

**Closed Loop (Detection + Removal):**
1. Backpressure
2. Choke Packet
3. Implicit Signaling
4. Explicit Signaling
5. ECN (Explicit Congestion Notification)

---

### Q1g. 🔴 NEW — Role of Stub in RPC.
**Answer:**
In Remote Procedure Call (RPC), a **stub** acts as a proxy/representative:
- **Client Stub:** Marshals (packs) the procedure parameters into a message, sends it to the server, and unmarshals the returned result.
- **Server Stub:** Receives the message, unmarshals the parameters, calls the actual procedure on the server, marshals the result, and sends it back.
- Stubs make the remote call appear **local** to the programmer.

---

## SECTION B — Attempt any 3 of 5 (7 marks each)

---

### Q2a. CRC Numerical — Polynomial form ⭐⭐⭐
**Data:** x⁸+x⁶+x³+x²+x+1 = **101001111**
**Generator:** x⁴+x²+x+1 = **10111**

**Answer:**
```
Data bits:     101001111
Generator:     10111 (5 bits → append 4 zeros)
Augmented:     1010011110000

Perform XOR division:
10100 ÷ 10111 = 
10100
⊕10111
------
00011  → bring down → 00111 → 01111 → 11111
11111
⊕10111
------
01000 → bring down → 10001
10001
⊕10111
------
00110 → bring down → 01100
01100
⊕00000  (first bit is 0, XOR with 0s)
------
01100 → bring down → 11000
11000
⊕10111
------
01111

Remainder = 1111 (4 bits)
Transmitted codeword = 101001111|1111 = 1010011111111

Verification (3rd bit inverted):
Original:  1010011111111
Corrupted: 1000011111111 (3rd bit flipped)
Divide by 10111 → remainder ≠ 0 → ERROR DETECTED ✓
```

---

### Q2b. Subnetting: 192.168.10.0/24 into 4 subnets ⭐⭐⭐
**Answer:**
```
Need 4 subnets → 2^n = 4 → n = 2 bits borrowed
New mask: /24 + 2 = /26 → 255.255.255.192
Host bits: 32 - 26 = 6 → Hosts/subnet = 2⁶ - 2 = 62
Block size: 256 - 192 = 64

| Subnet | Network Address     | Range                      | Broadcast       |
|--------|--------------------|-----------------------------|-----------------|
| 1      | 192.168.10.0/26    | 192.168.10.1 – .62          | 192.168.10.63   |
| 2      | 192.168.10.64/26   | 192.168.10.65 – .126        | 192.168.10.127  |
| 3      | 192.168.10.128/26  | 192.168.10.129 – .190       | 192.168.10.191  |
| 4      | 192.168.10.192/26  | 192.168.10.193 – .254       | 192.168.10.255  |
```
✅ Already in our notes (exact same question pattern).

---

### Q2c. Leaky Bucket + Token Bucket ⭐⭐
✅ Already covered in Unit 3 notes.

---

### Q2d. RSA Algorithm with example ⭐⭐⭐
✅ Already covered in Unit 5 notes with multiple examples.

---

### Q2e. SNMP + DNS + Data Compression
✅ Already covered in Unit 5 notes.

---

## SECTION C — Attempt 1 part from each question (7 marks each)

---

### Q3a. 🔴 NEW — Slotted ALOHA Numerical ⭐⭐⭐

**Q:** 10% slots idle. Find channel load and throughput.

**Answer:**
```
In Slotted ALOHA:
Probability of idle slot = e^(-G)    (where G = channel load)
Throughput S = G × e^(-G)

Given: 10% idle → e^(-G) = 0.10
→ -G = ln(0.10) = -2.302
→ G = 2.302 (channel load)

Throughput S = G × e^(-G) = 2.302 × 0.10 = 0.2302
→ Throughput = 23.02%
```

**Key Formulas to memorize:**
- Idle slot probability: **P(idle) = e^(-G)**
- Throughput: **S = G × e^(-G)**
- Max throughput (at G=1): S = 1/e = 36.8%

---

### Q3b. 🔴 NEW — Total Delay Calculation with Routers ⭐⭐⭐

**Q:** 4 MB frame, 1000 km, 2 Mbps, speed = 2×10⁸ m/s, 5 routers (1 μs processing + 2 μs queuing each)

**Answer:**
```
Transmission Delay = Frame size / Bandwidth
= (4 × 10⁶ × 8 bits) / (2 × 10⁶ bps)
= 32,000,000 / 2,000,000 = 16 seconds

Propagation Delay = Distance / Speed
= (1000 × 10³ m) / (2 × 10⁸ m/s)
= 10⁶ / (2 × 10⁸) = 0.005 seconds = 5 ms

Processing Delay = 5 routers × 1 μs = 5 μs = 0.000005 s
Queuing Delay = 5 routers × 2 μs = 10 μs = 0.00001 s

Total Delay = Transmission + Propagation + Processing + Queuing
= 16 + 0.005 + 0.000005 + 0.00001
= 16.005015 seconds ≈ 16.005 seconds
```

**Key Formula:** Total Delay = T_trans + T_prop + T_proc + T_queue

---

### Q4a/b. DVR with Count-to-Infinity + DVR Table Calculation ⭐⭐⭐

**Q4b — DVR Table for Router C:**
```
Vectors received:
From B: (5, 0, 8, 12, 6, 2)    → destinations A,B,C,D,E,F
From D: (16, 12, 6, 0, 9, 10)
From E: (7, 6, 3, 9, 0, 4)

Measured delays: C→B = 6, C→D = 3, C→E = 5

For each destination, compute min cost:
Dest A: min(6+5, 3+16, 5+7) = min(11, 19, 12) = 11 via B
Dest B: min(6+0, 3+12, 5+6) = min(6, 15, 11) = 6 via B
Dest C: 0 (self)
Dest D: min(6+12, 3+0, 5+9) = min(18, 3, 14) = 3 via D
Dest E: min(6+6, 3+9, 5+0) = min(12, 12, 5) = 5 via E
Dest F: min(6+2, 3+10, 5+4) = min(8, 13, 9) = 8 via B

Router C's New Table:
| Dest | Delay | Via |
|------|-------|-----|
| A    | 11    | B   |
| B    | 6     | B   |
| C    | 0     | -   |
| D    | 3     | D   |
| E    | 5     | E   |
| F    | 8     | B   |
```

---

### Q5a. 🔴 NEW — IPv6 Features + Multiple Headers ⭐⭐

**Answer:**
1. **New Features in IPv6 over IPv4:**
   - 128-bit addresses (vs 32-bit)
   - Simplified header (8 fields vs 12)
   - No checksum (removed for speed)
   - Built-in IPSec security
   - Auto-configuration (SLAAC)
   - No NAT needed
   - No broadcasting (replaced by multicast + anycast)
   - Flow labeling for QoS

2. **Multiple Headers (Extension Headers):**
   - IPv6 uses a **base header (40 bytes)** + optional **extension headers**
   - Each header has a "Next Header" field pointing to the next one
   - Chain: Base Header → Hop-by-Hop → Routing → Fragment → Authentication → ESP → Destination
   - **Purpose:** Modular design; routers only process headers they need → faster forwarding
   - Only Hop-by-Hop is processed by every router; others processed at destination

---

### Q5b. 🔴 NEW (Partial) — RARP + DHCP + VPN

**VPN (Virtual Private Network):**
- Creates a secure, encrypted tunnel over a public network (Internet)
- Uses **tunneling protocols** (IPSec, L2TP, PPTP, SSL/TLS)
- Data is encrypted before entering tunnel, decrypted at exit
- Provides: Confidentiality, Integrity, Authentication
- Types: Remote Access VPN, Site-to-Site VPN
- Use case: Employees accessing company network remotely

---

### Q6a. 🔴 NEW — Silly Window Syndrome ⭐⭐⭐

**Answer:**
1. **Problem:** When sender sends very small segments (1 byte) or receiver advertises tiny window → extremely inefficient. Header overhead (40 bytes) for 1 byte data = 97.5% waste!

2. **Sender-side Solution — Nagle's Algorithm:**
   - If data < MSS AND there are unacknowledged segments → **buffer the data**
   - Send only when: (a) MSS worth of data collected, OR (b) ACK for previous segment arrives
   - Prevents sending many tiny segments

3. **Receiver-side Solution — Clark's Solution:**
   - Don't advertise small windows
   - Announce window = 0 until buffer has space for either:
     - **MSS** bytes, OR
     - **Half the buffer** is empty
   - Also called **Delayed ACK** — wait before sending ACK to accumulate buffer space

---

### Q6b. TCP Segment Header + Connection Management ⭐⭐⭐
✅ Already fully covered (TCP header + 3-way handshake + 4-way termination).

---

### Q7a. 🔴 NEW — SMTP handling multimedia (MIME) ⭐⭐

**Answer:**
SMTP by itself can only handle **7-bit ASCII text**. To send images/videos:

1. **MIME (Multipurpose Internet Mail Extensions)** is used
2. MIME adds headers to email:
   - **MIME-Version:** 1.0
   - **Content-Type:** multipart/mixed, image/jpeg, video/mp4
   - **Content-Transfer-Encoding:** Base64 (converts binary to ASCII)
3. Process: Binary data (image/video) → Base64 encoded → sent as ASCII via SMTP → decoded at receiver
4. **Multipart messages:** Boundary separates text, images, attachments

**IMAP4 advantages over POP3:**
| Feature | POP3 | IMAP4 |
|---------|------|-------|
| Storage | Downloads locally, deletes from server | Keeps on server |
| Multi-device | Poor (mail on one device) | Excellent (sync across devices) |
| Folder management | No | Yes (create/delete/rename folders) |
| Search | Local only | Server-side search |
| Partial download | No (full message) | Yes (headers first, then body) |
| Bandwidth | Higher (downloads everything) | Lower (selective download) |

---

### Q7b. FTP + HTTP + Telnet
✅ Already fully covered in Unit 5 notes.

---

# ═══════════════════════════════════════════
# 🎯 UPDATED PRIORITY RANKING (After 2024-25 Analysis)
# ═══════════════════════════════════════════

## 🔴 CRITICAL — Study These FIRST (100% chance)

| # | Topic | Why |
|---|-------|-----|
| 1 | **CRC Numerical** (polynomial form) | Asked in 2024-25, 23-24, 22-23 |
| 2 | **Subnetting Numerical** | Asked every single year |
| 3 | **DVR Table Calculation** | Asked in 2024-25, 23-24 |
| 4 | **RSA Algorithm** | Asked in 2024-25, 22-23 |
| 5 | **TCP Header + Connection Management** | Asked every year |
| 6 | **OSI Model with diagram** | Asked every year |
| 7 | **Congestion Control Policies** | New in 2024-25 (open/closed loop) |

## 🟡 HIGH — Study These SECOND (80% chance)

| # | Topic | Why |
|---|-------|-----|
| 8 | **Silly Window Syndrome** + Nagle/Clark | NEW in 2024-25 — likely to repeat! |
| 9 | **Slotted ALOHA numerical** | NEW type of numerical |
| 10 | **Total Delay calculation** | NEW — multi-component delay |
| 11 | **IPv6 vs IPv4 + Extension Headers** | NEW depth asked |
| 12 | **Leaky/Token Bucket** | Repeated |
| 13 | **SMTP + MIME + IMAP vs POP3** | NEW angle (multimedia) |
| 14 | **VPN concept** | NEW — short note likely |
| 15 | **Signal Attenuation (dB)** | NEW 2-mark type |

## 🟢 MEDIUM — Quick Read

| # | Topic |
|---|-------|
| 16 | RPC Stub mechanism |
| 17 | Piggybacking |
| 18 | Contention-based MAC protocols |
| 19 | SNMP + DNS + Data Compression |
| 20 | FTP + HTTP + Telnet |

---

# ═══════════════════════════════════════════
# 📌 KEY FORMULAS TO MEMORIZE (Updated)
# ═══════════════════════════════════════════

```
MESH LINKS:         n(n-1)/2
dB ATTENUATION:     dB = 10 × log₁₀(P_out/P_in)
                    -3 dB = half power, +3 dB = double power
TOTAL DELAY:        T_trans + T_prop + T_processing + T_queuing
  T_trans:          Frame Size / Bandwidth
  T_prop:           Distance / Speed
SLOTTED ALOHA:      S = G × e^(-G), idle = e^(-G), max S = 36.8% at G=1
PURE ALOHA:         S = G × e^(-2G), max S = 18.4% at G=0.5
CRC:                Append (n-1) zeros, XOR divide
HAMMING:            2^r ≥ m + r + 1
SUBNETTING:         Subnets = 2^n, Hosts = 2^h - 2, Block = 256 - mask
DVR:                D(x,y) = min{C(x,v) + D(v,y)}
RSA:                C = P^e mod n, P = C^d mod n, φ(n) = (p-1)(q-1)
STOP-WAIT EFF:      η = 1/(1+2a), a = Tp/Tt
```
