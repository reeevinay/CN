# 🔥 COMPUTER NETWORKS — UNIT 5 + EXAM STRATEGY
### AKTU Exam-Ready | Application Layer + Top 30 Questions + Revision Plan

---

# ═══════════════════════════════════════════
# UNIT 5: APPLICATION LAYER
# ═══════════════════════════════════════════

## 5.1 Application Layer — Overview
- Topmost layer in both OSI and TCP/IP
- Provides **network services directly to end-users**
- Protocols: DNS, HTTP, FTP, SMTP, POP3, IMAP, Telnet, SSH, SNMP

---

## 5.2 DNS (Domain Name System) ⭐⭐⭐ (Most Asked from Unit 5)

### What is DNS?
- Translates **domain names → IP addresses** (e.g., google.com → 142.250.190.14)
- Uses **hierarchical, distributed database**
- Port: **53** | Protocol: **UDP** (queries), **TCP** (zone transfers)

### DNS Hierarchy:
```
                    Root DNS (.)
                   /     |      \
             .com       .org      .in
            /    \        |       /   \
       google  amazon   wiki   gov   co
         |       |        |     |     |
       www     www      www   nic   amazon
```

### Types of DNS Resolution: ⭐⭐ (DRAW DIAGRAMS)

**1. Recursive Resolution:**
```
Client → Local DNS → Root DNS → TLD DNS → Authoritative DNS
         ←←←←←←←← Final IP returned back through chain ←←←←
```
- Client asks Local DNS → Local DNS does ALL the work
- Local DNS queries Root → TLD → Authoritative on behalf of client
- Client gets **final answer** from Local DNS

**2. Iterative Resolution:**
```
Client → Local DNS → Root DNS (returns TLD address)
         Local DNS → TLD DNS (returns Auth address)
         Local DNS → Authoritative DNS (returns IP)
         Local DNS → Client (final IP)
```
- Each server returns **referral** (next server to ask)
- Local DNS makes multiple queries itself

### DNS Record Types:
| Type | Purpose | Example |
|------|---------|---------|
| **A** | Domain → IPv4 | google.com → 142.250.x.x |
| **AAAA** | Domain → IPv6 | google.com → 2404:6800::... |
| **CNAME** | Alias for another domain | www.google.com → google.com |
| **MX** | Mail server for domain | google.com → mail.google.com |
| **NS** | Name server for domain | google.com → ns1.google.com |

---

## 5.3 HTTP (HyperText Transfer Protocol) ⭐⭐

- **Port:** 80 (HTTP), 443 (HTTPS)
- **Protocol:** TCP (connection-oriented)
- **Stateless** — Each request is independent

### HTTP Methods:
| Method | Purpose |
|--------|---------|
| **GET** | Retrieve data from server |
| **POST** | Send data to server |
| **PUT** | Update existing resource |
| **DELETE** | Remove a resource |
| **HEAD** | Same as GET but returns headers only |

### HTTP Versions:
| Version | Feature |
|---------|---------|
| HTTP/1.0 | Non-persistent (new TCP connection per request) |
| HTTP/1.1 | Persistent (reuses TCP connection), pipelining |
| HTTP/2.0 | Multiplexing, header compression, server push |

### Persistent vs Non-Persistent:
| Feature | Non-Persistent | Persistent |
|---------|---------------|------------|
| Connections | New TCP per object | Single TCP reused |
| RTT | 2 RTT per object | 1 RTT after initial setup |
| Overhead | High | Low |
| Default | HTTP/1.0 | HTTP/1.1+ |

---

## 5.4 FTP (File Transfer Protocol) ⭐⭐

- **Port:** 20 (Data), 21 (Control)
- **Protocol:** TCP
- Uses **two parallel connections:**
  - **Control Connection (Port 21):** Commands & responses (persistent)
  - **Data Connection (Port 20):** Actual file transfer (non-persistent)

### FTP vs TFTP:

| Feature | FTP | TFTP |
|---------|-----|------|
| Full Form | File Transfer Protocol | Trivial FTP |
| Protocol | TCP | UDP |
| Port | 20 & 21 | 69 |
| Authentication | Yes (username/password) | No |
| Security | Basic | None |
| Complexity | Complex | Simple |
| Operations | Full file management | Read/Write only |
| Speed | Slower (reliable) | Faster (simple) |

---

## 5.5 Email Protocols ⭐⭐

### SMTP (Simple Mail Transfer Protocol):
- **Port:** 25
- Used to **SEND** emails
- Push protocol (sender pushes mail to server)
- Works between: Client→Server and Server→Server

### POP3 (Post Office Protocol v3):
- **Port:** 110
- Used to **RECEIVE/DOWNLOAD** emails
- Downloads mail to local device → **deletes from server**
- Offline access

### IMAP (Internet Message Access Protocol):
- **Port:** 143
- Used to **RECEIVE** emails
- Keeps mail **on server** → access from multiple devices
- Allows folder management on server

### SMTP vs POP3 vs IMAP:

| Feature | SMTP | POP3 | IMAP |
|---------|------|------|------|
| Purpose | Send | Receive (download) | Receive (sync) |
| Port | 25 | 110 | 143 |
| Type | Push | Pull | Pull |
| Mail storage | On server (relay) | Downloaded locally | Stays on server |
| Multi-device | N/A | Poor | Excellent |

### Email Flow:
```
Sender → [SMTP] → Sender's Mail Server → [SMTP] → Receiver's Mail Server → [POP3/IMAP] → Receiver
```

---

## 5.6 Telnet & SSH (2-Mark)

| Feature | Telnet | SSH |
|---------|--------|-----|
| Port | 23 | 22 |
| Security | Unsecure (plain text) | Secure (encrypted) |
| Purpose | Remote login | Remote login |
| Data | Not encrypted | Encrypted |

---

## 5.7 SNMP (Simple Network Management Protocol) (2-Mark)

- **Port:** 161 (agent), 162 (trap)
- Used to **monitor and manage** network devices
- Components:
  - **Manager:** Monitors network (NMS - Network Management Station)
  - **Agent:** Software on managed devices
  - **MIB:** Management Information Base (database of objects)
- **Operations:** GET, SET, TRAP (alert from agent to manager)

---

## 5.8 Data Compression (2-Mark)

### Types:
| Type | Description | Data Loss | Ratio |
|------|------------|-----------|-------|
| **Lossless** | Removes redundancy only; fully reversible | No loss | Low compression |
| **Lossy** | Removes some data permanently; not fully reversible | Some loss | High compression |

- **Compression Ratio** = Original Data / Compressed Data
- **Encoder** compresses data; **Decoder** decompresses data

---

## 5.9 Cryptography ⭐⭐

### Types:

**1. Symmetric Key (Private Key):**
- **Same key** for encryption & decryption
- Both sender & receiver must know the secret key
- **Algorithms:** DES, AES
- Fast but key distribution is a problem

**2. Asymmetric Key (Public Key):** ⭐⭐
- **Two keys:** Public Key (encrypt) + Private Key (decrypt)
- Public key shared openly; Private key kept secret
- **Algorithm:** RSA
- Slower but solves key distribution problem

**3. Digital Signature:**
- Sign with **Private Key** → Verify with **Public Key**
- Proves authenticity and integrity
- More secure than handwritten signature

### Cryptography Goals:
1. **Confidentiality** — Only intended receiver reads data
2. **Integrity** — Data not altered in transit
3. **Authentication** — Verify sender identity
4. **Non-repudiation** — Sender cannot deny sending

---

## 5.10 RSA Algorithm ⭐⭐⭐ (MUST DO Numerical)

### RSA Steps:
```
Step 1: Choose two large primes: p and q
Step 2: Compute n = p × q
Step 3: Compute Euler's totient: φ(n) = (p-1)(q-1)
Step 4: Choose e such that: 1 < e < φ(n) AND gcd(e, φ(n)) = 1
Step 5: Compute d such that: d × e mod φ(n) = 1

Public Key = (e, n)
Private Key = (d, n)

Encryption: C = P^e mod n
Decryption: P = C^d mod n
```

### RSA Numerical Example:
```
Step 1: p = 3, q = 5
Step 2: n = 3 × 5 = 15
Step 3: φ(n) = (3-1)(5-1) = 2 × 4 = 8
Step 4: Choose e: gcd(e, 8) = 1 AND 1 < e < 8
        Try e = 3: gcd(3, 8) = 1 ✓ → e = 3
Step 5: d × 3 mod 8 = 1
        Try d = 3: 3 × 3 = 9, 9 mod 8 = 1 ✓ → d = 3

Public Key = (3, 15)
Private Key = (3, 15)

Encryption (Plaintext P = 8):
C = 8³ mod 15 = 512 mod 15 = 2

Decryption (Ciphertext C = 2):
P = 2³ mod 15 = 8 mod 15 = 8 ✓ (Original plaintext recovered!)
```

> [!IMPORTANT]
> **RSA Exam Tip:** Always write all 5 steps clearly with formulas. Show gcd verification for e. Show d×e mod φ(n) = 1 verification. Then do encryption AND decryption to prove correctness. This alone is worth 7 marks.

---

# ═══════════════════════════════════════════
# 🎯 TOP 30 PREDICTED QUESTIONS (AKTU 2025-26)
# ═══════════════════════════════════════════

## UNIT 1 — Fundamentals (Expect ~20 marks)

| # | Question | Marks | Priority |
|---|----------|-------|----------|
| 1 | Explain OSI model with functions of each layer (with diagram) | 7 | 🔴 MUST |
| 2 | Compare OSI and TCP/IP model | 7 | 🔴 MUST |
| 3 | Explain different network topologies with diagrams | 7 | 🟡 HIGH |
| 4 | Differentiate between Circuit, Packet, and Message switching | 7 | 🟡 HIGH |
| 5 | Write short notes on: Hub, Switch, Router, Bridge, Gateway | 2×5 | 🟡 HIGH |
| 6 | Explain types of computer networks (LAN, MAN, WAN) | 2 | 🟢 MED |

## UNIT 2 — Data Link Layer (Expect ~20 marks)

| # | Question | Marks | Priority |
|---|----------|-------|----------|
| 7 | Perform CRC calculation (numerical) | 7 | 🔴 MUST |
| 8 | Construct Hamming code / Detect & correct error | 7 | 🔴 MUST |
| 9 | Explain error control mechanisms in DLL with examples | 7/10 | 🔴 MUST |
| 10 | Explain Go-Back-N ARQ and Selective Repeat ARQ | 7 | 🟡 HIGH |
| 11 | Stop-and-Wait efficiency numerical | 7/10 | 🟡 HIGH |
| 12 | Draw and explain CSMA/CD and CSMA/CA flowcharts | 7/10 | 🟡 HIGH |
| 13 | Explain Multiple Access Protocols (with flowchart) | 7 | 🟡 HIGH |
| 14 | What is piggybacking? Explain sliding window protocol | 2+5 | 🟢 MED |
| 15 | Explain IEEE 802.3 and 802.5 frame formats | 7 | 🟢 MED |

## UNIT 3 — Network Layer (Expect ~20 marks)

| # | Question | Marks | Priority |
|---|----------|-------|----------|
| 16 | Explain classful IP addressing with classes A-E | 7 | 🔴 MUST |
| 17 | Subnetting numerical (find subnets, ranges, broadcasts) | 7 | 🔴 MUST |
| 18 | Explain Distance Vector Routing with example | 7 | 🔴 MUST |
| 19 | Compare Distance Vector and Link State Routing | 7 | 🟡 HIGH |
| 20 | Explain ARP and RARP with working | 2/7 | 🟡 HIGH |
| 21 | Explain IPv4 header format with diagram | 7 | 🟡 HIGH |
| 22 | Differentiate IPv4 and IPv6 | 2/7 | 🟢 MED |
| 23 | Explain Leaky Bucket and Token Bucket algorithms | 7 | 🟢 MED |

## UNIT 4 — Transport Layer (Expect ~20 marks)

| # | Question | Marks | Priority |
|---|----------|-------|----------|
| 24 | Compare TCP and UDP with header formats | 7 | 🔴 MUST |
| 25 | Explain TCP header format (diagram + all fields) | 7 | 🔴 MUST |
| 26 | Explain Three-Way Handshake (with diagram) | 7 | 🔴 MUST |
| 27 | Explain TCP Congestion Control (3 phases + graph) | 7 | 🔴 MUST |
| 28 | TCP Header numerical (hex to fields extraction) | 7 | 🟡 HIGH |

## UNIT 5 — Application Layer (Expect ~20 marks)

| # | Question | Marks | Priority |
|---|----------|-------|----------|
| 29 | Explain DNS with recursive and iterative resolution | 7 | 🔴 MUST |
| 30 | Solve RSA algorithm numerical | 7 | 🔴 MUST |
| 31 | Compare FTP and TFTP | 2/7 | 🟡 HIGH |
| 32 | Explain HTTP (persistent vs non-persistent) | 7 | 🟡 HIGH |
| 33 | Compare SMTP, POP3, and IMAP | 7 | 🟡 HIGH |
| 34 | Explain Symmetric vs Asymmetric cryptography | 7 | 🟡 HIGH |
| 35 | Write short note on SNMP | 2 | 🟢 MED |

---

# ═══════════════════════════════════════════
# ⏰ 3-HOUR EMERGENCY REVISION PLAN
# ═══════════════════════════════════════════

## Hour 1 (0:00 – 1:00) — HIGH-SPEED THEORY SWEEP

| Time | Topic | Action |
|------|-------|--------|
| 0:00–0:10 | OSI Model | Memorize 7 layers + mnemonic + functions table |
| 0:10–0:15 | OSI vs TCP/IP | Read comparison table 3 times |
| 0:15–0:25 | TCP vs UDP | Memorize comparison + header sizes (20 vs 8) |
| 0:25–0:35 | TCP Header | Draw header diagram from memory twice |
| 0:35–0:40 | 3-Way Handshake | Draw SYN→SYN+ACK→ACK diagram |
| 0:40–0:50 | Congestion Control | Memorize 3 phases + draw graph |
| 0:50–1:00 | DNS Resolution | Draw recursive + iterative diagrams |

## Hour 2 (1:00 – 2:00) — NUMERICALS PRACTICE

| Time | Topic | Action |
|------|-------|--------|
| 1:00–1:15 | CRC | Solve 1 full CRC division step-by-step |
| 1:15–1:30 | Hamming Code | Solve 1 construction + 1 error detection |
| 1:30–1:45 | RSA Algorithm | Solve 1 complete RSA (p,q → encrypt → decrypt) |
| 1:45–2:00 | Subnetting | Solve 1 full subnetting problem with table |

## Hour 3 (2:00 – 3:00) — REMAINING TOPICS + QUICK REVIEW

| Time | Topic | Action |
|------|-------|--------|
| 2:00–2:10 | Network Devices | Quick read: Hub, Switch, Router, Bridge differences |
| 2:10–2:20 | Topologies | Visualize Bus/Star/Ring/Mesh + 1 advantage/disadvantage each |
| 2:20–2:30 | Flow Control | Go-Back-N vs Selective Repeat table |
| 2:30–2:40 | CSMA/CD vs CSMA/CA | Read flowcharts + key differences |
| 2:40–2:50 | Email Protocols | SMTP(send,25) POP3(download,110) IMAP(sync,143) |
| 2:50–3:00 | **FINAL SPEED RUN** | Flip through all comparison tables one last time |

---

## 🧠 LAST-MINUTE MEMORY ANCHORS

```
OSI Layers:     "Please Do Not Throw Sausage Pizza Away"
IP Classes:      A(1-126) B(128-191) C(192-223) D(224-239) E(240-255)
TCP Header:      20 bytes minimum
UDP Header:      8 bytes fixed
TCP Port:        HTTP=80, FTP=20/21, SMTP=25, DNS=53, Telnet=23, SSH=22, POP3=110, IMAP=143
CRC Rule:        Append (n-1) zeros, XOR divide, remainder = CRC
Hamming Rule:    2^r ≥ m+r+1, parity at powers of 2
RSA Formula:     Encrypt: C = P^e mod n  |  Decrypt: P = C^d mod n
Congestion:      Slow Start(exponential) → Avoidance(linear) → Detection(reset)
Efficiency:      η = 1/(1+2a)  where a = Tp/Tt
ALOHA:           Pure=18.4%, Slotted=36.8%
```

> [!CAUTION]
> **GOLDEN RULES FOR EXAM DAY:**
> 1. **ALWAYS draw diagrams** — OSI model, TCP header, 3-way handshake, congestion graph, DNS resolution
> 2. **Show all working** in numericals — partial marks for steps even if final answer is wrong
> 3. **Use tables for comparisons** — TCP vs UDP, OSI vs TCP/IP, FTP vs TFTP — examiners love structured answers
> 4. **Write headings & subheadings** — Makes your answer look organized
> 5. **Attempt all questions** — Even 2-3 lines with a diagram can get you 3-4 marks on a 7-mark question
