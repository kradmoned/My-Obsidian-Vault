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

# Authentication vs AuthorizationIslamabad

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
  - We check for parity both in rows and columns
  - The last row contains the parity bit of a specific columns
  - A question since the last row is for column partiy what does its row parity bit show, or last bit column parity or row partiy
- Check Sum
  -Check sum is noting but addition and wrap around(It is simply the most significant carry added to result)?
  - First step is simply binary addition
  - The other is a wrap around of the carry?
  - Checksum is commonly used in transport layer integrity
- Cyclic Redundancy Check (CRC)
  -It is commonly used in layer 2 data link layer.
  - IT is used for error Detection
  - It has two things crc checker , crc generator and works on the principle of binary Division
  - [CRC Onlince reading](https://www.sunshine2k.de/articles/coding/crc/understanding_crc.html)
  - Calculate CRC of data - 100100 with divisor 1101

# Error Detection vs Error Correction

- Error Corrections
  - It is computationaly cost and time inefective
  - What algorithms exists for error corrections?

---

# Check SUm from geeks for geeks

Here is the content you provided, preserved as requested and organized into a clean Markdown format.
A **Checksum** is an error detection method used by upper-layer protocols. It is considered to be more reliable than Longitudinal Redundancy Check (LRC), Vertical Redundancy Check (VRC), and Cyclic Redundancy Check (CRC).

- **Sender Side:** This method uses a **Checksum Generator**.
- **Receiver Side:** A **Checksum Checker** is used.
- **Integrity Verification:** The checksum is a unique number generated from the data to verify its integrity. If the two checksums match, the data is likely error-free.

---

## How Checksum Works?

Checksum works by summing all data segments using **1’s complement arithmetic**, taking the complement of the result, appending it to the data, and verifying at the receiver by checking if the final complemented sum (including checksum) equals zero.

### Sender Side

- **Data Division:** The data is divided into equal-sized subunits of bits (commonly 16 bits).
- **Addition Using 1’s Complement:** All the subunits are added together using 1’s complement arithmetic. If a carry is generated beyond the most significant bit, it is wrapped around and added to the least significant bit.
- **Checksum Calculation:** The final sum is then complemented (1’s complement). This result is known as the checksum.
- **Transmission:** The original data along with the checksum is transmitted to the receiver as a single unit.

### Receiver Side

- **Receiving Data and Checksum:** The receiver gets the combined block of original data and checksum.
- **Data Division:** The received block is divided into subunits of bits, same as at the sender side.
- **Addition Using 1’s Complement:** All subunits, including the checksum, are added together using 1’s complement addition with end-around carry.
- **Final Complement and Validation:** The result of the sum is complemented. If the final result is all zeros, the data is considered to be error-free.
- **Error Detection:** If the result is non-zero, it indicates that an error has occurred during transmission, and the receiver rejects the data.

---

## Factors for Inconsistent Checksum Number

Whenever checksum values don't match, it seems that some disturbance happened in the data during transmission. Several factors which can create disturbance are mentioned below:

- **Interruption in the network connection** can create inconsistent checksum numbers.
- **Issue in the storage space or hard drives** can also lead to problems in checksum.
- **Corrupted Disk and Corrupted File** can lead to errors in Checksum.
- **Third-party interference** while transferring the data can also lead to checksum errors.

--

# Self Assessment and - task

- How torrents work?
- Data Chunkls?
- Peers?
- Seeders?
- Leechers?
- Download vs upload
- PirateBay
