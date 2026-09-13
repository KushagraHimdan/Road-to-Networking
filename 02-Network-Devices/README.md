# Network Devices

Network devices are hardware or software-based components used to connect devices, transmit data, forward traffic, or provide network security.

## 1. Communication Media

Communication media provide the path through which data travels.

### UTP (Unshielded Twisted Pair)

* Commonly used in homes, offices, and Ethernet networks.
* Contains pairs of copper wires twisted together.
* Twisting reduces electromagnetic interference (EMI).
* Common Ethernet cable categories include Cat5e, Cat6, and Cat6a.

### Coaxial Cable

* Contains a central copper conductor surrounded by insulation and shielding.
* Commonly used for cable television and some broadband connections.
* Provides better shielding than ordinary unshielded twisted-pair cable.

### Fiber-Optic Cable

* Transmits data using light signals.
* Provides very high bandwidth and supports long-distance communication.
* Resistant to electromagnetic interference.
* Commonly used in backbone and high-speed networks.

---

# 2. Repeater

**OSI Layer:** Physical Layer (Layer 1)

A repeater receives a weakened signal and **regenerates/restores** it so that it can travel farther.

### Key Points

* Used when signals weaken because of distance, a phenomenon called **attenuation**.
* Works with signals rather than MAC or IP addresses.
* Does not make forwarding decisions.
* Does not filter traffic.
* Does not divide a collision domain.

### Repeater vs Amplifier

| Repeater                        | Amplifier                               |
| ------------------------------- | --------------------------------------- |
| Regenerates/restores the signal | Increases signal amplitude              |
| Networking device               | General signal-strengthening device     |
| Can restore signal quality      | May amplify noise along with the signal |

**Remember:**

> Amplifier → makes the signal stronger
> Repeater → receives and regenerates the signal

---

# 3. Hub

**OSI Layer:** Physical Layer (Layer 1)

A hub is essentially a **multiport repeater**.

When a hub receives a signal on one port, it repeats that signal out through its other ports.

### Key Points

* Does not understand MAC addresses.
* Does not selectively forward frames.
* All connected devices share the same collision domain.
* Traditionally operates using half-duplex communication.
* Collisions can occur because devices share the same communication medium.
* Hubs are largely obsolete in modern Ethernet networks.

### Example

```text
        A
        |
        |
B ---- HUB ---- C
        |
        D
```

If A sends data intended for B, the hub repeats the signal toward B, C, and D. The other devices receive the signal but discard the frame if the destination MAC address is not theirs.

**Remember:**

> Hub → Repeat everywhere

---

# 4. Bridge

**OSI Layer:** Data Link Layer (Layer 2)

A bridge connects LAN segments and makes forwarding decisions using **MAC addresses**.

### Key Points

* Uses MAC addresses for filtering and forwarding.
* Maintains a MAC address table.
* Learns source MAC addresses from incoming frames.
* Can reduce unnecessary traffic between LAN segments.
* Separates collision domains.

### Example

```text
LAN Segment 1              LAN Segment 2

M1 ---- M2                 M7 ---- M8
          \               /
           \--- Bridge ---/
```

If M1 sends a frame to M2 on the same segment, the bridge does not need to forward it to Segment 2.

If M1 sends a frame to M7, the bridge forwards it toward Segment 2.

### Static vs Dynamic Bridge

| Static Bridge                        | Dynamic / Transparent Bridge         |
| ------------------------------------ | ------------------------------------ |
| MAC entries configured manually      | Learns MAC addresses automatically   |
| Requires manual updates              | Adapts automatically                 |
| Less flexible                        | More flexible                        |
| Suitable for controlled environments | Common concept in Ethernet switching |

An unknown destination may initially be **flooded** while the bridge/switch learns the network, depending on the situation.

---

# 5. Switch

**OSI Layer:** Data Link Layer (Layer 2)

A switch is essentially a **high-performance multiport bridge** used to connect devices within a LAN.

### Key Points

* Uses MAC addresses to forward Ethernet frames.
* Maintains a MAC address table.
* Learns which MAC address is reachable through which port.
* Normally forwards a frame only toward the required destination port.
* Each switch port generally represents a separate collision domain in typical switched Ethernet.
* Modern Ethernet switches normally use full-duplex links.
* A switch does not normally connect different IP networks; that is primarily the router's role.

### Example

```text
A ----\
B ----- SWITCH ----- C
D ----/
```

If A sends a frame to C:

```text
A → Switch → C
```

The switch checks the destination MAC address and uses its MAC table to determine the appropriate port.

**Remember:**

> Hub → Repeat
> Switch → Decide where to forward

---

# 6. Hub vs Switch

| Feature          | Hub                       | Switch                    |
| ---------------- | ------------------------- | ------------------------- |
| OSI Layer        | Layer 1                   | Layer 2                   |
| Address used     | None                      | MAC address               |
| Operation        | Repeats signal            | Forwards frames           |
| Forwarding       | To other ports            | Specific destination port |
| Collision domain | Shared                    | Usually separate per port |
| Duplex           | Traditionally half-duplex | Commonly full-duplex      |
| Efficiency       | Low                       | High                      |
| Intelligence     | Very low                  | Higher                    |

---

# 7. Router

**OSI Layer:** Network Layer (Layer 3)

A router connects different networks and forwards packets using **IP addresses** and a **routing table**.

### Key Points

* Uses IP addresses for routing decisions.
* Connects different IP networks.
* Maintains or learns routing information.
* Selects an appropriate path toward the destination.
* Separates broadcast domains.
* Also separates collision domains between its interfaces.
* Common routing protocols include RIP, OSPF, and BGP.

### Example

```text
Laptop
   |
Switch
   |
Router
   |
Internet
```

The switch handles local Layer 2 forwarding, while the router determines where packets should go between different networks.

**Remember:**

> Switch → MAC → Frame → Local network
> Router → IP → Packet → Between networks

---

# 8. Gateway

A gateway connects systems or networks and can **translate between different protocols, formats, or communication systems**.

Unlike a switch or router, the term gateway is not restricted to one specific OSI layer.

### Key Points

* Can operate across multiple layers depending on its function.
* May translate between different protocols.
* Can connect fundamentally different systems.
* May also provide functions such as routing, NAT, or firewalling depending on the device.

### Example

A VoIP gateway can connect an IP-based voice network with a traditional telephone network.

**Remember:**

> Gateway → Connects and/or translates different systems

Do not simply memorize:

> Gateway = Layer 7

The actual layer depends on what the gateway is doing.

---

# 9. Firewall

A firewall is a security mechanism that **monitors and controls network traffic according to predefined rules**.

It can be implemented as hardware, software, or a combination of both.

### Key Points

* Controls incoming and outgoing traffic.
* Can allow or block traffic based on security rules.
* Depending on its type, it may inspect:

  * IP addresses
  * Ports
  * Protocols
  * Connection state
  * Application-level information
* Helps prevent unauthorized network access.

**Remember:**

> Firewall → Should this traffic be allowed?

---

# 10. IDS (Intrusion Detection System)

An IDS monitors network or system activity to identify **suspicious or potentially malicious behavior**.

Its traditional role is to **detect and alert**, rather than directly block the activity.

### Types

#### NIDS — Network IDS

Monitors network traffic for suspicious activity.

#### HIDS — Host IDS

Monitors activity on an individual computer or server.

### Examples

* Snort → commonly used as a Network IDS.
* OSSEC → commonly used as a Host IDS.

**Remember:**

> IDS → Detects and alerts

---

# 11. Firewall vs IDS vs IPS

| Device/System | Main Purpose                                                |
| ------------- | ----------------------------------------------------------- |
| Firewall      | Controls and blocks traffic according to rules              |
| IDS           | Detects suspicious activity and generates alerts            |
| IPS           | Detects suspicious activity and actively prevents/blocks it |

### Simple Mental Model

```text
Firewall → "Should I allow this traffic?"

IDS      → "Does this activity look suspicious?"

IPS      → "This activity is suspicious, so I should stop it."
```

---

# 12. Complete Network Device Mental Model

```text
Physical Layer
    |
    ├── Repeater → Regenerates signal
    └── Hub      → Repeats signal to ports

Data Link Layer
    |
    ├── Bridge   → MAC-based forwarding/filtering
    └── Switch   → High-performance multiport bridging

Network Layer
    |
    └── Router   → IP-based routing

Multiple Layers / Translation
    |
    └── Gateway  → Connects/translates systems

Security
    |
    ├── Firewall → Controls/blocks traffic
    └── IDS      → Detects/alerts
```

# 13. Placement Cheat Sheet

| Layer / Function | Device   | Main Concept                |
| ---------------- | -------- | --------------------------- |
| Layer 1          | Repeater | Signal regeneration         |
| Layer 1          | Hub      | Signal repetition           |
| Layer 2          | Bridge   | MAC filtering               |
| Layer 2          | Switch   | MAC forwarding              |
| Layer 3          | Router   | IP routing                  |
| Multiple layers  | Gateway  | Protocol/system translation |
| Security         | Firewall | Traffic control             |
| Security         | IDS      | Intrusion detection         |

# 14. Important Placement Points

* **Repeater:** Regenerates weakened signals.
* **Hub:** Repeats signals to multiple ports.
* **Bridge:** Uses MAC addresses to filter/forward frames.
* **Switch:** Uses MAC addresses to efficiently forward frames.
* **Router:** Uses IP addresses to route packets between networks.
* **Gateway:** Connects or translates different systems/protocols.
* **Firewall:** Controls or blocks traffic according to security rules.
* **IDS:** Detects suspicious activity and generates alerts.
* **IPS:** Detects and actively prevents suspicious activity.

## Quick Revision

```text
Signal → Repeater
Repeat → Hub
MAC → Bridge
MAC + Multiple Ports → Switch
IP → Router
Translation → Gateway
Control → Firewall
Detection → IDS
Prevention → IPS
```
