# Important Questions — Physical Layer

## Quick Revision Questions

### 1. What is the Physical Layer?

**Expected answer:**

The Physical Layer is Layer 1 of the OSI model. It is responsible for transmitting raw bits as physical signals through a communication medium.

---

### 2. What is the data unit of the Physical Layer?

**Answer:** Bits.

---

### 3. What is a bit?

**Answer:**

A bit is a unit of digital information represented as `0` or `1`.

---

### 4. What is a signal?

**Answer:**

A signal is the physical representation used to carry information through a communication medium.

---

### 5. What is the difference between a bit and a signal?

**Expected answer:**

A bit represents digital information, while a signal is the physical representation used to transmit that information.

---

### 6. What are common Physical Layer components?

**Expected points:**

* Cables
* Repeaters
* Hubs
* Physical connectors/interfaces

---

### 7. What are the main types of cables?

**Answer:**

* UTP
* Coaxial
* Fiber-optic

---

### 8. Why are twisted pairs used in UTP cables?

**Answer:**

The twisting helps reduce electromagnetic interference between wires.

---

### 9. What is attenuation?

**Answer:**

Attenuation is the weakening or reduction of signal strength as it travels through a communication medium.

---

### 10. What is a repeater?

**Answer:**

A repeater is a Layer 1 device that receives a weakened signal, regenerates/restores it, and transmits it onward.

---

# Encoding and Modulation

### 11. What is encoding?

**Expected answer:**

Encoding maps data or bits into a suitable physical signaling representation for transmission.

---

### 12. What is modulation?

**Expected answer:**

Modulation varies a carrier signal according to the information being transmitted.

---

### 13. What is demodulation?

**Expected answer:**

Demodulation extracts the information from a received modulated carrier signal.

---

### 14. What is a modem?

**Answer:**

A modem is a device that performs modulation and demodulation.

```text
Modem = Modulator + Demodulator
```

---

### 15. Differentiate between encoding and modulation.

Focus on:

* What is being changed?
* Purpose
* Role of the carrier signal
* Where each is commonly encountered

---

# Connection Questions

### 16. What is a point-to-point connection?

**Answer:**

A point-to-point connection uses a link connecting exactly two devices.

---

### 17. What is a multipoint connection?

**Answer:**

A multipoint connection allows multiple devices to share a communication link or medium.

---

### 18. Differentiate between point-to-point and multipoint connections.

| Point-to-Point                       | Multipoint                  |
| ------------------------------------ | --------------------------- |
| Two devices                          | Multiple devices            |
| Dedicated link between two endpoints | Shared link                 |
| Direct connection                    | Shared communication medium |

---

# Delivery Questions

### 19. What is unicast?

**Answer:** One sender → one specific receiver.

---

### 20. What is anycast?

**Answer:** One sender → one selected receiver from a group of possible receivers.

---

### 21. What is multicast?

**Answer:** One sender → selected group of receivers.

---

### 22. What is broadcast?

**Answer:** One sender → all applicable devices within the broadcast domain.

---

### 23. Differentiate between unicast, anycast, multicast, and broadcast.

```text
Unicast    → One specific receiver
Anycast    → One selected receiver from a group
Multicast  → Selected group of receivers
Broadcast  → All applicable receivers
```

---

### 24. Does unicast mean a dedicated physical connection exists?

**Answer:**

No. Unicast describes one-to-one delivery. It does not necessarily mean that a dedicated physical connection has been established.

---

### 25. Is multipoint the same as multicast?

**Answer:**

No.

* Multipoint describes a shared connection/link.
* Multicast describes delivery of data to a selected group.

---

# Communication Direction Questions

### 26. What is simplex communication?

**Answer:**

Communication occurs in only one direction.

---

### 27. What is half-duplex communication?

**Answer:**

Both devices can communicate, but only one direction can transmit at a time.

---

### 28. What is full-duplex communication?

**Answer:**

Both devices can transmit and receive simultaneously.

---

### 29. Differentiate between simplex, half-duplex, and full-duplex.

| Mode        | Communication                  |
| ----------- | ------------------------------ |
| Simplex     | One direction                  |
| Half-duplex | Both directions, one at a time |
| Full-duplex | Both directions simultaneously |

---

### 30. What is the difference between delivery mode and communication direction?

**Expected answer:**

Delivery mode describes **who receives the data**, while communication direction describes **how data can flow between communicating endpoints**.

```text
Delivery:
Unicast / Anycast / Multicast / Broadcast

Direction:
Simplex / Half-Duplex / Full-Duplex
```

---

# Scenario-Based Questions

### 31. A signal becomes weak after traveling a long distance. Which device can help?

**Answer:** Repeater.

---

### 32. Why does a repeater operate at Layer 1?

**Expected answer:**

Because it works directly with physical signals and regenerates weakened signals. It does not use MAC or IP addresses for forwarding decisions.

---

### 33. Can a repeater determine the destination MAC address?

**Answer:** No.

**Reason:** MAC addresses belong to the Data Link Layer, while a repeater operates at the Physical Layer.

---

### 34. A network needs to transmit data over a long distance through fiber. Which medium would be suitable?

**Answer:** Fiber-optic cable.

**Reason:** It provides high bandwidth, supports long distances, and is resistant to electromagnetic interference.

---

### 35. Multiple devices need to share one communication medium. What type of connection is this?

**Answer:** Multipoint.

---

### 36. A sender needs to send data to one specific receiver. Which delivery mode is used?

**Answer:** Unicast.

---

### 37. A service is available from several servers, and routing selects one appropriate server. Which delivery method is this?

**Answer:** Anycast.

---

### 38. A sender needs to deliver the same data to a selected group of receivers. Which method is used?

**Answer:** Multicast.

---

### 39. A sender needs to reach all applicable devices in its local broadcast domain. Which method is used?

**Answer:** Broadcast.

---

### 40. A communication system allows both devices to transmit, but only one can transmit at a time. What is it?

**Answer:** Half-duplex.

---

### 41. Two devices transmit to each other simultaneously. What communication mode is being used?

**Answer:** Full-duplex.

---

# Interview Questions

### 42. Why is the Physical Layer important?

**Expected answer:**

It provides the foundation for network communication by defining how raw bits are physically represented and transmitted through the communication medium.

---

### 43. Why can't the Physical Layer understand an IP address?

**Expected answer:**

IP addresses are used at the Network Layer. The Physical Layer deals with physical signals and raw bit transmission.

---

### 44. Why can't a repeater filter traffic?

**Expected answer:**

Because filtering requires examining information such as MAC addresses, while a repeater operates only with physical signals at Layer 1.

---

### 45. Why is a hub considered a Layer 1 device?

**Expected answer:**

A hub repeats physical signals between its ports without examining MAC addresses or making Layer 2 forwarding decisions.

---

### 46. Why is fiber-optic cable preferred for long-distance/high-bandwidth communication?

**Expected points:**

* High bandwidth.
* Long transmission distances.
* Low susceptibility to electromagnetic interference.
* Uses light for transmission.

---

# 5-Mark Questions

### 47. Explain the functions of the Physical Layer.

Include:

1. Bit transmission.
2. Encoding and decoding.
3. Signal transmission.
4. Modulation and demodulation.
5. Physical representation of data.

---

### 48. Explain point-to-point and multipoint connections with diagrams.

Include:

```text
Point-to-Point:

A ───────── B


Multipoint:

       B
       |
A ─────┼──── C
       |
       D
```

---

### 49. Explain unicast, anycast, multicast, and broadcast with examples.

Include:

* Definition.
* Communication pattern.
* Simple diagram.
* One practical example.

---

### 50. Explain simplex, half-duplex, and full-duplex communication.

Include:

* Direction of communication.
* Diagram.
* Example.
* Difference between the three modes.

---

# Rapid-Fire Test

Try answering these without looking at the notes:

1. Which OSI layer is the Physical Layer?
2. What is its data unit?
3. What is a bit?
4. What is a signal?
5. What is attenuation?
6. What is encoding?
7. What is modulation?
8. What does a modem do?
9. What is point-to-point?
10. What is multipoint?
11. What is unicast?
12. What is anycast?
13. What is multicast?
14. What is broadcast?
15. What is simplex?
16. What is half-duplex?
17. What is full-duplex?
18. What does a repeater do?
19. Why does a repeater operate at Layer 1?
20. Can a repeater read MAC addresses?
21. What is the difference between unicast and point-to-point?
22. What is the difference between multipoint and multicast?
23. What is the difference between full-duplex and broadcast?
24. Why are collisions normally absent on full-duplex Ethernet?
25. Which cable is particularly suitable for long-distance, high-bandwidth communication?

# One-Minute Revision

```text
Physical Layer → Layer 1
Data Unit      → Bits

Signal         → Physical representation
Encoding       → Maps data to signaling representation
Modulation     → Varies carrier to carry information
Modem          → Modulator + Demodulator

Point-to-Point → Two devices
Multipoint     → Multiple devices sharing a link

Unicast        → One specific receiver
Anycast        → One selected receiver from a group
Multicast      → Selected group
Broadcast      → All applicable devices

Simplex        → One direction
Half-Duplex    → Both directions, one at a time
Full-Duplex    → Both simultaneously

Repeater       → Regenerates weakened signal
```
