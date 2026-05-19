# UNIT 2 — DATA LINK LAYER
## 30 × 2-Mark Questions + 15 × 7-Mark Questions

---

# 📝 2-MARK QUESTIONS (30)

---

### Q1. What are the functions of the Data Link Layer?
Framing, Physical addressing (MAC), Error control, Flow control, Access control. It ensures reliable node-to-node delivery of data over the physical link.

---

### Q2. What is Framing?
Framing is the process of dividing a continuous bit stream from the network layer into manageable units called frames. Each frame has a header, data, and trailer for addressing and error checking.

---

### Q3. Define Bit Stuffing with example.
Bit stuffing is a technique where a 0 is inserted after every five consecutive 1s in the data to prevent the flag pattern (01111110) from appearing in the data. Example: Data = 01111110 → After stuffing: 011111010.

---

### Q4. What is Byte Stuffing?
Byte stuffing is a framing technique where a special escape byte (ESC) is inserted before any occurrence of the flag byte or escape byte within the data, preventing misinterpretation.

---

### Q5. Differentiate between Error Detection and Error Correction.
| Feature | Error Detection | Error Correction |
|---------|----------------|-----------------|
| Function | Identifies if error occurred | Identifies AND fixes the error |
| Overhead | Lower | Higher (more redundant bits) |
| Example | CRC, Parity, Checksum | Hamming Code |

---

### Q6. What is Even Parity? Give example.
In even parity, a parity bit is added to make the total number of 1s in the data **even**. Example: Data = 1011001 (four 1s → already even) → Parity bit = 0 → Transmitted: 10110010.

---

### Q7. What is CRC? Which layer uses it?
CRC (Cyclic Redundancy Check) is an error detection technique that uses polynomial division (XOR) to generate a checksum appended to data. It is used at the **Data Link Layer**. It can detect single-bit, double-bit, and burst errors.

---

### Q8. What is Hamming Distance?
Hamming distance between two binary strings of equal length is the number of positions at which the corresponding bits differ. Example: 10110 and 11010 → differ at positions 2 and 3 → Hamming distance = 2.

---

### Q9. What is the formula for finding the number of parity bits in Hamming Code?
**2^r ≥ m + r + 1**, where m = number of data bits and r = number of parity (redundant) bits. Parity bits are placed at positions that are powers of 2 (1, 2, 4, 8...).

---

### Q10. What is Checksum error detection?
In Checksum: (1) Divide data into equal segments, (2) Add all segments using 1's complement addition, (3) Take 1's complement of sum = Checksum. Receiver adds all segments + checksum; result should be all 1s.

---

### Q11. What is the difference between Stop-and-Wait and Sliding Window?
| Feature | Stop-and-Wait | Sliding Window |
|---------|--------------|---------------|
| Frames sent | 1 at a time | Multiple (window size) |
| Efficiency | Low | High |
| Waiting | Waits for each ACK | Sends multiple before ACK |

---

### Q12. What is ARQ?
ARQ (Automatic Repeat reQuest) is an error control mechanism where the receiver requests retransmission of corrupted or lost frames. Types: Stop-and-Wait ARQ, Go-Back-N ARQ, Selective Repeat ARQ.

---

### Q13. What is Piggybacking?
Piggybacking is a technique where the acknowledgment (ACK) is attached to the next outgoing data frame instead of sending a separate ACK frame. This reduces overhead and improves efficiency.

---

### Q14. What is the vulnerable time of Pure ALOHA and Slotted ALOHA?
- **Pure ALOHA:** Vulnerable time = **2 × Tfr** (frame transmission time)
- **Slotted ALOHA:** Vulnerable time = **Tfr**
- Max efficiency: Pure = 18.4%, Slotted = 36.8%

---

### Q15. What is CSMA?
CSMA (Carrier Sense Multiple Access) is a protocol where a device **listens to the channel before transmitting**. If the channel is idle, it transmits; if busy, it waits. This reduces collision compared to ALOHA.

---

### Q16. Differentiate between CSMA/CD and CSMA/CA.
| Feature | CSMA/CD | CSMA/CA |
|---------|---------|---------|
| Full Form | Collision Detection | Collision Avoidance |
| Used in | Ethernet (wired) | WiFi (wireless) |
| Mechanism | Detect collision during transmission | Avoid collision using RTS/CTS |
| After collision | Send Jam signal | Wait + retry |

---

### Q17. What is a Jam Signal?
A Jam signal is a special signal sent by a station in CSMA/CD when it detects a collision during transmission. It alerts all other stations on the network to stop transmitting and wait for a random backoff time.

---

### Q18. What is Token Passing?
Token passing is a controlled access protocol where a special frame called a "token" circulates in a ring network. Only the station holding the token can transmit data. After sending, it passes the token to the next station.

---

### Q19. What is Polling?
Polling is a controlled access method where a primary (controller) station sequentially asks each secondary station if it has data to send. If yes → data is sent; if no → NAK is returned. It eliminates collision.

---

### Q20. What is FDMA?
FDMA (Frequency Division Multiple Access) divides the available bandwidth into separate frequency bands. Each station is allocated a unique frequency band for transmission. Used in analog communication.

---

### Q21. Differentiate between TDMA and FDMA.
| Feature | FDMA | TDMA |
|---------|------|------|
| Division basis | Frequency | Time |
| Channel sharing | Each user gets a frequency band | Each user gets a time slot |
| Simultaneous use | Yes (different frequencies) | No (different time slots) |

---

### Q22. What is the maximum frame size in IEEE 802.3?
The maximum frame size in IEEE 802.3 (Ethernet) is **1518 bytes** (6B DA + 6B SA + 2B Length/Type + 1500B Data + 4B FCS). The minimum data field is 46 bytes.

---

### Q23. What is a Bridge? Name its types.
A bridge connects two LAN segments and filters traffic using MAC addresses. Types:
- **Static Bridge:** Manual mapping table
- **Dynamic (Learning/Transparent) Bridge:** Automatically learns MAC-port mappings

---

### Q24. What is the Back-off Algorithm?
When collision occurs in CSMA/CD, stations wait for a **random backoff time** before retransmitting. The time is chosen using Binary Exponential Backoff: wait time = random(0 to 2^k - 1) × slot time, where k = collision attempt number.

---

### Q25. What is 1-Persistent CSMA?
In 1-Persistent CSMA, the station continuously senses the channel. If idle → transmit immediately with probability 1. If busy → keep sensing until idle, then transmit. High collision probability when multiple stations wait.

---

### Q26. What is the difference between Reservation and Token Passing?
| Feature | Reservation | Token Passing |
|---------|------------|---------------|
| Mechanism | Reserve slot before sending | Hold token to send |
| Topology | Any | Ring |
| Overhead | Mini-slot reservation | Token circulation |

---

### Q27. What is the Spanning Tree Protocol?
Spanning Tree Protocol (STP) is used to prevent loops in bridged/switched networks. It creates a loop-free logical topology by blocking redundant paths. Steps: Select root bridge → Find root ports → Find designated ports → Block remaining ports.

---

### Q28. What is 2D Parity Check?
Two-dimensional parity arranges data bits in a matrix and adds parity bits for each row AND each column. It can detect single, double, and some triple-bit errors. It can also **correct single-bit errors**.

---

### Q29. What is CDMA?
CDMA (Code Division Multiple Access) allows all stations to transmit simultaneously using the full bandwidth. Each station is assigned a unique code sequence. Data + Code is shared; receiver uses the code to extract the correct data.

---

### Q30. What is flow control? Why is it needed?
Flow control is a mechanism to match the data transmission rate of the sender with the receiving capacity of the receiver. It prevents the receiver's buffer from overflowing, ensuring smooth and reliable communication.

---

---

# 📝 7-MARK QUESTIONS (15)

---

### Q1. Explain CRC error detection method with a numerical example. ⭐⭐⭐
**Answer Structure:**
1. Define CRC (2 lines)
2. Steps: (a) Append n-1 zeros to data, (b) XOR divide by generator, (c) Remainder = CRC
3. **Full numerical:** Data = 1101011011, Generator = 10011
   - Append 4 zeros → 11010110110000
   - Show complete XOR division (step by step)
   - Remainder = 1110
   - Transmitted = 1101011011|1110
4. Receiver side: Divide received data by generator → remainder 0 = no error
5. Draw the XOR division clearly

---

### Q2. Explain Hamming Code with example. Show how to detect and correct errors. ⭐⭐⭐
**Answer Structure:**
1. Define Hamming Code (error detection + correction)
2. Formula: 2^r ≥ m + r + 1
3. **Example 1 — Code Construction:** Data = 1011
   - m=4, r=3, total = 7 bits
   - Position parity bits at 1, 2, 4
   - Fill data at 3, 5, 6, 7
   - Calculate P1, P2, P4 using even parity
   - Show final 7-bit code
4. **Example 2 — Error Detection:** Given received code = 1100101
   - Check P1, P2, P4
   - Find syndrome bits → error position
   - Flip the bit to correct

---

### Q3. Explain error control mechanisms in Data Link Layer. ⭐⭐⭐
**Answer Structure:**
1. Define error control (2 lines)
2. **Error Detection Methods:**
   - Parity Check (single, 2D)
   - Checksum
   - CRC (with brief example)
3. **Error Correction Methods:**
   - Hamming Code
4. **ARQ Mechanisms:**
   - Stop-and-Wait ARQ
   - Go-Back-N ARQ
   - Selective Repeat ARQ
5. Brief comparison table of ARQ methods

---

### Q4. Explain Go-Back-N ARQ and Selective Repeat ARQ with diagrams. ⭐⭐
**Answer Structure:**
1. **Go-Back-N ARQ:**
   - Sender window = N, Receiver window = 1
   - If frame lost → retransmit all N frames from lost point
   - Diagram showing sender-receiver with lost frame → all retransmitted
2. **Selective Repeat ARQ:**
   - Sender window = N, Receiver window = N
   - Only lost frame retransmitted
   - Receiver buffers out-of-order frames, sends NACK
   - Diagram showing only lost frame retransmitted
3. Comparison table (5+ points)

---

### Q5. Explain the Stop-and-Wait protocol. Derive its efficiency formula and solve a numerical. ⭐⭐
**Answer Structure:**
1. Define Stop-and-Wait (send 1 frame → wait for ACK → send next)
2. Diagram: sender-receiver with frame and ACK arrows
3. **Efficiency = 1/(1+2a)** where a = Tp/Tt
4. Tp = Distance/Speed, Tt = Frame Size/Bandwidth
5. **Numerical:** Given: BW=20Kbps, Frame=4500bits, Distance=30000km, Speed=2.8×10⁸ m/s
   - Calculate Tp, Tt, a, and efficiency
   - If fault delay given: η = 1/(1+2a+fault/Tt)
   - Calculate decrease in efficiency

---

### Q6. Explain Multiple Access Protocols. Draw the classification flowchart. ⭐⭐⭐
**Answer Structure:**
1. Define Multiple Access Protocols (2 lines)
2. **DRAW FLOWCHART:**
   - Random Access: ALOHA, CSMA, CSMA/CD, CSMA/CA
   - Controlled Access: Reservation, Polling, Token Passing
   - Channelization: FDMA, TDMA, CDMA
3. Brief explanation of each (2-3 lines per protocol)
4. Key metrics: Vulnerable time, max efficiency for ALOHA

---

### Q7. Explain CSMA/CD and CSMA/CA protocols with flowcharts. ⭐⭐⭐
**Answer Structure:**
1. **CSMA/CD:**
   - Used in Ethernet; Detect collision during transmission
   - Flowchart: Start → Set backoff=0 → Persistent strategy → Send frame → Collision? → No: Success / Yes: Send Jam → Backoff limit exceeded? → Yes: Abort / No: Wait backoff → Repeat
2. **CSMA/CA:**
   - Used in WiFi; Avoid collision using RTS/CTS
   - Flowchart: Start → Set backoff=0 → Persistent strategy → IFS wait → Random wait → Set timer → ACK received? → Yes: Success / No: Increment backoff → Check limit → Wait → Repeat
3. Comparison table

---

### Q8. Explain Pure ALOHA and Slotted ALOHA with diagrams. Compare them. ⭐⭐
**Answer Structure:**
1. **Pure ALOHA:** Transmit anytime; collision detected via ACK timeout; vulnerable time = 2Tfr; efficiency = 18.4%. Diagram showing partial collisions.
2. **Slotted ALOHA:** Transmit only at slot start; only total collisions; vulnerable time = Tfr; efficiency = 36.8%. Diagram showing time slots.
3. Comparison table (5+ points)

---

### Q9. Explain framing techniques: Byte Stuffing and Bit Stuffing with examples. ⭐
**Answer Structure:**
1. Why framing? (2 lines)
2. **Byte Stuffing:** Flag byte marks start/end; ESC byte before flag/ESC in data. Example with actual bytes.
3. **Bit Stuffing:** Flag = 01111110; insert 0 after five consecutive 1s. Full example: Original data → Stuffed data → Show insertion points.
4. Diagrams for both methods

---

### Q10. Explain IEEE 802.3 and IEEE 802.5 frame formats with diagrams. ⭐
**Answer Structure:**
1. **802.3 (Ethernet):**
   - Preamble(7B) + SFD(1B) + DA(6B) + SA(6B) + Length(2B) + Data(46-1500B) + FCS(4B)
   - Uses CSMA/CD, Bus/Star topology
   - Max frame = 1518 bytes
   - Draw frame format diagram
2. **802.5 (Token Ring):**
   - SD(1B) + AC(1B) + FC(1B) + DA(6B) + SA(6B) + Data(0-4500B) + FCS(4B) + ED(1B) + FS(1B)
   - Uses Token Passing, Ring topology
   - Token format: SD + AC + ED
   - Draw frame format diagram

---

### Q11. Explain the Sliding Window Protocol. How does it improve efficiency? ⭐⭐
**Answer Structure:**
1. Define sliding window (multiple frames sent before ACK)
2. Concept: Window size N → send N frames → slide window as ACKs arrive
3. Sequence numbers for ordering
4. Uses piggybacking
5. Diagram: Show window sliding as ACKs received
6. Comparison with Stop-and-Wait
7. Efficiency formula for sliding window

---

### Q12. Explain the Checksum error detection method with example. ⭐
**Answer Structure:**
1. Define Checksum (2 lines)
2. **Sender side steps:**
   - Divide data into 16-bit segments
   - Add all using 1's complement addition
   - 1's complement of sum = Checksum
   - Append checksum to data
3. **Receiver side:** Add all segments + checksum → all 1s = no error
4. Full numerical example with actual binary addition
5. Advantages and limitations

---

### Q13. Explain controlled access protocols: Reservation, Polling, and Token Passing. ⭐
**Answer Structure:**
1. **Reservation:** Station reserves mini-slot before transmitting. Diagram with 5 stations showing reservation bits (0/1) and data slots.
2. **Polling:** Primary controller polls each secondary. Diagram showing POLL → Data/NAK exchange.
3. **Token Passing:** Token circulates in ring; holder transmits. Diagram of ring with token movement.
4. Brief advantages/disadvantages of each

---

### Q14. What is the Spanning Tree Algorithm? Explain with example. ⭐
**Answer Structure:**
1. Purpose: Prevent loops in bridged networks
2. **4 Steps:**
   - Step 1: Select Root Bridge (lowest Bridge ID)
   - Step 2: Find Root Port on each non-root bridge (lowest cost to root)
   - Step 3: Find Designated Port on each segment (lowest cost)
   - Step 4: Block all remaining ports
3. Example with 3-4 bridges showing the process
4. Diagram: Before (with loops) → After (loop-free tree)

---

### Q15. Explain the concept of Error Detection using Parity Check methods (Single Parity, 2D Parity). ⭐
**Answer Structure:**
1. **Single Parity:**
   - Add 1 bit to make total 1s even (even parity) or odd (odd parity)
   - Can detect single-bit errors only
   - Example with 7-bit data
2. **2D Parity:**
   - Arrange in matrix; add row parity + column parity
   - Can detect 1-bit, 2-bit, some 3-bit errors
   - Can correct single-bit error (intersection of failed row & column)
   - Full numerical example with matrix
3. Limitations of parity methods
