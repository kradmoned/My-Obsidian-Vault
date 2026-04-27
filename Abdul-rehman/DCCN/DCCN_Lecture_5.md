05/03/2026

- Just came to class dont know whats happeningm i think we are doing revision
- No Need to software for network core devices
  - These means routers.
  - Firmwares
- in p2p no servers are involved.
  - Self Scalability
- IN client server, server listens, client requests/Establish connection

# Sockets

- Socket is binded to ip adress and port

- ## It is between application layer and transport layer

- Application programs uses socket to forward data/ messages into the transport layer,
- All communication passes through the socket.
- Every process/ application running will have its own port number. THe process itself has port number. For example the webservice process will do communication through prot 80.
- In case of two services running such as email and web, then we will have two proceses.
- Thus each process will have other different sockets.

---

- tHERE ARE two types of protocol, open(Https and smtp.) and propriertary.they mean they are not proprierty.
- What are RFC.
  - This stands for request for comments.
  - This is documentt containingn documentaion for all open protocols.

- ## Application layer is running on top of transport layer

- Some applications require data integrity, meaning they require 100% reliable file transfer. This is done by transport layer but is a requirement of some apps in application layer.
- Timing in application means some application require low delay to be effective
- Some apps require minimum ammount of throuput to be effective.
- Other apps make use of whatever throuput they get.
- Some apps require encryption.
- TCP Requires 3 way handshake.
