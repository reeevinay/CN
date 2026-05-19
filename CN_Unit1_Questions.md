# UNIT 1 — INTRODUCTION TO COMPUTER NETWORKS
## 30 × 2-Mark Questions + 15 × 7-Mark Questions

---

# 📝 2-MARK QUESTIONS (30)

---

### Q1. Define Computer Network.
A computer network is a collection of interconnected devices (computers, servers, printers) that communicate with each other using defined protocols to share data and resources over transmission media.

---

### Q2. What is the difference between LAN and WAN?
| Feature | LAN | WAN |
|---------|-----|-----|
| Range | Building/Campus | Country/Globe |
| Speed | High (10Mbps–10Gbps) | Lower (variable) |
| Ownership | Private | Public/Private |
| Example | Office Ethernet | Internet |

---

### Q3. Define Protocol.
A protocol is a set of rules and conventions that govern how data is formatted, transmitted, received, and acknowledged between communicating devices in a network. Example: HTTP, TCP, IP.

---

### Q4. What is a Topology?
Topology refers to the physical or logical arrangement of nodes (devices) and connections (links) in a network. Common types: Bus, Star, Ring, Mesh, Tree, Hybrid.

---

### Q5. What is the function of the Physical Layer in OSI?
The Physical Layer (Layer 1) is responsible for the actual transmission and reception of raw bit streams (0s and 1s) over a physical medium. It defines electrical signals, cable types, connectors, and data rates.

---

### Q6. Differentiate between Hub and Switch.
| Feature | Hub | Switch |
|---------|-----|--------|
| Layer | Physical (L1) | Data Link (L2) |
| Intelligence | Broadcasts to all ports | Forwards to specific port using MAC table |
| Collision | High (shared bandwidth) | Low (dedicated bandwidth per port) |

---

### Q7. What is the role of a Router?
A router operates at the Network Layer (L3). It routes packets between different networks using IP addresses, determines the best path using routing algorithms, and connects heterogeneous networks.

---

### Q8. Define Bandwidth.
Bandwidth is the maximum amount of data that can be transmitted over a network link in a given time period, measured in bits per second (bps). Higher bandwidth = more data capacity.

---

### Q9. What is a Gateway?
A gateway is a network device that operates across all layers of the OSI model. It acts as a protocol converter, allowing communication between two networks that use different protocols or architectures.

---

### Q10. What is the difference between Simplex and Full-Duplex?
| Mode | Description | Example |
|------|------------|---------|
| **Simplex** | One-way communication only | Keyboard → Computer |
| **Full-Duplex** | Two-way simultaneous communication | Telephone call |

---

### Q11. What is a Repeater?
A repeater is a Physical Layer (L1) device that regenerates and amplifies a weakened signal to extend the transmission distance. It does not filter or interpret data.

---

### Q12. Define the term "Encapsulation" in networking.
Encapsulation is the process of adding protocol-specific headers (and trailers) to data as it moves down through the OSI layers. Each layer wraps the data from the layer above. Example: Data → Segment → Packet → Frame → Bits.

---

### Q13. What is a Bridge?
A bridge is a Data Link Layer (L2) device that connects two LANs and filters traffic based on MAC addresses. It reduces collision domains and creates a mapping table of MAC addresses and ports.

---

### Q14. Name the layers of the TCP/IP model.
The TCP/IP model has 4 layers (bottom to top):
1. Network Access Layer (Physical + Data Link)
2. Internet Layer (Network)
3. Transport Layer
4. Application Layer

---

### Q15. What is Multiplexing?
Multiplexing is the technique of combining multiple signals or data streams into one signal over a shared medium. Types: FDM (Frequency Division), TDM (Time Division), WDM (Wavelength Division), CDM (Code Division).

---

### Q16. What is the Session Layer responsible for?
The Session Layer (Layer 5) manages sessions (connections) between applications. It handles session establishment, maintenance, synchronization (checkpoints), and termination.

---

### Q17. Define Modem.
A modem (Modulator-Demodulator) is a device that converts digital signals to analog (modulation) for transmission over telephone lines and converts analog back to digital (demodulation) at the receiver.

---

### Q18. What is a Peer-to-Peer network?
In a peer-to-peer (P2P) network, all devices have equal status — each can act as both client and server. There is no centralized server. Example: File sharing via BitTorrent.

---

### Q19. What is the function of the Presentation Layer?
The Presentation Layer (Layer 6) handles data translation (encoding/decoding), encryption/decryption, and compression/decompression. It ensures data is in a readable format for the Application Layer.

---

### Q20. Differentiate between Connection-oriented and Connectionless services.
| Feature | Connection-oriented | Connectionless |
|---------|-------------------|---------------|
| Setup | Connection established first | No prior connection |
| Reliability | Reliable, ordered delivery | Unreliable, unordered |
| Protocol | TCP | UDP |
| Analogy | Phone call | Postal mail |

---

### Q21. What is a Client-Server model?
In the Client-Server model, a dedicated server provides resources/services, and clients request those services. The server is always active; clients initiate communication. Example: Web browser (client) accessing a website (server).

---

### Q22. What is the difference between Star and Bus topology?
| Feature | Star | Bus |
|---------|------|-----|
| Central device | Hub/Switch required | No central device |
| Failure impact | One device fails → others unaffected | Backbone fails → all down |
| Cost | Higher (more cables) | Lower |
| Adding devices | Easy | Difficult |

---

### Q23. What is Latency in networking?
Latency is the total time taken for a data packet to travel from source to destination. It includes propagation delay, transmission delay, queuing delay, and processing delay.

---

### Q24. Define Half-Duplex communication.
Half-Duplex allows two-way communication but only one direction at a time. Both parties can send and receive but not simultaneously. Example: Walkie-talkie.

---

### Q25. What are the advantages of layered architecture?
1. **Modularity** — Each layer has a specific function, simplifying design
2. **Interoperability** — Standard interfaces between layers
3. **Ease of maintenance** — Changes in one layer don't affect others
4. **Reusability** — Layers can be reused across different implementations

---

### Q26. What is the difference between Analog and Digital signals?
| Feature | Analog | Digital |
|---------|--------|---------|
| Signal | Continuous waveform | Discrete values (0, 1) |
| Noise | More susceptible | Less susceptible |
| Example | Human voice | Computer data |

---

### Q27. What is Mesh Topology? Give the formula for number of links.
In mesh topology, every device is connected to every other device. It provides high redundancy and fault tolerance.
**Formula:** Number of links = **n(n-1)/2** (for full mesh, where n = number of devices)

---

### Q28. What is the role of the Network Layer?
The Network Layer (Layer 3) handles logical addressing (IP), routing packets across multiple networks, packet fragmentation/reassembly, and congestion control. Key protocol: IP.

---

### Q29. Define Throughput.
Throughput is the actual rate at which data is successfully transmitted over a network, measured in bps. It is always ≤ bandwidth due to overhead, congestion, and errors.

---

### Q30. What is the difference between Baseband and Broadband transmission?
| Feature | Baseband | Broadband |
|---------|----------|-----------|
| Signal | Digital | Analog |
| Channels | Single channel (entire bandwidth) | Multiple channels (divided bandwidth) |
| Direction | Bidirectional | Unidirectional |
| Distance | Short | Long |
| Example | Ethernet | Cable TV |

---

---

# 📝 7-MARK QUESTIONS (15)

---

### Q1. Explain the OSI Reference Model in detail with functions of each layer. ⭐⭐⭐
**Answer Structure:**
1. **Introduction** (2 lines): OSI = Open Systems Interconnection, developed by ISO, 7 layers
2. **Diagram**: Draw the 7-layer stack with PDU names
3. **Explain each layer** (1-2 lines each):
   - **Physical**: Bit transmission, cables, signals, connectors
   - **Data Link**: Framing, MAC addressing, error detection, flow control
   - **Network**: Logical addressing (IP), routing, packet forwarding
   - **Transport**: End-to-end delivery, segmentation, TCP/UDP, flow & error control
   - **Session**: Session management, synchronization checkpoints
   - **Presentation**: Encryption, compression, data format translation
   - **Application**: User interface, HTTP, FTP, SMTP, DNS
4. **Conclusion**: Each layer communicates with peer layer; encapsulation top→down, decapsulation bottom→up

---

### Q2. Compare OSI and TCP/IP models with diagram. ⭐⭐⭐
**Answer Structure:**
1. Draw both models side-by-side
2. Comparison table (minimum 7 points):
   - Number of layers (7 vs 4)
   - Developer (ISO vs DoD/DARPA)
   - Approach (Theoretical vs Practical)
   - Protocol dependency (Independent vs Dependent)
   - Session/Presentation (Separate vs Merged in Application)
   - Transport (supports both connection/connectionless vs same)
   - Network layer (connection + connectionless vs connectionless only)
   - Usage (Reference model vs Implemented on Internet)
3. Conclude with: OSI is theoretical reference; TCP/IP is practical implementation

---

### Q3. Explain different types of network topologies with diagrams, advantages, and disadvantages. ⭐⭐
**Answer Structure:**
For each topology (Bus, Star, Ring, Mesh, Tree) write:
- Definition (1 line) + Diagram
- 2 Advantages + 2 Disadvantages
- Cover at least 4-5 topologies for full marks

---

### Q4. Explain Circuit Switching, Packet Switching, and Message Switching. ⭐⭐
**Answer Structure:**
1. **Circuit Switching**: Dedicated path, 3 phases (setup→transfer→release), example: telephone. Diagram showing dedicated circuit.
2. **Packet Switching**: Data split into packets, two types:
   - Datagram (connectionless, independent routing)
   - Virtual Circuit (connection-oriented, same path)
3. **Message Switching**: Store-and-forward at each node, no dedicated path
4. Comparison table of all three
5. Conclusion with when to use each

---

### Q5. Explain different types of computer networks (LAN, MAN, WAN, PAN). ⭐
**Answer Structure:**
For each type:
- Full form + Definition (2 lines)
- Range/Coverage
- Speed
- Example
- Use case
- Include a comparison table at the end

---

### Q6. Describe the functions of various network devices (Hub, Switch, Router, Bridge, Gateway, Repeater). ⭐⭐
**Answer Structure:**
For each device:
- OSI layer it operates at
- Primary function (2-3 lines)
- Example use case
- Draw a simple network diagram showing all devices

---

### Q7. What is Multiplexing? Explain FDM, TDM, and CDM with diagrams. ⭐
**Answer Structure:**
1. Define multiplexing + why it's needed
2. **FDM**: Bandwidth divided into frequency bands, each user gets a band. Draw frequency vs time diagram.
3. **TDM**: Bandwidth divided into time slots, users take turns. Draw time-slot diagram.
4. **CDM**: Each user assigned unique code; all use full bandwidth simultaneously. Draw code matrix diagram.
5. Comparison table of all three

---

### Q8. Explain the Client-Server and Peer-to-Peer models. Compare them. ⭐
**Answer Structure:**
1. **Client-Server**: Dedicated server, clients request services. Diagram.
2. **Peer-to-Peer**: All nodes equal, each can be client/server. Diagram.
3. Comparison (5+ points): Scalability, cost, management, security, reliability
4. Examples of each

---

### Q9. What is the Transport Layer? Explain its functions in detail. ⭐⭐
**Answer Structure:**
1. Definition + Position in OSI (Layer 4)
2. Functions:
   - Segmentation & Reassembly
   - Service Point Addressing (port numbers)
   - Connection Control (TCP/UDP)
   - Flow Control
   - Error Control
3. Briefly mention TCP and UDP as transport layer protocols
4. Diagram showing segment creation

---

### Q10. Explain data flow through the OSI model using encapsulation and decapsulation. ⭐⭐
**Answer Structure:**
1. Define encapsulation (adding headers going down) and decapsulation (removing headers going up)
2. Step-by-step flow at sender:
   - Application → Data
   - Transport → Segment (+ port numbers)
   - Network → Packet (+ IP addresses)
   - Data Link → Frame (+ MAC addresses)
   - Physical → Bits
3. Reverse at receiver
4. Diagram showing both sender and receiver stacks with arrows

---

### Q11. What are the different transmission modes? Explain Simplex, Half-Duplex, and Full-Duplex. ⭐
**Answer Structure:**
1. **Simplex**: One-way only. Example: TV broadcast. Diagram.
2. **Half-Duplex**: Two-way but one at a time. Example: Walkie-talkie. Diagram.
3. **Full-Duplex**: Two-way simultaneous. Example: Telephone. Diagram.
4. Comparison table
5. Use cases for each

---

### Q12. What is Data Communication? Explain its components. ⭐
**Answer Structure:**
1. Definition: Exchange of data between two devices via a transmission medium
2. **5 Components**:
   - Message (data)
   - Sender
   - Receiver
   - Transmission Medium (channel)
   - Protocol (rules)
3. Diagram showing all 5 components
4. Brief explanation of each (2-3 lines)

---

### Q13. Explain different types of Guided and Unguided transmission media. ⭐
**Answer Structure:**
1. **Guided (Wired)**:
   - Twisted Pair Cable (UTP, STP) — cheap, short distance
   - Coaxial Cable — better shielding, used in cable TV
   - Fiber Optic Cable — fastest, uses light, long distance
2. **Unguided (Wireless)**:
   - Radio Waves — broadcasting
   - Microwaves — point-to-point
   - Infrared — short range, line of sight
3. Comparison table

---

### Q14. What is the difference between Datagram and Virtual Circuit in packet switching? ⭐
**Answer Structure:**
1. **Datagram**: Connectionless, each packet routed independently, packets may arrive out of order. Diagram.
2. **Virtual Circuit**: Connection-oriented, path established first, all packets follow same path, in-order delivery. Diagram.
3. Comparison table (7+ points): Setup, ordering, reliability, speed, header info, routing, examples

---

### Q15. Explain the concept of Layered Architecture in networking. Why is it important? ⭐
**Answer Structure:**
1. Define layered architecture (dividing network functions into modular layers)
2. Advantages:
   - Modularity
   - Separation of concerns
   - Easy debugging/maintenance
   - Interoperability
   - Standardization
3. Example: OSI Model — show how each layer has specific role
4. Concept of peer-to-peer communication
5. Concept of service access points (SAPs)
