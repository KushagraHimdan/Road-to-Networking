# Extra Notes — Physical Layer

## 1. Bit vs Signal

A **bit** is digital information, while a **signal** is the physical mechanism used to carry that information.

```text
Bit
0 / 1
 ↓
Encoding / Signaling
 ↓
Physical Signal
 ↓
Transmission Medium
```

The signal can have electrical, optical, or electromagnetic/radio characteristics depending on the technology.

---

## 2. Encoding vs Modulation

These terms are often confused.

### Encoding

Encoding maps data into a signaling representation suitable for transmission.

```text
Data / Bits
     ↓
 Encoding
     ↓
Signal representation
```

### Modulation

Modulation varies a carrier signal according to information being transmitted.

```text
Information
     ↓
Modulation
     ↓
Carrier-based signal
```

A simple way to remember:

> **Encoding → Represents data for signaling**
> **Modulation → Changes a carrier to carry information**

The exact implementation depends on the communication technology.

---

# 3. Attenuation

**Attenuation** is the reduction in signal strength as a signal travels through a medium.

```text
Strong signal ─────→ Weaker signal
```

A repeater can regenerate the signal so that it can continue traveling.

> **Attenuation → Signal weakens with distance**

---

# 4. Repeater Does Not Check Data

A repeater does not inspect the contents of a frame and decide where it should go.

It does not normally examine:

* Destination MAC address
* Source MAC address
* Destination IP address
* Source IP address

Its job is related to the physical signal.

```text
Receive signal
      ↓
Regenerate signal
      ↓
Transmit signal
```

This is why it belongs to Layer 1.

---

# 5. Point-to-Point vs Unicast

These concepts sound similar but describe different things.

### Point-to-Point

Describes the **connection/link arrangement**.

> One link connects exactly two devices.

### Unicast

Describes the **delivery of data**.

> One sender sends data to one specific receiver.

Therefore, unicast does not automatically mean that a dedicated physical connection was created.

---

# 6. Multipoint vs Multicast

These are also different.

### Multipoint

Describes a **shared communication link**.

> Multiple devices share the same physical communication medium.

### Multicast

Describes **data delivery to a selected group**.

> One sender sends data to multiple selected receivers.

So:

```text
Multipoint → Connection arrangement
Multicast  → Delivery method
```

---

# 7. Broadcast Domain

A broadcast is not necessarily received by every device on the entire Internet.

It is normally limited to the relevant **Layer 2 broadcast domain**.

For example:

```text
LAN
 ├── PC A
 ├── PC B
 ├── PC C
 └── PC D

Broadcast from A
      ↓
B, C, D receive it
```

A router normally does not forward ordinary Layer 2 broadcasts between its interfaces.

---

# 8. Anycast vs Unicast

Both can result in communication with one receiver, but their destination selection differs.

### Unicast

The sender communicates with a specific destination.

```text
A → Server B
```

### Anycast

The sender addresses a service available from multiple possible locations, and routing selects one destination.

```text
             Server A
            /
Client ─── Server B
            \
             Server C

        One is selected
```

Anycast is commonly used by distributed services such as DNS infrastructure and CDNs.

---

# 9. Four Delivery Modes

```text
             DELIVERY
                |
      ┌─────────┼──────────┐
      ↓         ↓          ↓
   One      Selected     Everyone
    |          |            |
 Unicast    Multicast    Broadcast
              |
           Anycast
       (one selected
        from a group)
```

More precisely:

| Mode      | Sender | Receivers               |
| --------- | -----: | ----------------------- |
| Unicast   |      1 | 1 specific              |
| Anycast   |      1 | 1 selected from a group |
| Multicast |      1 | Selected group          |
| Broadcast |      1 | All applicable devices  |

---

# 10. Three Communication Directions

```text
Simplex
A ─────────→ B

Half-Duplex
A ─────────→ B
A ←───────── B
(one direction at a time)

Full-Duplex
A ─────────→ B
A ←───────── B
(simultaneously)
```

### Important

**Full-duplex does not mean "no collision" by definition.**

Rather, full-duplex allows simultaneous transmission in both directions. On typical full-duplex Ethernet links, this means collisions do not occur because both ends are not competing for a shared medium.

---

# 11. Physical Layer and OSI

The Physical Layer is concerned with the actual physical transmission rather than the meaning of the data.

A simplified view:

```text
Application
    ↓
Transport
    ↓
Network
    ↓
Data Link
    ↓
Physical
    ↓
Actual physical transmission
```

The Physical Layer does not decide:

* Which application should receive the data.
* Which IP network the packet belongs to.
* Which MAC address should receive a frame.

Those responsibilities belong to higher layers.

---

# 12. High-Value Interview Distinctions

### Physical Layer vs Data Link Layer

> Physical Layer transmits raw bits/signals, while Data Link Layer handles frames and MAC-based communication.

### Bit vs Signal

> A bit is digital information; a signal is its physical representation for transmission.

### Encoding vs Modulation

> Encoding maps data into a signaling representation, while modulation varies a carrier signal according to information.

### Point-to-Point vs Multipoint

> Point-to-point uses a link between two devices, while multipoint allows multiple devices to share a link.

### Unicast vs Broadcast

> Unicast delivers data to one specific receiver, while broadcast delivers it to all applicable devices within the broadcast domain.

### Simplex vs Full-Duplex

> Simplex allows communication in one direction, while full-duplex allows simultaneous communication in both directions.

### Repeater vs Switch

> A repeater works with physical signals at Layer 1, while a switch works primarily with Layer 2 frames and MAC addresses.
