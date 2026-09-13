# Important Questions — Network Devices

## Quick Revision Questions

### 1. What is a repeater?

**Expected points:**

* Layer 1 device.
* Receives a weakened signal.
* Regenerates/restores the signal.
* Used to overcome attenuation.
* Does not use MAC or IP addresses.

---

### 2. What is the difference between a repeater and an amplifier?

**Expected points:**

* Repeater regenerates/restores the signal.
* Amplifier increases signal amplitude.
* Amplifier may also amplify noise.
* Repeater is specifically used as a networking device.

---

### 3. What is a hub?

**Expected points:**

* Layer 1 device.
* Multiport repeater.
* Repeats incoming signals to other ports.
* Does not use MAC addresses for forwarding.
* All connected devices share a collision domain.

---

### 4. What is a bridge?

**Expected points:**

* Layer 2 device.
* Connects LAN segments.
* Uses MAC addresses.
* Maintains a MAC address table.
* Filters and forwards frames.

---

### 5. What is a switch?

**Expected points:**

* Layer 2 device.
* High-performance multiport bridge.
* Uses MAC addresses.
* Maintains a MAC address table.
* Forwards frames toward the appropriate port.

---

### 6. What is a router?

**Expected points:**

* Layer 3 device.
* Connects different IP networks.
* Uses IP addresses.
* Uses a routing table.
* Forwards packets based on routing decisions.

---

### 7. What is a gateway?

**Expected points:**

* Connects different systems/networks.
* Can translate between protocols or formats.
* Not restricted to one OSI layer.
* Function depends on implementation.

---

### 8. What is a firewall?

**Expected points:**

* Security mechanism.
* Monitors traffic.
* Applies predefined rules.
* Allows or blocks traffic.
* Can be hardware, software, or both.

---

### 9. What is an IDS?

**Expected points:**

* Intrusion Detection System.
* Monitors network/system activity.
* Detects suspicious behavior.
* Generates alerts.
* NIDS monitors networks; HIDS monitors hosts.

---

# Comparison Questions

### 10. Differentiate between a hub and a switch.

Focus on:

* OSI layer
* MAC address usage
* Forwarding behavior
* Collision domains
* Duplex
* Efficiency

---

### 11. Differentiate between a switch and a router.

Focus on:

* Layer 2 vs Layer 3
* MAC vs IP
* Frame vs packet
* LAN connectivity vs inter-network connectivity
* MAC table vs routing table
* Broadcast domains

---

### 12. Differentiate between a repeater and a hub.

Focus on:

* Both operate at Layer 1.
* Repeater is generally used to regenerate/extend a signal.
* Hub is a multiport repeater.
* Hub connects multiple devices and repeats traffic to its other ports.

---

### 13. Differentiate between a bridge and a switch.

Focus on:

* Both primarily operate at Layer 2.
* Both use MAC addresses.
* Switch is essentially a high-performance multiport bridge.
* Switches are more common in modern Ethernet networks.

---

### 14. Differentiate between a firewall and IDS.

Focus on:

```text
Firewall → Control / Allow / Block
IDS      → Detect / Alert
```

---

### 15. Differentiate between IDS and IPS.

Focus on:

```text
IDS → Detects and alerts
IPS → Detects and actively prevents
```

---

# Scenario-Based Questions

### 16. A signal becomes weak after traveling a long distance. Which device can help?

**Answer:** Repeater.

**Reason:** It regenerates/restores the weakened signal.

---

### 17. A company wants to connect many computers and selectively forward Ethernet frames using MAC addresses. Which device should be used?

**Answer:** Switch.

**Reason:** A switch uses MAC addresses to forward frames to appropriate ports.

---

### 18. A network needs communication between two different IP networks. Which device is primarily responsible?

**Answer:** Router.

**Reason:** Routers operate at Layer 3 and forward packets between networks using IP addresses.

---

### 19. A device receives a frame but has no idea which MAC address belongs to which port. What can it do while learning?

**Answer:** It may flood an unknown-destination frame within the relevant Layer 2 domain/VLAN while learning MAC information.

---

### 20. A security system should detect suspicious activity and notify an administrator without necessarily blocking the traffic. What should be used?

**Answer:** IDS.

---

### 21. A security system should actively block malicious traffic. What is more appropriate?

**Answer:** IPS or an appropriately configured firewall, depending on the type of threat and policy.

---

### 22. Why can collisions occur with a hub?

**Expected answer:**

Because all devices connected through a traditional hub share the same communication medium/collision domain, so simultaneous transmissions can interfere with one another.

---

### 23. Why are collisions normally absent on a modern full-duplex switch link?

**Expected answer:**

Because full-duplex Ethernet allows simultaneous transmission and reception without devices competing for a shared medium.

---

# Conceptual Questions

### 24. Why can't a repeater make a forwarding decision using a MAC address?

**Expected answer:**

A repeater operates at the Physical Layer and works with signals. MAC addresses belong to the Data Link Layer, so a repeater does not use MAC addresses for forwarding decisions.

---

### 25. Why is a hub less efficient than a switch?

**Expected answer:**

A hub repeats signals to its other ports and creates a shared collision domain, whereas a switch learns MAC addresses and can forward frames only toward the appropriate destination port.

---

### 26. How does a switch learn a MAC address?

**Expected answer:**

The switch examines the source MAC address of an incoming frame and associates that address with the incoming port in its MAC address table.

---

### 27. What happens when a switch receives a frame for an unknown destination MAC?

**Expected answer:**

The switch may flood the frame out the other relevant ports within the same VLAN, except the incoming port, while continuing to learn MAC addresses.

---

### 28. Does a switch separate broadcast domains?

**Expected answer:**

A normal Layer 2 switch does not separate broadcast domains. Broadcasts are normally forwarded within the same VLAN. A router or Layer 3 boundary separates broadcast domains.

---

### 29. Does a switch separate collision domains?

**Expected answer:**

In typical switched Ethernet, each switch port represents a separate collision domain.

---

### 30. Is a gateway always a Layer 7 device?

**Expected answer:**

No. Gateway is a broad term. A gateway can operate at different layers depending on the functionality it provides.

---

# Long-Answer Questions

### 31. Explain the different network devices according to the OSI model.

Include:

```text
Layer 1 → Repeater, Hub
Layer 2 → Bridge, Switch
Layer 3 → Router
Multiple Layers → Gateway
Security → Firewall, IDS
```

For each device explain:

* Main function
* Address/data handled
* Typical use

---

### 32. Explain hub, bridge, switch, and router with differences.

A strong answer should cover:

1. OSI layer.
2. Address used.
3. Data unit handled.
4. Forwarding behavior.
5. Collision/broadcast domains.
6. Practical applications.

---

### 33. Explain how a switch forwards an Ethernet frame.

Expected flow:

```text
Frame arrives
     ↓
Read source MAC
     ↓
Learn/update MAC table
     ↓
Read destination MAC
     ↓
Look up destination
     ↓
Known → Forward to correct port
Unknown → Flood within VLAN
```

---

### 34. Explain firewall, IDS, and IPS.

Include:

* Purpose
* Detection vs prevention
* Traffic control
* Alerts
* Blocking behavior

A useful summary:

```text
Firewall → Control traffic
IDS      → Detect and alert
IPS      → Detect and prevent
```

---

# Rapid-Fire Interview Test

Try answering these without looking at the notes:

1. Which layer does a repeater operate at?
2. Which layer does a switch operate at?
3. Which layer does a router primarily operate at?
4. Which address does a switch use?
5. Which address does a router use?
6. What does a repeater regenerate?
7. What is a hub?
8. Why are hubs inefficient?
9. What does a bridge use for forwarding?
10. What is a MAC address table?
11. What is a routing table?
12. What is the difference between a frame and a packet?
13. What is a collision domain?
14. What is a broadcast domain?
15. Which device normally separates broadcast domains?
16. Why are collisions normally absent on full-duplex Ethernet?
17. Is every switch port literally a collision domain?
18. Is a gateway always Layer 7?
19. What does a firewall do?
20. What does IDS stand for?
21. What is the difference between IDS and IPS?
22. What does NIDS monitor?
23. What does HIDS monitor?
24. Why is a switch called a multiport bridge?
25. Which device would you choose to connect different IP networks?

## One-Line Revision

```text
Repeater → Regenerate
Hub      → Repeat
Bridge   → Filter using MAC
Switch   → Forward using MAC
Router   → Route using IP
Gateway  → Translate/connect
Firewall → Control
IDS      → Detect
IPS      → Prevent
```
