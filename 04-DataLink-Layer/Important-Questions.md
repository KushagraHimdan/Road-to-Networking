# Data Link Layer — Important Questions

These questions are selected for **placement preparation, interviews, and quick revision**.

---

## 1. Basic Concepts

### 1. What is the Data Link Layer?

The Data Link Layer is Layer 2 of the OSI model. It provides reliable node-to-node delivery of frames over a physical link and handles framing, MAC addressing, flow control, error control, and medium access control.

### 2. What is the data unit of the Data Link Layer?

**Frame**

```text
Network Layer → Packet
Data Link Layer → Frame
Physical Layer → Bits
```

### 3. What are the two sublayers of the Data Link Layer?

* LLC — Logical Link Control
* MAC — Media Access Control

### 4. What is the difference between LLC and MAC?

**LLC** mainly provides an interface between upper layers and the MAC sublayer, including flow-control and error-related functions.

**MAC** handles MAC addressing and access to the physical transmission medium.

### 5. Which devices operate at the Data Link Layer?

* Switch
* Bridge
* NIC
* Wireless Access Point

---

# 2. MAC Addressing

### 6. What is a MAC address?

A MAC address is a hardware-level address associated with a network interface and is primarily used for communication within a local network.

### 7. What is the difference between MAC address and IP address?

| MAC Address                 | IP Address                          |
| --------------------------- | ----------------------------------- |
| Layer 2                     | Layer 3                             |
| Used for local delivery     | Used for logical addressing/routing |
| Used by switches            | Used by routers                     |
| Hardware/interface-oriented | Logical address                     |

### 8. Why are both MAC and IP addresses required?

MAC addresses are used for local frame delivery, while IP addresses provide logical addressing and routing between different networks.

---

# 3. Framing

### 9. What is framing?

Framing is the process of dividing a continuous stream of bits into identifiable units called frames.

### 10. Why is framing required?

It allows the receiver to determine where one frame starts and ends and provides a structured unit for local delivery and error checking.

### 11. What are the main parts of a frame?

Generally:

```text
Header → Payload → Trailer
```

The header contains addressing/control information, the payload contains the actual data, and the trailer may contain error-detection information.

### 12. What is fixed-size framing?

Every frame has a predefined fixed size, so its boundaries can be determined from its length.

### 13. What is variable-size framing?

Frames can have different sizes, so additional mechanisms such as a length field or delimiters are required to identify frame boundaries.

### 14. What is byte stuffing?

Byte stuffing inserts an extra byte when a special byte appears inside the data so that it is not confused with a frame delimiter.

### 15. What is bit stuffing?

Bit stuffing inserts extra bits into the data to prevent a special bit pattern from being mistaken for a frame boundary.

---

# 4. Flow Control

### 16. What is flow control?

Flow control prevents a fast sender from overwhelming a slower receiver.

### 17. What is Stop-and-Wait?

The sender sends one frame and waits for an acknowledgment before sending the next frame.

### 18. What are the disadvantages of Stop-and-Wait?

* Low efficiency.
* Sender remains idle while waiting for ACK.
* Performance decreases when propagation delay is high.

### 19. What is Go-Back-N?

Go-Back-N is a sliding-window protocol in which the sender can transmit multiple frames before receiving acknowledgments. If a frame is lost or damaged, the sender retransmits that frame and the following frames in the affected sequence.

### 20. What happens if frame 2 is lost in Go-Back-N?

Suppose:

```text
0 1 2 3 4
```

If frame 2 is lost, the sender eventually retransmits:

```text
2 3 4 ...
```

This may cause unnecessary retransmissions.

### 21. What is Selective Repeat?

Selective Repeat is a sliding-window protocol in which only lost or damaged frames are retransmitted. Correctly received out-of-order frames can be temporarily buffered.

### 22. Why is Selective Repeat more efficient than Go-Back-N?

Because it retransmits only the frames that actually need retransmission instead of retransmitting subsequent correctly received frames.

### 23. Which is simpler: Go-Back-N or Selective Repeat?

**Go-Back-N** is simpler.

Selective Repeat requires additional buffering and management of individually acknowledged frames.

---

# 5. Error Detection

### 24. What is an error in data transmission?

An error occurs when the data received by the receiver differs from the data sent by the sender.

### 25. What is parity checking?

Parity checking adds an extra parity bit to data so that the receiver can detect certain transmission errors.

### 26. What is a checksum?

A checksum is a calculated value derived from the transmitted data. The receiver calculates it again and compares the result to detect errors.

### 27. What is CRC?

CRC, or Cyclic Redundancy Check, is an error-detection technique based on polynomial division. It is stronger than simple parity and is widely used in networking.

### 28. Which is generally stronger for error detection: parity or CRC?

**CRC** provides much stronger error detection than simple parity.

### 29. Can error detection itself correct the corrupted data?

Usually no.

Error detection tells the receiver that corruption occurred. Correction requires mechanisms such as retransmission or error-correcting codes.

---

# 6. Error Correction

### 30. What is the difference between error detection and error correction?

**Error detection** determines whether data has been corrupted.

**Error correction** determines the error and allows the receiver to recover the correct data, either directly or through retransmission.

### 31. What is Hamming Code?

Hamming Code is an error-correction technique that adds parity bits at positions that are powers of two, such as:

```text
1, 2, 4, 8, ...
```

The receiver uses the parity results to identify the position of certain bit errors.

### 32. What is Forward Error Correction?

The sender includes enough additional information with the data so that the receiver can detect and correct certain errors without requesting retransmission.

### 33. What is Backward Error Correction?

The receiver detects an error and requests the sender to retransmit the affected data.

---

# 7. MAC and Multiple Access

### 34. What is MAC in the Data Link Layer?

MAC, or Media Access Control, determines how devices access and share a communication medium.

### 35. What are the major types of MAC protocols?

```text
MAC
├── Random Access
├── Controlled Access
└── Channelization
```

### 36. What is Random Access?

In Random Access, devices compete for access to the communication medium and collisions may occur.

Examples:

* ALOHA
* CSMA
* CSMA/CD
* CSMA/CA

### 37. What is Pure ALOHA?

A device can transmit whenever it has data. It does not first sense the channel. If an acknowledgment is not received, it assumes a collision and retransmits after a random backoff.

### 38. What is Slotted ALOHA?

Time is divided into equal slots, and a station can begin transmission only at the beginning of a slot.

### 39. Why is Slotted ALOHA better than Pure ALOHA?

Because restricting transmissions to slot boundaries reduces the possibility of overlapping transmissions and therefore reduces collisions.

---

# 8. CSMA

### 40. What is CSMA?

CSMA stands for **Carrier Sense Multiple Access**.

A device senses the communication medium before transmitting.

### 41. Why can collisions still occur in CSMA?

Two devices may sense the channel as idle at nearly the same time because of propagation delay and then transmit simultaneously.

### 42. What is 1-Persistent CSMA?

The station continuously senses the channel and transmits immediately when it becomes idle.

### 43. What is P-Persistent CSMA?

When the channel is idle, the station transmits with probability `p` and waits with probability `1-p`.

### 44. What is 0-Persistent CSMA?

When the channel is busy, the station waits for a period before checking the channel again rather than continuously sensing it.

---

# 9. CSMA/CD

### 45. What is CSMA/CD?

CSMA/CD stands for **Carrier Sense Multiple Access with Collision Detection**.

A device senses the channel, transmits when appropriate, detects a collision if one occurs, sends a jam signal, waits for a random backoff period, and retries.

### 46. Where was CSMA/CD traditionally used?

It was traditionally used in **shared Ethernet networks**.

### 47. Why is CSMA/CD not normally used in modern switched full-duplex Ethernet?

Modern switched full-duplex Ethernet provides dedicated links between devices and the switch, so the traditional shared-medium collision problem does not normally exist.

### 48. What happens after a collision in CSMA/CD?

```text
Collision
   ↓
Jam Signal
   ↓
Random Backoff
   ↓
Retransmission
```

### 49. What is the relationship between transmission time and propagation delay in CSMA/CD?

For proper collision detection in traditional Ethernet:

```text
Transmission Time ≥ 2 × Propagation Delay
```

---

# 10. CSMA/CA

### 50. What is CSMA/CA?

CSMA/CA stands for **Carrier Sense Multiple Access with Collision Avoidance**.

It attempts to reduce the probability of collisions before transmission.

### 51. Why is CSMA/CA commonly associated with Wi-Fi?

Wireless devices cannot reliably detect collisions while transmitting in the same way as shared wired Ethernet, so Wi-Fi uses mechanisms designed to avoid collisions.

### 52. What is the basic CSMA/CA process?

```text
Sense
 ↓
IFS
 ↓
Random Backoff
 ↓
Transmit
 ↓
Wait for ACK
 ↓
Success / Retry
```

### 53. What is a contention window?

It is the range from which a station selects a random backoff period before attempting transmission.

### 54. What is exponential backoff?

After repeated transmission failures, the contention window is increased so that devices are less likely to transmit at the same time.

### 55. What is the difference between CSMA/CD and CSMA/CA?

| CSMA/CD                                 | CSMA/CA                         |
| --------------------------------------- | ------------------------------- |
| Collision Detection                     | Collision Avoidance             |
| Detects collisions                      | Attempts to reduce collisions   |
| Historically used in shared Ethernet    | Commonly used in Wi-Fi          |
| Uses collision detection and jam signal | Uses backoff and ACK mechanisms |

---

# 11. Controlled Access

### 56. What is Controlled Access?

Controlled Access regulates which device is allowed to transmit on a shared medium to prevent collisions.

### 57. What is Reservation?

Devices reserve future transmission opportunities before sending their data.

### 58. What is Polling?

A central controller gives devices permission to transmit one at a time.

### 59. What is Token Passing?

A special token circulates between devices. Only the device holding the token can transmit.

### 60. Which controlled-access method uses a circulating token?

**Token Passing**

---

# 12. Channelization

### 61. What is Channelization?

Channelization divides a shared communication resource among multiple users so that they can communicate with reduced interference.

### 62. What is FDMA?

FDMA divides the available frequency spectrum into separate frequency bands for different users.

### 63. What is TDMA?

TDMA divides communication into time slots and assigns different slots to different users.

### 64. What is CDMA?

CDMA allows multiple users to share the same frequency and time while distinguishing their transmissions using unique codes.

### 65. How can you remember FDMA, TDMA, and CDMA?

```text
FDMA → Frequency
TDMA → Time
CDMA → Code
```

---

# 13. Ethernet Frame

### 66. What are the fields of an Ethernet frame?

```text
Preamble
SFD
Destination MAC
Source MAC
Length / Type
Data + Padding
FCS
```

### 67. What is the purpose of the preamble?

It provides synchronization between the sender and receiver before the actual frame begins.

### 68. What is SFD?

SFD stands for **Start Frame Delimiter**. It indicates the beginning of the actual Ethernet frame.

### 69. What is FCS?

FCS stands for **Frame Check Sequence**. It contains a CRC-based value used to detect corruption in the received frame.

### 70. What is the minimum Ethernet frame size?

The minimum Ethernet frame size is **64 bytes**, excluding the preamble and SFD.

```text
14-byte header
+ 46-byte payload
+ 4-byte FCS
= 64 bytes
```

### 71. Why is padding added to an Ethernet frame?

If the actual payload is smaller than the minimum required payload size of 46 bytes, padding is added to meet the minimum frame size.

---

# 14. Important Conceptual Questions

### 72. Why is a switch better than a hub?

A hub broadcasts incoming data to all connected devices, while a switch learns MAC addresses and normally forwards a frame only through the appropriate port.

### 73. Does a switch use IP addresses for normal Layer 2 forwarding?

No. A Layer 2 switch primarily uses **MAC addresses** for frame forwarding.

### 74. Does a router use MAC addresses?

A router uses **IP addresses** to make routing decisions. However, it also uses Layer 2 addressing on each directly connected network interface when sending frames on that link.

### 75. Does a switch separate collision domains?

Yes. Each switch port normally represents a separate collision domain.

### 76. Does a router separate broadcast domains?

Yes. Routers normally separate Layer 2 broadcast domains.

### 77. Why does a hub create more collisions?

A hub forwards incoming signals to all connected ports, so all devices share the same collision domain and medium.

### 78. Why don't normal full-duplex switch links have Ethernet collisions?

Because the link provides simultaneous independent transmission and reception rather than using a shared half-duplex medium.

---

# 15. Scenario-Based Questions

### 79. A sender transmits one frame and waits for ACK before sending another. Which protocol?

**Stop-and-Wait**

### 80. A sender retransmits frame 5, 6, 7, and 8 because frame 5 was lost. Which protocol?

**Go-Back-N**

### 81. Only frame 5 is retransmitted while frames 6, 7, and 8 were already received and buffered. Which protocol?

**Selective Repeat**

### 82. A device transmits without first checking whether the medium is free. Which protocol?

**Pure ALOHA**

### 83. A device checks whether the channel is idle before transmitting. Which family of protocols is being used?

**CSMA**

### 84. A device detects a collision and then waits for a random backoff period. Which protocol?

**CSMA/CD**

### 85. A wireless station senses the channel, waits for IFS, performs random backoff, transmits, and waits for ACK. Which protocol?

**CSMA/CA**

### 86. A controller gives each device permission to transmit one at a time. Which method?

**Polling**

### 87. A special token circulates among devices and the token holder is allowed to transmit. Which method?

**Token Passing**

### 88. Users are assigned different frequency bands. Which channelization method?

**FDMA**

### 89. Users are assigned different time slots. Which method?

**TDMA**

### 90. Users share the same frequency and time but use different codes. Which method?

**CDMA**

---

# 16. High-Priority Placement Questions

If time is limited, prepare these first:

1. What is the Data Link Layer?
2. What are LLC and MAC?
3. What is framing?
4. What is the difference between MAC and IP addresses?
5. What is flow control?
6. Explain Stop-and-Wait.
7. Explain Go-Back-N with an example.
8. Explain Selective Repeat with an example.
9. Go-Back-N vs Selective Repeat.
10. What is CRC?
11. Parity vs Checksum vs CRC.
12. What is Hamming Code?
13. What is MAC / Multiple Access Control?
14. Explain Pure ALOHA and Slotted ALOHA.
15. ALOHA vs CSMA.
16. Explain 1-Persistent, P-Persistent, and 0-Persistent CSMA.
17. Explain CSMA/CD.
18. Why is CSMA/CD not normally needed in modern switched Ethernet?
19. Explain CSMA/CA.
20. CSMA/CD vs CSMA/CA.
21. Explain Reservation, Polling, and Token Passing.
22. Explain FDMA, TDMA, and CDMA.
23. Explain the Ethernet frame format.
24. What is FCS?
25. Why is Ethernet's minimum frame size 64 bytes?
26. Switch vs Hub.
27. Switch vs Router.
28. Collision domain vs Broadcast domain.
29. Why don't full-duplex Ethernet links normally have collisions?
30. Scenario-based questions involving GBN, SR, CSMA/CD, and CSMA/CA.

---

# Quick Interview Traps

### Trap 1

**"Switches eliminate all collisions."**

Not exactly.

A switch separates collision domains, and a full-duplex switch link normally has no Ethernet collisions. However, saying that a switch universally "eliminates collisions" is too broad.

### Trap 2

**"Router only uses IP addresses."**

A router uses IP addresses for routing decisions, but it also participates in Layer 2 communication on each directly connected interface.

### Trap 3

**"CRC corrects errors."**

CRC is primarily an **error detection** mechanism, not an error correction mechanism.

### Trap 4

**"Go-Back-N retransmits only the lost frame."**

Incorrect.

Go-Back-N retransmits the problematic frame and subsequent frames that need retransmission.

### Trap 5

**"Selective Repeat retransmits the entire window."**

Incorrect.

Selective Repeat retransmits only the missing or damaged frames.

### Trap 6

**"CSMA prevents all collisions."**

Incorrect.

CSMA reduces collisions by sensing the channel, but collisions can still occur because of propagation delay and simultaneous sensing.

### Trap 7

**"CSMA/CD is used by modern Wi-Fi."**

Incorrect.

Wi-Fi is associated with **CSMA/CA**, while CSMA/CD was historically used for shared Ethernet.

---

# Final Memory Map

```text
                 DATA LINK LAYER
                       │
        ┌──────────────┴──────────────┐
        │                             │
       LLC                            MAC
        │                             │
 Flow/Error                    Multiple Access
 Control                        Control
        │                             │
   ┌────┼────┐              ┌─────────┼─────────┐
   │    │    │              │         │         │
 Stop  GBN   SR          Random    Controlled Channel
                          Access      Access   ization
                            │           │         │
                       ALOHA/CSMA    Polling   FDMA
                       CD/CA         Token      TDMA
                                    Reservation CDMA

Error Control
      │
 ┌────┴───────────┐
 │                │
Detection       Correction
 │                │
Parity          Hamming
Checksum        Retransmission
CRC
```
