# Physical Layer

The **Physical Layer** is the **1st layer of the OSI model**. It is responsible for the physical transmission of raw bits through a communication medium.

## 1. Position in OSI Model

```text
7 → Application
6 → Presentation
5 → Session
4 → Transport
3 → Network
2 → Data Link
1 → Physical
```

> **Physical Layer = Layer 1**

---

## 2. Data Unit

The data unit of the Physical Layer is **bits**.

```text
10110010
```

A bit represents digital data as `0` or `1`.

### Bit vs Signal

* **Bit:** A unit of digital information represented as `0` or `1`.
* **Signal:** The physical representation used to carry information through a communication medium.

```text
Bits
10110
  ↓
Physical signaling
  ↓
Electrical / Optical / Radio signal
```

---

## 3. Components and Devices

Common Physical Layer components include:

* Cables
* Repeaters
* Hubs
* Physical connectors and interfaces

### Cables

Cables provide a physical medium for transmitting signals.

#### UTP — Unshielded Twisted Pair

* Commonly used in homes, offices, and Ethernet networks.
* Contains pairs of twisted copper wires.
* Twisting helps reduce electromagnetic interference.

#### Coaxial Cable

* Contains a central copper conductor with insulation and shielding.
* Commonly used for cable television and some broadband connections.

#### Fiber-Optic Cable

* Uses light to transmit information.
* Provides high bandwidth.
* Supports long-distance communication.
* Resistant to electromagnetic interference.

---

# 4. Functions of the Physical Layer

## A. Bit-by-Bit Transmission

The Physical Layer transmits a stream of bits through the physical medium.

```text
101101001...
     ↓
Physical medium
     ↓
101101001...
```

It is concerned with the physical representation and transmission of the bits rather than their meaning.

---

## B. Encoding and Decoding

### Encoding

Encoding maps bits/data into a suitable physical signal representation for transmission.

```text
Bits
 ↓
Encoding
 ↓
Physical signal
```

### Decoding

At the receiving side, the physical signal is interpreted back into bits.

```text
Physical signal
 ↓
Decoding
 ↓
Bits
```

---

## C. Signal Transmission

The Physical Layer transmits signals through media such as:

* Copper cables
* Fiber-optic cables
* Wireless medium

Signals may use electrical, optical, or radio characteristics depending on the communication technology.

---

## D. Modulation and Demodulation

### Modulation

Modulation involves varying a carrier signal according to the information being transmitted.

```text
Information
     ↓
Modulation
     ↓
Modulated carrier
     ↓
Transmission
```

### Demodulation

Demodulation extracts the information from the received modulated carrier signal.

```text
Received signal
     ↓
Demodulation
     ↓
Information
```

### Modem

**Modem = Modulator + Demodulator**

A modem performs modulation and demodulation.

---

# 5. Types of Connection

## Point-to-Point

A point-to-point connection uses a link connecting **exactly two devices**.

```text
A ───────── B
```

The link is used for communication between those two endpoints.

## Multipoint

A multipoint connection allows **multiple devices to share a communication link or medium**.

```text
       B
       |
A ─────┼──── C
       |
       D
```

### Remember

> **Point-to-Point → Two devices**
> **Multipoint → Multiple devices sharing a link**

---

# 6. Communication Delivery Modes

These describe **who receives the communication**.

## Unicast

One sender sends data to **one specific receiver**.

```text
A ─────────→ B
```

> **Unicast = One-to-One**

---

## Anycast

One sender sends data to **one selected receiver from a group of possible receivers**.

```text
             Server A
            /
Client ─── Server B  ← Selected
            \
             Server C
```

The selected destination is generally determined by network routing.

> **Anycast = One-to-One selected from a group**

---

## Multicast

One sender sends data to a **selected group of receivers**.

```text
           B
          /
A ─────── D
          \
           F
```

> **Multicast = One-to-Many selected**

---

## Broadcast

One sender sends data to **all applicable devices within the broadcast domain**.

```text
           B
          /
A ─────── C
          \
           D
```

Examples include IPv4 ARP requests and the initial stages of DHCP communication within a LAN.

> **Broadcast = One-to-All within the broadcast domain**

---

# 7. Communication Direction

Do not confuse communication direction with delivery mode.

## Simplex

Communication occurs in **only one direction**.

```text
A ─────────→ B
```

> **Simplex = One direction**

---

## Half-Duplex

Both devices can communicate, but **only one direction can transmit at a time**.

```text
A ─────────→ B
A ←───────── B
     one at a time
```

Example: Walkie-talkie.

> **Half-Duplex = Both directions, one at a time**

---

## Full-Duplex

Both devices can transmit and receive **simultaneously**.

```text
A ─────────→ B
A ←───────── B
  simultaneously
```

Example: Telephone conversation.

> **Full-Duplex = Both directions simultaneously**

---

# 8. Delivery Mode vs Communication Direction

These are different concepts.

### Delivery Mode — Who receives the data?

```text
Unicast    → One specific receiver
Anycast    → One selected receiver from a group
Multicast  → Selected group
Broadcast  → All applicable receivers
```

### Communication Direction — How can data flow?

```text
Simplex       → One direction
Half-Duplex   → Both directions, one at a time
Full-Duplex   → Both directions simultaneously
```

For example, a network communication can be:

> **Unicast + Full-Duplex**

One specific receiver is involved, while both devices can communicate simultaneously.

---

# 9. Repeater

A repeater is a **Layer 1 device** that regenerates a weakened physical signal.

### Why is a Repeater Needed?

Signals can become weaker as they travel through a medium. This weakening is called **attenuation**.

```text
Weak signal
     ↓
 Repeater
     ↓
Regenerated signal
     ↓
Further transmission
```

### Key Points

* Operates at Layer 1.
* Works with physical signals.
* Regenerates/restores weakened signals.
* Does not use MAC addresses.
* Does not use IP addresses.
* Does not make forwarding decisions based on addresses.
* Does not filter traffic.

### Why Layer 1?

The repeater works directly with **physical signals**, which are the concern of the Physical Layer.

> **Repeater → Regenerates signals**

---

# 10. Quick Revision

```text
Physical Layer
      ↓
Layer 1
      ↓
Bits
      ↓
Physical signals
      ↓
Copper / Fiber / Wireless
```

### Core Functions

```text
Bit transmission
Encoding / Decoding
Signal transmission
Modulation / Demodulation
```

### Connection Types

```text
Point-to-Point → Two devices
Multipoint     → Multiple devices sharing a link
```

### Delivery Types

```text
Unicast    → One
Anycast    → One selected
Multicast  → Selected many
Broadcast  → All applicable
```

### Direction Types

```text
Simplex      → One direction
Half-Duplex  → Both, one at a time
Full-Duplex  → Both simultaneously
```

### Device

```text
Repeater → Regenerates physical signals
```
