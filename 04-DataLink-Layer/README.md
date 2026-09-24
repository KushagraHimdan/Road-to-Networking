# Data Link Layer

The **Data Link Layer** is the **2nd layer from the bottom (Layer 2)** of the OSI model. It provides reliable **node-to-node (hop-to-hop) delivery** of data over a physical link.

## 1. Basic Information

* **OSI Layer:** Layer 2
* **Data Unit:** Frame
* **Main Address:** MAC Address
* **Main Purpose:** Reliable delivery of frames between directly connected devices.
* **Devices:** Switch, Bridge, NIC, Wireless Access Point (WAP)

### Main Functions

* Framing
* MAC addressing
* Flow control
* Error detection and correction
* Media access control

---

# 2. Sublayers

The Data Link Layer is divided into two sublayers:

## LLC — Logical Link Control

LLC provides communication between the upper layers and the MAC sublayer.

Responsibilities:

* Provides flow control.
* Provides error detection information to higher layers.
* Handles communication between upper-layer protocols and MAC.

## MAC — Media Access Control

MAC manages access to the physical transmission medium.

Responsibilities:

* Handles MAC addressing.
* Encapsulates Network Layer packets into frames.
* Controls access to the shared medium.
* Passes frames to the Physical Layer for transmission.

---

# 3. Services of Data Link Layer

## Framing

Framing divides a stream of bits into identifiable units called **frames**.

```text
Bits → Frame → Frame → Frame
```

This allows the receiver to identify where one frame starts and ends.

## Physical / MAC Addressing

Each network interface has a MAC address used for local network communication.

```text
Source MAC → Destination MAC
```

## Flow Control

Flow control prevents a fast sender from overwhelming a slower receiver.

Main protocols:

* Stop-and-Wait
* Go-Back-N
* Selective Repeat

## Error Control

Error control detects and, in some cases, corrects corrupted data.

### Error Detection

* Single-bit parity
* Two-dimensional parity
* Checksum
* CRC

### Error Correction

* Hamming Code
* Retransmission-based correction

## Access Control

When multiple devices share a communication medium, access control determines when each device can transmit.

Methods include:

* Random Access
* Controlled Access
* Channelization

---

# 4. How the Data Link Layer Works

The Data Link Layer receives bits from the Physical Layer and organizes them into frames.

```text
Physical Layer
      ↓
     Bits
      ↓
Data Link Layer
      ↓
    Frames
      ↓
Network Layer
```

It:

1. Creates frames from incoming data.
2. Adds source and destination MAC addresses.
3. Detects transmission errors.
4. Controls access to the shared medium.
5. Provides the resulting frame to the Network Layer.

The Data Link Layer mainly handles **local delivery**, while the Network Layer handles **IP addressing and routing between networks**.

---

# 5. Framing

Framing groups raw bits into meaningful units called frames.

A simplified frame contains:

```text
+---------+----------+---------+---------+
| Header  | Payload  | Trailer |         |
+---------+----------+---------+---------+
```

### Header

Contains control information such as:

* Source MAC address
* Destination MAC address

### Payload

Contains the actual data received from the Network Layer.

### Trailer

Contains error-detection information such as CRC/FCS.

---

## Types of Framing

### Fixed-Size Framing

Every frame has the same size.

* Frame boundaries are known from the fixed length.
* Delimiters are generally unnecessary.

### Variable-Size Framing

Frames can have different sizes.

Frame boundaries can be identified using:

* Length field
* End delimiter

### Byte Stuffing

Extra bytes are inserted when a special byte appears inside the data so that it is not confused with a delimiter.

### Bit Stuffing

Extra bits are inserted to prevent data from being confused with a special bit pattern.

---

# 6. MAC Addressing

A **MAC address** is a hardware-level identifier associated with a network interface.

* Usually 48 bits (6 bytes).
* Used for local network communication.
* Operates at the Data Link Layer.

Example:

```text
00:1A:2B:3C:4D:5E
```

### NIC

A **Network Interface Card (NIC)** connects a device to a network.

It may provide:

* Ethernet connectivity
* Wireless connectivity

### WAP

A **Wireless Access Point (WAP)** allows wireless devices to connect to a wired network through Wi-Fi.

---

# 7. Flow Control

Flow control prevents the sender from sending data faster than the receiver can process it.

## Stop-and-Wait

The sender sends one frame and waits for its acknowledgment before sending the next frame.

```text
Sender                Receiver
  |                      |
  |------ Frame 0 ------>|
  |<------- ACK ---------|
  |------ Frame 1 ------>|
  |<------- ACK ---------|
```

### Characteristics

* Window size = 1
* Simple to implement.
* Prevents receiver overload.
* Inefficient because the sender may remain idle while waiting.

### Problems

* Lost frame
* Lost ACK
* Delayed frame/ACK

---

# 8. Go-Back-N

Go-Back-N is a **sliding-window protocol** used for flow and error control.

The sender can send multiple frames before receiving acknowledgments.

Example:

```text
Window Size = 4

[0] [1] [2] [3]
```

If frame 2 is lost:

```text
0 ✓
1 ✓
2 ✗
3 received
```

The sender eventually retransmits:

```text
2, 3, ...
```

The important idea is:

> **Go-Back-N retransmits the erroneous/missing frame and all subsequent frames in the affected window.**

### Key Points

* Uses sliding window.
* Receiver sends cumulative acknowledgments.
* Multiple frames can be in transit.
* Retransmission can be wasteful because correctly received frames may be sent again.

---

# 9. Selective Repeat ARQ

Selective Repeat also allows multiple frames to be transmitted.

However, only the frames that are lost or corrupted are retransmitted.

Example:

```text
0 ✓
1 ✓
2 ✗
3 ✓
4 ✓
```

Only frame 2 needs retransmission.

### Key Points

* Receiver can buffer out-of-order frames.
* Individual acknowledgments are used.
* Lost/damaged frames are retransmitted.
* More efficient than Go-Back-N.
* More complex to implement.

### Comparison

| Feature           | Stop-and-Wait | Go-Back-N                      | Selective Repeat |
| ----------------- | ------------- | ------------------------------ | ---------------- |
| Frames in transit | 1             | Multiple                       | Multiple         |
| Window            | 1             | Sliding                        | Sliding          |
| Retransmission    | One frame     | Error frame + following frames | Only error frame |
| Efficiency        | Low           | Medium                         | High             |
| Complexity        | Low           | Medium                         | High             |

---

# 10. Error Detection and Correction

An error occurs when received data differs from the data sent.

## Single-Bit Parity

Adds one parity bit to the data.

For even parity:

* Odd number of `1`s → add `1`
* Even number of `1`s → add `0`

The receiver checks whether the expected parity is maintained.

### Limitation

Simple parity cannot reliably detect all multiple-bit error patterns.

---

## Checksum

A checksum is calculated from the data and sent along with it.

The receiver calculates the checksum again.

```text
Sender:
Data → Checksum

Receiver:
Data → Recalculate Checksum
              ↓
          Compare
```

If the values do not match, an error is detected.

---

## CRC

**CRC = Cyclic Redundancy Check**

CRC uses polynomial-based division to calculate a check value.

* Stronger than simple parity.
* Widely used for error detection.
* Ethernet uses CRC-based error detection through the FCS field.

---

# 11. Error Correction

## Backward Error Correction

The receiver detects an error and requests retransmission.

```text
Error detected
      ↓
Request retransmission
      ↓
Sender sends data again
```

## Forward Error Correction

Extra information is sent with the original data so that the receiver can detect and correct certain errors without retransmission.

---

# 12. Hamming Code

Hamming Code is an error-correction technique.

Parity bits are placed at positions that are powers of 2:

```text
1, 2, 4, 8, 16, ...
```

The receiver checks the parity bits.

The combination of failed parity checks identifies the position of the erroneous bit.

The receiver can then flip that bit to correct the error.

---

# 13. MAC — Multiple Access Control

MAC determines how multiple devices share a common communication medium.

There are three major approaches:

```text
MAC
├── Random Access
├── Controlled Access
└── Channelization
```

---

# 14. Random Access

In Random Access:

* No device has permanent priority.
* Devices compete for access to the medium.
* Collisions can occur.

Protocols include:

* ALOHA
* CSMA
* CSMA/CD
* CSMA/CA

---

## ALOHA

### Pure ALOHA

A device transmits whenever it has data.

If an acknowledgment is not received, the device assumes a collision and retries after a random backoff period.

```text
Transmit
   ↓
Wait for ACK
   ↓
No ACK?
   ↓
Random Backoff
   ↓
Retry
```

Pure ALOHA does not sense the channel before transmission.

### Slotted ALOHA

Time is divided into equal slots.

A device can start transmission only at the beginning of a slot.

This reduces collisions compared with Pure ALOHA.

### Comparison

| Pure ALOHA                  | Slotted ALOHA                 |
| --------------------------- | ----------------------------- |
| Transmit anytime            | Transmit at slot boundaries   |
| More collisions             | Fewer collisions              |
| No synchronization required | Requires time synchronization |

---

# 15. CSMA

**CSMA = Carrier Sense Multiple Access**

A device listens to the channel before transmitting.

```text
Sense channel
      ↓
Idle? → Transmit
Busy? → Wait
```

Collisions can still occur because two devices may sense the channel as idle at nearly the same time due to propagation delay.

---

## CSMA Access Methods

### 1-Persistent CSMA

* Sense the channel.
* If idle, transmit immediately.
* If busy, continuously sense until it becomes idle.
* High chance of collision when multiple stations are waiting.

### P-Persistent CSMA

* If the channel is idle, transmit with probability `p`.
* With probability `(1-p)`, wait and try again.
* Provides a balance between transmission and collision probability.

### 0-Persistent CSMA

* If the channel is busy, the station waits for a predetermined/random period rather than continuously sensing.
* It then checks the channel again.

---

# 16. CSMA/CD

**CSMA/CD = Carrier Sense Multiple Access with Collision Detection**

Used historically in shared Ethernet.

Process:

```text
Sense
  ↓
Transmit
  ↓
Detect collision?
  ↓
Yes
  ↓
Send jam signal
  ↓
Random backoff
  ↓
Retry
```

### Important

CSMA/CD is generally **not used in modern switched full-duplex Ethernet**, because each device has a dedicated link and collisions do not normally occur.

---

# 17. CSMA/CA

**CSMA/CA = Carrier Sense Multiple Access with Collision Avoidance**

Commonly associated with wireless LANs.

The device tries to reduce the probability of collisions before transmitting.

Basic process:

```text
Sense channel
      ↓
IFS
      ↓
Random Backoff
      ↓
Transmit
      ↓
Wait for ACK
      ↓
ACK received?
   /       \
 Yes       No
  ↓         ↓
Success   Retry
```

### Important Components

#### IFS — Interframe Space

A short waiting period before transmission.

#### Contention Window

The device randomly selects a backoff period.

#### Backoff

If the channel becomes busy, the timer pauses and resumes when the channel becomes available.

#### ACK

The receiver sends an acknowledgment after successfully receiving the frame.

#### Exponential Backoff

After repeated failures, the contention window increases, providing a larger range of possible backoff values.

---

# 18. CSMA/CD vs CSMA/CA

| CSMA/CD                                                   | CSMA/CA                                                      |
| --------------------------------------------------------- | ------------------------------------------------------------ |
| Collision Detection                                       | Collision Avoidance                                          |
| Detects collision after/during transmission               | Attempts to reduce collision probability before transmission |
| Historically used in shared Ethernet                      | Commonly associated with Wi-Fi                               |
| Uses collision detection and jam signal                   | Uses backoff and ACK mechanisms                              |
| Not normally used in modern full-duplex switched Ethernet | Used in wireless LAN access                                  |

---

# 19. Controlled Access

Controlled Access regulates which device can transmit.

## Reservation

Devices reserve transmission opportunities before sending data.

> Reserve first, transmit later.

## Polling

A central controller gives devices permission to transmit one at a time.

> Controller asks, device responds.

## Token Passing

A special token circulates between devices.

Only the device holding the token can transmit.

> Hold the token → transmit.

---

# 20. Channelization

Channelization divides communication resources among users.

### FDMA

**Frequency Division Multiple Access**

Different users receive different frequency bands.

> **FDMA → Frequency**

### TDMA

**Time Division Multiple Access**

Different users receive different time slots.

> **TDMA → Time**

### CDMA

**Code Division Multiple Access**

Users can share the same frequency and time while using different codes.

> **CDMA → Code**

### Comparison

| FDMA                              | TDMA                             | CDMA                              |
| --------------------------------- | -------------------------------- | --------------------------------- |
| Frequency division                | Time division                    | Code division                     |
| Different frequencies             | Different time slots             | Different codes                   |
| Users can transmit simultaneously | Users transmit in assigned slots | Users can transmit simultaneously |

---

# 21. Ethernet Frame

Ethernet frames carry data over Ethernet networks.

```text
+----------+-----+-------------+-------------+--------------+--------------+------+
| Preamble | SFD | Destination | Source MAC  | Length/Type  | Data + Pad   | FCS  |
|  7 B     | 1 B |     6 B     |     6 B     |      2 B     |   46-1500 B  | 4 B |
+----------+-----+-------------+-------------+--------------+--------------+------+
```

## Fields

### Preamble — 7 Bytes

Used for synchronization between sender and receiver.

### SFD — 1 Byte

**Start Frame Delimiter**

Marks the beginning of the actual Ethernet frame.

### Destination MAC — 6 Bytes

Identifies the intended Layer 2 destination.

It can represent:

* Unicast
* Multicast
* Broadcast

### Source MAC — 6 Bytes

Identifies the sending network interface.

### Length / Type — 2 Bytes

Depending on the Ethernet frame format:

* IEEE 802.3 → Length
* Ethernet II → EtherType

### Data / Payload — 46–1500 Bytes

Contains the Network Layer packet and other upper-layer data.

If the payload is smaller than 46 bytes, padding is added.

### FCS — 4 Bytes

**Frame Check Sequence**

Contains a CRC-based value used to detect frame corruption.

---

# 22. Ethernet Frame Size

Minimum Ethernet frame size:

```text
14-byte header
+ 46-byte payload
+ 4-byte FCS
----------------
64 bytes
```

The preamble and SFD are not included in this 64-byte minimum frame size.

Maximum normal Ethernet payload:

```text
1500 bytes
```

---

# 23. Important Comparisons

### Switch vs Router

| Switch                        | Router                      |
| ----------------------------- | --------------------------- |
| Layer 2                       | Layer 3                     |
| Uses MAC addresses            | Uses IP addresses           |
| Connects devices within a LAN | Connects different networks |
| Forwards frames               | Forwards packets            |

### Go-Back-N vs Selective Repeat

```text
Go-Back-N
→ Retransmits the error frame and following frames.

Selective Repeat
→ Retransmits only the missing/damaged frames.
```

### ALOHA vs CSMA

```text
ALOHA
→ Transmit without first sensing the channel.

CSMA
→ Sense the channel before transmitting.
```

### CSMA/CD vs CSMA/CA

```text
CSMA/CD
→ Detect collision.

CSMA/CA
→ Try to avoid collision.
```

### FDMA / TDMA / CDMA

```text
FDMA → Frequency
TDMA → Time
CDMA → Code
```

---

# 24. Quick Revision

```text
Data Link Layer
→ Layer 2
→ Data = Frames
→ Address = MAC

Sublayers
→ LLC + MAC

Main Functions
→ Framing
→ MAC Addressing
→ Flow Control
→ Error Control
→ Access Control

Flow Control
→ Stop-and-Wait
→ Go-Back-N
→ Selective Repeat

Error Detection
→ Parity
→ Checksum
→ CRC

Error Correction
→ Hamming Code
→ Retransmission

Random Access
→ ALOHA
→ CSMA
→ CSMA/CD
→ CSMA/CA

Controlled Access
→ Reservation
→ Polling
→ Token Passing

Channelization
→ FDMA
→ TDMA
→ CDMA

Ethernet
→ Preamble
→ SFD
→ Destination MAC
→ Source MAC
→ Length/Type
→ Data/Pad
→ FCS
```

## Key Takeaways

1. The Data Link Layer is **Layer 2** of the OSI model.
2. Its data unit is a **frame**.
3. It uses **MAC addresses** for local delivery.
4. **LLC** and **MAC** are its two sublayers.
5. Framing separates a continuous bit stream into meaningful units.
6. Flow control prevents a sender from overwhelming a receiver.
7. Go-Back-N retransmits from the problematic frame onward.
8. Selective Repeat retransmits only the problematic frames.
9. CRC is widely used for error detection.
10. Hamming Code can locate and correct certain bit errors.
11. MAC protocols determine how multiple devices access a shared medium.
12. CSMA/CD detects collisions; CSMA/CA attempts to avoid them.
13. Controlled access includes Reservation, Polling, and Token Passing.
14. FDMA divides frequency, TDMA divides time, and CDMA divides access using codes.
15. Ethernet frames use MAC addressing and FCS for error detection.
