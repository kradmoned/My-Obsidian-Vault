# TCP And UDP

| TCP                 | UDP             |
| ------------------- | --------------- |
| Connection Oriented | Connection Less |
| Reliable            | Not Reliable    |
| Item1.3             | Item2.3         |
| Item1.4             | Item2.4         |

- Tranport protocol runs in end system.
- **Send SIde** breaks the message into segments pass to network layer
- **Recieving side** reassembles segments in to meesages , passes to app layer.

## TCP

- **In Order Delivery**
  - The segment will be recieved in the same order they are sent.
- **Congestion Control**
  - It is the management of segments at network layer
  - It occurs due to network.
  - The network informs about congestion, Such as devices such as router
- **Flow Control**
  - You do not overwhelm the reciever.
  - Basically do not send so much segments such that buffer is overflowed or the device doesnt manage.
  - The reciever informs the sender
- **Connection Setup**
  - It is the handshake between sender and reciever.
- **Bandwith Gurantee**
  - Does not provide Bandwith Gurantee/
- **Delay Gurantee**
  - Does not provide Delay Gurantee.

# Port Number

- Port number is the identifier used in transport layer.
  - Port number is nothing but an identifier of 16 bits(2 Byte).
  - There are 65535 unique identifier at transport layer.

# Multiplexing and Demultiplexing

## Connection Oriented

- in connection oriented one socket one process communicate with only one other process
- In other words connection must be established.
- There is also concept of threaded server.

## Demultiplexing

## Multiplexing

## ConnectionLess Demux

- In case of ConnectionLess there is no one to one relation. thus one process and socket can communicate with multiple processes on different Host

# TCP Socket Connection ORiented

- TCP is socket is identified by tuple of 4
  - Source IP Adress
  - Source port number
  - Dest IP Adress
  - Dest Port number
- Web server has different socket for each connecting clients. This is due to TCP Which requires a connection to be established first

---

## GEmini Explanation

Here are the complete details to flesh out your outline on Transport Layer Multiplexing and Demultiplexing.

### General Concepts

Before splitting into connection-oriented and connectionless protocols, the core definitions apply to both:

- **Multiplexing (Sender Side):** The process of gathering data chunks from different sockets (applications), adding the Transport Layer headers (which include the Source Port and Destination Port), and passing the resulting segments down to the Network Layer to be sent over a single network link.
- **Demultiplexing (Receiver Side):** The process of receiving segments from the Network Layer, examining the Transport Layer headers (specifically the Destination Port), and directing the data to the correct, matching socket so the right application receives it.

---

### Connection-Oriented Demultiplexing (TCP)

In TCP, reliability and strict state management are required. Because of this, the demultiplexing process is highly specific.

- **The 4-Tuple Identifier:** A TCP socket is uniquely identified by four pieces of information:
  1. Source IP Address
  2. Source Port Number
  3. Destination IP Address
  4. Destination Port Number
- **Strict One-to-One:** Because all four elements are checked, two packets arriving at the same Destination IP and Destination Port but from _different_ Source IPs will be routed to completely different sockets.
- **The Threaded Server Concept:** This is how heavy-duty web servers handle thousands of TCP connections simultaneously.
  - A server starts a **"Welcome Socket"** (e.g., listening on Port 80).
  - When Client A requests a connection, the server accepts it and instantly spawns a **new, dedicated socket** (and often a new thread or process) specifically tied to Client A's 4-tuple.
  - When Client B connects, the Welcome Socket spawns another completely separate socket/thread just for Client B. This prevents data from overlapping and allows the server to handle multiple clients in parallel.

---

### Connectionless Demultiplexing (UDP)

In UDP, there is no handshake, no connection state, and no guarantee of delivery. The demultiplexing process is lightweight and permissive.

- **The 2-Tuple Identifier:** A UDP socket is identified by only two pieces of information:
  1. Destination IP Address
  2. Destination Port Number
- **Many-to-One Relationship:** The receiving operating system does **not** check the Source IP or Source Port to determine where to route the packet. If a packet arrives addressed to Port 53, it goes into the socket bound to Port 53.
- **Handling Multiple Hosts:** Because of this 2-tuple routing, a single process with a single UDP socket can receive data from hundreds of different hosts simultaneously.
- **Application-Level Burden:** Because the socket accepts everything addressed to that port, the single process running the application must read the Source IP/Port attached to the incoming data chunk if it wants to know who sent the message or if it needs to send a reply.

---

## TCP Header Size

- TCP header size is 20 bytes plus, can add addition flags

# UDP

- Yaar slides se dekh lo
- SNMP(Simple network message protocols)
- There are four elements in udp header.
- IN UDP Demultiplexing is done using **Only** The destination port number
- UDP Header has size of 4 bytes.
- Each socket also has a life
