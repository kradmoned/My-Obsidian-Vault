# DCCN Lecture 2

Secuirty

# CIA

C -> **Confidentiality** -> the message should only be read by intended party. It also uses techniques for encryption of data so it cant be red by others
I -> **Integrity** -> Integrity is the message should not be altered. Prevent intentional or distortion
A -> **Availability** -> Whenever you need a resource that resource is available to you. Example when you open facebook, it is not opening. MAybe the server is down then we will have backup servers. _DOS_ It stands as denial of service attacks. In it fake/bogus are sent to the website. The website thinks these requests are legit. When the website reply to these bogus requests , the serer gets busy and cant help the genuine user

# **Client Server Architecture**

- There is one central server adressing multiple request by the different clients.
- In client server file sharig can be done by means of central server sharing data
- Servers can be of multiple types such as Webserver, FTP Server, Mail Server.

# **Peer to Peer Architecture**

- That there is no central server or clients The individual both share and send the data. The indiviual is known as peers.
- Torrents are example of peer to peer.
- There is no single point of failure
- No bandwidth bottleneck
- The greater the number of peers, the lesser the chance of bottleneck.
- A file is divided into multiple chunks, In peer to peer, All chunks should be available for successful transfer.

# Trackers

- Trackers are list of peers along with their chunks.
- It is a single document that says x has chunk 93 of movie
-

# PirateBay

- Famous torrenting website. IT was basically a tracking repository. PirateBay servers were tried to take down by its authority.

# What can bad guy do?

- Eavesdrop
  - Sniffing no alterration is done you just quietly listen
- Impersonation
  - Can spoof(Impersonation of source address by changing it), just see the slides.
- Hijacking
  ?
- Denial of Service

# Source Address vs destination Address

- SRC/Source is the one sending the messages
- destination is the one receiving meesages

# Packet Crafting / message crafting. Payload crafting

- A new packet is crafted with false source Address

# Authentication vs Authorization

- Authentication is basically the validation of credentials/
- Authorization is basically what level of accessibility you have.

# Data At rest, Data in transit and Data in motion

- **Data at rest** -> is the data which you have access to
- **Data in motion** -> Data is moving, Something is being downloaded or being uploaded.
  - It is hadled through computer networks
- **Data in Transit** -> what is this? Do your own research

# Defense in Depth

- Secuirty is done in layers.

- | Layer   | NAme                                                                                                      |
  | ------- | --------------------------------------------------------------------------------------------------------- |
  | LAyer 1 | Physical Layer -> Surveilance , people etc doors                                                          |
  | Layer 2 | Software Secuirty -> Credentials , Operating system, Hostbased, Passwords etc basically you need to login |
  | LAyer 3 | Enctypted data``                                                                                          |
  There are more just see the slides

# Language of Cryptography

- To acheive Confidentiality encryption is done. Cryptography is done for encryption it has two types symmetric and asymetric.
- In symmetric encryption one key is used for both encryption and decryption.
  - AES and DES``
- Assymetric is also called public key cryptography, It is acieved through public and private key.
  - Example algorith RSA

# Types of Error Detection

- Parity Check
  - There is a parity check bit which is usually the last or least significant bit
  - We are counting Numbers of ones
    - Even Parity Check and ODD parity Check
- Two Dimensional Parity Check
- Check Sum
- Cyclic Redundancy Check (CRC)

# Self Assessment and - task

- How torrents work?
- Data Chunkls?
- Peers?
- Seeders?
- Leechers?
- Download vs upload
- PirateBay
