# Extra Notes — Network Devices

These notes cover useful distinctions that are easy to confuse in exams and interviews.

## 1. Collision Domain vs Broadcast Domain

### Collision Domain

A collision domain is a portion of a network in which devices could potentially interfere with one another when transmitting over a shared medium.

* A traditional hub creates one shared collision domain.
* A switch normally creates a separate collision domain for each port.
* A router separates collision domains between its interfaces.
* Full-duplex Ethernet eliminates collisions on that link because both directions can transmit simultaneously without competing for a shared medium.

### Broadcast Domain

A broadcast domain is the set of devices that receive a Layer 2 broadcast frame.

* Switches normally forward broadcasts within the same VLAN.
* Routers normally do not forward Layer 2 broadcasts between interfaces.
* Therefore, routers separate broadcast domains.

**Key distinction:**

> Switch → normally separates collision domains
> Router → separates broadcast domains

---

# 2. Why Hubs Are Obsolete

Hubs repeat signals without making forwarding decisions.

Suppose 20 devices are connected to a hub. When one device transmits, the signal is repeated to the other ports.

This causes:

* More unnecessary traffic.
* A shared collision domain.
* Lower efficiency.
* Traditionally half-duplex communication.

A switch solves this by learning MAC addresses and forwarding frames toward the appropriate port.

---

# 3. How a Switch Learns MAC Addresses

Suppose A is connected to Port 1.

When the switch receives a frame from A:

```text
Source MAC = A
Incoming Port = 1
```

The switch learns:

```text
A → Port 1
```

Later, if another device sends a frame to A, the switch checks its MAC table and forwards the frame to Port 1.

### Basic Process

```text
Receive frame
      ↓
Learn source MAC
      ↓
Check destination MAC
      ↓
Find destination port
      ↓
Forward / flood / filter
```

If the destination MAC is unknown, the switch may flood the frame within the relevant VLAN.

---

# 4. Why a Switch Is Called a Multiport Bridge

A traditional bridge connects a small number of LAN segments.

A switch performs the same fundamental Layer 2 function but provides many ports and is optimized for modern Ethernet networks.

Therefore:

> Switch = Practical, high-performance multiport bridge

---

# 5. Repeater vs Hub

A hub can be considered a **multiport repeater**.

```text
Repeater
   ↓
Regenerates signal

Hub
   ↓
Regenerates/repeats signal across multiple ports
```

Neither device uses MAC addresses to make forwarding decisions.

---

# 6. Switch vs Router

This is one of the most important interview comparisons.

| Switch                                       | Router                         |
| -------------------------------------------- | ------------------------------ |
| Mainly Layer 2                               | Mainly Layer 3                 |
| Uses MAC addresses                           | Uses IP addresses              |
| Forwards frames                              | Routes packets                 |
| Connects devices/segments within a LAN       | Connects different IP networks |
| Uses MAC table                               | Uses routing table             |
| Normally does not separate broadcast domains | Separates broadcast domains    |

### Example

```text
PC A ── Switch ── PC B
       Same LAN

PC A ── Switch ── Router ── Internet
                   |
             Different networks
```

---

# 7. Port Is Not the Same as Collision Domain

It is common to hear:

> "Each switch port is a collision domain."

A more precise statement is:

> In typical switched Ethernet, each switch port corresponds to a separate collision domain.

A **port** is a physical/logical interface on the switch.

A **collision domain** is a networking concept describing where transmission collisions could occur.

They are related, but they are not the same thing.

---

# 8. Full-Duplex and Collisions

In full-duplex Ethernet:

```text
A  ─────────→  B
A  ←─────────  B
```

Both directions can transmit simultaneously.

There is no need for devices to compete for a shared medium on that link, so Ethernet collisions do not occur there.

This is why modern switched Ethernet is normally collision-free under full-duplex operation.

However, saying that "switches can never have collisions" is too broad. Half-duplex Ethernet can still experience collisions.

---

# 9. Gateway Is a Broad Term

The word **gateway** is used in several contexts.

It can refer to a device or system that serves as an entry/exit point or performs translation between different systems.

Depending on the implementation, a gateway may perform:

* Routing
* NAT
* Protocol translation
* Application-level translation
* Security functions

Therefore:

> Gateway does not automatically mean Layer 7.

---

# 10. Firewall vs IDS

These are often confused.

### Firewall

The firewall makes an access-control decision.

```text
Traffic → Firewall → Allow / Block
```

### IDS

An IDS observes activity and reports suspicious behavior.

```text
Traffic → IDS → Detect → Alert
```

### IPS

An IPS can actively prevent suspicious traffic.

```text
Traffic → IPS → Detect → Block
```

---

# 11. Modem

A modem is a **modulator-demodulator**.

Its traditional purpose is to convert digital data into signals suitable for transmission over a particular communication medium and convert received signals back into usable data.

```text
Digital Data
     ↓
   Modem
     ↓
Transmission Medium
     ↓
   Modem
     ↓
Digital Data
```

Modern broadband equipment often combines modem, router, switch, Wi-Fi access point, and firewall functionality into one device.

Do not assume every device sold as a "modem" performs only modem functionality.

---

# 12. Device + Data Unit Cheat Sheet

A useful placement shortcut is:

```text
Repeater → Signal
Hub      → Signal
Bridge   → Frame + MAC
Switch   → Frame + MAC
Router   → Packet + IP
```

This helps connect OSI layers with actual networking terminology.

---

# 13. Easy Analogy

Imagine a large apartment complex.

* **Repeater:** Makes a weak announcement audible again.
* **Hub:** Repeats the announcement to everyone.
* **Switch:** Knows which apartment should receive a package and sends it there.
* **Router:** Decides which road/network the package should take to reach another area.
* **Gateway:** Translates between two systems that communicate differently.
* **Firewall:** Checks whether the package is allowed through.
* **IDS:** Watches for suspicious activity and raises an alarm.

This analogy is useful for remembering the **role**, but actual networking behavior should be understood using OSI layers and addresses.

---

# 14. High-Value Interview Distinctions

### Repeater vs Amplifier

> Repeater regenerates/restores a signal; an amplifier increases signal amplitude and may amplify noise.

### Hub vs Switch

> Hub repeats signals to ports, while a switch uses MAC addresses to selectively forward frames.

### Switch vs Router

> A switch primarily forwards Layer 2 frames using MAC addresses, while a router forwards Layer 3 packets using IP addresses.

### Firewall vs IDS

> A firewall controls traffic according to rules, while an IDS detects suspicious activity and generates alerts.

### IDS vs IPS

> IDS detects and alerts; IPS detects and actively prevents.

### Bridge vs Switch

> A switch is essentially a high-performance multiport bridge used extensively in modern Ethernet networks.

---

# 15. Final Mental Model

```text
             NETWORK DEVICE DECISION

       "How does this device handle data?"
                       |
       ┌───────────────┼────────────────┐
       ↓               ↓                ↓
    Signal            MAC              IP
       |               |                |
   Repeater        Bridge/Switch      Router
       |
      Hub

Security:
       |
   ┌───┴────┐
   ↓        ↓
Firewall   IDS
 Control   Detect
```
