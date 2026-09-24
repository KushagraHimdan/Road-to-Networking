# Data Link Layer — Extra Notes

These notes contain supporting concepts, explanations, and mental models that are useful for understanding the Data Link Layer but are not necessary to memorize line-by-line.

---

# 1. Where Data Link Layer Fits

The Data Link Layer sits between the Physical Layer and Network Layer.

```text
Network Layer
     ↓
   Packet
     ↓
Data Link Layer
     ↓
   Frame
     ↓
Physical Layer
     ↓
    Bits
```

The Data Link Layer takes a Network Layer packet and places it inside a frame.

This process is called **encapsulation**.

---

# 2. Frame vs Packet vs Segment vs Bits

Different OSI layers use different names for their data units.

```text
Application
     ↓
Transport     → Segment / Datagram
     ↓
Network       → Packet
     ↓
Data Link     → Frame
     ↓
Physical      → Bits
```

A useful way to think about it:

> Each lower layer wraps the data received from the layer above it with information needed for its own job.

For example:

```text
IP Packet
   ↓
+---------------------------+
| Ethernet Header | Packet |
+---------------------------+
          ↓
       Frame
          ↓
        Bits
```

---

# 3. MAC Address vs IP Address

This is one of the most important concepts for networking interviews.

## MAC Address

* Used mainly for local network delivery.
* Operates at Layer 2.
* Associated with a network interface.
* Switches use MAC addresses to forward frames.

## IP Address

* Used for logical addressing between networks.
* Operates at Layer 3.
* Routers use IP addresses to forward packets.

### Simple Example

Suppose:

```text
PC A → Switch → Router → Switch → PC B
```

The communication can be understood as:

```text
MAC address
→ Used for local hop/frame delivery

IP address
→ Used for logical end-to-end routing
```

A MAC address identifies the local interface involved in a frame, while an IP address provides logical addressing used for routing.

---

# 4. Why Do We Need Both MAC and IP?

MAC and IP solve different problems.

Imagine sending a parcel.

```text
IP Address
→ Destination's logical location

MAC Address
→ Local device/interface involved in the current delivery
```

A router may receive a packet and create a new Layer 2 frame for the next network segment.

Therefore, the MAC addresses in the frame can change from hop to hop, while the IP addresses normally represent the source and final destination of the packet.

---

# 5. Switch and MAC Address Table

A switch learns which MAC addresses are reachable through which ports.

Example:

```text
MAC Address       Port
-----------------------
AA:AA:AA:AA:AA:AA → P1
BB:BB:BB:BB:BB:BB → P2
CC:CC:CC:CC:CC:CC → P3
```

Suppose A sends a frame to B.

```text
A → Switch → B
```

The switch checks the destination MAC address.

If B is known on `P2`, the switch forwards the frame only through `P2`.

This is why a switch is much more efficient than a hub.

---

# 6. What Happens When a Switch Does Not Know the Destination?

If the destination MAC address is unknown, the switch may **flood** the frame out of the appropriate ports, except the port from which it was received.

When the destination device responds, the switch can learn its MAC address from the incoming frame.

This is part of the switch's MAC learning process.

---

# 7. Collision Domain

A **collision domain** is a portion of a network where devices could potentially have their transmissions collide.

### Hub

A hub creates one shared collision domain.

```text
      Hub
   /  |  |  \
  A   B  C   D
```

All devices share the same medium.

### Switch

With a switch, each switch port normally represents a separate collision domain.

```text
A ── P1
B ── P2
C ── P3
D ── P4
```

In full-duplex switched Ethernet, collisions do not normally occur.

---

# 8. Broadcast Domain

A **broadcast domain** is the set of devices that receive a Layer 2 broadcast.

A basic switch forwards broadcasts within the same broadcast domain.

A router normally separates broadcast domains.

```text
Network A
A ─ Switch ─ Router ─ Switch ─ B
                       Network B
```

The router separates the two networks.

### Quick Memory

```text
Switch
→ Separates collision domains

Router
→ Separates broadcast domains
```

---

# 9. Why Full-Duplex Ethernet Does Not Normally Have Collisions

In a full-duplex connection, communication can happen in both directions simultaneously.

```text
A ─────────────── B
   → Data
   ← Data
```

The sending and receiving paths can operate simultaneously without the classic shared-medium collision problem.

Therefore:

> Modern switched full-duplex Ethernet does not normally require CSMA/CD.

---

# 10. Why CSMA/CD Became Less Important

Older Ethernet networks could use a shared medium.

Example:

```text
A ─┐
B ─┼── Shared Medium
C ─┤
D ─┘
```

Two devices could transmit simultaneously.

```text
A →→→
B →→→
   ↓
Collision
```

CSMA/CD was designed to detect such collisions.

Modern switched Ethernet instead gives devices dedicated links:

```text
A ── Switch ── B
C ── Switch ── D
```

With full-duplex links, the traditional collision problem is removed.

---

# 11. Why Wi-Fi Uses CSMA/CA Instead

Wireless devices cannot reliably detect collisions in the same way as wired Ethernet.

A wireless station transmitting cannot simply listen for a collision while it is transmitting because its own transmitted signal can overwhelm the received signal.

Therefore, Wi-Fi uses **Collision Avoidance**.

```text
Sense
 ↓
Wait
 ↓
Random Backoff
 ↓
Transmit
 ↓
ACK
```

The goal is to reduce the probability of two stations transmitting simultaneously.

---

# 12. Flow Control vs Error Control

These concepts are easy to confuse.

## Flow Control

Question:

> "Can the receiver handle the data at this rate?"

Purpose:

```text
Prevent receiver overload
```

Examples:

* Stop-and-Wait
* Go-Back-N
* Selective Repeat

## Error Control

Question:

> "Did the data arrive correctly?"

Purpose:

```text
Detect or recover from corrupted/lost data
```

Examples:

* Parity
* Checksum
* CRC
* Hamming Code
* Retransmission mechanisms

### Memory Trick

```text
Flow Control
→ How fast?

Error Control
→ Was it correct?
```

---

# 13. Flow Control vs Congestion Control

These are also different.

### Flow Control

Controls communication between:

```text
Sender ↔ Receiver
```

It prevents the sender from overwhelming the receiver.

### Congestion Control

Deals with:

```text
Network traffic
```

It prevents excessive traffic from overwhelming the network.

```text
Flow Control
→ Receiver problem

Congestion Control
→ Network problem
```

---

# 14. Go-Back-N Example

Suppose:

```text
Frames:
0 1 2 3 4
```

Frame 2 is lost.

```text
0 ✓
1 ✓
2 ✗
3 ✓
4 ✓
```

Because Go-Back-N uses cumulative acknowledgment, the receiver does not treat frame 3 as successfully accepted in sequence for normal delivery.

After timeout, the sender goes back and retransmits from frame 2:

```text
2 → 3 → 4
```

This is why it is called:

> **Go-Back-N**

It goes back to the problematic frame.

---

# 15. Selective Repeat Example

Same situation:

```text
0 ✓
1 ✓
2 ✗
3 ✓
4 ✓
```

Selective Repeat can buffer frames 3 and 4.

Only frame 2 needs retransmission:

```text
2 → retransmit
```

Therefore:

```text
Go-Back-N
→ More retransmissions

Selective Repeat
→ Fewer retransmissions
```

Selective Repeat is more efficient but requires more receiver-side buffering and management.

---

# 16. CRC vs Checksum vs Parity

Think of these as different levels of error detection.

### Parity

Very simple.

```text
Data + Parity Bit
```

Good for basic error detection but limited.

### Checksum

Calculates a value from the data and compares it at the receiver.

```text
Data → Calculation → Checksum
```

### CRC

Uses polynomial division and provides stronger error detection.

```text
Data → CRC Calculation → FCS
```

### Memory

```text
Parity
→ Simple

Checksum
→ Calculated value

CRC
→ Polynomial-based error detection
```

---

# 17. Error Detection vs Error Correction

Detection and correction are not the same.

## Error Detection

The receiver determines:

> "Something is wrong."

Examples:

* Parity
* Checksum
* CRC

## Error Correction

The receiver determines:

> "Something is wrong, and I can identify/correct it."

Example:

* Hamming Code

Another approach is retransmission:

```text
Detect error
     ↓
Request retransmission
     ↓
Receive correct data
```

---

# 18. Frame Padding

Ethernet requires a minimum payload size.

Suppose:

```text
Actual data = 30 bytes
Minimum payload = 46 bytes
```

Ethernet adds:

```text
46 - 30 = 16 bytes padding
```

Therefore:

```text
30 bytes actual data
+
16 bytes padding
=
46 bytes payload
```

The minimum Ethernet frame is:

```text
14 bytes header
+ 46 bytes payload
+ 4 bytes FCS
= 64 bytes
```

Preamble and SFD are not included in this calculation.

---

# 19. Ethernet Frame — What to Remember

The complete order is:

```text
Preamble
   ↓
SFD
   ↓
Destination MAC
   ↓
Source MAC
   ↓
Length / EtherType
   ↓
Data + Padding
   ↓
FCS
```

### Sizes

```text
Preamble       → 7 bytes
SFD            → 1 byte
Destination    → 6 bytes
Source         → 6 bytes
Length/Type    → 2 bytes
Data           → 46–1500 bytes
FCS            → 4 bytes
```

---

# 20. Why Ethernet Has a Minimum Frame Size

Historically, the minimum frame size was important for collision detection in shared Ethernet.

A transmitting station needed to remain transmitting long enough for a collision occurring at the farthest part of the network to propagate back.

This is related to the CSMA/CD requirement:

```text
Transmission time ≥ 2 × propagation delay
```

Modern full-duplex switched Ethernet does not rely on collision detection, but the Ethernet frame format retains its minimum size requirements.

---

# 21. LLC vs MAC — Easy Distinction

Think of the two sublayers this way:

```text
Data Link Layer
│
├── LLC
│   └── Communication with upper layers
│
└── MAC
    └── Communication with the physical medium
```

### LLC

Focus:

> **How does the Data Link Layer communicate with upper layers?**

### MAC

Focus:

> **How does the device access the physical medium and identify local interfaces?**

---

# 22. Random vs Controlled vs Channelization

These three MAC approaches solve the same general problem differently.

### Random Access

Devices compete.

```text
"Can I transmit?"
→ Try
```

Possible collisions.

Examples:

* ALOHA
* CSMA

### Controlled Access

Devices take turns according to a mechanism.

```text
"Whose turn is it?"
```

Examples:

* Reservation
* Polling
* Token Passing

### Channelization

Resources are divided.

```text
"Which resource belongs to each user?"
```

Examples:

* FDMA → Frequency
* TDMA → Time
* CDMA → Code

---

# 23. Important Interview Mental Models

### Hub

```text
Receives → Broadcasts to all
```

### Switch

```text
Receives frame
→ Checks destination MAC
→ Forwards through appropriate port
```

### Router

```text
Receives packet
→ Checks destination IP
→ Chooses route
→ Forwards packet
```

### Firewall

```text
Checks traffic against rules
→ Allows or blocks
```

### IDS

```text
Monitors
→ Detects suspicious activity
→ Generates alert
```

---

# 24. One-Line Revision Sheet

```text
Layer 2
→ Data Link Layer

Data
→ Frame

Address
→ MAC

Sublayers
→ LLC + MAC

Framing
→ Packet → Frame

Flow Control
→ Stop-and-Wait / GBN / SR

Error Detection
→ Parity / Checksum / CRC

Error Correction
→ Hamming Code / Retransmission

Random Access
→ ALOHA / CSMA

Collision Detection
→ CSMA/CD

Collision Avoidance
→ CSMA/CA

Controlled Access
→ Reservation / Polling / Token

Channelization
→ FDMA / TDMA / CDMA

Ethernet
→ MAC-based LAN technology

FCS
→ CRC-based error detection

Switch
→ MAC

Router
→ IP
```
