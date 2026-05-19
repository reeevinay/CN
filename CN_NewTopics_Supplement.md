# 🚨 EMERGENCY SUPPLEMENT — NEW TOPICS FROM 2024-25 PAPER
### These were NOT in previous papers. HIGH chance of appearing again!

---

# 1️⃣ SIGNAL ATTENUATION (dB Calculation) — Unit 1

### Key Formulas:
```
Decibel (dB) = 10 × log₁₀(P_output / P_input)

Quick Rules:
  -3 dB  → Power becomes HALF         (×0.5)
  +3 dB  → Power becomes DOUBLE       (×2)
  -10 dB → Power becomes 1/10         (×0.1)
  +10 dB → Power becomes 10×           (×10)
  0 dB   → No change
```

### Practice Problems:

**Q1:** Signal of 4W, attenuation = -3 dB. Find received power.
```
-3 dB = half → P_out = 4 × 0.5 = 2W ✅
```

**Q2:** Signal of 100W, attenuation = -10 dB. Find received power.
```
-10 dB → P_out = 100 × 0.1 = 10W ✅
```

**Q3:** Signal of 5W, attenuation = -6 dB. Find received power.
```
-6 dB = -3 dB + (-3 dB) = half × half = ×0.25
P_out = 5 × 0.25 = 1.25W ✅

OR: -6 = 10 × log₁₀(P/5) → log₁₀(P/5) = -0.6 → P/5 = 10^(-0.6) = 0.251 → P = 1.255W
```

**Q4:** Input = 2W, Output = 0.5W. Find attenuation in dB.
```
dB = 10 × log₁₀(0.5/2) = 10 × log₁₀(0.25) = 10 × (-0.602) = -6.02 dB ✅
```

---

# 2️⃣ RPC STUB MECHANISM — Unit 5

### What is RPC?
Remote Procedure Call allows a program to execute a procedure on a remote server as if it were local.

### Role of Stubs:
```
CLIENT MACHINE                              SERVER MACHINE
┌─────────────┐                            ┌──────────────┐
│ Client App  │                            │ Server Proc  │
│  calls      │                            │  executes    │
│  function() │                            │  function()  │
├─────────────┤                            ├──────────────┤
│ Client Stub │ ──── Network Message ────→ │ Server Stub  │
│  (Proxy)    │ ←── Return Message ──────  │  (Skeleton)  │
└─────────────┘                            └──────────────┘
```

### Client Stub Functions:
1. **Marshalling:** Packs parameters into a network message (serialization)
2. Sends message to server via network
3. **Waits** for response
4. **Unmarshalling:** Unpacks returned result and passes to client app

### Server Stub Functions:
1. Receives the network message
2. **Unmarshalling:** Unpacks parameters from message
3. Calls the **actual procedure** on server
4. **Marshalling:** Packs the result into response message
5. Sends response back to client

### Why Stubs?
- Make remote calls **transparent** — programmer writes code as if calling local function
- Handle all network communication details

---

# 3️⃣ SLOTTED ALOHA NUMERICAL — Unit 2

### Core Formulas (MUST MEMORIZE):
```
G = Channel Load (offered load)
S = Throughput = G × e^(-G)
P(success)    = G × e^(-G)
P(idle)       = e^(-G)
P(collision)  = 1 - e^(-G) - G × e^(-G)
                = 1 - P(idle) - P(success)

Maximum throughput: S_max = 1/e ≈ 0.368 = 36.8% (at G = 1)
```

### For Pure ALOHA:
```
S = G × e^(-2G)
Maximum throughput: S_max = 1/(2e) ≈ 0.184 = 18.4% (at G = 0.5)
```

### Solved Examples:

**Q1 (from 2024-25):** 10% slots idle. Find channel load and throughput.
```
e^(-G) = 0.10
-G = ln(0.10) = -2.3026
G = 2.3026

S = G × e^(-G) = 2.3026 × 0.10 = 0.23026
Throughput = 23.03%
```

**Q2:** 50% slots idle. Find G and S.
```
e^(-G) = 0.50
-G = ln(0.50) = -0.693
G = 0.693

S = 0.693 × 0.50 = 0.3465
Throughput = 34.65%
```

**Q3:** 36.8% slots idle. Find G and S.
```
e^(-G) = 0.368
-G = ln(0.368) = -1.0
G = 1.0

S = 1.0 × 0.368 = 0.368
Throughput = 36.8% ← This is MAXIMUM throughput!
```

**Q4:** Channel load G = 2. Find throughput and idle percentage.
```
P(idle) = e^(-2) = 0.1353 = 13.53%
S = 2 × e^(-2) = 2 × 0.1353 = 0.2707 = 27.07%
```

---

# 4️⃣ TOTAL DELAY CALCULATION — Unit 2

### Four Components of Delay:
```
Total Delay = Transmission Delay + Propagation Delay + Processing Delay + Queuing Delay

Transmission Delay (T_trans) = Frame Size (bits) / Bandwidth (bps)
Propagation Delay (T_prop)   = Distance (m) / Propagation Speed (m/s)
Processing Delay (T_proc)    = Number of routers × Processing time per router
Queuing Delay (T_queue)      = Number of routers × Queuing time per router
```

### Solved Example (from 2024-25):
```
Frame = 4 MB = 4 × 10⁶ × 8 = 32 × 10⁶ bits
Distance = 1000 km = 10⁶ m
Bandwidth = 2 Mbps = 2 × 10⁶ bps
Speed = 2 × 10⁸ m/s
5 routers: 1 μs processing + 2 μs queuing each

T_trans = 32×10⁶ / 2×10⁶ = 16 seconds
T_prop  = 10⁶ / 2×10⁸ = 0.005 s = 5 ms
T_proc  = 5 × 1 μs = 5 μs = 0.000005 s
T_queue = 5 × 2 μs = 10 μs = 0.00001 s

Total = 16 + 0.005 + 0.000005 + 0.00001 = 16.005015 s ≈ 16.005 s
```

### Practice:
**Q:** 1 KB frame, 500 km, 10 Mbps, speed = 2×10⁸ m/s, 3 routers (2μs proc, 3μs queue each)
```
T_trans = (1024 × 8) / (10 × 10⁶) = 8192 / 10⁷ = 0.0008192 s ≈ 0.82 ms
T_prop  = 500000 / (2 × 10⁸) = 0.0025 s = 2.5 ms
T_proc  = 3 × 2 μs = 6 μs = 0.006 ms
T_queue = 3 × 3 μs = 9 μs = 0.009 ms
Total ≈ 0.82 + 2.5 + 0.006 + 0.009 = 3.335 ms
```

---

# 5️⃣ IPv6 EXTENSION HEADERS — Unit 3

### IPv6 Base Header (40 bytes fixed):
| Field | Size | Purpose |
|-------|------|---------|
| Version | 4 bits | Always 6 |
| Traffic Class | 8 bits | Priority/QoS |
| Flow Label | 20 bits | Identifies packet flow |
| Payload Length | 16 bits | Length of data + extensions |
| Next Header | 8 bits | **Points to next header type** |
| Hop Limit | 8 bits | Same as TTL in IPv4 |
| Source Address | 128 bits | Sender's IPv6 |
| Destination Address | 128 bits | Receiver's IPv6 |

### Extension Header Chain:
```
┌──────────┐   ┌──────────────┐   ┌──────────┐   ┌──────────┐   ┌─────────┐
│ IPv6 Base│──→│ Hop-by-Hop   │──→│ Routing  │──→│ Fragment │──→│ Payload │
│ Header   │   │ Options      │   │ Header   │   │ Header   │   │ (Data)  │
│ Next=0   │   │ Next=43      │   │ Next=44  │   │ Next=6   │   │         │
└──────────┘   └──────────────┘   └──────────┘   └──────────┘   └─────────┘
```

### Extension Header Types (in recommended order):
| Order | Header | Next Header Value | Purpose |
|-------|--------|------------------|---------|
| 1 | **Hop-by-Hop Options** | 0 | Processed by EVERY router on path |
| 2 | **Destination Options** | 60 | Only for destination node |
| 3 | **Routing Header** | 43 | Specifies route (intermediate nodes) |
| 4 | **Fragment Header** | 44 | Fragmentation info (sender only) |
| 5 | **Authentication (AH)** | 51 | Data integrity + authentication |
| 6 | **ESP** | 50 | Encrypted payload (confidentiality) |

### Why Multiple Headers?
1. **Modular design** — add only needed headers
2. **Faster processing** — routers skip irrelevant headers (only check Hop-by-Hop)
3. **Extensibility** — new headers can be added without changing base header
4. **Security built-in** — AH + ESP headers for IPSec

---

# 6️⃣ VPN (Virtual Private Network) — Unit 3

### Definition:
VPN creates a **secure, encrypted communication tunnel** over a public network (Internet), making it function like a private network.

### How it works:
```
┌────────┐    Encrypted Tunnel     ┌────────┐
│ Client │ ═══════════════════════ │ VPN    │ ──→ Private Network
│        │  (over public Internet) │ Server │
└────────┘                         └────────┘
```

### VPN Tunneling Process:
1. Original packet is **encapsulated** inside a new packet
2. New packet is **encrypted**
3. Transmitted over public network
4. At VPN endpoint: **decrypted** and **de-encapsulated**
5. Original packet delivered to destination

### Types:
| Type | Use Case |
|------|----------|
| **Remote Access VPN** | Employee connects to office from home |
| **Site-to-Site VPN** | Two office branches connected |

### Tunneling Protocols:
- **IPSec** — Network layer, most secure
- **L2TP** — Layer 2, often combined with IPSec
- **PPTP** — Older, less secure
- **SSL/TLS VPN** — Application layer, browser-based

### Advantages:
- Privacy & Security (encryption)
- Cost-effective (uses Internet instead of leased lines)
- Remote access capability
- Bypasses geographical restrictions

---

# 7️⃣ SILLY WINDOW SYNDROME — Unit 4

### The Problem:
When the receiver's buffer is almost full, it advertises a **tiny window** (e.g., 1 byte). The sender then sends a tiny segment (1 byte data + 40 bytes header = 41 bytes total). This is **97.5% overhead** — extremely wasteful!

```
Sender                              Receiver
  │──── 1 byte data (41B total) ───→│  Buffer almost full
  │←── ACK, Window = 1 byte ────────│  Only 1 byte freed
  │──── 1 byte data (41B total) ───→│  Again 1 byte freed
  │←── ACK, Window = 1 byte ────────│  ... cycle continues
  │                                  │  VERY INEFFICIENT!
```

### Solution 1 — Nagle's Algorithm (SENDER side):
```
Rule: 
  IF data_to_send < MSS AND there_are_unACKed_segments:
      BUFFER the data (don't send yet)
  SEND when:
      (a) MSS worth of data accumulated, OR
      (b) ACK for previous segment received

Effect: Collects small data into larger segments before sending
```

### Solution 2 — Clark's Solution (RECEIVER side):
```
Rule:
  Don't advertise window until buffer has EITHER:
      (a) Space for 1 MSS (Maximum Segment Size), OR  
      (b) Half the buffer is empty

  Until then: Advertise Window = 0 (tells sender to stop)

Effect: Prevents advertising tiny windows
```

### Solution 3 — Delayed ACK (RECEIVER side):
- Don't send ACK immediately
- Wait for a short time (e.g., 200ms) hoping to piggyback ACK with outgoing data
- Or until enough buffer space freed up

### Summary Table:
| Solution | Side | Mechanism |
|----------|------|-----------|
| **Nagle's Algorithm** | Sender | Buffer small data, wait for ACK |
| **Clark's Solution** | Receiver | Don't advertise small windows |
| **Delayed ACK** | Receiver | Delay ACK to accumulate buffer |

---

# 8️⃣ SMTP + MIME (Multimedia Emails) — Unit 5

### The Problem:
SMTP was designed for **7-bit ASCII text only**. It cannot directly handle:
- Images (JPEG, PNG)
- Videos (MP4)
- Audio (MP3)
- Binary files

### The Solution — MIME (Multipurpose Internet Mail Extensions):

MIME extends email to support multimedia by adding special headers:

| MIME Header | Purpose | Example |
|-------------|---------|---------|
| **MIME-Version** | Version number | 1.0 |
| **Content-Type** | Type of content | text/plain, image/jpeg, multipart/mixed |
| **Content-Transfer-Encoding** | How binary→text | Base64, Quoted-Printable |
| **Content-Disposition** | Inline or attachment | attachment; filename="photo.jpg" |

### How it works:
```
Original Image (Binary) 
    ↓ Base64 Encoding
ASCII Text (safe for SMTP)
    ↓ SMTP Transfer  
ASCII Text received
    ↓ Base64 Decoding
Original Image restored
```

### Multipart Message Structure:
```
MIME-Version: 1.0
Content-Type: multipart/mixed; boundary="----BOUNDARY"

------BOUNDARY
Content-Type: text/plain
Hello, see the attached image.

------BOUNDARY
Content-Type: image/jpeg
Content-Transfer-Encoding: base64

/9j/4AAQSkZJRgABAQAA... (Base64 encoded image)

------BOUNDARY--
```

### Base64 Encoding:
- Converts binary data into **64 safe ASCII characters** (A-Z, a-z, 0-9, +, /)
- Every 3 bytes → 4 ASCII characters (33% size increase)
- Padding with `=` if input not multiple of 3

---

# 📌 CONGESTION CONTROL POLICIES (Also asked in 2024-25, Q1f)

### Open Loop Policies (Prevention — before congestion):
| Policy | Description |
|--------|------------|
| **Retransmission Policy** | Don't retransmit too aggressively (use good timers) |
| **Window Policy** | Use selective repeat over go-back-N (less retransmission) |
| **ACK Policy** | Don't ACK every packet; use delayed/cumulative ACKs |
| **Discarding Policy** | Router selectively drops lower-priority packets |
| **Admission Policy** | Network may refuse new connections during congestion |

### Closed Loop Policies (Reaction — after congestion detected):
| Policy | Description |
|--------|------------|
| **Backpressure** | Congested node tells upstream to slow down (hop-by-hop) |
| **Choke Packet** | Router sends control packet to source saying "slow down" |
| **Implicit Signaling** | Source detects congestion via timeouts/dup ACKs |
| **Explicit Signaling** | Router sets ECN bit in packet header |

---

> [!IMPORTANT]
> **TONIGHT'S UPDATED PRIORITY:** After analyzing 2024-25, add these to your study plan:
> 1. ⏱️ 10 min → Silly Window Syndrome (Nagle + Clark) — brand new, likely to repeat
> 2. ⏱️ 10 min → Slotted ALOHA formulas + 1 numerical
> 3. ⏱️ 5 min → dB formula (-3dB = half power)
> 4. ⏱️ 5 min → Total Delay formula (4 components)
> 5. ⏱️ 5 min → VPN + RPC stub (2-mark short notes)
> 6. ⏱️ 5 min → MIME in SMTP
> 7. ⏱️ 5 min → IPv6 extension headers chain
