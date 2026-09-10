# Computer Networks — Important Questions

## Basic Concepts

1. What is a computer network?
2. What is a node? Give examples.
3. What is a communication link?
4. What is the difference between an end node and an intermediary node?
5. What is a network protocol?
6. Why are protocols necessary for communication?
7. What are the major characteristics of a computer network?
8. What is fault tolerance?
9. What is scalability?
10. What is Quality of Service (QoS)?
11. What is the CIA Triad in network security?

---

## Data Flow

12. What is simplex communication?
13. What is half-duplex communication?
14. What is full-duplex communication?
15. What is the difference between half duplex and full duplex?
16. Give a real-world example of simplex communication.
17. Give a real-world example of half-duplex communication.
18. Give a real-world example of full-duplex communication.

---

## Network Types

19. What are PAN, LAN, CAN, MAN, and WAN?
20. Arrange PAN, LAN, CAN, MAN, and WAN in increasing order of geographical coverage.
21. What is the difference between LAN and CAN?
22. Which type of network is commonly used inside an office building?
23. Which type of network connects multiple buildings across a university campus?
24. What type of network can connect offices located in different countries?
25. Why should exact kilometer ranges of PAN/LAN/CAN/MAN/WAN not always be memorized?

---

## Client-Server and P2P

26. What is client-server architecture?
27. What is peer-to-peer architecture?
28. What is the difference between client-server and P2P architecture?
29. What are the advantages of client-server architecture?
30. What are the disadvantages of client-server architecture?
31. Why is centralized authentication easier in client-server architecture?
32. Why can P2P networks be difficult to manage as they grow?
33. Is P2P always insecure? Explain.

---

## Network Topology

34. What is network topology?
35. What is the difference between physical and logical topology?
36. What is bus topology?
37. What is ring topology?
38. What is star topology?
39. What is mesh topology?
40. What is tree topology?
41. What is hybrid topology?
42. Which topology is generally the most expensive?
43. Which topology provides multiple alternative paths?
44. Which topology is commonly used in modern Ethernet LANs?
45. What happens if the central device of a star topology fails?
46. What happens if the backbone of a bus topology fails?
47. Why is full mesh expensive?
48. How many links are required for a full mesh containing 5 devices?
49. What is the formula for calculating links in a full mesh?
50. What are the advantages and disadvantages of mesh topology?

---

## Architecture vs Topology

51. What is the difference between network topology and network architecture?
52. Can a client-server network use a star topology?
53. Is the central device in a star topology necessarily a server?
54. What is the difference between a switch and a server?

---

## Switching

55. What is switching in computer networks?
56. What are the three major switching techniques?
57. What is circuit switching?
58. What are the three phases of circuit switching?
59. What are the advantages and disadvantages of circuit switching?
60. What is message switching?
61. What does store-and-forward mean?
62. Why is message switching slower than packet switching?
63. What is packet switching?
64. Why is packet switching efficient for modern data networks?
65. What are the disadvantages of packet switching?

---

## Datagram and Virtual Circuit

66. What is the datagram approach?
67. Why is datagram packet switching called connectionless?
68. Can two datagram packets take different routes to the same destination?
69. Can two datagram packets take the same route?
70. What is a virtual circuit?
71. Why does a virtual circuit require a setup phase?
72. How does a virtual circuit reduce per-packet addressing overhead?
73. What is the difference between a datagram and a virtual circuit?
74. Which approach is used by IP networks?
75. Give examples of virtual-circuit technologies.

---

# Interview-Oriented Questions

## Q1. What is the fundamental difference between circuit switching and packet switching?

**Expected answer:**

Circuit switching establishes and reserves a dedicated communication path for the duration of communication, while packet switching divides data into packets and shares network resources among multiple communications.

---

## Q2. Why is message switching slower than packet switching?

**Expected answer:**

Message switching stores the complete message at every intermediate node before forwarding it. Packet switching divides the message into smaller packets, allowing packets to be forwarded individually, reducing the waiting time associated with storing the entire message.

---

## Q3. Can all packets in a datagram network follow the same route?

**Expected answer:**

Yes, they can happen to follow the same route, but they are not required to. Each packet is independently routed according to the network's routing decisions.

---

## Q4. Why does a virtual circuit need a setup phase?

**Expected answer:**

The setup phase establishes the logical path and necessary state in the network. After setup, packets can use the established virtual-circuit identifier instead of carrying complete routing information in the same way as independent datagrams.

---

## Q5. Which topology is the most expensive and why?

**Expected answer:**

Full mesh is generally the most expensive because every device must have a direct connection to every other device. The number of links is:

```text
n(n − 1) / 2
```

---

## Q6. A company has 100 computers in one office building. Which network type is appropriate?

**Answer:**

**LAN (Local Area Network)** because the devices are located within a relatively small geographical area.

---

## Q7. A university connects networks across several buildings. Which network type is appropriate?

**Answer:**

**CAN (Campus Area Network)** because it connects multiple LANs across a campus.

---

## Q8. A network uses a central switch to connect computers. Which topology is this?

**Answer:**

**Star topology.**

---

## Q9. A company uses centralized authentication and a dedicated server to provide resources to users. Which architecture is this?

**Answer:**

**Client-server architecture.**

---

## Q10. Can a network be both client-server and star topology?

**Answer:**

Yes.

These describe different aspects of a network:

* **Client-server** → architecture
* **Star** → topology

---

# Quick Revision Questions

Before moving to the next Networking phase, make sure you can answer these without notes:

1. What is a network?
2. What is a node?
3. What is a protocol?
4. Explain simplex, half duplex, and full duplex.
5. Explain PAN → LAN → CAN → MAN → WAN.
6. Differentiate client-server and P2P.
7. Differentiate topology and architecture.
8. Explain all six major topologies.
9. Why is mesh highly fault tolerant?
10. What is switching?
11. Differentiate circuit, message, and packet switching.
12. Differentiate datagram and virtual circuit.
13. Why does virtual circuit require setup?
14. Why is packet switching efficient?
15. Why is full mesh expensive?
