# MODULE 4 – TRANSPORT LAYER
## Easy Exam Notes in Marathi + English

---

## TRANSPORT LAYER - Overview

### Definition

**Transport Layer म्हणजे** OSI model चा 4th layer आहे.

**In English:** The Transport Layer (Layer 4) provides end-to-end process-to-process communication between applications on different hosts.

### Position in OSI Model

```
┌───────────────────────────┐
│ 7. Application Layer      │
├───────────────────────────┤
│ 6. Presentation Layer     │
├───────────────────────────┤
│ 5. Session Layer          │
├───────────────────────────┤
│ 4. TRANSPORT LAYER ⭐      │
├───────────────────────────┤
│ 3. Network Layer          │
├───────────────────────────┤
│ 2. Data Link Layer        │
├───────────────────────────┤
│ 1. Physical Layer         │
└───────────────────────────┘
```

---

## MAIN FUNCTIONS OF TRANSPORT LAYER (6 Functions)

### 🎯 Memory Trick: "PSMFCE"
- **P** → Process delivery
- **S** → Segmentation
- **M** → Multiplexing
- **F** → Flow control
- **C** → Congestion control
- **E** → Error control

---

### 1. Process-to-Process Delivery

**Definition:** Correct application को सही process ला data deliver करना using port numbers (0-65535).

#### 📊 Diagram

```
┌──────────────────────────────────────┐
│        COMPUTER                      │
├──────────────────────────────────────┤
│  Web Browser  │ Port 80              │
│  Email Client │ Port 25/110          │
│  DNS Client   │ Port 53              │
│  Video Call   │ Port 5060            │
└──────────────────────────────────────┘
```

---

### 2. Segmentation & Reassembly

**Definition:** Large messages को छोटे segments में divide करना and receiver पर reassemble करना.

**Why?** Network has MTU (Maximum Transmission Unit) limit (~1500 bytes).

#### 📊 Diagram

```
SENDER SIDE:
Large Message (10,000 bytes)
    ↓ (Segmentation)
┌────────┬────────┬────────┬────────┐
│Seg 1   │Seg 2   │Seg 3   │Seg 4   │
│1500 B  │1500 B  │1500 B  │1500 B  │
└────────┴────────┴────────┴────────┘

RECEIVER SIDE:
    ↓ (Reassembly)
Original Large Message (10,000 bytes)
```

---

### 3. Multiplexing & Demultiplexing

**Multiplexing:** Multiple applications' data को एक stream में collect करना.

**Demultiplexing:** Incoming data को सही application को deliver करना.

#### 📊 Diagram

```
SENDER SIDE (MULTIPLEXING):
Chrome Port 80  ─┐
Gmail Port 25   ├─► MULTIPLEXER ──► Network
DNS Port 53     ─┘

RECEIVER SIDE (DEMULTIPLEXING):
Network ──► DEMULTIPLEXER ──┬─► Chrome Port 80
                            ├─► Gmail Port 25
                            └─► DNS Port 53
```

---

### 4. Flow Control

**Definition:** Fast sender को slow receiver से overwhelm होने से रोकना.

Receiver अपनी **buffer capacity** भेजता है; sender उससे ज्यादा नहीं भेजता।

---

### 5. Congestion Control

**Definition:** Network में बहुत सारे packets होने पर traffic control करना.

Transport Layer जब congestion detect करता है तो transmission rate reduce करता है।

---

### 6. Error Control

**Definition:** Checksum वापरून packets में errors detect करना.

Sender calculates checksum → Receiver recalculates → Compare करके verify करता है।

---

## HOST-TO-HOST vs PROCESS-TO-PROCESS

| Aspect | Host-to-Host | Process-to-Process |
|--------|--------------|-------------------|
| **Layer** | Network Layer (L3) | Transport Layer (L4) |
| **Addressing** | IP Address | Port Number |
| **Communication** | Between computers | Between applications |
| **Example** | 192.168.1.10 | 192.168.1.10:80 |

### Easy Analogy

```
IP Address = Building Address
Port Number = Room Number

Complete Address = 192.168.1.10:80 (Building + Room)
```

---

## UDP (User Datagram Protocol)

### Definition

**UDP म्हणजे** connectionless, unreliable, fast protocol.

### Features

| Feature | Status |
|---------|--------|
| **Connection** | ❌ No |
| **Reliability** | ❌ No |
| **Speed** | ✅ Fast |
| **Flow Control** | ❌ No |
| **Error Recovery** | ❌ No |

### UDP HEADER FORMAT (8 Bytes)

```
Bit: 0-15            | 16-31
─────────────────────────────────
Source Port          | Destination Port
─────────────────────────────────
Length               | Checksum
─────────────────────────────────
            Data (Variable)
```

### UDP Header Fields

| Field | Size | Function |
|-------|------|----------|
| **Source Port** | 16 bits | Sender process |
| **Destination Port** | 16 bits | Receiver process |
| **Length** | 16 bits | Total size (min 8) |
| **Checksum** | 16 bits | Error detection |

### Uses of UDP

- Live streaming (YouTube Live, Twitch)
- Online gaming (FPS games)
- VoIP/Video calls (WhatsApp, Skype)
- DNS queries (Domain lookup)
- DHCP (Auto IP assignment)

### 🎯 UDP Memory Trick: "SLDC"
- **S** → Source Port
- **L** → Length
- **D** → Destination Port
- **C** → Checksum

---

## TCP (Transmission Control Protocol)

### Definition

**TCP म्हणजे** connection-oriented, reliable, ordered delivery protocol.

### Features

| Feature | Status |
|---------|--------|
| **Connection** | ✅ Yes |
| **Reliability** | ✅ Yes |
| **Ordered Delivery** | ✅ Yes |
| **Flow Control** | ✅ Yes |
| **Congestion Control** | ✅ Yes |

### TCP HEADER FORMAT (20-60 Bytes)

```
Bit: 0-15            | 16-31
─────────────────────────────────────
Source Port          | Destination Port
─────────────────────────────────────
         Sequence Number (32-bit)
─────────────────────────────────────
     Acknowledgment Number (32-bit)
─────────────────────────────────────
Offset|Res|Flags|  Window Size
─────────────────────────────────────
Checksum             | Urgent Pointer
─────────────────────────────────────
    Options + Padding (if any)
─────────────────────────────────────
            Data (Variable)
```

### Important TCP Fields

| Field | Function |
|-------|----------|
| **Sequence Number** | First byte of data in segment |
| **Acknowledgment** | Next expected byte from other side |
| **Window Size** | Flow control (receiver buffer) |
| **Checksum** | Error checking |
| **Flags** | Connection management (SYN, ACK, FIN, etc.) |

---

### TCP FLAGS (6 Control Bits)

| Flag | Purpose |
|------|---------|
| **SYN** | Start connection |
| **ACK** | Acknowledgment |
| **FIN** | Finish/close connection |
| **RST** | Reset connection |
| **PSH** | Push data immediately |
| **URG** | Urgent data |

### 🎯 TCP FLAGS Memory Trick: "SAFRPU"
- **S** → SYN
- **A** → ACK
- **F** → FIN
- **R** → RST
- **P** → PSH
- **U** → URG

---

## TCP THREE-WAY HANDSHAKE

### Definition

Connection establish करण्याची process.

### 📊 Diagram

```
CLIENT                          SERVER

SYN, Seq=100 ─────────────────►
                                (Step 1)
                                
            ◄───── SYN+ACK ─────
                    Seq=300
                    Ack=101
                    (Step 2)

ACK, Seq=101, Ack=301 ────────►
                                (Step 3)

✅ CONNECTION ESTABLISHED
```

### STEPS

1. **Client sends SYN** - Seq=100, initiates connection
2. **Server responds SYN+ACK** - Seq=300, Ack=101
3. **Client sends ACK** - Seq=101, Ack=301
4. **Connection Ready** - Both sides can send data

---

## TCP vs UDP - Complete Comparison

| Feature | TCP | UDP |
|---------|-----|-----|
| **Connection** | Connection-oriented | Connectionless |
| **Reliability** | Reliable | Unreliable |
| **Speed** | Slower | Faster |
| **Header** | 20-60 bytes | 8 bytes |
| **ACK** | Yes | No |
| **Flow Control** | Yes | No |
| **Ordering** | Ordered | Unordered |
| **Uses** | Web, Email, FTP | Gaming, DNS, Streaming |

---

## COMMON TCP & UDP PORT NUMBERS

| Service | TCP | UDP | Purpose |
|---------|-----|-----|---------|
| **SSH** | 22 | - | Secure login |
| **SMTP** | 25 | - | Email sending |
| **DNS** | 53 | 53 | Domain lookup |
| **HTTP** | 80 | - | Web browsing |
| **HTTPS** | 443 | - | Secure web |
| **DHCP** | - | 67/68 | Auto IP |
| **NTP** | 123 | 123 | Time sync |

### Port Ranges

```
0-1023: Well-known (HTTP=80, SSH=22, DNS=53)
1024-49151: Registered (MySQL=3306, VNC=5900)
49152-65535: Dynamic/Private (Client-side)
```

---

## 5-MARK EXAM QUESTIONS

### Q1: Explain Functions of Transport Layer

**Answer:** Transport Layer (Layer 4) provides process-to-process communication with 6 main functions:

1. **Process-to-Process Delivery** - Uses port numbers to deliver data to correct applications
2. **Segmentation & Reassembly** - Splits large messages into segments and reassembles at receiver
3. **Multiplexing/Demultiplexing** - Combines data from multiple apps; delivers to correct app
4. **Flow Control** - Prevents fast sender from overwhelming slow receiver
5. **Congestion Control** - Reduces rate if network is congested
6. **Error Control** - Detects errors using checksums

**Memory:** PSMFCE

---

### Q2: Draw and Explain UDP Header

**Answer:** UDP Header (8 bytes fixed):

- **Source Port (16 bits)** - Sender process identifier
- **Destination Port (16 bits)** - Receiver process identifier
- **Length (16 bits)** - Total UDP packet size
- **Checksum (16 bits)** - Error detection

**Characteristics:** Connectionless, unreliable, fast. Used for gaming, DNS, streaming.

---

### Q3: Draw and Explain TCP Header

**Answer:** TCP Header (20-60 bytes):

Key fields:
- **Sequence Number** - First byte of data
- **Acknowledgment Number** - Next expected byte
- **Flags** - SYN, ACK, FIN, RST, PSH, URG
- **Window Size** - Flow control
- **Checksum** - Error detection

**Characteristics:** Connection-oriented, reliable, ordered. Used for web, email, FTP.

---

### Q4: Explain TCP Three-Way Handshake

**Answer:**

**Step 1:** Client sends SYN with Seq=x
**Step 2:** Server responds with SYN+ACK, Ack=x+1
**Step 3:** Client sends ACK with Ack=y+1

**Result:** Connection established. Both sides ready for data transfer.

---

### Q5: Differentiate TCP and UDP

TCP is reliable, ordered, connection-oriented but slower.
UDP is fast, unreliable, connectionless.

**Use TCP for:** Web, Email, FTP (reliability matters)
**Use UDP for:** Gaming, DNS, Streaming (speed matters)

---

## ✅ EXAM CHECKLIST

- [ ] Transport Layer functions (PSMFCE)
- [ ] Port numbers (0-65535)
- [ ] UDP header structure
- [ ] TCP header structure
- [ ] TCP flags (SAFRPU)
- [ ] 3-way handshake
- [ ] TCP vs UDP
- [ ] Common port numbers
- [ ] Flow control concept
- [ ] Error control concept

---

**Good Luck! 🎓📚**

*Repository: kakdekaran/notes*
