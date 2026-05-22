# MODULE 2 – Physical & Data Link Layer
## Easy Exam Notes in Marathi + English

---

## 1. Network Topologies

### Definition

**Topology म्हणजे** network devices कसे connect आहेत त्याची structure/layout.

**In English:** A network topology is the physical or logical arrangement of network devices and their interconnections.

---

### A) BUS TOPOLOGY

#### 📊 Diagram

```
PC1 ---- PC2 ---- PC3 ---- PC4
  |
  |
Backbone Cable (Main Cable)
```

#### **Working**

सर्व devices एकाच main cable ला connect असतात.

**How it works:**
- Single central cable connects all devices
- Data transmitted to all devices
- Only intended device processes it
- Linear arrangement

#### **Advantages**

| Advantage | Explanation |
|-----------|-------------|
| **Cheap** | Low cost implementation |
| **Easy Installation** | Simple to set up |
| **Less Cable Required** | Minimal cabling needed |
| **Easy Expansion** | Adding devices is simple |

#### **Disadvantages**

| Disadvantage | Explanation |
|--------------|-------------|
| **Single Point of Failure** | Backbone cable fail → complete network fail |
| **Heavy Traffic** | Too much traffic → slow speed |
| **Collision** | Devices collide on same cable |
| **Limited Distance** | Cable length limitation |
| **Difficult Troubleshooting** | Hard to identify problems |

#### 🎯 Memory Trick

**"Single cable = Bus"** (एकच cable = Bus)

---

### B) STAR TOPOLOGY

#### 📊 Diagram

```
             PC1
              |
              |
PC2 ------- SWITCH ------- PC3
              |
              |
             PC4
             
(Central device connects all)
```

#### **Working**

सर्व devices central hub/switch ला connect असतात.

**How it works:**
- Central device (Switch/Hub) is the center
- Each device connects directly to center
- Star-like shape
- Device-to-device communication through center

#### **Advantages**

| Advantage | Explanation |
|-----------|-------------|
| **Most Common** | Industry standard topology |
| **Fault Tolerant** | One device fail → network continues |
| **Easy Troubleshooting** | Simple to identify problems |
| **High Reliability** | Better overall reliability |
| **Scalable** | Easy to add/remove devices |
| **Performance** | Better speed than bus |

#### **Disadvantages**

| Disadvantage | Explanation |
|--------------|-------------|
| **Central Point Failure** | Switch fail → complete network fail |
| **More Cable Required** | Extra cabling to center |
| **Expensive** | More hardware needed |
| **Hub/Switch Cost** | Central device is costly |

#### 🎯 Memory Trick

**"Everything around center"** (सर्व काही मध्यभागी)

---

### C) RING TOPOLOGY

#### 📊 Diagram

```
      PC1 ------- PC2
       |           |
       |           |
      PC4 ------- PC3

(Circular connection)
```

#### **Working**

Data circular path मध्ये travel करतो.

**How it works:**
- Devices arranged in circular path
- Data travels in one direction (or both)
- Each device forwards to next device
- Token passing mechanism
- Used in Token Ring network

#### **Advantages**

| Advantage | Explanation |
|-----------|-------------|
| **Equal Access** | All devices equal opportunity |
| **No Data Collision** | Controlled by token |
| **Fair Distribution** | Resources equally shared |
| **Predictable** | Behavior is predictable |

#### **Disadvantages**

| Disadvantage | Explanation |
|--------------|-------------|
| **Single Device Failure** | One device fail → entire network affected |
| **Unidirectional** | Data flow in one direction |
| **Difficult Troubleshooting** | Complex to diagnose issues |
| **Cable Break** | Ring breaks → network breaks |
| **Slow Speed** | Sequential processing |

#### 🎯 Memory Trick

**"Circle Network"** (गोल नेटवर्क)

---

### D) MESH TOPOLOGY

#### 📊 Diagram

```
        PC1 -------- PC2
         |\          /|
         | \        / |
         |  \      /  |
         |   \    /   |
         |    \  /    |
         |     \/     |
         |     /\     |
         |    /  \    |
         |   /    \   |
         |  /      \  |
         | /        \ |
        PC3 -------- PC4

(Every device connected to every other)
```

#### **Working**

Every device connects to every other device.

**How it works:**
- Direct connection between all devices
- Multiple paths available
- Data can travel multiple routes
- Highly connected network

#### **Types**

| Type | Description |
|------|-------------|
| **Full Mesh** | Every device connected to every other |
| **Partial Mesh** | Some devices have redundant connections |

#### **Advantages**

| Advantage | Explanation |
|-----------|-------------|
| **Very Reliable** | Multiple paths ensure connectivity |
| **Fault Tolerant** | No single point of failure |
| **Multiple Paths** | Data can take alternate routes |
| **High Redundancy** | High backup capability |
| **Security** | Direct connections more secure |

#### **Disadvantages**

| Disadvantage | Explanation |
|--------------|-------------|
| **Very Expensive** | Lots of cables required |
| **Complex Installation** | Difficult to set up |
| **Many Cables Needed** | Excessive cabling |
| **Difficult Maintenance** | Hard to manage |
| **Not Scalable** | Difficult to expand |

#### 🎯 Memory Trick

**"Everyone connected to everyone"** (सब एक-दुसरे से जुड़े हैं)

---

### E) TREE TOPOLOGY

#### 📊 Diagram

```
                MAIN SWITCH
                 /      \
                /        \
            SWITCH1     SWITCH2
             /   \        /   \
           PC1  PC2    PC3   PC4
           
(Hierarchical structure)
```

#### **Working**

Hierarchical combination of star + bus.

**How it works:**
- Parent-child relationship
- Multiple levels of hierarchy
- Looks like upside-down tree
- Bus topology at each level

#### **Characteristics**

- Central root device
- Multiple levels of switches
- Star within Star
- Hierarchical structure

#### **Advantages**

| Advantage | Explanation |
|-----------|-------------|
| **Hierarchical** | Organized structure |
| **Scalable** | Easy to expand at each level |
| **Good Reliability** | Multiple paths possible |
| **Easy Maintenance** | Organized troubleshooting |

#### **Disadvantages**

| Disadvantage | Explanation |
|--------------|-------------|
| **Complex** | Complicated design |
| **Expensive** | Many devices needed |
| **Heavy Traffic at Root** | Root device congestion |

#### 🎯 Memory Trick

**"Tree = Multiple branches"** (पेड़ = कई शाखाएं)

---

### F) HYBRID TOPOLOGY

#### 📊 Diagram

```
       STAR NETWORK
        ┌─────────┐
        │ SWITCH  │
        └────┬────┘
             │
        MAIN CABLE (Bus)
             │
        ┌────┴────┐
        │          │
       RING    MESH
       Network Network

(Two or more topologies combined)
```

#### **Working**

Two or more topologies combined.

**How it works:**
- Combines benefits of multiple topologies
- Different areas use different topologies
- Large enterprise networks
- Best of both worlds approach

#### **Example Combinations**

- Star + Bus
- Star + Mesh
- Star + Ring
- Any combination

#### **Advantages**

| Advantage | Explanation |
|-----------|-------------|
| **Flexible** | Mix best of all topologies |
| **Reliable** | Combined reliability benefits |
| **Scalable** | Easy to expand |

#### **Disadvantages**

| Disadvantage | Explanation |
|--------------|-------------|
| **Very Expensive** | Most costly option |
| **Complex** | Difficult to manage |
| **Hard Troubleshooting** | Multiple systems to manage |

---

### 📊 TOPOLOGY COMPARISON TABLE

| Topology | Cost | Reliability | Main Problem | Best For |
|----------|------|-------------|--------------|----------|
| **Bus** | Low | Low | Cable failure | Small offices |
| **Star** | Medium | High | Switch failure | Most common |
| **Ring** | Medium | Medium | One node breaks ring | Token passing |
| **Mesh** | Very High | Very High | Expensive/Complex | Critical systems |
| **Tree** | High | Good | Heavy root traffic | Large networks |
| **Hybrid** | Very High | Very High | Very complex | Enterprise |

---

### 🎯 TOPOLOGY MEMORY TRICKS

```
Cost Order (Cheap to Expensive):
Bus < Ring < Star < Tree < Mesh < Hybrid

Reliability Order:
Bus < Ring < Tree < Star < Hybrid < Mesh

Most Common:
★ STAR TOPOLOGY ★ (यह सबसे ज्यादा use होता है)
```

---

## 2. TRANSMISSION MEDIA

### Definition

**Transmission Media म्हणजे** data travel करण्याचा path/माध्यम.

**In English:** Transmission media are physical pathways used to transmit data between devices on a network.

---

### Types of Transmission Media

```
Transmission Media
        |
  ------+-------
  |             |
Wired         Wireless
(Guided)     (Unguided)
|               |
├─ Twisted Pair  ├─ Radio Waves
├─ Coaxial       ├─ Microwave
└─ Fiber Optic   ├─ Infrared
                 └─ Satellite
```

---

### A) TWISTED PAIR CABLE

#### 📊 Diagram

```
))))))))))))))))))))
((((((((((((((((((((

(Two wires twisted together)

Cross Section:
    ┌─────────┐
    │    O    │ ← Wire 1
    │   O O   │ ← Wire 2 twisted
    │    O    │
    └─────────┘
```

#### **Description**

Most common cable in LANs.

#### **Types**

| Type | Full Form | Shielding | Use |
|------|-----------|-----------|-----|
| **UTP** | Unshielded Twisted Pair | None | Common LANs |
| **STP** | Shielded Twisted Pair | Yes | Better protection |

#### **Specifications**

- **Wire Gauge:** 24-26 AWG
- **Bandwidth:** Low to Medium
- **Distance:** ~100 meters
- **Cost:** Cheapest option

#### **Advantages**

| Advantage | Explanation |
|-----------|-------------|
| **Cheapest** | Lowest cost option |
| **Easy Installation** | Simple to install |
| **Easy Handling** | Flexible and bendable |
| **Compact** | Small diameter |

#### **Disadvantages**

| Disadvantage | Explanation |
|--------------|-------------|
| **Low Bandwidth** | Limited data rates |
| **Poor EMI Protection** | Susceptible to interference |
| **Short Distance** | Limited transmission distance |
| **Attenuation** | Signal degrades over distance |
| **Crosstalk** | Signal interference between wires |

#### **Uses**

- Local Area Networks (LAN)
- Telephone lines
- Ethernet (Cat 5, Cat 6)
- DSL connections

#### 🎯 Memory Trick

**"Twisted = Twisted Pair"** (सबसे सस्ता)

---

### B) COAXIAL CABLE

#### 📊 Diagram

```
Cross Section:
 ─────────────────────
| Shielding Layer     |
|  ───────────────    |
| | Copper Center  |  |
| |    Wire        |  |
|  ───────────────    |
| | Dielectric     |  |
|  ───────────────    |
| | Outer Jacket   |  |
 ─────────────────────

Structure:
Center Wire ─ Insulator ─ Mesh Shield ─ Outer Covering
```

#### **Description**

Cable with central conductor surrounded by shield.

#### **Specifications**

- **Center Conductor:** Copper wire
- **Insulation:** Dielectric material
- **Shielding:** Copper mesh
- **Bandwidth:** Medium
- **Distance:** ~250 meters

#### **Advantages**

| Advantage | Explanation |
|-----------|-------------|
| **Better EMI Protection** | Shielded design protects signal |
| **Moderate Bandwidth** | Better than twisted pair |
| **Longer Distance** | Can transmit further |
| **Better Signal Quality** | Less interference |

#### **Disadvantages**

| Disadvantage | Explanation |
|--------------|-------------|
| **Bulkier** | Thicker than twisted pair |
| **More Expensive** | Costlier than twisted pair |
| **Difficult Installation** | Harder to install |
| **Harder to Maintain** | More complex |

#### **Uses**

- Cable Television (CATV)
- Broadband internet
- RF transmission
- Legacy networks

#### 🎯 Memory Trick

**"Coax = Cable TV"** (केबल टीवी के लिए)

---

### C) FIBER OPTIC CABLE

#### 📊 Diagram

```
Cross Section:
 ═══════════════════════════
| Protective Jacket (Plastic)│
|  ──────────────────────    |
| | Cladding (Glass)    |   |
| |  ──────────────     |   |
| | | Core (Glass) |    |   |
| |  ──────────────     |   |
|  ──────────────────────    |
 ═══════════════════════════

Working:
┌─────────────────────────────┐
│ Light Signal   ╱╲ ╱╲ ╱╲ ╱╲  │
│ (Laser/LED)   ╱  ╲╱  ╲╱  ╲  │
└─────────────────────────────┘
```

#### **Description**

Uses light pulses for data transmission through glass/plastic fiber.

#### **Transmission Method**

- **Total Internal Reflection** (TIR)
- Light bounces inside core
- Information encoded as light pulses
- 1 = Light pulse, 0 = No light

#### **Specifications**

- **Core Diameter:** 8-50 micrometers
- **Bandwidth:** Extremely High (Terabits/s)
- **Distance:** Kilometers (100+ km)
- **Speed:** Near speed of light

#### **Types of Fiber**

| Type | Core Size | Distance | Use |
|------|-----------|----------|-----|
| **Single Mode** | 8-10 µm | Very Long (100 km+) | Long distance |
| **Multi Mode** | 50-62.5 µm | Shorter (2 km) | Medium distance |

#### **Advantages**

| Advantage | Explanation |
|-----------|-------------|
| **Highest Speed** | Terabits per second |
| **Very Long Distance** | 100+ kilometers |
| **Excellent EMI Immunity** | Not affected by electromagnetic interference |
| **No Signal Degradation** | Signal stays strong over distance |
| **Secure** | Difficult to tap/intercept |
| **Small Size** | Very thin diameter |
| **High Bandwidth** | Huge data capacity |

#### **Disadvantages**

| Disadvantage | Explanation |
|--------------|-------------|
| **Very Expensive** | Highest cost option |
| **Fragile** | Glass breaks easily |
| **Difficult Installation** | Requires precision |
| **Complex Equipment** | Expensive connectors/adapters |
| **Difficult Repair** | Breaks easily, hard to fix |
| **Needs Skilled Technicians** | Not easy to maintain |

#### **Uses**

- Internet backbone (main lines)
- Long-distance telecommunications
- High-speed communication
- Submarine cables
- Data centers
- Military/critical infrastructure

#### 🎯 Memory Trick

**"Fiber = FAST & FAR"** (सबसे तेज़ और लंबी दूरी)

---

### 📊 TRANSMISSION MEDIA COMPARISON

| Property | Twisted Pair | Coaxial | Fiber Optic |
|----------|--------------|---------|------------|
| **Cost** | Low | Medium | High |
| **Speed** | Low | Medium | Very High |
| **Distance** | Short (100m) | Medium (250m) | Very Long (100km+) |
| **Bandwidth** | Low | Medium | Extremely High |
| **EMI Immunity** | Poor | Good | Excellent |
| **Attenuation** | High | Medium | Very Low |
| **Installation** | Easy | Medium | Difficult |
| **Maintenance** | Easy | Medium | Complex |
| **Size** | Thick | Thicker | Thin |
| **Scalability** | Limited | Limited | Excellent |
| **Best For** | LAN | CATV | Internet Backbone |

---

### 🎯 TRANSMISSION MEDIA MEMORY TRICKS

```
Speed Order (Slow to Fast):
Twisted Pair < Coaxial < Fiber Optic

Distance Order (Short to Long):
Twisted Pair < Coaxial < Fiber Optic

Cost Order (Cheap to Expensive):
Twisted Pair < Coaxial < Fiber Optic

Characteristics:
TP → Cheap & Close
Coax → Medium & Medium
Fiber → Fast & Far
```

---

## 3. FRAME STRUCTURE

### Definition

**Framing म्हणजे** raw bits को organized units called frames मध्ये convert करणे.

**In English:** Framing is the process of organizing raw data into structured units called frames for transmission.

---

### Purpose of Framing

| Purpose | Explanation |
|---------|-------------|
| **Organization** | Organize data into manageable units |
| **Synchronization** | Sender and receiver synchronization |
| **Error Detection** | Detect errors in transmission |
| **Flow Control** | Manage data flow |
| **Addressing** | MAC addresses for device identification |

---

### GENERAL FRAME STRUCTURE

#### 📊 Diagram

```
┌─────────┬────────┬──────────────────┬─────────┬──────────────┐
│  Start  │ Header │  Payload/Data    │ Trailer │ End          │
│Delimiter│        │  (Actual Data)   │(Error)  │ Delimiter    │
└─────────┴────────┴──────────────────┴─────────┴──────────────┘
```

#### **Field Definitions**

| Part | Function | Details |
|------|----------|---------|
| **Start Delimiter** | Marks frame start | Signals frame beginning |
| **Header** | Address information | Source, destination MAC |
| **Payload/Data** | Actual message | User data to transmit |
| **Trailer** | Error checking | CRC (Cyclic Redundancy Check) |
| **End Delimiter** | Marks frame end | Signals frame ending |

---

### ETHERNET FRAME STRUCTURE

#### 📊 Diagram

```
┌──────────┬──────────┬──────────┬────────┬───────────────┬─────┐
│ Preamble │ Dest MAC │Source MAC│ Type   │  Data/Payload │ FCS │
│ 8 Bytes  │ 6 Bytes  │ 6 Bytes  │ 2 Bytes│  46-1500 B    │ 4 B │
└──────────┴──────────┴──────────┴────────┴───────────────┴─────┘

Total Frame Size: 72-1518 bytes
```

#### **Detailed Field Explanation**

##### **1. Preamble (8 Bytes)**

**Function:** Synchronization and signal detection

- **Pattern:** Alternating 10101010 (7 bytes)
- **Last byte:** 10101011 (Start Frame Delimiter)
- **Purpose:** Clock synchronization
- **Receiver:** Detects frame arrival

##### **2. Destination MAC Address (6 Bytes)**

**Function:** Receiver identification

- **Format:** 48-bit address
- **Example:** `AA:BB:CC:DD:EE:FF`
- **Use:** Switch uses this to forward frame
- **Unicast/Multicast:** Different types

##### **3. Source MAC Address (6 Bytes)**

**Function:** Sender identification

- **Format:** 48-bit address
- **Example:** `11:22:33:44:55:66`
- **Use:** Receiver knows where packet came from
- **Tracking:** Identifies source device

##### **4. Type/Length Field (2 Bytes)**

**Function:** Protocol information

- **Type Field (Modern):** Indicates upper layer protocol
  - `0x0800` → IPv4
  - `0x0806` → ARP
  - `0x86DD` → IPv6
- **Length Field (Legacy):** Frame payload length

##### **5. Data/Payload (46-1500 Bytes)**

**Function:** Actual message/data

- **Minimum:** 46 bytes (padding if less)
- **Maximum:** 1500 bytes (MTU - Maximum Transmission Unit)
- **Content:** User data from upper layers
- **Padding:** Added if payload < 46 bytes

##### **6. FCS (Frame Check Sequence) (4 Bytes)**

**Function:** Error detection

- **Full Form:** Frame Check Sequence
- **Method:** CRC-32 (Cyclic Redundancy Check)
- **Calculation:** Computed on entire frame
- **Receiver:** Recalculates and compares
- **Action:** If mismatch → frame discarded

---

### Frame Transmission Flow

```
Application Data
        ↓
  +─────────────────────────────+
  │ Add Transport Layer Header  │ (TCP/UDP header)
  +─────────────────────────────+
        ↓
  +─────────────────────────────+
  │ Add Network Layer Header    │ (IP header)
  +─────────────────────────────+
        ↓
  +─────────────────────────────+
  │ Add MAC Layer Header/Trailer│ (Ethernet Frame)
  +─────────────────────────────+
        ↓
    TRANSMISSION
```

---

### 🎯 ETHERNET FRAME MEMORY TRICK

**"Please Don't Send The Data Fast"**

- **P** → Preamble (8B)
- **D** → Destination MAC (6B)
- **S** → Source MAC (6B)
- **T** → Type (2B)
- **D** → Data (46-1500B)
- **F** → FCS (4B)

---

### Frame Size Calculations

| Component | Size |
|-----------|------|
| Preamble | 8 bytes |
| Destination MAC | 6 bytes |
| Source MAC | 6 bytes |
| Type | 2 bytes |
| **Minimum** Data | 46 bytes |
| **Maximum** Data | 1500 bytes |
| FCS | 4 bytes |
| **Minimum Frame** | 64 bytes |
| **Maximum Frame** | 1518 bytes |

---

## 4. FLOW CONTROL PROTOCOLS

### Definition

**Flow Control म्हणजे** fast sender को slow receiver से overwhelm होने से prevent करणे.

**In English:** Flow control is a mechanism to prevent a fast sender from overwhelming a slow receiver by regulating data transmission rate.

---

### Purpose of Flow Control

| Purpose | Explanation |
|---------|-------------|
| **Prevent Buffer Overflow** | Don't overfill receiver buffer |
| **Avoid Data Loss** | Prevent packet dropping |
| **Smooth Transmission** | Ensure reliable delivery |
| **Efficiency** | Optimal use of resources |
| **Reliability** | Guaranteed delivery |

---

### A) STOP-AND-WAIT PROTOCOL

#### 📊 Diagram

```
Sender                              Receiver

Frame 1 ────────────────────────────────>
                                  (Process)
        <──────────────────────────── ACK

        (Wait for ACK)

Frame 2 ────────────────────────────────>
                                  (Process)
        <──────────────────────────── ACK

        (Wait for ACK)

Frame 3 ────────────────────────────────>
        ...continues...
```

#### **Working Mechanism**

1. Sender sends **one frame**
2. Sender **waits** for acknowledgment (ACK)
3. Receiver receives frame
4. Receiver **processes** frame
5. Receiver sends **ACK**
6. Sender receives ACK
7. Sender sends **next frame**
8. **Repeat** process

#### **Advantages**

| Advantage | Explanation |
|-----------|-------------|
| **Very Simple** | Easy to understand and implement |
| **Reliable** | Guaranteed delivery |
| **No Buffering Needed** | Receiver doesn't need buffer |

#### **Disadvantages**

| Disadvantage | Explanation |
|--------------|-------------|
| **Very Slow** | Lots of waiting time |
| **Low Efficiency** | Sender idle most of time |
| **Wasted Bandwidth** | Network underutilized |
| **High Latency** | Long delays between frames |

#### **Efficiency Calculation**

```
Efficiency = (Frame Transmission Time) / (Frame Time + ACK Time)

If Frame Time = 1ms, ACK Time = 1ms, Propagation Delay = 10ms
Efficiency = 1 / (1 + 1 + 10 + 10) ≈ 4.5%
```

#### 🎯 Memory Trick

**"One-by-One"** (एक-एक करके)

---

### B) GO-BACK-N (GBN) PROTOCOL

#### 📊 Diagram

```
Sender                          Receiver

F1 ──────────────────────────────>
F2 ──────────────────────────────>
F3 ──────X (Frame Lost/Damaged)
F4 ──────────────────────────────>
F5 ──────────────────────────────>

        <────── NACK/No ACK for F3

Receiver rejects F4 and F5
Sender retransmits from F3:

F3 ──────────────────────────────>
F4 ──────────────────────────────>
F5 ──────────────────────────────>

        <────── ACK for all frames
```

#### **Working Mechanism**

1. Sender sends **multiple frames** (N frames)
2. Sender has **transmission window** (N)
3. If frame is **lost/damaged**
4. Receiver sends **NACK** (Negative Acknowledgment)
5. Sender **goes back** to lost frame
6. Sender **retransmits** from lost frame onwards
7. All lost + subsequent frames retransmitted
8. **Repeat** process

#### **Key Points**

| Aspect | Details |
|--------|---------|
| **Transmission** | Multiple frames at once |
| **Sliding Window** | N frames can be in transit |
| **Error Recovery** | Retransmit from lost frame |
| **Buffering** | Receiver buffers correct frames |
| **Efficiency** | Better than Stop-and-Wait |

#### **Advantages**

| Advantage | Explanation |
|-----------|-------------|
| **Faster than Stop-and-Wait** | Multiple frames sent |
| **Better Bandwidth Utilization** | Keeps link busy |
| **Reasonable Efficiency** | 50-70% typical |

#### **Disadvantages**

| Disadvantage | Explanation |
|--------------|-------------|
| **Wastes Bandwidth** | Retransmits correct frames too |
| **More Complex** | More complicated than Stop-and-Wait |
| **Receiver Buffering** | Needs buffer for out-of-order frames |

#### **Example**

```
Window Size = 4 (Sender can send 4 frames without ACK)

F1, F2, F3, F4 sent

F3 lost

F4, F5, F6 arrive but out of order

Receiver stores F4, F5, F6
Sender gets NACK for F3

Retransmits: F3, F4, F5, F6, ...
```

#### 🎯 Memory Trick

**"Send Many, Retransmit Many"** (बहुत भेजो, बहुत दोबारा भेजो)

---

### C) SELECTIVE REPEAT (SR) PROTOCOL

#### 📊 Diagram

```
Sender                          Receiver

F1 ──────────────────────────────>  ✓
F2 ──────X (Lost)
F3 ──────────────────────────────>  ✓ (Buffered)
F4 ──────────────────────────────>  ✓ (Buffered)
F5 ──────────────────────────────>  ✓

        <────── NACK for F2 only

Sender retransmits ONLY F2:

F2 ──────────────────────────────>  ✓

Receiver delivers F1, F2, F3, F4, F5
```

#### **Working Mechanism**

1. Sender sends **multiple frames**
2. Receiver **buffers** correct frames
3. If frame is **lost/damaged**
4. Receiver sends **NACK** for **only that frame**
5. Sender retransmits **only lost frame**
6. Receiver **assembles** frames in order
7. **Delivers** to upper layer
8. **Repeat** process

#### **Key Points**

| Aspect | Details |
|--------|---------|
| **Transmission** | Multiple frames at once |
| **Sliding Window** | N frames can be in transit |
| **Error Recovery** | Retransmit only lost frame |
| **Receiver Buffering** | Must buffer out-of-order frames |
| **Efficiency** | Best efficiency |

#### **Advantages**

| Advantage | Explanation |
|-----------|-------------|
| **Most Efficient** | Only retransmits lost frames |
| **Better Bandwidth** | No unnecessary retransmissions |
| **Faster Recovery** | Quicker retransmission |
| **Reduces Wasted Traffic** | Sends only needed frames |

#### **Disadvantages**

| Disadvantage | Explanation |
|--------------|-------------|
| **Complex** | More complex implementation |
| **Buffering Required** | Receiver must buffer frames |
| **Ordering Logic** | Must reassemble out-of-order frames |
| **More Memory** | Receiver needs more memory |

#### **Example**

```
Window Size = 5

F1, F2, F3, F4, F5 sent

F3 lost

F1 ✓, F2 ✓, F3 ✗, F4 ✓, F5 ✓

Receiver buffers F4, F5
Sender gets NACK for F3 only

Sender retransmits F3 only

Receiver now has all frames
Delivers: F1, F2, F3, F4, F5
```

#### 🎯 Memory Trick

**"Retransmit Only Lost One"** (सिर्फ खोए हुए को भेजो)

---

### GBN vs SR - COMPLETE COMPARISON

| Feature | Go-Back-N | Selective Repeat |
|---------|-----------|------------------|
| **Error Frame** | Retransmits all after error | Retransmits only lost frame |
| **Efficiency** | ~50-70% | ~80-90% |
| **Bandwidth** | Less efficient (wasted) | More efficient |
| **Complexity** | Simpler | Complex |
| **Buffering** | Minimal | Significant buffering |
| **Memory** | Less memory needed | More memory needed |
| **Speed** | Medium | Faster |
| **Implementation** | Easier | Harder |
| **Retransmission** | Multiple frames | Single frame |
| **Use Case** | Unreliable links | Reliable links |

---

### 📊 FLOW CONTROL PROTOCOLS COMPARISON

| Protocol | Method | Frames | Efficiency | Complexity |
|----------|--------|--------|-----------|-----------|
| **Stop-and-Wait** | 1 frame, wait for ACK | 1 at a time | ~5% | Very Simple |
| **Go-Back-N** | N frames, retransmit from lost | Multiple | ~60% | Medium |
| **Selective Repeat** | N frames, retransmit lost only | Multiple | ~85% | Complex |

---

## ✅ LAST MINUTE SUPER MEMORY TRICKS

### TOPOLOGIES

```
🎯 Quick Remembering:

Bus → Single cable (Cheap but fragile)
Star → Central switch (Most common)
Ring → Circle (Token passing)
Mesh → Everyone connected (Expensive)
Tree → Multiple branches (Hierarchical)
Hybrid → Mixed topology (Very complex)

Speed: Star > Ring > Bus
Reliability: Mesh > Hybrid > Tree > Star > Ring > Bus
Cost: Bus < Star < Ring < Tree < Mesh < Hybrid
```

---

### TRANSMISSION MEDIA

```
🎯 Quick Remembering:

TP (Twisted Pair) → Cheap & Close
   └─ Used: LAN, Telephone
   
Coax (Coaxial) → Medium & Medium
   └─ Used: Cable TV, Broadband
   
FO (Fiber Optic) → Fast & Far
   └─ Used: Internet backbone, Long distance

Speed: TP < Coax < Fiber
Distance: TP < Coax < Fiber
Cost: TP < Coax < Fiber
Reliability: TP < Coax < Fiber

Best For:
- Cheap: Twisted Pair
- Balanced: Coaxial
- Premium: Fiber Optic
```

---

### FRAME STRUCTURE

```
🎯 Ethernet Frame Fields:

"Please Don't Send The Data Fast"

P → Preamble (8B) - Synchronization
D → Destination MAC (6B) - Receiver address
S → Source MAC (6B) - Sender address
T → Type (2B) - Protocol type
D → Data (46-1500B) - Actual message
F → FCS (4B) - Error check (CRC)

Total: 64-1518 bytes
```

---

### FLOW CONTROL PROTOCOLS

```
🎯 Quick Comparison:

Stop-and-Wait:
├─ Send 1 frame
├─ Wait for ACK
├─ Send next frame
└─ Result: SLOW (5% efficiency)

Go-Back-N:
├─ Send N frames
├─ If error: Retransmit from lost frame
├─ Retransmit all subsequent frames
└─ Result: MEDIUM (60% efficiency)

Selective Repeat:
├─ Send N frames
├─ If error: Retransmit only lost frame
├─ Keep correct frames buffered
└─ Result: FAST (85% efficiency)

BEST: Selective Repeat (Most efficient)
SIMPLEST: Stop-and-Wait
BALANCED: Go-Back-N
```

---

### 🎯 DATA LINK LAYER (MODULE 2) SUMMARY

```
LAYER 2 - DATA LINK LAYER

Functions:
1. Framing - Organize bits into frames
2. Physical Addressing - MAC addresses
3. Flow Control - Stop-and-Wait/GBN/SR
4. Error Control - CRC detection
5. Media Access Control - Who transmits

Devices: Switch, NIC

Protocols: Ethernet, PPP, Frame Relay

Data Unit: FRAMES
```

---

## ✅ EXAM CHECKLIST - MODULE 2

Before your exam, verify you know:

- [ ] Definition of Network Topology
- [ ] 6 Types of Topologies (Bus, Star, Ring, Mesh, Tree, Hybrid)
- [ ] Advantages and Disadvantages of each topology
- [ ] Best topology for different scenarios
- [ ] Definition of Transmission Media
- [ ] 3 Types of Wired Media (TP, Coax, Fiber)
- [ ] Specifications of each transmission media
- [ ] Comparison of transmission media
- [ ] Definition of Framing
- [ ] General frame structure
- [ ] Ethernet frame structure and fields
- [ ] Meaning of each Ethernet field (Preamble, MAC, Type, Data, FCS)
- [ ] FCS (CRC) purpose
- [ ] Definition of Flow Control
- [ ] Stop-and-Wait protocol (working and efficiency)
- [ ] Go-Back-N protocol (working and efficiency)
- [ ] Selective Repeat protocol (working and efficiency)
- [ ] Comparison of all three protocols
- [ ] Memory tricks for all concepts
- [ ] All diagrams

---

## 📥 HOW TO DOWNLOAD AS PDF

### **Method 1: Browser Print (EASIEST)**
```
1. Go to: https://github.com/kakdekaran/notes/blob/main/MODULE2_PHYSICAL_DATALINK.md
2. Press: Ctrl+P (Windows) or Cmd+P (Mac)
3. Click: "Save as PDF"
4. Download ✅
```

### **Method 2: Online Converter**
- Visit: https://md-to-pdf.herokuapp.com/
- Paste: https://raw.githubusercontent.com/kakdekaran/notes/main/MODULE2_PHYSICAL_DATALINK.md
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
