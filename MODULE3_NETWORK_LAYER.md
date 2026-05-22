# MODULE 3 – Network Layer & IP Addressing
## Easy Exam Notes in Marathi + English

---

## 1. IP ADDRESSING

### Definition

**IP Address म्हणजे** network मधील प्रत्येक device चा logical address.

**In English:** An IP address is a unique numerical label assigned to each device connected to a network.

**It identifies:**
- **Network ID** - Identifies the network
- **Host ID** - Identifies the device on that network

---

### TYPES OF IP ADDRESS

| Type | Size | Format | Use |
|------|------|--------|-----|
| **IPv4** | 32-bit | Decimal (0-255.0-255.0-255.0-255) | Current standard |
| **IPv6** | 128-bit | Hexadecimal | Future standard |

---

## IPv4 ADDRESS

### Format

```
192 . 168 . 1 . 10
 │    │    │   │
Octet1 Octet2 Octet3 Octet4
```

**Characteristics:**
- 4 octets separated by dots
- Each octet = 8 bits
- Each octet range: 0-255
- Total: 8 × 4 = **32 bits**

### IPv4 Structure

```
┌──────────────────────────────────────────────┐
│ Network ID           │ Host ID              │
└──────────────────────────────────────────────┘
```

**Example:**
```
IP: 192.168.1.10
Subnet Mask: 255.255.255.0

Network ID: 192.168.1 (first 3 octets)
Host ID: 10 (last octet)
```

---

### IPv4 HEADER FORMAT (20-60 bytes)

#### 📊 Diagram

```
Bit Position: 0              8             16            31
          ┌─────────────────────────────────────────────────┐
          │Version│  IHL  │ ToS │  Total Length (16 bits)   │
          ├─────────────────────────────────────────────────┤
          │ Identification (16 bits)  │Flags│Fragment Offset │
          ├─────────────────────────────────────────────────┤
          │ TTL  │ Protocol │  Header Checksum (16 bits)     │
          ├─────────────────────────────────────────────────┤
          │        Source IP Address (32 bits)              │
          ├─────────────────────────────────────────────────┤
          │     Destination IP Address (32 bits)            │
          ├─────────────────────────────────────────────────┤
          │  Options (if IHL > 5) + Padding (variable)      │
          └─────────────────────────────────────────────────┘
```

---

### IPv4 Header Fields - Detailed Explanation

#### **1. Version (4 bits)**
- **Function:** Specifies IP version
- **Value:** 4 for IPv4
- **Example:** 0100 (binary)

#### **2. IHL - Internet Header Length (4 bits)**
- **Function:** Length of IP header
- **Unit:** 32-bit words
- **Range:** 5-15 (minimum 5 = 20 bytes)
- **Example:** 0101 (binary) = 5 × 4 = 20 bytes

#### **3. ToS - Type of Service (8 bits)**
- **Function:** Quality of Service (QoS) indication
- **Use:** Priority of packet
- **Bits:** 
  - DSCP (6 bits) - Differentiated Services Code Point
  - ECN (2 bits) - Explicit Congestion Notification

#### **4. Total Length (16 bits)**
- **Function:** Total packet size (header + data)
- **Unit:** Bytes
- **Range:** 20-65,535 bytes
- **Maximum:** 65,535 (MTU usually 1500)

#### **5. Identification (16 bits)**
- **Function:** Unique identifier for packet
- **Use:** Reassembly of fragmented packets
- **Scope:** Per source-destination pair

#### **6. Flags (3 bits)**
- **Bit 0:** Reserved (always 0)
- **Bit 1:** DF (Don't Fragment)
  - 0 = Can fragment
  - 1 = Don't fragment
- **Bit 2:** MF (More Fragments)
  - 0 = Last fragment
  - 1 = More fragments follow

#### **7. Fragment Offset (13 bits)**
- **Function:** Position of fragment in original packet
- **Unit:** 8-byte blocks
- **Range:** 0-8191

#### **8. TTL - Time To Live (8 bits)**
- **Function:** Prevents infinite looping
- **Range:** 0-255
- **Mechanism:** 
  - Decremented by 1 at each router
  - When TTL = 0 → packet discarded
- **Typical Values:**

  - Windows: 128
  - Linux: 64
  - Mac: 64

#### **9. Protocol (8 bits)**
- **Function:** Identifies upper layer protocol
- **Common Values:**
  - 1 = ICMP (ping)
  - 6 = TCP
  - 17 = UDP
  - 41 = IPv6
  - 50 = ESP (Encryption)
  - 51 = AH (Authentication)

#### **10. Header Checksum (16 bits)**
- **Function:** Error checking for header only
- **Method:** One's complement
- **Calculation:** Recalculated at each router
- **Check:** If mismatch → packet discarded

#### **11. Source IP Address (32 bits)**
- **Function:** IP address of sender
- **Format:** 192.168.1.10
- **Use:** Reply routing

#### **12. Destination IP Address (32 bits)**
- **Function:** IP address of receiver
- **Format:** 192.168.1.20
- **Use:** Packet forwarding

#### **13. Options (variable, 0-40 bytes)**
- **Function:** Optional header fields
- **Examples:**
  - Record Route (RR)
  - Time Stamp (TS)
  - Loose Source Route (LSR)
  - Strict Source Route (SSR)
- **Padding:** Added to make header multiple of 32 bits

---

### 🎯 IPv4 HEADER MEMORY TRICK

**"Very Intelligent Teachers Teach Proper Checking"**

- **V** → **Version** (4 bits)
- **I** → **IHL** (4 bits)
- **T** → **ToS** (8 bits)
- **T** → **Total Length** (16 bits)
- **P** → **Protocol** (8 bits)
- **C** → **Checksum** (16 bits)

---

## IPv6 ADDRESS

### Format

```
2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

**Characteristics:**
- 8 groups of 16-bit hexadecimal numbers
- Separated by colons (:)
- Total: 8 × 16 = **128 bits**
- Much larger address space

### IPv6 Shortened Format

```
Full:       2001:0db8:85a3:0000:0000:8a2e:0370:7334
Shortened:  2001:db8:85a3::8a2e:370:7334
            (consecutive zeros replaced with ::)
```

---

### Features of IPv6

| Feature | Benefit |
|---------|---------|
| **128-bit addressing** | 2^128 addresses (340 undecillion) |
| **Huge address space** | No address shortage |
| **No NAT required** | Direct end-to-end communication |
| **Better security (IPsec)** | Built-in encryption/authentication |
| **Faster routing** | Simplified header |
| **Auto configuration** | SLAAC (StateLess Address AutoConfiguration) |
| **Multicast support** | More efficient |
| **Anycast support** | Route to nearest device |

---

### IPv6 HEADER FORMAT (Fixed 40 bytes)

#### 📊 Diagram

```
Bit Position: 0              8             16            31
          ┌─────────────────────────────────────────────────┐
          │Version│ Traffic Class │  Flow Label (20 bits)    │
          ├─────────────────────────────────────────────────┤
          │ Payload Length (16 bits) │Next Header│Hop Limit  │
          ├─────────────────────────────────────────────────┤
          │                                                 │
          │   Source IPv6 Address (128 bits)               │
          │   (16 bytes)                                    │
          │                                                 │
          ├─────────────────────────────────────────────────┤
          │                                                 │
          │   Destination IPv6 Address (128 bits)          │
          │   (16 bytes)                                    │
          │                                                 │
          └─────────────────────────────────────────────────┘
```

---

### IPv6 Header Fields - Detailed Explanation

#### **1. Version (4 bits)**
- **Function:** IP version
- **Value:** 6 (for IPv6)

#### **2. Traffic Class (8 bits)**
- **Function:** Packet priority/QoS
- **Replaces:** ToS from IPv4
- **Use:** Differentiated services

#### **3. Flow Label (20 bits)**
- **Function:** Identifies flow for QoS
- **Use:** Special handling for packet flow
- **Enables:** Real-time services

#### **4. Payload Length (16 bits)**
- **Function:** Size of data portion
- **Unit:** Bytes
- **Range:** 0-65,535

#### **5. Next Header (8 bits)**
- **Function:** Identifies next header type
- **Similar to:** Protocol field in IPv4
- **Values:**
  - 6 = TCP
  - 17 = UDP
  - 58 = ICMPv6
  - 59 = No Next Header

#### **6. Hop Limit (8 bits)**
- **Function:** Prevents infinite looping
- **Similar to:** TTL in IPv4
- **Decrements:** By 1 at each router
- **Typical Value:** 64

#### **7. Source IPv6 Address (128 bits)**
- **Function:** Sender address
- **Format:** 2001:db8::1
- **Fixed size:** 16 bytes

#### **8. Destination IPv6 Address (128 bits)**
- **Function:** Receiver address
- **Format:** 2001:db8::2
- **Fixed size:** 16 bytes

---

### 📊 IPv4 vs IPv6 - COMPLETE COMPARISON

| Aspect | IPv4 | IPv6 |
|--------|------|------|
| **Address Size** | 32-bit | 128-bit |
| **Address Format** | Decimal (dotted) | Hexadecimal (colon) |
| **Total Addresses** | ~4.3 billion (2^32) | ~340 undecillion (2^128) |
| **Header Size** | 20-60 bytes (variable) | 40 bytes (fixed) |
| **Address Shortage** | Yes | No |
| **NAT (Network Address Translation)** | Required | Not needed |
| **Security** | Optional (IPsec) | Built-in (IPsec) |
| **Fragmentation** | By routers & hosts | By source only |
| **Error Handling** | ICMP | ICMPv6 |
| **Broadcast** | Yes | No (uses multicast) |
| **Multicast** | Limited | Enhanced |
| **Routing** | Complex (more hops) | Simpler (fewer hops) |
| **Auto Configuration** | Manual/DHCP | SLAAC/DHCPv6 |
| **DNS** | A records | AAAA records |
| **Example Address** | 192.168.1.10 | 2001:db8::1 |
| **Adoption** | ~95% (still dominant) | ~35% (growing) |

---

## 2. SUBNETTING & SUBNET MASK

### Definition

**Subnetting म्हणजे** one network ला smaller networks मध्ये divide करणे.

**In English:** Subnetting is the process of dividing a large network into smaller, manageable sub-networks.

---

### SUBNET MASK

#### Definition

A **subnet mask** is a 32-bit number that separates:
- **Network bits** (1s in mask)
- **Host bits** (0s in mask)

#### Example

```
IP Address:     192.168.1.10
Subnet Mask:    255.255.255.0

Network:        192.168.1.0 (identifies network)
Host ID:        10 (identifies device)
Broadcast:      192.168.1.255
Usable IPs:     192.168.1.1 - 192.168.1.254
```

#### How Subnet Mask Works

```
IP Address (Binary):    11000000.10101000.00000001.00001010
Subnet Mask (Binary):   11111111.11111111.11111111.00000000
                        ↑ Network bits  ↑ Host bits

Network ID:             11000000.10101000.00000001.00000000 (192.168.1.0)
Host ID:                00000000.00000000.00000000.00001010 (10)
```

---

### DEFAULT SUBNET MASKS (Classful Addressing)

| Class | First Octet | Network Bits | Default Mask | CIDR |
|-------|-------------|--------------|--------------|------|
| **A** | 1-126 | 8 bits | 255.0.0.0 | /8 |
| **B** | 128-191 | 16 bits | 255.255.0.0 | /16 |
| **C** | 192-223 | 24 bits | 255.255.255.0 | /24 |
| **D** | 224-239 | Multicast | - | - |
| **E** | 240-255 | Reserved | - | - |

---

### SUBNETTING FORMULAS

#### **1. Number of Subnets**
```
Number of Subnets = 2^n

Where: n = number of borrowed bits from host portion
```

#### **2. Number of Hosts Per Subnet**
```
Number of Hosts = 2^h - 2

Where: h = number of remaining host bits
(Subtract 2 for network address and broadcast address)
```

#### **3. New Subnet Mask**
```
After borrowing n bits:
Usable Host Bits = Original Host Bits - n
```

#### **4. Subnet Increment (Block Size)**
```
Block Size = 2^h

Where: h = remaining host bits
```

---

### PRACTICAL SUBNETTING PROBLEM

#### **Question:** 
Subnet 192.10.20.0 into subnets that can accommodate 52 hosts each.

#### **Solution:**

##### **STEP 1 → Find Host Bits Needed**

```
Need: 2^h - 2 ≥ 52

Test values:
2^5 - 2 = 30  ❌ (too small)
2^6 - 2 = 62  ✅ (sufficient)

Therefore: h = 6 host bits needed
```

##### **STEP 2 → Determine Borrowed Bits**

```
Class C has 8 host bits originally

Borrowed bits = 8 - 6 = 2 bits

n = 2 bits borrowed for subnets
```

##### **STEP 3 → Calculate New Subnet Mask**

```
Original Mask:  255.255.255.0
Binary:         11111111.11111111.11111111.00000000

New Mask:       11111111.11111111.11111111.11000000
                (2 bits borrowed = 2 ones added)

Decimal:        255.255.255.192

CIDR Notation:  /26
(8+8+8+2 = 26 network bits)
```

##### **STEP 4 → Calculate Number of Subnets**

```
Number of Subnets = 2^n = 2^2 = 4 subnets
```

##### **STEP 5 → Verify Hosts Per Subnet**

```
Hosts Per Subnet = 2^h - 2 = 2^6 - 2 = 64 - 2 = 62 hosts

Each subnet can accommodate 62 usable hosts ✅
```

---

### FINAL ANSWER

| Parameter | Value |
|-----------|-------|
| **Original Network** | 192.10.20.0/24 |
| **New Subnet Mask** | 255.255.255.192 |
| **CIDR Notation** | /26 |
| **Number of Subnets** | 4 |
| **Hosts per Subnet** | 62 |
| **Subnet Increment (Block Size)** | 64 |

---

### SUBNET RANGES

#### **Calculation Method:**
- Block Size = 2^h = 2^6 = 64
- Start from 0, increment by 64

| Subnet | Network Address | Usable Range | Broadcast |
|--------|-----------------|--------------|-----------|
| **1** | 192.10.20.0 | 192.10.20.1 - 63 | 192.10.20.63 |
| **2** | 192.10.20.64 | 192.10.20.65 - 127 | 192.10.20.127 |
| **3** | 192.10.20.128 | 192.10.20.129 - 191 | 192.10.20.191 |
| **4** | 192.10.20.192 | 192.10.20.193 - 255 | 192.10.20.255 |

---

### SUBNETTING QUICK REFERENCE TABLE

| Host Bits | Subnets | Hosts | Mask | CIDR |
|-----------|---------|-------|------|------|
| 8 (0 borrowed) | 1 | 254 | 255.255.255.0 | /24 |
| 7 (1 borrowed) | 2 | 126 | 255.255.255.128 | /25 |
| 6 (2 borrowed) | 4 | 62 | 255.255.255.192 | /26 |
| 5 (3 borrowed) | 8 | 30 | 255.255.255.224 | /27 |
| 4 (4 borrowed) | 16 | 14 | 255.255.255.240 | /28 |
| 3 (5 borrowed) | 32 | 6 | 255.255.255.248 | /29 |
| 2 (6 borrowed) | 64 | 2 | 255.255.255.252 | /30 |

---

## 3. ROUTING PROTOCOLS

### Definition

**Routing Protocols** determine how routers exchange information and find optimal paths to forward packets.

---

### A) RIP (Routing Information Protocol)

#### **Full Form:** Routing Information Protocol

#### **Type:** Distance Vector Routing Protocol

#### **How It Works:**

1. Each router maintains **routing table**
2. Router shares entire routing table with neighbors
3. Distance measured in **hop count**
4. Updates sent every **30 seconds**

#### 📊 Diagram

```
┌────────────┐  1 hop  ┌────────────┐  1 hop  ┌────────────┐
│ Router A   ├─────────┤ Router B   ├─────────┤ Router C   │
└────────────┘         └────────────┘         └────────────┘
     ↓
  Network 1
```

#### **Distance Vector Mechanism:**

```
Router A's Routing Table:
Destination  | Next Hop    | Hop Count
─────────────┼─────────────┼──────────
Network 1    | Direct      | 0
Network 2    | Router B    | 1
Network 3    | Router B    | 2
Network 4    | Router B    | 3
```

#### **Features**

| Feature | Details |
|---------|---------|
| **Metric** | Hop Count (number of router hops) |
| **Max Hops** | 15 |
| **Unreachable** | 16 hops = unreachable |
| **Update Interval** | 30 seconds |
| **UDP Port** | 520 |
| **Versions** | RIPv1, RIPv2 |

#### **Advantages**

| Advantage | Explanation |
|-----------|-------------|
| **Simple** | Easy to understand |
| **Easy Configuration** | Minimal setup needed |
| **Low Overhead** | Simple calculations |
| **Works Everywhere** | Universal support |

#### **Disadvantages**

| Disadvantage | Explanation |
|--------------|-------------|
| **Slow Convergence** | Takes time to learn new routes |
| **Inefficient** | 30-second updates waste bandwidth |
| **Limited Scalability** | Max 15 hops = small networks only |
| **Poor Route Selection** | Uses only hop count, not bandwidth |
| **Counted-to-Infinity Problem** | Routing loops possible |
| **Large Overhead** | Sends entire table regularly |

#### **Use Cases**

- Small networks
- Simple network topologies
- Legacy systems

#### 🎯 Memory Trick

**"RIP Counts Hops"** (हॉप गिनता है)

---

### B) OSPF (Open Shortest Path First)

#### **Full Form:** Open Shortest Path First

#### **Type:** Link State Routing Protocol

#### **How It Works:**

1. Each router builds **complete network map** (topology)
2. Uses **Dijkstra's shortest path algorithm**
3. Calculates **shortest path** to each network
4. Shares only **changed information**
5. **Event-driven updates** (not periodic)

#### 📊 Diagram

```
        ┌─────────────────┐
        │   Router A      │
        └────────┬────────┘
                / \
              5/   \3
              /     \
             /       \
    ┌───────┘         └───────┐
    │                         │
    │                         │
┌───┴──────┐           ┌──────┴────┐
│ Router B  │     1     │ Router C   │
│           ├───────────┤           │
└───────────┘           └────────────┘

OSPF chooses: A→C (cost 3) instead of A→B→C (cost 6)
```

#### **Cost Calculation**

```
Cost = 100 Mbps / Link Speed

Example:
- 100 Mbps link → Cost = 100/100 = 1
- 10 Mbps link → Cost = 100/10 = 10
- 1 Gbps link → Cost = 100/1000 = 0.1
```

#### **Dijkstra's Algorithm**

```
Algorithm:
1. Start at source router
2. Calculate cost to directly connected routers
3. Choose router with lowest cost
4. From that router, recalculate costs
5. Repeat until all routers reached
6. Build shortest path tree
```

#### **Features**

| Feature | Details |
|---------|---------|
| **Metric** | Cost (based on bandwidth) |
| **Maximum Paths** | No limit |
| **Convergence** | Fast (seconds) |
| **Updates** | Event-driven (only changes) |
| **Protocol** | IP protocol 89 |
| **Areas** | Hierarchical (backbone + areas) |

#### **Advantages**

| Advantage | Explanation |
|-----------|-------------|
| **Fast Convergence** | Quickly adapts to changes |
| **Scalable** | Works for large networks |
| **Efficient Routing** | Uses bandwidth, not just hops |
| **Bandwidth Aware** | Considers link speed |
| **Event-Driven** | Updates only when needed |
| **Hierarchical** | Areas reduce overhead |
| **Lower Overhead** | Minimal bandwidth usage |
| **Load Balancing** | Distributes traffic |

#### **Disadvantages**

| Disadvantage | Explanation |
|--------------|-------------|
| **Complex Configuration** | Difficult to set up |
| **Higher CPU/Memory** | More processing needed |
| **Steeper Learning Curve** | Harder to understand |
| **Requires Planning** | Network design needed |

#### **OSPF Hierarchical Structure**

```
┌─────────────────────────────────────┐
│     OSPF Autonomous System (AS)     │
├─────────────────────────────────────┤
│   Backbone Area (Area 0)            │
│   ┌─────────────────────────────┐   │
│   │ ABR: Area Border Router     │   │
│   └──────────┬──────────────────┘   │
│         ↑    ↓                       │
│    ┌────┴────┴────┐                  │
│    │               │                 │
│  Area 1         Area 2               │
│  (Regular)      (Stub)               │
│                                      │
└─────────────────────────────────────┘

Router Types:
- Internal Router: Inside one area
- Area Border Router (ABR): Between areas
- Backbone Router: In backbone area
- ASBR: Connects to other ASes
```

#### **Use Cases**

- Large networks
- Enterprise networks
- ISP backbones
- Complex topologies

#### 🎯 Memory Trick

**"OSPF Finds Shortest Path Fast"** (सबसे छोटा रास्ता तेजी से)

---

### 📊 RIP vs OSPF - COMPLETE COMPARISON

| Feature | RIP | OSPF |
|---------|-----|------|
| **Type** | Distance Vector | Link State |
| **Metric** | Hop Count | Cost (Bandwidth) |
| **Maximum Hops** | 15 (unreachable at 16) | No limit |
| **Convergence** | Slow (minutes) | Fast (seconds) |
| **Scalability** | Small networks | Large networks |
| **Bandwidth Usage** | High (periodic updates) | Low (event-driven) |
| **Update Frequency** | 30 seconds (periodic) | Only when changes occur |
| **Complexity** | Simple | Complex |
| **CPU/Memory** | Low | High |
| **Route Selection** | Poor (hops only) | Excellent (bandwidth aware) |
| **Load Balancing** | Limited | Advanced |
| **Hierarchical** | No | Yes (areas) |
| **Routing Loop** | Possible | Not possible (SPF) |
| **Protocol Number** | UDP 520 | IP 89 |
| **Version** | RIPv1, RIPv2 | OSPFv2, OSPFv3 |
| **Best For** | Small offices | Enterprise networks |

---

## 4. NAT (Network Address Translation)

### Definition

**NAT म्हणजे** private IP address को public IP address मध्ये convert करणे.

**In English:** Network Address Translation is a technique that allows multiple devices with private IP addresses to communicate with external networks using a single public IP address.

---

### Purpose of NAT

| Purpose | Explanation |
|---------|-------------|
| **Save Public IPs** | Multiple devices share one public IP |
| **Security** | Hide internal network structure |
| **Firewall** | Acts as basic firewall |
| **Connect Incompatible Networks** | Bridge different addressing schemes |
| **IP Conservation** | Reduce IPv4 address shortage |

---

### How NAT Works

```
Private Network              Router (NAT)         Public Internet
                            ┌──────────┐
192.168.1.10:5000 ──────────┤ NAT      ├──────── 203.0.113.50:8000
192.168.1.20:5001 ──────────┤ Table    ├──────── 203.0.113.50:8001
192.168.1.30:5002 ──────────┤          ├──────── 203.0.113.50:8002
                            └──────────┘
                             (Mapping)
```

**NAT Table (Example):**

| Private IP:Port | Public IP:Port |
|-----------------|----------------|
| 192.168.1.10:5000 | 203.0.113.50:8000 |
| 192.168.1.20:5001 | 203.0.113.50:8001 |
| 192.168.1.30:5002 | 203.0.113.50:8002 |

---

### TYPES OF NAT

#### **1. STATIC NAT**

##### **Mapping:**
```
One Private IP Address ↔ One Public IP Address
(1:1 mapping - permanent)
```

##### **Working:**
- Each private IP permanently mapped to specific public IP
- Fixed relationship
- One-to-one basis

##### **Advantages**
- Permanent mapping
- Easier for external access
- Good for servers

##### **Disadvantages**
- Requires many public IPs
- Expensive
- Limited scalability

##### **Use Cases**
- Web servers
- Mail servers
- Database servers
- Systems requiring external access

##### 📊 Diagram

```
Private Network              NAT (Static)        Public Internet
┌──────────────┐            ┌─────────┐         ┌──────────────┐
│ 192.168.1.10 ├────────────┤ Maps to ├────────→│ 203.0.113.1  │
└──────────────┘            └─────────┘         └──────────────┘

┌──────────────┐            ┌─────────┐         ┌──────────────┐
│ 192.168.1.20 ├────────────┤ Maps to ├────────→│ 203.0.113.2  │
└──────────────┘            └─────────┘         └──────────────┘

┌──────────────┐            ┌─────────┐         ┌──────────────┐
│ 192.168.1.30 ├────────────┤ Maps to ├────────→│ 203.0.113.3  │
└──────────────┘            └─────────┘         └──────────────┘
```

---

#### **2. DYNAMIC NAT**

##### **Mapping:**
```
Private IP Address ↔ Public IP Address Pool
(Many private IPs map to multiple public IPs)
```

##### **Working:**
- Router has pool of public IPs
- Allocates public IP from pool when needed
- Releases IP when connection closes
- Different mappings each time

##### **Advantages**
- Fewer public IPs needed than Static NAT
- More efficient than Static NAT
- Automatic allocation
- More scalable

##### **Disadvantages**
- Not permanent (IPs change)
- More complex management
- Still requires multiple public IPs

##### **Use Cases**
- Medium-sized networks
- Organizations with limited public IPs
- Temporary connection needs

##### 📊 Diagram

```
Private Network              NAT (Dynamic)       Public Internet
                            ┌──────────────┐
192.168.1.10 ────────────→ │ Public IP Pool  │ → 203.0.113.50 (Time 1)
192.168.1.10 ────────────→ │ (10 addresses)  │ → 203.0.113.51 (Time 2)
                            └──────────────┘

192.168.1.20 ────────────→ │ Public IP Pool  │ → 203.0.113.52 (Time 1)
192.168.1.20 ────────────→ │ (10 addresses)  │ → 203.0.113.53 (Time 2)
                            └──────────────┘
```

---

#### **3. PAT (Port Address Translation) / NAT Overload**

##### **Mapping:**
```
Many Private IPs + Many Private Ports ↔ One Public IP + Multiple Public Ports
(Many-to-One mapping using ports)
```

##### **Working:**
```
Private IP:Port          → Public IP:Port
192.168.1.10:5000        → 203.0.113.50:8000
192.168.1.20:5000        → 203.0.113.50:8001
192.168.1.30:5000        → 203.0.113.50:8002

(Same private port, different public ports)
```

##### **Port Translation Mechanism:**

```
Original Packet:
Source: 192.168.1.10:5000
Destination: 10.0.0.1:80

Translated Packet:
Source: 203.0.113.50:8000
Destination: 10.0.0.1:80

Return Packet:
Source: 10.0.0.1:80
Destination: 203.0.113.50:8000

PAT converts back to:
Source: 10.0.0.1:80
Destination: 192.168.1.10:5000
```

##### **Advantages**
- Only one public IP needed
- Most efficient IP usage
- Supports unlimited devices (with different ports)
- Very scalable

##### **Disadvantages**
- External access difficult (incoming connections)
- Port forwarding required for services
- Adds processing overhead
- Can have port conflicts

##### **Use Cases**
- Home WiFi routers (most common)
- Small office networks
- Soho (Small Office Home Office)
- Situations with limited public IPs

##### 📊 Diagram

```
┌─────────────────────────────────────────────────┐
│         Private Network (192.168.1.0/24)        │
│                                                 │
│   PC1:5000  PC2:5001  PC3:5002  PC4:5003      │
│     │         │         │         │            │
│     └─────────┴─────────┴─────────┘            │
│                │                               │
│          ┌─────────────┐                       │
│          │   ROUTER    │                       │
│          │   (NAT)     │                       │
│          └─────┬───────┘                       │
│                │                               │
└────────────────┼───────────────────────────────┘
                 │
    ┌────────────┴────────────┐
    │                         │
 Port 8000                 Port 8001
Public IP: 203.0.113.50:8000
Public IP: 203.0.113.50:8001
Public IP: 203.0.113.50:8002
Public IP: 203.0.113.50:8003

(One public IP, multiple ports for multiple devices)
```

---

### 📊 NAT TYPES COMPARISON

| Feature | Static NAT | Dynamic NAT | PAT |
|---------|-----------|------------|-----|
| **Mapping** | 1:1 (permanent) | N:M (temporary) | N:1 (using ports) |
| **Public IPs Needed** | Same as private IPs | Less than private IPs | Only 1 |
| **Cost** | Expensive | Moderate | Cheap |
| **Configuration** | Manual | Automatic | Automatic |
| **Scalability** | Poor | Good | Excellent |
| **External Access** | Easy | Difficult | Very Difficult |
| **Port Forwarding** | Not needed | Not needed | Required |
| **Use Case** | Servers | Medium networks | Home/Small office |
| **Typical Users** | Enterprise servers | ISPs | Home routers |

---

### REAL-WORLD NAT EXAMPLE - Home WiFi Router

#### **Scenario:**

```
Three devices on home WiFi connect to internet

Device 1: 192.168.1.10 (Laptop browsing www.google.com)
Device 2: 192.168.1.20 (Phone watching YouTube)
Device 3: 192.168.1.30 (Tablet downloading email)

All devices share:
Public IP: 203.0.113.50
```

#### **NAT Table Created:**

| Device | Private IP:Port | Public IP:Port | Destination |
|--------|-----------------|----------------|-------------|
| Laptop | 192.168.1.10:54321 | 203.0.113.50:10001 | 142.251.41.14:443 (google.com) |
| Phone | 192.168.1.20:54322 | 203.0.113.50:10002 | 172.217.14.206:443 (youtube.com) |
| Tablet | 192.168.1.30:54323 | 203.0.113.50:10003 | 64.233.165.19:993 (gmail.com) |

#### **Packet Translation Process:**

```
1. Laptop sends packet:
   Source: 192.168.1.10:54321
   Destination: 142.251.41.14:443

2. Router performs PAT:
   Source: 203.0.113.50:10001
   Destination: 142.251.41.14:443

3. Reply comes back:
   Source: 142.251.41.14:443
   Destination: 203.0.113.50:10001

4. Router translates back:
   Source: 142.251.41.14:443
   Destination: 192.168.1.10:54321

5. Laptop receives response
```

---

### Common NAT Issues & Solutions

| Problem | Cause | Solution |
|---------|-------|----------|
| **Cannot access from outside** | Incoming connections blocked | Port forwarding |
| **Port conflicts** | Multiple same ports | Use different ports |
| **Connection drops** | Session timeout | Increase timeout value |
| **Slow speeds** | NAT processing overhead | Upgrade router |
| **Cannot run server** | Incoming blocked | DMZ or port forward |

---

## ✅ LAST MINUTE MEMORY TRICKS

### IP ADDRESSING

```
🎯 Quick Remembering:

IPv4:
├─ 32 bits (4 octets)
├─ Decimal format (0-255.0-255...)
├─ Limited addresses (~4.3 billion)
└─ Currently dominant

IPv6:
├─ 128 bits (8 groups of 16-bit hex)
├─ Hexadecimal format
├─ Huge address space (340 undecillion)
└─ Future standard

IPv4 Header Memory:
"Very Intelligent Teachers Teach Proper Checking"
V→Version, I→IHL, T→ToS, T→Total Length, P→Protocol, C→Checksum
```

---

### SUBNETTING

```
🎯 Quick Formulas:

Subnets = 2^n (where n = borrowed bits)
Hosts = 2^h - 2 (where h = host bits remaining)

Quick Reference:
├─ /24 = 1 subnet, 254 hosts
├─ /25 = 2 subnets, 126 hosts each
├─ /26 = 4 subnets, 62 hosts each
├─ /27 = 8 subnets, 30 hosts each
├─ /28 = 16 subnets, 14 hosts each
└─ /30 = 64 subnets, 2 hosts each (router links)

Default Masks:
├─ Class A: /8 (255.0.0.0)
├─ Class B: /16 (255.255.0.0)
└─ Class C: /24 (255.255.255.0)
```

---

### ROUTING PROTOCOLS

```
🎯 Quick Comparison:

RIP (Distance Vector):
├─ Counts HOPS
├─ Max 15 hops
├─ 30-second updates
├─ Simple but SLOW
└─ Small networks only

OSPF (Link State):
├─ Uses COST (bandwidth)
├─ No hop limit
├─ Event-driven updates
├─ Complex but FAST
└─ Large networks

Best for:
├─ Small office → RIP
└─ Enterprise → OSPF
```

---

### NAT TYPES

```
🎯 Quick Comparison:

STATIC NAT:
├─ 1:1 mapping
├─ Permanent
├─ Many public IPs needed
└─ Servers (costly)

DYNAMIC NAT:
├─ N:M mapping
├─ Temporary
├─ Fewer public IPs
└─ Medium networks

PAT (NAT Overload):
├─ N:1 mapping (many-to-one)
├─ Uses different PORTS
├─ Only 1 public IP
└─ Home WiFi routers ⭐

Most Common: PAT (home routers use this)
```

---

## ✅ EXAM CHECKLIST - MODULE 3

Before your exam, verify you know:

- [ ] Definition of IP address
- [ ] Network ID and Host ID
- [ ] IPv4 format (32-bit, 4 octets)
- [ ] IPv6 format (128-bit, hexadecimal)
- [ ] All 10 fields of IPv4 header
- [ ] IPv4 header memory trick
- [ ] Meaning of Version, IHL, ToS, Total Length, TTL, Protocol, Checksum
- [ ] IPv6 advantages over IPv4
- [ ] All fields of IPv6 header
- [ ] IPv4 vs IPv6 comparison
- [ ] Definition of subnet mask
- [ ] Default subnet masks for Classes A, B, C
- [ ] Subnetting formula: 2^n for subnets
- [ ] Subnetting formula: 2^h - 2 for hosts
- [ ] How to solve practical subnetting problems
- [ ] CIDR notation
- [ ] Definition of RIP protocol
- [ ] RIP characteristics (15 hops max, 30-sec updates)
- [ ] RIP advantages and disadvantages
- [ ] Definition of OSPF protocol
- [ ] OSPF uses shortest path (Dijkstra algorithm)
- [ ] OSPF hierarchical areas
- [ ] OSPF advantages and disadvantages
- [ ] RIP vs OSPF comparison
- [ ] Definition of NAT
- [ ] Purpose of NAT
- [ ] Static NAT (1:1 permanent mapping)
- [ ] Dynamic NAT (N:M temporary mapping)
- [ ] PAT (Port Address Translation) - N:1 using ports
- [ ] NAT types comparison
- [ ] When to use each NAT type
- [ ] Memory tricks for all concepts
- [ ] All diagrams

---

## 📥 HOW TO DOWNLOAD AS PDF

### **Method 1: Browser Print (EASIEST)**
```
1. Go to: https://github.com/kakdekaran/notes/blob/main/MODULE3_NETWORK_LAYER.md
2. Press: Ctrl+P (Windows) or Cmd+P (Mac)
3. Click: "Save as PDF"
4. Download ✅
```

### **Method 2: Online Converter**
- Visit: https://md-to-pdf.herokuapp.com/
- Paste: https://raw.githubusercontent.com/kakdekaran/notes/main/MODULE3_NETWORK_LAYER.md
- Click: Convert ✅

### **Method 3: VS Code**
- Install: "Markdown PDF" extension
- Right-click file → Markdown PDF ✅

### **Method 4: Typora**
- Open in Typora → File → Export as PDF ✅

---

**Good Luck with your exam! 🎓📚**

*Last Updated: 2026-05-22*
*Repository: kakdekaran/notes*
