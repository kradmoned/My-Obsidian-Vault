13/04/2026

# FSM

- Stands for Finite Stake Machine.
- It has 2 major think state and transition
- See my excalidraw

# Reliable data transfer

# RDT 1.0

# RDT 2.0

## RDT 2.0 FLAW

- ACK and NAK may get corrupted.
- Sender Adds sequence number to each packet
- Reciever discards DOesnt deliver up) duplicate pkt
- **_STOP AND WAIT_**
  - SEnder does not send another packet till it gets a response from reciever.

# RDT 2.1

- rdt rcv packet that is not corrup and has sequence 1.
  - When will this scenario occur.
- Why is sequence number added?
  - 1. Sender Creates packet of sequence 0
    2. It is succesfully recieved.
    3. Reciver sends acknowledgment
    4. Moves to next packet.
    5. Recives packet checks it sequence number realizes the sender has sent the prev packet again
    6. This means the acknowledgment sent in step 3 got corrupted
    7. Reciever sents the previios acknowledgment again.

# What if you want to eliminate the negative acknowledgment

# TIll now we can send only one packet at a time

# What if we want to send multippe segments at once

# Will there be any underutilized link/bandwith

# There are two approaches to pipelining/ sending packets simultaneious

- The first is go back in (gbN)
- The second one is selective repeat

# RDT 3.0

- What if in the case of packet loss
- When will delayed packet and delayed ACK occur
  - Will there be any systematic issue in this
  - Stuck in loop

# How is performance evaluated

- RTT time starts when the whole packet including the last bit is out of package
- Pakcet size is 800 rtt is 30 mili sec bandwith is 1 Gb we have to make utilization 25% how many packet sjould be sent in the pipeline to achieve the utilization of sender 0.25

# GBN

- Go back n is a protocol used for pipleining.
- THere will be a senders window
- If window size is 4 we can send 4 packet at once
- **If a packet is recieved out of order then it will be discared, and acknowledgement of last sucksexfuly received packet will be sent again.**
- **The sender will ignore any duplicate acknowledgment and will wait for timeouts**
- It will not consider any packet untill and unless an expected packet is released

# Selective repeat

- If a packet is recieved out of order it will be stored in a **buffer**
- Both sender and reciever have windowns
- The sequence number / sequence window is agreed upon at the time of connection
- What should be the optimal sequence number and window size ratio
  - THe sequence number should be double the size of window
- Sequence is only for identification, it has nothing to do with the content of the packet,
