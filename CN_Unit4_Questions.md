# UNIT 4 — TRANSPORT LAYER
## 30 × 2-Mark Questions + 15 × 7-Mark Questions

---

# 📝 2-MARK QUESTIONS (30)

---

### Q1. What is the Transport Layer responsible for?
The Transport Layer (Layer 4) provides end-to-end communication between processes on different hosts. It handles segmentation, flow control, error control, connection management, and multiplexing/demultiplexing.

---

### Q2. Differentiate between TCP and UDP (3 points).
| Feature | TCP | UDP |
|---------|-----|-----|
| Connection | Connection-oriented | Connectionless |
| Reliability | Reliable (ACK-based) | Unreliable |
| Header size | 20 bytes (min) | 8 bytes (fixed) |

---

### Q3. What is a Port Number?
A port number is a 16-bit integer (0–65535) that identifies a specific application/process on a host. It enables multiplexing — multiple apps sharing the same IP. Well-known ports: HTTP=80, FTP=21, DNS=53, SMTP=25.

---

### Q4. What is the size of TCP header?
The minimum TCP header size is **20 bytes** (without options). The maximum is 60 bytes. The HLEN field (4 bits) specifies header length in 32-bit words (min value = 5, i.e., 5×4 = 20 bytes).

---

### Q5. What is the size of UDP header?
The UDP header is always **8 bytes** (fixed). It contains only 4 fields: Source Port (2B), Destination Port (2B), Length (2B), and Checksum (2B).

---

### Q6. What are the 6 flag bits in TCP header?
| Flag | Full Form | Purpose |
|------|-----------|---------|
| **URG** | Urgent | Urgent data present |
| **ACK** | Acknowledgment | ACK field is valid |
| **PSH** | Push | Push data to application immediately |
| **RST** | Reset | Reset the connection |
| **SYN** | Synchronize | Initiate connection (handshake) |
| **FIN** | Finish | Terminate connection |

---

### Q7. What is a Sequence Number in TCP?
The Sequence Number (32 bits) identifies the byte number of the first data byte in the segment. It enables ordered delivery and reassembly. Example: If seq=1001 and segment has 500 bytes, next seq = 1501.

---

### Q8. What is an Acknowledgment Number in TCP?
The ACK Number (32 bits) indicates the **next byte** the receiver expects. Example: If receiver got bytes up to 1500, it sends ACK=1501, meaning "I expect byte 1501 next."

---

### Q9. What is the Window Size field in TCP?
Window Size (16 bits) indicates the amount of data (in bytes) the receiver can accept. It is used for **flow control** — the sender must not send more than the advertised window size before receiving an ACK.

---

### Q10. What is a Three-Way Handshake?
Three-Way Handshake establishes a TCP connection:
1. Client → Server: **SYN** (seq=x)
2. Server → Client: **SYN+ACK** (seq=y, ack=x+1)
3. Client → Server: **ACK** (ack=y+1)
Connection is now established.

---

### Q11. How is a TCP connection terminated?
TCP uses a 4-step termination:
1. Client → FIN
2. Server → ACK
3. Server → FIN
4. Client → ACK
This is called a **Four-Way Handshake** or graceful close.

---

### Q12. What is Flow Control?
Flow control is a mechanism to prevent the sender from overwhelming the receiver with too much data too quickly. TCP uses the **sliding window** mechanism — receiver advertises its buffer capacity via the Window Size field.

---

### Q13. What is Congestion?
Congestion occurs when the load offered to a network exceeds its capacity, causing packet loss, increased delay, and reduced throughput. TCP uses congestion control mechanisms (Slow Start, Congestion Avoidance) to handle it.

---

### Q14. What is the Congestion Window (cwnd)?
The congestion window is a TCP sender-side variable that limits how much data can be in transit. If the network is congested, cwnd is reduced. It works alongside the receiver's advertised window for flow control.

---

### Q15. Name the three phases of TCP Congestion Control.
1. **Slow Start Phase** — Exponential increase of cwnd (1→2→4→8...) until threshold
2. **Congestion Avoidance Phase** — Linear increase (+1 per RTT) after threshold
3. **Congestion Detection Phase** — On loss: reset cwnd (timeout → slow start; 3 dup ACK → fast recovery)

---

### Q16. What happens on Timeout in TCP Congestion Control?
On timeout: ssthresh = cwnd/2, cwnd is reset to **1 MSS**, and TCP goes back to **Slow Start Phase**. This is a severe reaction because timeout indicates heavy congestion.

---

### Q17. What happens on 3 Duplicate ACKs?
On receiving 3 duplicate ACKs: ssthresh = cwnd/2, cwnd = ssthresh, and TCP enters **Congestion Avoidance Phase** directly (Fast Recovery). This is a milder reaction since some packets are still getting through.

---

### Q18. What is Multiplexing at the Transport Layer?
**Multiplexing (sender side):** Collecting data from multiple application processes, adding transport headers (port numbers), and combining them into segments for transmission over the network.

---

### Q19. What is Demultiplexing?
**Demultiplexing (receiver side):** Receiving incoming segments and delivering them to the correct application process based on the destination port number in the segment header.

---

### Q20. What is a Segment?
A segment is the PDU (Protocol Data Unit) at the Transport Layer. In TCP, a segment consists of the TCP header (20+ bytes) + application data. In UDP, the PDU is called a **datagram**.

---

### Q21. What is Retransmission in TCP?
If the sender does not receive an ACK within a specified timeout period, it assumes the segment was lost and **retransmits** it. TCP also uses Fast Retransmit (on 3 duplicate ACKs) without waiting for timeout.

---

### Q22. What is MSS (Maximum Segment Size)?
MSS is the maximum amount of **data** (excluding TCP header) that can be sent in a single TCP segment. Typical MSS = MTU - 40 bytes (20B IP header + 20B TCP header). For Ethernet: 1500 - 40 = 1460 bytes.

---

### Q23. What is RTT (Round Trip Time)?
RTT is the time taken for a signal to travel from sender to receiver and for the acknowledgment to return. TCP uses RTT to calculate the **retransmission timeout (RTO)**. Estimated dynamically.

---

### Q24. What is the Urgent Pointer in TCP?
The Urgent Pointer (16 bits) is used when the URG flag is set. It points to the end of urgent data within the segment, allowing the receiver to prioritize this data for immediate processing.

---

### Q25. What is the Checksum field in UDP?
The UDP Checksum (16 bits) is used for error detection of the header and data. It is **optional in IPv4** (can be 0) but **mandatory in IPv6**. It covers a pseudo-header, UDP header, and data.

---

### Q26. Why is UDP faster than TCP?
UDP is faster because: (1) No connection setup (no handshake), (2) Smaller header (8B vs 20B), (3) No flow/congestion control, (4) No ordering or retransmission overhead. Ideal for real-time applications.

---

### Q27. Give 3 applications each of TCP and UDP.
| TCP Applications | UDP Applications |
|-----------------|-----------------|
| HTTP (web browsing) | DNS (name resolution) |
| FTP (file transfer) | DHCP (IP assignment) |
| SMTP (email sending) | VoIP (voice calls) |

---

### Q28. What is a Well-Known Port?
Well-known ports range from **0 to 1023** and are reserved for standard services. Examples: HTTP=80, HTTPS=443, FTP=21, SSH=22, DNS=53, SMTP=25, Telnet=23, POP3=110.

---

### Q29. What is Jitter?
Jitter is the **variation in packet delay**. If packet 1 takes 10ms and packet 2 takes 50ms, jitter = 40ms. High jitter degrades quality of real-time applications (VoIP, video streaming). Buffering can smooth jitter.

---

### Q30. What is the difference between Reliable and Unreliable delivery?
| Feature | Reliable (TCP) | Unreliable (UDP) |
|---------|---------------|-----------------|
| ACK | Yes | No |
| Retransmission | Yes (on loss) | No |
| Ordering | Guaranteed | Not guaranteed |
| Use case | File transfer, email | Streaming, gaming |

---

---

# 📝 7-MARK QUESTIONS (15)

---

### Q1. Compare TCP and UDP protocols in detail. Draw header formats of both. ⭐⭐⭐
**Answer:**
1. Define TCP (connection-oriented, reliable) and UDP (connectionless, unreliable)
2. **TCP Header diagram** (20 bytes): Source Port, Dest Port, Seq No, ACK No, HLEN, Flags, Window, Checksum, Urgent Ptr
3. **UDP Header diagram** (8 bytes): Source Port, Dest Port, Length, Checksum
4. **Comparison table (10+ points):**
   - Connection, Reliability, Ordering, Speed, Header size, Flow control, Congestion control, Broadcasting, Error control, Applications, PDU name, Overhead

---

### Q2. Explain the TCP header format in detail with diagram. ⭐⭐⭐
**Answer:**
1. Draw TCP header (5 rows of 32 bits each)
2. Explain ALL fields with size and purpose:
   - Source Port (16b), Destination Port (16b)
   - Sequence Number (32b)
   - Acknowledgment Number (32b)
   - HLEN (4b), Reserved (6b), Flags: URG/ACK/PSH/RST/SYN/FIN (6b), Window Size (16b)
   - Checksum (16b), Urgent Pointer (16b)
   - Options (variable, up to 40 bytes)
3. Minimum header = 20 bytes, Maximum = 60 bytes
4. Explain significance of SYN, ACK, FIN flags

---

### Q3. Explain Three-Way Handshake for TCP connection establishment and Four-Way for termination. ⭐⭐⭐
**Answer:**
1. **Connection Establishment (3-Way):**
   - Step 1: Client sends SYN (seq=x)
   - Step 2: Server sends SYN+ACK (seq=y, ack=x+1)
   - Step 3: Client sends ACK (ack=y+1)
   - Draw timing diagram
   - After this, connection is ESTABLISHED
2. **Connection Termination (4-Way):**
   - Step 1: Client sends FIN
   - Step 2: Server sends ACK
   - Step 3: Server sends FIN
   - Step 4: Client sends ACK
   - Draw timing diagram
   - After this, connection is CLOSED
3. Explain why 3 steps for open but 4 for close (half-close concept)

---

### Q4. Explain TCP Congestion Control mechanism with graph. ⭐⭐⭐
**Answer:**
1. Define congestion (load > capacity)
2. **cwnd (Congestion Window)** and **ssthresh (Slow Start Threshold)**
3. **Phase 1 — Slow Start:** cwnd starts at 1 MSS, doubles each RTT (exponential: 1→2→4→8→16). Until cwnd reaches ssthresh.
4. **Phase 2 — Congestion Avoidance:** cwnd increases by 1 MSS per RTT (linear). Until packet loss detected.
5. **Phase 3 — Congestion Detection:**
   - **Timeout:** ssthresh = cwnd/2, cwnd = 1, go to Slow Start
   - **3 Dup ACKs:** ssthresh = cwnd/2, cwnd = ssthresh, go to Congestion Avoidance (Fast Recovery)
6. **DRAW THE GRAPH:** X-axis = Time/RTT, Y-axis = cwnd. Show exponential rise → threshold → linear rise → max → drop (either to 1 or to new threshold)

---

### Q5. Explain the UDP header format and when UDP is preferred over TCP. ⭐⭐
**Answer:**
1. Draw UDP header (2 rows of 32 bits):
   - Source Port (16b) | Destination Port (16b)
   - Length (16b) | Checksum (16b)
2. Total header = 8 bytes (fixed)
3. Explain each field
4. **When UDP is preferred:**
   - Real-time apps (VoIP, video streaming, gaming)
   - DNS queries (small, quick)
   - Broadcasting/Multicasting
   - When speed > reliability
   - IoT sensor data
5. Advantages of UDP: Fast, low overhead, no connection setup delay
6. Disadvantages: No reliability, no ordering, no congestion control

---

### Q6. Explain Flow Control mechanism in TCP with diagram. ⭐⭐
**Answer:**
1. Define flow control: Match sender speed with receiver capacity
2. **Sliding Window mechanism:**
   - Receiver advertises window size in TCP header
   - Sender can send up to window size bytes without ACK
   - As ACKs arrive, window slides forward
3. **Example with diagram:**
   - Client sends seq 101-200, ACK=5001
   - Server sends seq 5001-6000, ACK=401
   - Server sends seq 6001-7000, ACK=401 (before getting ACK)
   - Client sends ACK=7001 after receiving all
4. Explain how window size adjustment prevents buffer overflow

---

### Q7. Explain TCP Retransmission mechanism with diagram. ⭐⭐
**Answer:**
1. Define retransmission: Resending lost/corrupted segments
2. **Timeout-based retransmission:**
   - Sender starts timer after sending segment
   - If ACK not received before timeout → retransmit
3. **Example with diagram:**
   - Client sends 101-200, 201-300 → Server ACKs 301
   - Client sends 301-500 (LOST!), 501-600
   - Server receives 501-600 → buffers it → sends ACK 301 (duplicate)
   - Client retransmits 301-500
   - Server combines buffer → sends ACK 601
4. **Fast Retransmit:** On 3 duplicate ACKs → retransmit immediately without waiting for timeout
5. Role of buffers at receiver side

---

### Q8. Explain Multiplexing and Demultiplexing at Transport Layer. ⭐
**Answer:**
1. **Multiplexing (Sender):**
   - Multiple apps (HTTP, FTP, SMTP) run simultaneously
   - Transport layer collects data from all, adds headers (port numbers)
   - Combines into single stream for network layer
   - Diagram: Multiple apps → Transport → Single output
2. **Demultiplexing (Receiver):**
   - Transport layer receives segments
   - Uses destination port number to deliver to correct app
   - Diagram: Single input → Transport → Multiple apps
3. Types: FDM, TDM, CDM (brief mention)
4. Importance of port numbers in this process

---

### Q9. Explain Quality of Service (QoS) parameters and improvement techniques. ⭐⭐
**Answer:**
1. Define QoS: Overall network performance measure
2. **Parameters:**
   - **Reliability:** Packet delivery guarantee (email, file transfer need high)
   - **Delay:** Source-to-destination time (VoIP needs low)
   - **Jitter:** Variation in delay (video streaming needs low)
   - **Bandwidth:** Data rate capacity (video needs high)
3. **Application table:**

| Application | Reliability | Delay | Jitter | Bandwidth |
|------------|------------|-------|--------|-----------|
| Email | High | Low | Low | Low |
| Video | Low | High | High | High |
| VoIP | Low | High | High | Low |
| File Transfer | High | Low | Low | Medium |

4. **Techniques:**
   - Over-provisioning (increase capacity)
   - Buffering (smooth jitter)
   - Scheduling (FIFO, Priority Queuing)
   - Traffic Shaping (Leaky Bucket, Token Bucket)

---

### Q10. Solve a TCP Header numerical: Extract fields from hex data. ⭐⭐
**Q:** Given first 20 bytes of TCP header in hex: `00 50 00 17 00 00 00 01 00 00 00 00 50 02 20 00 1A 2F 00 00`. Find Source Port, Dest Port, Seq No, ACK No, HLEN, Window Size.

**Answer:**
```
Bytes 0-1: 00 50 → Source Port = 0x0050 = 80 (HTTP)
Bytes 2-3: 00 17 → Dest Port = 0x0017 = 23 (Telnet)
Bytes 4-7: 00 00 00 01 → Seq Number = 1
Bytes 8-11: 00 00 00 00 → ACK Number = 0
Byte 12: 50 → Binary: 0101 0000 → HLEN = 5 (first 4 bits) → 5×4 = 20 bytes
         Remaining 4 bits = 0000 (reserved)
Byte 13: 02 → Binary: 00000010 → Flags: SYN=1 (connection initiation)
Bytes 14-15: 20 00 → Window Size = 0x2000 = 8192 bytes
Bytes 16-17: 1A 2F → Checksum = 0x1A2F
Bytes 18-19: 00 00 → Urgent Pointer = 0
```

---

### Q11. What is the difference between Connection-oriented and Connectionless services? Explain with examples. ⭐
**Answer:**
1. **Connection-oriented (TCP):**
   - Connection established before data transfer (handshake)
   - Reliable, ordered delivery, error recovery
   - Higher overhead
   - Analogy: Phone call
   - Examples: HTTP, FTP, SMTP
2. **Connectionless (UDP):**
   - No prior connection setup
   - Unreliable, unordered, no error recovery
   - Lower overhead, faster
   - Analogy: Postal mail
   - Examples: DNS, DHCP, VoIP
3. Detailed comparison table (7+ points)

---

### Q12. Explain the concept of Sliding Window Protocol at Transport Layer. ⭐⭐
**Answer:**
1. Define: Allows sending multiple frames before needing ACK
2. Window size determines how many unacknowledged segments allowed
3. **Sender window:** Tracks sent but unacknowledged segments
4. **Receiver window:** Buffer for incoming segments
5. Window slides as ACKs received
6. Detailed diagram showing window positions over time
7. Efficiency comparison with Stop-and-Wait
8. Piggybacking concept

---

### Q13. Explain the role of timers in TCP. ⭐
**Answer:**
1. **Retransmission Timer:** Started when segment sent; if expires before ACK → retransmit. RTO calculated from RTT.
2. **Persistence Timer:** Started when receiver advertises window=0. Prevents deadlock by sending probe segments.
3. **Keep-Alive Timer:** Detects idle connections. If no data exchanged for a period → send probe to check if other side is alive.
4. **Time-Wait Timer (2MSL):** After sending final ACK in connection termination. Ensures all segments are received. Duration = 2 × Maximum Segment Lifetime.

---

### Q14. What is the Silly Window Syndrome? How is it resolved? ⭐
**Answer:**
1. **Problem:** Sender sends very small segments (e.g., 1 byte) and receiver advertises tiny window → very inefficient (high header overhead for little data)
2. **Sender-side solution — Nagle's Algorithm:**
   - Collect small data until ACK for previous segment arrives
   - Then send all accumulated data in one segment
3. **Receiver-side solution — Clark's Solution / Delayed ACK:**
   - Don't advertise small windows
   - Wait until buffer has enough space (≥ MSS or ≥ half buffer)
   - Then advertise updated window

---

### Q15. Explain TCP connection management with state transition diagram. ⭐⭐
**Answer:**
1. **Client states:** CLOSED → SYN_SENT → ESTABLISHED → FIN_WAIT_1 → FIN_WAIT_2 → TIME_WAIT → CLOSED
2. **Server states:** CLOSED → LISTEN → SYN_RCVD → ESTABLISHED → CLOSE_WAIT → LAST_ACK → CLOSED
3. Draw state transition diagram showing:
   - Connection establishment (SYN, SYN+ACK, ACK)
   - Data transfer (ESTABLISHED)
   - Connection termination (FIN, ACK sequence)
4. Explain TIME_WAIT state (2MSL wait) and why it's needed
5. Half-close concept
