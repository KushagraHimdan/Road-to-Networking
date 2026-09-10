# Computer Networks — Introduction

## 1. What is a Computer Network?

A **computer network** is a group of interconnected devices that communicate with each other to share data, information, and resources through communication links.

A basic network consists of:

* **Devices/Nodes** — Participate in communication.
* **Communication Links** — Carry data between devices.
* **Protocols** — Define the rules for communication.

```text
        COMPUTER NETWORK
              │
      ┌───────┼───────┐
      ↓       ↓       ↓
   Devices   Links   Protocols
   (Nodes)          (Rules)
```

---

# 2. Nodes

A **node** is a device that participates in network communication by sending, receiving, or forwarding data.

### Examples

* Computer
* Smartphone
* Printer
* Server
* Router
* Switch

### End Nodes

End nodes generally generate or consume data.

Examples:

* PC
* Smartphone
* Printer
* Server

### Intermediary Nodes

Intermediary nodes help forward or manage data between devices.

Examples:

* Router
* Switch
* Bridge

---

# 3. Communication Link

A **communication link** is the medium through which data travels between network devices.

### Wired Links

* Ethernet cable
* Coaxial cable
* Fiber-optic cable

### Wireless Links

* Wi-Fi
* Bluetooth
* Zigbee

---

# 4. Uses of Computer Networks

Computer networks are used for:

* Communication
* Resource sharing
* Remote access
* Collaboration
* Entertainment
* Education
* E-commerce
* Online gaming
* File sharing
* Web browsing

---

# 5. Characteristics of Computer Networks

### Fault Tolerance

The ability of a network to continue providing service even when some components fail.

**Example:** If one network path fails, traffic can use another available path.

### Scalability

The ability of a network to grow by adding more users or devices without causing unacceptable performance problems.

### Quality of Service (QoS)

QoS manages network traffic to provide appropriate performance to different applications.

Important factors include:

* Bandwidth
* Delay
* Jitter
* Packet loss

### Security

Network security protects data, devices, and resources from unauthorized access and attacks.

A common security model is the **CIA Triad**:

* **Confidentiality** — Prevent unauthorized access to information.
* **Integrity** — Prevent unauthorized modification of information.
* **Availability** — Keep systems and information accessible when required.

---

# 6. Network Services

Computer networks provide or support many services, including:

* Email
* Instant messaging
* Video calls
* Cloud/storage services
* Online gaming
* Web browsing
* File sharing
* VoIP

**VoIP (Voice over Internet Protocol)** allows voice communication over IP networks.

---

# 7. Protocol

A **protocol** is a set of rules that defines how devices communicate and exchange data over a network.

Protocols can define:

* Data format
* Data transmission
* Timing
* Error handling
* Communication procedures
* Connection establishment and termination

### Example

When two devices communicate, both must follow compatible protocol rules so that the receiver can correctly understand the transmitted data.

> **Placement Definition:**
> A protocol is a set of rules that governs communication between devices on a network.

---

# 8. Data Flow

Data flow describes the direction in which data travels between communicating devices.

## Simplex

Data travels in **only one direction**.

```text
A ─────────→ B
```

**Example:** Traditional television broadcasting.

## Half Duplex

Data can travel in **both directions, but not simultaneously**.

```text
A ─────→ B
A ←───── B
```

**Example:** Walkie-talkie.

## Full Duplex

Data can travel in **both directions simultaneously**.

```text
A ─────────→ B
A ←───────── B
```

**Example:** Telephone conversation.

### Comparison

| Mode        | Communication                  |
| ----------- | ------------------------------ |
| Simplex     | One direction only             |
| Half Duplex | Both directions, one at a time |
| Full Duplex | Both directions simultaneously |

---

# 9. Elements of Network Communication

Effective communication involves several elements.

### Message Encoding

Data must be converted into a suitable form for transmission.

### Formatting / Encapsulation

Data is organized and wrapped with required control information before transmission.

### Timing

Devices need rules that determine when data should be transmitted and how communication should be coordinated.

### Message Size

Large amounts of data may need to be divided into smaller units for efficient transmission.

### Delivery Options

Data can be delivered using different communication patterns.

**Unicast**

One sender → One receiver

```text
A ─────→ B
```

**Broadcast**

One sender → All relevant devices

```text
       → B
A ──── → C
       → D
```

**Multicast**

One sender → Selected group of receivers

```text
       → B
A ──── → D
       → F
```

---

# 10. Types of Networks

Networks can be classified according to their geographical coverage.

```text
PAN → LAN → CAN → MAN → WAN
```

The coverage generally increases from PAN to WAN.

| Type | Full Form                 | Typical Coverage       | Example            |
| ---- | ------------------------- | ---------------------- | ------------------ |
| PAN  | Personal Area Network     | Personal space         | Phone + smartwatch |
| LAN  | Local Area Network        | Home/building          | Office network     |
| CAN  | Campus Area Network       | Campus/organization    | University campus  |
| MAN  | Metropolitan Area Network | City/metropolitan area | City-wide network  |
| WAN  | Wide Area Network         | Large geographic area  | Internet           |

> Exact distance boundaries can vary. Focus on the **relative geographical coverage** rather than memorizing fixed numbers.

---

## 10.1 PAN

A **Personal Area Network** connects devices around an individual.

### Examples

* Smartphone + wireless earbuds
* Smartphone + smartwatch
* Personal devices connected through Bluetooth

### Common Technologies

* Bluetooth
* Zigbee
* IrDA

---

## 10.2 LAN

A **Local Area Network** connects devices within a relatively small area such as a:

* Home
* Office
* Building
* Laboratory

### Technologies

* Ethernet
* Wi-Fi

LANs are generally privately managed and provide high-speed communication.

---

## 10.3 CAN

A **Campus Area Network** connects multiple LANs across a campus or organization.

### Examples

* University campus
* Corporate campus
* Research institution

### Technologies

* Ethernet
* Fiber optics
* Wi-Fi

### Important Distinction

```text
One building/office       → LAN
Multiple buildings/campus → CAN
```

---

## 10.4 MAN

A **Metropolitan Area Network** covers a city or metropolitan region.

Common technologies include:

* Metro Ethernet
* MPLS

---

## 10.5 WAN

A **Wide Area Network** covers a large geographical area such as multiple cities, countries, or continents.

Examples:

* Corporate networks connecting different cities
* Global enterprise networks
* The Internet

Technologies can include:

* Leased lines
* MPLS
* VPN
* Satellite communication

---

# 11. Client-Server Architecture

In a **client-server architecture**, one or more dedicated servers provide services or resources to client devices.

```text
             SERVER
          /     |     \
         /      |      \
     Client  Client  Client
```

### Characteristics

* Centralized management
* Dedicated server(s)
* Centralized authentication and access control
* Easier resource management
* Suitable for large organizations
* Higher infrastructure and maintenance cost

### Examples

* Websites
* Email systems
* Enterprise applications
* Database systems

---

# 12. Peer-to-Peer (P2P) Architecture

In a **peer-to-peer architecture**, there is no requirement for a dedicated central server. Each peer can act as both a client and a server.

```text
       Peer
      /    \
   Peer ── Peer
      \    /
       Peer
```

### Characteristics

* Decentralized
* Lower infrastructure cost
* No dedicated central server required
* Difficult centralized management
* Security and backups can be harder to manage
* Can become difficult to manage as the network grows

### Examples

* Some file-sharing systems
* Blockchain networks
* Small peer-based networks

### Important

Do not memorize:

> Client-server = secure
> P2P = insecure

Security depends on the actual system design. Client-server architecture simply makes **centralized authentication and access control easier**.

---

# 13. Network Topology

**Network topology** describes how devices and connections are arranged in a network.

### Physical Topology

Describes the physical arrangement of devices and cables.

### Logical Topology

Describes how data flows through the network.

---

# 14. Types of Network Topology

The major topologies are:

* Bus
* Ring
* Star
* Mesh
* Tree
* Hybrid

---

## 14.1 Bus Topology

All devices share a common communication cable called the **backbone**.

```text
A      B      C      D
│      │      │      │
══════════════════════
        Backbone
```

### Advantages

* Simple design
* Less cabling
* Easy to set up for small networks

### Disadvantages

* Backbone failure can affect the entire network
* Performance decreases as traffic increases
* Limited scalability
* Troubleshooting can be difficult

---

## 14.2 Ring Topology

Devices are connected in a closed loop, with each device connected to two neighboring devices.

```text
      A ─── B
     /       \
    D         C
     \       /
      ───────
```

Traditional ring networks may use a **token** to control transmission.

### Advantages

* Orderly data transmission
* Predictable access in token-based implementations

### Disadvantages

* A failure can disrupt communication depending on the implementation
* Troubleshooting can be difficult
* Less common in modern LANs

---

## 14.3 Star Topology

All devices connect to a central device, usually a switch.

```text
          A
          |
          |
B ───── SWITCH ───── C
          |
          |
          D
```

### Advantages

* Easy to install
* Easy to troubleshoot
* Failure of one device/link usually does not affect other devices
* Easy to expand

### Disadvantages

* Central device is critical
* Failure of the central device can affect connected devices
* Requires more cabling than bus topology

Star topology is very common in modern Ethernet LANs.

---

## 14.4 Mesh Topology

Devices have direct connections to multiple or all other devices.

A **full mesh** connects every device directly to every other device.

```text
A ───── B
|\     /|
| \   / |
|  \ /  |
|  / \  |
| /   \ |
C ───── D
```

### Advantages

* Multiple communication paths
* Excellent fault tolerance
* Link failure can often be bypassed
* High reliability

### Disadvantages

* Expensive
* Complex installation
* Requires many cables and ports

### Full Mesh Formula

For `n` devices:

```text
Number of links = n(n − 1) / 2
```

For 5 devices:

```text
5(5 − 1) / 2 = 10 links
```

---

## 14.5 Tree Topology

Tree topology is a hierarchical arrangement of interconnected networks.

```text
              Root
             /    \
           SW1    SW2
          /  \    /  \
         A    B  C    D
```

### Advantages

* Scalable
* Hierarchical management
* Easier expansion
* Fault isolation between branches

### Disadvantages

* Failure of an upper-level component can affect multiple branches
* More cabling and configuration
* More complex than simple star networks

---

## 14.6 Hybrid Topology

A **hybrid topology** combines two or more different topologies.

Examples:

* Star + Bus
* Star + Ring
* Multiple topology combinations

### Advantages

* Flexible
* Scalable
* Can be customized according to requirements
* Suitable for large networks

### Disadvantages

* More complex
* Higher implementation cost
* Requires careful management

---

# 15. Topology Comparison

| Topology | Main Feature          | Major Advantage      | Major Disadvantage          |
| -------- | --------------------- | -------------------- | --------------------------- |
| Bus      | Common backbone       | Less cabling         | Backbone failure            |
| Ring     | Closed loop           | Orderly transmission | Failure can disrupt network |
| Star     | Central device        | Easy management      | Central device failure      |
| Mesh     | Multiple direct paths | High reliability     | Very expensive              |
| Tree     | Hierarchical          | Scalable             | Upper-level failure         |
| Hybrid   | Combination           | Flexible             | Complex and costly          |

### Important Topology Questions

* **Most expensive:** Full Mesh
* **Traditional one-direction/token-based topology:** Ring
* **Best fault tolerance:** Mesh
* **Common modern LAN topology:** Star

---

# 16. Switching

**Switching** is the process of forwarding data from a source to a destination through a network by selecting an appropriate path or forwarding method.

The major switching techniques are:

1. Circuit Switching
2. Message Switching
3. Packet Switching

---

# 17. Circuit Switching

In **circuit switching**, a dedicated communication path is established between two endpoints for the duration of communication.

### Phases

```text
Connection Establishment
          ↓
      Data Transfer
          ↓
 Connection Termination
```

### Example

Traditional telephone networks.

### Advantages

* Dedicated path
* Predictable communication after setup
* Suitable for continuous communication

### Disadvantage

Network resources remain reserved even when no data is being transmitted, which can waste bandwidth.

### Mental Model

> **Reserve the road before travelling.**

---

# 18. Message Switching

In **message switching**, the complete message is stored at an intermediate node before being forwarded to the next node.

This is called **store-and-forward**.

```text
Sender
  ↓
Node 1
  ↓
Node 2
  ↓
Receiver
```

Each intermediate node stores the complete message before forwarding it.

### Advantages

* No dedicated communication path
* Can handle variable-length messages

### Disadvantages

* High delay
* Requires storage for complete messages
* Not suitable for real-time communication

### Example

Email is a useful conceptual example of delay-tolerant communication, although modern email itself runs over packet-switched networks.

### Mental Model

> **Store the whole message, then forward it.**

---

# 19. Packet Switching

In **packet switching**, data is divided into smaller units called **packets**.

Each packet is transmitted through the network and may be forwarded independently.

```text
Large Data
    ↓
┌────┬────┬────┬────┐
│ P1 │ P2 │ P3 │ P4 │
└────┴────┴────┴────┘
    ↓
Network
    ↓
Destination
```

Packet switching is the fundamental switching approach used by modern IP networks, including the Internet.

### Advantages

* Efficient bandwidth utilization
* Supports bursty traffic
* Scalable
* Multiple paths can be used
* No dedicated path is required in datagram packet switching

### Disadvantages

* Variable delay
* Possible packet loss
* Packets may arrive out of order
* Routing is more complex

### Mental Model

> **Break data into packets and share the network.**

---

# 20. Types of Packet Switching

Packet switching can be implemented using:

1. Datagram Approach
2. Virtual Circuit

---

# 21. Datagram Approach

The datagram approach is **connectionless**.

No path is established before transmission. Each packet is treated independently and can potentially take a different route.

```text
P1 ──→ Route A ──→
P2 ──→ Route B ──→ Destination
P3 ──→ Route A ──→
P4 ──→ Route C ──→
```

### Characteristics

* No connection setup
* Each packet is routed independently
* Packets contain destination addressing information
* Packets may take different routes
* Packets may arrive out of order
* Packets may be lost
* Higher per-packet addressing overhead

### Example

IP networks use the datagram approach.

> **Important:** Packets *can* happen to follow the same route, but they are not required to.

### Mental Model

> **Every packet makes its own routing decision.**

---

# 22. Virtual Circuit

A virtual circuit is a **connection-oriented** packet-switching approach.

A logical path is established before data transfer.

```text
Setup
  ↓
Logical Path Established
  ↓
Packet 1 ─────────→
Packet 2 ─────────→
Packet 3 ─────────→
  ↓
Teardown
```

### Characteristics

* Requires setup
* Establishes a logical path
* Packets generally follow the established logical route
* Packets can use a short virtual-circuit identifier
* Lower per-packet addressing overhead
* Packets generally arrive in order

### Examples

* ATM
* Frame Relay

### Important

A virtual circuit is not automatically guaranteed to be reliable. Reliability depends on the complete protocol and network design.

---

# 23. Datagram vs Virtual Circuit

| Feature    | Datagram                               | Virtual Circuit                    |
| ---------- | -------------------------------------- | ---------------------------------- |
| Connection | Connectionless                         | Connection-oriented                |
| Setup      | Not required                           | Required                           |
| Route      | Packets routed independently           | Logical path established           |
| Addressing | Destination information in each packet | Short VC identifier can be used    |
| Path       | May vary                               | Generally follows established path |
| Ordering   | May be out of order                    | Generally ordered                  |
| Overhead   | Higher per packet                      | Lower per packet after setup       |
| Example    | IP                                     | ATM, Frame Relay                   |

---

# 24. Switching Comparison

| Feature             | Circuit                  | Message                      | Packet                 |
| ------------------- | ------------------------ | ---------------------------- | ---------------------- |
| Data unit           | Continuous communication | Complete message             | Small packets          |
| Dedicated path      | Yes                      | No                           | Usually no             |
| Store-and-forward   | No                       | Whole message                | Per packet             |
| Resource efficiency | Lower                    | Moderate                     | High                   |
| Delay               | Predictable after setup  | High                         | Variable               |
| Main use            | Traditional telephone    | Delay-tolerant communication | Internet/data networks |

---

# 25. Important Conceptual Distinctions

## LAN vs CAN

```text
One office/building      → LAN
Multiple buildings/campus → CAN
```

## Topology vs Architecture

**Topology** describes **how devices are physically/logically connected**.

**Architecture** describes **how roles and services are organized**.

```text
Topology:
How are devices connected?

Architecture:
Who provides services/resources?
```

A client-server network can use a star topology.

---

## Circuit vs Packet Switching

**Circuit switching:**

> Reserve a dedicated path.

**Packet switching:**

> Share network resources by sending data as packets.

---

## Message vs Packet Switching

**Message switching** stores the **entire message** before forwarding.

**Packet switching** divides data into **smaller packets**, allowing packets to be forwarded individually.

---

## Datagram vs Virtual Circuit

**Datagram:**

> No setup; each packet is independently routed.

**Virtual Circuit:**

> Setup first; packets use an established logical path.

---

# 26. Placement Revision

### Must Know

* Definition of computer network
* Node and communication link
* Protocol
* Simplex, half duplex, full duplex
* PAN, LAN, CAN, MAN, WAN
* Client-server vs P2P
* Physical vs logical topology
* Bus, Ring, Star, Mesh, Tree, Hybrid
* Circuit, Message, and Packet switching
* Datagram vs Virtual Circuit

### Frequently Tested Concepts

* Mesh provides high fault tolerance but is expensive.
* Star is common in modern LANs.
* LAN covers a smaller area than CAN.
* Client-server and star topology are different concepts.
* Circuit switching reserves a dedicated path.
* Message switching stores the complete message.
* Packet switching divides data into packets.
* Datagram packet switching is connectionless.
* Virtual circuit packet switching requires setup.
* Datagram packets may take different routes.
* A datagram packet can still happen to take the same route as another packet.

---

# 27. Quick Mental Map

```text
                    COMPUTER NETWORKS
                           │
        ┌──────────────────┼──────────────────┐
        ↓                  ↓                  ↓
     Network            Topology           Switching
      Types                │                  │
        │          ┌───────┼───────┐          ├── Circuit
        │          ↓       ↓       ↓          ├── Message
   PAN → LAN → CAN → MAN → WAN    ...         └── Packet
                                                 │
                                             ┌───┴────┐
                                             ↓        ↓
                                          Datagram   VC
```

### One-Line Revision

> **Networks connect devices, protocols control communication, topologies describe connections, architectures describe roles, and switching determines how data is forwarded through the network.**
