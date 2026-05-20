# 🎨 COMPUTER NETWORKS — PROTOCOL DIAGRAMS
### Master Diagram Cheat Sheet for AKTU Exams

> [!TIP]
> **Exam Strategy:** Examiners love diagrams. Use these simplified ASCII layouts to easily redraw them on your answer sheet. A well-drawn diagram can guarantee full marks even if your theory is brief.

---

## 1. TCP (Transmission Control Protocol)

### 3-Way Handshake (Connection Establishment)
```text
   CLIENT                                            SERVER
     |                                                 |
     | ─────── SYN (seq=x) ──────────────────────────→ |
     |                                                 |
     | ←────── SYN + ACK (seq=y, ack=x+1) ──────────── |
     |                                                 |
     | ─────── ACK (ack=y+1) ────────────────────────→ |
     |                                                 |
     ====== CONNECTION ESTABLISHED =====================
```

### 4-Way Handshake (Connection Termination)
```text
   CLIENT                                            SERVER
     |                                                 |
     | ─────── FIN ──────────────────────────────────→ |
     |                                                 |
     | ←────── ACK ─────────────────────────────────── |
     |                                                 |
     | ←────── FIN ─────────────────────────────────── |
     |                                                 |
     | ─────── ACK ──────────────────────────────────→ |
     |                                                 |
     ====== CONNECTION CLOSED ==========================
```

---

## 2. UDP (User Datagram Protocol)
```text
   CLIENT                                            SERVER
     |                                                 |
     | ─────── Data (Datagram 1) ────────────────────→ |
     |                                                 |
     | ─────── Data (Datagram 2) ────────────────────→ |
     |                                                 |
     | ←────── Data (Datagram 3) ───────────────────── |
     |                                                 |
     (No setup, no ACKs, independent packets)
```

---

## 3. DHCP (Dynamic Host Configuration Protocol)
**Remember: DORA Process (Discover, Offer, Request, Acknowledge)**
```text
   DHCP CLIENT (Port 68)                       DHCP SERVER (Port 67)
     |                                                 |
     | ─────── DHCP DISCOVER (Broadcast) ────────────→ |
     |         "I need an IP address"                  |
     |                                                 |
     | ←────── DHCP OFFER (Unicast/Broadcast) ──────── |
     |         "Here is IP 192.168.1.50"               |
     |                                                 |
     | ─────── DHCP REQUEST (Broadcast) ─────────────→ |
     |         "I accept 192.168.1.50"                 |
     |                                                 |
     | ←────── DHCP ACK (Unicast/Broadcast) ────────── |
     |         "Confirmed. Lease is yours."            |
     |                                                 |
```

---

## 4. DNS (Domain Name System)

### Recursive Resolution (Local DNS does the work)
```text
  CLIENT         LOCAL DNS          ROOT DNS         TLD DNS       AUTH DNS
    |               |                  |                |             |
    |── 1. Query ──→|                  |                |             |
    |               |── 2. Query ─────→|                |             |
    |               |                  |                |             |
    |               |←─ 3. Response ───|                |             |
    |               |                  |                |             |
    |               |── 4. Query ──────────────────────→|             |
    |               |                  |                |             |
    |               |←─ 5. Response ────────────────────|             |
    |               |                  |                |             |
    |               |── 6. Query ────────────────────────────────────→|
    |               |                  |                |             |
    |               |←─ 7. Final IP ──────────────────────────────────|
    |←─ 8. Final IP─|                  |                |             |
```

### Iterative Resolution (Server gives referrals)
```text
  CLIENT         LOCAL DNS          ROOT DNS         TLD DNS       AUTH DNS
    |               |                  |                |             |
    |── 1. Query ──→|                  |                |             |
    |               |── 2. Query ─────→|                |             |
    |               |←─ 3. Referral ───|                |             |
    |               |                  |                |             |
    |               |── 4. Query ──────────────────────→|             |
    |               |←─ 5. Referral ────────────────────|             |
    |               |                  |                |             |
    |               |── 6. Query ────────────────────────────────────→|
    |               |←─ 7. Final IP ──────────────────────────────────|
    |←─ 8. Final IP─|                  |                |             |
```
*(In iterative, Root/TLD servers reply with "I don't know, ask this other server")*

---

## 5. FTP (File Transfer Protocol)
**Requires TWO separate TCP connections.**
```text
   FTP CLIENT                                        FTP SERVER
     |                                                 |
     | ═══════ Control Connection (Port 21) ══════════ |  (Persistent)
     |         Commands (USER, PASS, RETR)             |
     |                                                 |
     | ─────── Data Connection (Port 20) ────────────→ |  (Non-Persistent)
     |         File Transfer (File 1)                  |
     | ─────── Connection Closed ────────────────────→ |
     |                                                 |
     | ─────── Data Connection (Port 20) ────────────→ |  (Opened again)
     |         File Transfer (File 2)                  |
     | ─────── Connection Closed ────────────────────→ |
     |                                                 |
```

---

## 6. HTTP (HyperText Transfer Protocol)

### Non-Persistent (HTTP/1.0) - e.g., 2 Objects
```text
   CLIENT                                            SERVER
     |                                                 |
     | ── TCP SYN, SYN-ACK, ACK ─────────────────────→ | (TCP Setup 1)
     | ── HTTP GET index.html ───────────────────────→ |
     | ←─ HTTP Response (HTML) ─────────────────────── |
     | ── TCP FIN, ACK... ───────────────────────────→ | (TCP Teardown)
     |                                                 |
     | ── TCP SYN, SYN-ACK, ACK ─────────────────────→ | (TCP Setup 2)
     | ── HTTP GET image.jpg ────────────────────────→ |
     | ←─ HTTP Response (Image) ────────────────────── |
     | ── TCP FIN, ACK... ───────────────────────────→ | (TCP Teardown)
```

### Persistent (HTTP/1.1) - e.g., 2 Objects
```text
   CLIENT                                            SERVER
     |                                                 |
     | ── TCP SYN, SYN-ACK, ACK ─────────────────────→ | (Single TCP Setup)
     |                                                 |
     | ── HTTP GET index.html ───────────────────────→ |
     | ←─ HTTP Response (HTML) ─────────────────────── |
     |                                                 |
     | ── HTTP GET image.jpg ────────────────────────→ |
     | ←─ HTTP Response (Image) ────────────────────── |
     |                                                 |
     | ── TCP FIN, ACK... ───────────────────────────→ | (TCP Teardown)
```

---

## 7. Email Flow (SMTP, POP3, IMAP)
```text
  SENDER                  SENDER'S                    RECEIVER'S                 RECEIVER
  CLIENT                MAIL SERVER                  MAIL SERVER                 CLIENT
 (e.g. Outlook)          (e.g. Gmail)               (e.g. Yahoo)              (e.g. Phone)
     |                        |                          |                         |
     | ─── 1. Push Message ─→ |                          |                         |
     |      (SMTP - Port 25)  |                          |                         |
     |                        | ─── 2. Push Message ───→ |                         |
     |                        |     (SMTP - Port 25)     |                         |
     |                        |                          |                         |
     |                        |                          | ←── 3. Pull Message ─── |
     |                        |                          | (POP3: 110 / IMAP: 143) |
```

---

## 8. SNMP (Simple Network Management Protocol)
```text
   SNMP MANAGER (NMS)                                SNMP AGENT (Router/Switch)
     |                                                 |
     | ── GET Request (Port 161) ────────────────────→ |
     |    "What is your CPU usage?"                    |
     |                                                 |
     | ←─ GET Response ─────────────────────────────── |
     |    "CPU is at 45%"                              |
     |                                                 |
     | ── SET Request (Port 161) ────────────────────→ |
     |    "Change interface state to DOWN"             |
     |                                                 |
     | ←─ SET Response ─────────────────────────────── |
     |    "State changed successfully"                 |
     |                                                 |
     |                                                 |
     | ←─ TRAP Message (Port 162) ──────────────────── | (Unsolicited Alert)
     |    "ALERT: Link just went down!"                |
```
