# UNIT 5 — APPLICATION LAYER
## 30 × 2-Mark Questions + 15 × 7-Mark Questions

---

# 📝 2-MARK QUESTIONS (30)

---

### Q1. What is the Application Layer?
The Application Layer is the topmost layer (Layer 7 in OSI, Layer 4 in TCP/IP). It provides network services directly to end-users and applications. Protocols: HTTP, FTP, SMTP, DNS, Telnet, SNMP.

---

### Q2. What is DNS?
DNS (Domain Name System) translates human-readable domain names (e.g., google.com) into IP addresses (e.g., 142.250.190.14). It uses a hierarchical, distributed database. Port: 53. Protocol: UDP (queries), TCP (zone transfers).

---

### Q3. Differentiate between Recursive and Iterative DNS resolution.
| Feature | Recursive | Iterative |
|---------|-----------|-----------|
| Who does the work | Local DNS does all queries | Each server gives a referral |
| Client involvement | Minimal (gets final answer) | Minimal (Local DNS makes multiple queries) |
| Load | Heavy on Local DNS | Distributed across servers |

---

### Q4. What is the port number of HTTP and HTTPS?
- **HTTP:** Port **80** (unencrypted)
- **HTTPS:** Port **443** (encrypted with SSL/TLS)
Both use TCP as the transport protocol.

---

### Q5. What is FTP? What ports does it use?
FTP (File Transfer Protocol) is used for transferring files between client and server. It uses TCP and two connections:
- **Port 21:** Control connection (commands & responses)
- **Port 20:** Data connection (actual file transfer)

---

### Q6. What is the difference between FTP and TFTP?
| Feature | FTP | TFTP |
|---------|-----|------|
| Protocol | TCP | UDP |
| Ports | 20 & 21 | 69 |
| Authentication | Yes | No |
| Operations | Full file management | Read/Write only |
| Security | Basic | None |

---

### Q7. What is SMTP?
SMTP (Simple Mail Transfer Protocol) is used to **send** emails from client to server and between mail servers. It is a **push protocol**. Port: **25**. It uses TCP.

---

### Q8. What is POP3?
POP3 (Post Office Protocol version 3) is used to **download** emails from the mail server to the local device. After download, emails are typically **deleted from server**. Port: **110**. It is a pull protocol.

---

### Q9. What is IMAP?
IMAP (Internet Message Access Protocol) is used to **access and manage** emails directly on the mail server. Emails **remain on server**, allowing access from multiple devices. Port: **143**. Supports folder management.

---

### Q10. Differentiate between SMTP and POP3.
| Feature | SMTP | POP3 |
|---------|------|------|
| Purpose | Send emails | Receive/download emails |
| Type | Push protocol | Pull protocol |
| Port | 25 | 110 |
| Direction | Client→Server, Server→Server | Server→Client |

---

### Q11. What is Telnet?
Telnet is a protocol for remote login to another computer over a network. Port: **23**. It transmits data (including passwords) in **plain text** (unencrypted), making it insecure. Replaced by SSH.

---

### Q12. What is SSH?
SSH (Secure Shell) is a protocol for secure remote login and command execution. Port: **22**. All data is **encrypted**, providing confidentiality and authentication. It is the secure replacement for Telnet.

---

### Q13. What is SNMP?
SNMP (Simple Network Management Protocol) is used to **monitor and manage** network devices (routers, switches, servers). Port: 161 (agent), 162 (trap). Components: Manager (NMS), Agent, MIB (Management Information Base).

---

### Q14. What are SNMP operations?
| Operation | Description |
|-----------|------------|
| **GET** | Manager retrieves info from agent |
| **SET** | Manager modifies a variable on agent |
| **GET-NEXT** | Manager retrieves next variable in MIB |
| **TRAP** | Agent sends unsolicited alert to manager |

---

### Q15. What is HTTP? Is it stateful or stateless?
HTTP (HyperText Transfer Protocol) is used for web communication between browsers and web servers. It is **stateless** — each request is independent; the server does not retain information about previous requests. Cookies are used to maintain state.

---

### Q16. What is the difference between Persistent and Non-Persistent HTTP?
| Feature | Non-Persistent (HTTP/1.0) | Persistent (HTTP/1.1) |
|---------|--------------------------|----------------------|
| TCP connection | New for each object | Reused for multiple objects |
| RTT per object | 2 RTT | 1 RTT (after initial setup) |
| Overhead | High | Low |

---

### Q17. What is Cryptography?
Cryptography is the technique of securing communication by converting **plaintext into ciphertext** (encryption) using algorithms and keys, and back (decryption). Goals: Confidentiality, Integrity, Authentication, Non-repudiation.

---

### Q18. Differentiate between Symmetric and Asymmetric encryption.
| Feature | Symmetric | Asymmetric |
|---------|-----------|------------|
| Keys | One shared secret key | Two keys (Public + Private) |
| Speed | Fast | Slower |
| Key distribution | Difficult | Easy (public key is open) |
| Algorithms | DES, AES | RSA |

---

### Q19. What is a Digital Signature?
A digital signature is created by encrypting a hash of the message with the sender's **private key**. The receiver verifies it using the sender's **public key**. It provides authentication, integrity, and non-repudiation.

---

### Q20. What is the RSA Algorithm?
RSA (Rivest-Shamir-Adleman) is an asymmetric cryptography algorithm that uses a pair of keys (public and private) for encryption and decryption. Encryption: C = P^e mod n. Decryption: P = C^d mod n.

---

### Q21. What is Plaintext and Ciphertext?
- **Plaintext:** The original, readable message before encryption. Example: "HELLO"
- **Ciphertext:** The encrypted, unreadable form of the message. Example: "KHOOR" (Caesar cipher +3)

---

### Q22. Name the HTTP request methods.
| Method | Purpose |
|--------|---------|
| **GET** | Retrieve resource |
| **POST** | Submit data to server |
| **PUT** | Update existing resource |
| **DELETE** | Remove a resource |
| **HEAD** | Retrieve headers only |

---

### Q23. What is Data Compression?
Data compression reduces the size of data for efficient storage and transmission. It uses an **Encoder** (compress) and **Decoder** (decompress). Types: Lossless (no data loss) and Lossy (some data loss).

---

### Q24. Differentiate between Lossless and Lossy compression.
| Feature | Lossless | Lossy |
|---------|----------|-------|
| Data loss | None | Some |
| Reversibility | Fully reversible | Not fully reversible |
| Compression ratio | Lower | Higher |
| Example | ZIP, PNG | JPEG, MP3 |
| Use | Text, code | Images, audio, video |

---

### Q25. What is the DNS Hierarchy?
DNS follows a hierarchical structure:
- **Root DNS Servers** (.) → Top-Level Domain (**TLD**: .com, .org, .in) → **Authoritative DNS** (google.com, amazon.com) → **Subdomains** (www, mail)

---

### Q26. What are DNS Record Types? Name any 3.
| Type | Purpose |
|------|---------|
| **A** | Maps domain to IPv4 address |
| **AAAA** | Maps domain to IPv6 address |
| **MX** | Specifies mail server for domain |
| **CNAME** | Alias for another domain |
| **NS** | Name server for the domain |

---

### Q27. What is the role of a URL?
A URL (Uniform Resource Locator) specifies the address of a resource on the web. Format: `protocol://domain:port/path?query#fragment`. Example: `https://www.google.com:443/search?q=test`

---

### Q28. What is the Euler's Totient Function in RSA?
Euler's Totient φ(n) = (p-1)(q-1), where p and q are prime numbers and n = p×q. It is used in RSA to determine the valid range for choosing the public key exponent (e) and computing the private key (d).

---

### Q29. What are the four goals of Cryptography?
1. **Confidentiality** — Only authorized parties can read the data
2. **Integrity** — Data is not altered during transmission
3. **Authentication** — Verifying the identity of the sender
4. **Non-repudiation** — Sender cannot deny having sent the message

---

### Q30. What is the email delivery process?
```
Sender's MUA → [SMTP] → Sender's Mail Server (MTA)
→ [SMTP] → Receiver's Mail Server (MTA)
→ [POP3/IMAP] → Receiver's MUA
```
MUA = Mail User Agent (client), MTA = Mail Transfer Agent (server)

---

---

# 📝 7-MARK QUESTIONS (15)

---

### Q1. Explain DNS with Recursive and Iterative resolution methods. Draw diagrams. ⭐⭐⭐
**Answer:**
1. Define DNS (2 lines): Domain → IP translation, hierarchical distributed database
2. DNS Hierarchy diagram: Root → TLD → Authoritative → Subdomains
3. **Recursive Resolution:**
   - Client asks Local DNS → Local DNS queries Root → TLD → Authoritative
   - Final IP returned back through the chain to client
   - Diagram with arrows showing full chain
   - Advantage: Simple for client; Disadvantage: Heavy load on Local DNS
4. **Iterative Resolution:**
   - Local DNS asks Root → gets TLD referral
   - Local DNS asks TLD → gets Authoritative referral
   - Local DNS asks Authoritative → gets final IP
   - Returns to client
   - Diagram with referral arrows
   - Advantage: Distributed load; Disadvantage: More work for Local DNS
5. DNS caching concept
6. Common record types: A, AAAA, MX, CNAME, NS

---

### Q2. Solve RSA Algorithm numerical completely. ⭐⭐⭐
**Answer:**
```
Step 1: Choose primes p = 7, q = 11
Step 2: n = 7 × 11 = 77
Step 3: φ(n) = (7-1)(11-1) = 6 × 10 = 60
Step 4: Choose e such that 1 < e < 60 and gcd(e, 60) = 1
        Try e = 7: gcd(7, 60) = 1 ✓
Step 5: Find d: d × 7 mod 60 = 1
        Try d = 43: 43 × 7 = 301, 301 mod 60 = 1 ✓

Public Key = (e, n) = (7, 77)
Private Key = (d, n) = (43, 77)

Encryption (Plaintext P = 2):
C = P^e mod n = 2^7 mod 77 = 128 mod 77 = 51

Decryption (Ciphertext C = 51):
P = C^d mod n = 51^43 mod 77 = 2 ✓
(Use modular exponentiation for large powers)
```
Always show: (1) All 5 steps with formulas, (2) gcd verification, (3) d verification, (4) Encryption, (5) Decryption proving correctness

**Alternate simpler example (p=3, q=5):**
```
n = 15, φ(n) = 8, e = 3, d = 3
Public = (3,15), Private = (3,15)
Encrypt P=8: C = 8³ mod 15 = 512 mod 15 = 2
Decrypt C=2: P = 2³ mod 15 = 8 ✓
```

---

### Q3. Compare FTP and TFTP in detail. Explain FTP working. ⭐⭐
**Answer:**
1. **FTP Working:**
   - Uses 2 parallel TCP connections:
     - Control (Port 21): Commands like LIST, RETR, STOR — persistent
     - Data (Port 20): File transfer — non-persistent (one per file)
   - Requires authentication (username/password)
   - Supports: upload, download, rename, delete, directory listing
   - Diagram: Client ↔ Control(21) ↔ Server, Client ↔ Data(20) ↔ Server
2. **FTP vs TFTP Table:**

| Feature | FTP | TFTP |
|---------|-----|------|
| Full Form | File Transfer Protocol | Trivial FTP |
| Protocol | TCP | UDP |
| Ports | 20 (data) & 21 (control) | 69 |
| Connections | 2 (control + data) | 1 |
| Authentication | Yes | No |
| Security | Basic | None |
| Complexity | Complex | Simple |
| Operations | Full management | Read/Write only |
| File size | Large files | Small files |
| Speed | Slower (reliable) | Faster (simple) |
| Use case | Web hosting, enterprise | Booting diskless devices |

---

### Q4. Explain HTTP protocol. Differentiate Persistent and Non-Persistent connections. ⭐⭐
**Answer:**
1. Define HTTP: Application layer protocol for web (client-server)
2. Port 80 (HTTP), 443 (HTTPS)
3. **Stateless** — each request independent
4. HTTP Request methods: GET, POST, PUT, DELETE, HEAD
5. HTTP Response codes: 200 OK, 301 Redirect, 404 Not Found, 500 Server Error
6. **Non-Persistent (HTTP/1.0):**
   - New TCP connection for EACH object
   - Steps: TCP open → Request → Response → TCP close (per object)
   - Time = 2 RTT per object (1 for TCP + 1 for HTTP)
   - Diagram showing multiple TCP connections
7. **Persistent (HTTP/1.1):**
   - Single TCP connection reused for all objects
   - Steps: TCP open → Request1 → Response1 → Request2 → Response2... → TCP close
   - Time = 1 RTT per object (after initial 1 RTT for TCP)
   - Supports pipelining
   - Diagram showing single TCP with multiple request-response

---

### Q5. Explain Email protocols: SMTP, POP3, and IMAP with comparison. ⭐⭐
**Answer:**
1. **Email architecture diagram:**
   Sender → MUA → [SMTP] → Sender MTA → [SMTP] → Receiver MTA → [POP3/IMAP] → MUA → Receiver
2. **SMTP (Port 25):**
   - Sends emails (push protocol)
   - Client→Server and Server→Server
   - Uses TCP, text-based commands (HELO, MAIL FROM, RCPT TO, DATA)
3. **POP3 (Port 110):**
   - Downloads emails to local device
   - Deletes from server after download
   - Simple, offline access
4. **IMAP (Port 143):**
   - Manages emails on server
   - Emails stay on server
   - Folder management, multi-device sync
5. **Comparison Table:**

| Feature | SMTP | POP3 | IMAP |
|---------|------|------|------|
| Purpose | Send | Download | Sync/Access |
| Port | 25 | 110 | 143 |
| Type | Push | Pull | Pull |
| Storage | Relay | Local (deleted from server) | Server |
| Multi-device | N/A | Poor | Excellent |
| Complexity | Medium | Simple | Complex |

---

### Q6. Explain Symmetric and Asymmetric Key Cryptography with diagrams. ⭐⭐
**Answer:**
1. **Symmetric Key (Private Key):**
   - Same key for encrypt AND decrypt
   - Sender and receiver must share secret key
   - Fast but key distribution is risky
   - Algorithms: DES, AES
   - Diagram: Plaintext → Encrypt(Key K) → Ciphertext → Decrypt(Key K) → Plaintext
2. **Asymmetric Key (Public Key):**
   - Two keys: Public Key (encrypt) + Private Key (decrypt)
   - Public key shared openly; private key secret
   - Slower but solves key distribution
   - Algorithm: RSA
   - Diagram: Plaintext → Encrypt(Public Key) → Ciphertext → Decrypt(Private Key) → Plaintext
3. **Comparison Table:**

| Feature | Symmetric | Asymmetric |
|---------|-----------|------------|
| Keys | 1 (shared) | 2 (public + private) |
| Speed | Fast | Slow |
| Key distribution | Difficult (must share secretly) | Easy (public key is open) |
| Security | Less (if key compromised) | More |
| Algorithm | DES, AES | RSA |
| Use case | Bulk data encryption | Key exchange, digital signatures |

---

### Q7. What is a Digital Signature? Explain how it works with diagram. ⭐⭐
**Answer:**
1. Define: Electronic equivalent of handwritten signature; provides authentication, integrity, non-repudiation
2. **How it works:**
   - Sender creates **hash** of message
   - Hash encrypted with sender's **Private Key** → Digital Signature
   - Message + Signature sent to receiver
   - Receiver decrypts signature with sender's **Public Key** → gets hash
   - Receiver independently hashes received message
   - If both hashes match → signature is VALID
3. **Diagram:**
```
SENDER:                          RECEIVER:
Message → Hash → Encrypt(PvtKey) = Signature    Signature → Decrypt(PubKey) → Hash₁
Message + Signature → ─────────────────────── → Message → Hash → Hash₂
                                                 If Hash₁ = Hash₂ → VALID ✓
```
4. Properties: Authentication, Integrity, Non-repudiation
5. More secure than handwritten signature
6. Used in: SSL certificates, code signing, legal documents

---

### Q8. Explain Data Compression types with examples. ⭐
**Answer:**
1. Define: Reducing data size for efficient storage and transmission
2. Components: Encoder (compress) + Decoder (decompress)
3. Compression Ratio = Original Data Size / Compressed Data Size
4. **Lossless Compression:**
   - No data loss; fully reversible
   - Removes redundancy only
   - Lower compression ratio
   - Examples: ZIP, PNG, GIF, Huffman coding, Run-Length Encoding
   - Used for: Text, source code, medical images
5. **Lossy Compression:**
   - Some data permanently lost
   - Not fully reversible
   - Higher compression ratio
   - Examples: JPEG, MP3, MP4, MPEG
   - Used for: Images, audio, video
6. Diagram: User → Encoder → Compressed → Network → Decoder → User
7. Comparison table

---

### Q9. Explain SNMP protocol with its components and operations. ⭐
**Answer:**
1. Define: Protocol for monitoring and managing network devices
2. Port: 161 (agent), 162 (trap)
3. **Components:**
   - **Manager (NMS):** Central monitoring station; sends requests
   - **Agent:** Software on each managed device; responds to manager
   - **MIB (Management Information Base):** Database of managed objects/variables
4. **Operations:**
   - **GET:** Manager reads variable from agent
   - **GET-NEXT:** Read next variable in MIB sequence
   - **SET:** Manager modifies variable on agent
   - **TRAP:** Agent sends unsolicited alert to manager (e.g., link down)
5. **SNMP Versions:** v1 (basic), v2 (improved), v3 (security added)
6. Diagram: Manager ↔ GET/SET ↔ Agent (MIB) + Agent → TRAP → Manager

---

### Q10. Explain the working of World Wide Web (WWW) and HTTP. ⭐
**Answer:**
1. **WWW:** System of interlinked hypertext documents accessed via Internet
2. Components: Web Browser (client), Web Server, HTTP protocol, URL, HTML
3. **URL format:** protocol://domain:port/path?query
4. **HTTP Working:**
   - Client sends HTTP Request (Method + URL + Headers + Body)
   - Server processes and sends HTTP Response (Status + Headers + Body)
5. HTTP methods: GET, POST, PUT, DELETE
6. Status codes: 1xx (Info), 2xx (Success), 3xx (Redirect), 4xx (Client Error), 5xx (Server Error)
7. Cookies for session management (stateless protocol)
8. HTTPS = HTTP + SSL/TLS encryption

---

### Q11. Explain Telnet and SSH. Why is SSH preferred? ⭐
**Answer:**
1. **Telnet:**
   - Remote login protocol; Port 23; TCP
   - Sends all data (including passwords) in **plaintext**
   - No encryption → vulnerable to sniffing/eavesdropping
   - NVT (Network Virtual Terminal) concept
2. **SSH:**
   - Secure remote login; Port 22; TCP
   - All data **encrypted** (symmetric + asymmetric)
   - Supports: Remote login, file transfer (SFTP/SCP), port forwarding
   - Public key authentication
3. **Comparison:**

| Feature | Telnet | SSH |
|---------|--------|-----|
| Port | 23 | 22 |
| Security | None (plaintext) | Encrypted |
| Authentication | Username/Password (plaintext) | Public key + password |
| Data integrity | No | Yes |
| Use today | Deprecated | Standard |

4. SSH is preferred because it provides confidentiality, integrity, and authentication

---

### Q12. Explain the RSA Algorithm with all steps and formulas. ⭐⭐⭐
**Answer:**
1. RSA = Rivest-Shamir-Adleman; Asymmetric key algorithm
2. **Formulas:**
   - Encryption: **C = P^e mod n**
   - Decryption: **P = C^d mod n**
   - Public Key: **(e, n)**
   - Private Key: **(d, n)**
3. **Steps:**
   - Step 1: Choose two primes p, q
   - Step 2: n = p × q
   - Step 3: φ(n) = (p-1)(q-1)
   - Step 4: Choose e: 1 < e < φ(n), gcd(e, φ(n)) = 1
   - Step 5: Find d: d × e mod φ(n) = 1
4. **Worked example** (p=3, q=11):
   - n = 33, φ(n) = 20
   - e = 3 (gcd(3,20) = 1 ✓)
   - d = 7 (7×3 = 21, 21 mod 20 = 1 ✓)
   - Public = (3, 33), Private = (7, 33)
   - Encrypt P=5: C = 5³ mod 33 = 125 mod 33 = 26
   - Decrypt C=26: P = 26⁷ mod 33 = 5 ✓
5. Security based on difficulty of factoring large numbers

---

### Q13. Explain the concept of Network Security Threats and Cryptographic Solutions. ⭐
**Answer:**
1. **Threats:**
   - **Eavesdropping:** Intercepting data in transit
   - **Man-in-the-Middle:** Attacker intercepts and modifies communication
   - **Spoofing:** Impersonating another device/user
   - **Denial of Service (DoS):** Flooding to make service unavailable
   - **Replay Attack:** Retransmitting captured data
2. **Solutions:**
   - **Encryption:** Symmetric (DES, AES) + Asymmetric (RSA)
   - **Digital Signatures:** Authentication + Non-repudiation
   - **Firewalls:** Filter incoming/outgoing traffic
   - **SSL/TLS:** Secure web communication
   - **IPSec:** Network layer security
3. Brief explanation of each solution (2-3 lines)

---

### Q14. What is DHCP? Explain its working. ⭐
**Answer:**
1. DHCP (Dynamic Host Configuration Protocol) automatically assigns IP addresses to devices on a network
2. Port: 67 (server), 68 (client). Protocol: UDP
3. **DORA Process:**
   - **D**iscover: Client broadcasts "I need an IP"
   - **O**ffer: DHCP server offers an IP address
   - **R**equest: Client requests the offered IP
   - **A**cknowledge: Server confirms assignment
4. Diagram showing 4-step exchange
5. DHCP assigns: IP, Subnet Mask, Default Gateway, DNS server
6. Lease concept: IP assigned for a limited time; must renew
7. Advantage: Eliminates manual IP configuration

---

### Q15. Explain the Application Layer protocols and their port numbers. Write short notes on any 5 protocols. ⭐⭐
**Answer:**

| Protocol | Port | Transport | Purpose |
|----------|------|-----------|---------|
| HTTP | 80 | TCP | Web browsing |
| HTTPS | 443 | TCP | Secure web |
| FTP | 20/21 | TCP | File transfer |
| SMTP | 25 | TCP | Send email |
| POP3 | 110 | TCP | Receive email |
| IMAP | 143 | TCP | Access email on server |
| DNS | 53 | UDP/TCP | Name resolution |
| Telnet | 23 | TCP | Remote login (insecure) |
| SSH | 22 | TCP | Secure remote login |
| SNMP | 161 | UDP | Network management |
| DHCP | 67/68 | UDP | Auto IP assignment |
| TFTP | 69 | UDP | Simple file transfer |

**Short notes on 5 (write 3-4 lines each):**
1. **DNS:** Translates domain names to IP. Hierarchical database. Recursive + Iterative resolution.
2. **HTTP:** Stateless web protocol. Request-response model. Methods: GET, POST. Persistent/Non-persistent.
3. **FTP:** File transfer using 2 TCP connections (control:21, data:20). Authentication required.
4. **SMTP:** Push protocol for sending email. Port 25. Text-based commands.
5. **SNMP:** Network monitoring. Manager-Agent-MIB model. Operations: GET, SET, TRAP.
