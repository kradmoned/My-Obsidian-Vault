# TCP Header

-

# Cumulative Acknowledgement

- In cumulative Acknowledgement if the previous acknowledgement is lost, it does not matter given that the next acknowledgement is succesfully recieved.
  - for example if ack 100 is not recieved but ack 120 is recieved , the sender will automaticallly consider it as acknowledgement of the last 20 bytes of data.

---

Is slide 52 gbn or go back

# Fast Retransmit

- > [!NOTE] Acknowldegment loss vs packet lost
  > There is a difference between a packet lost and acknowledgement lost
  > in Acknowldegment lost only the sender is unaware that the segment is succesfully recieved
  > In packet lost a packet is never recieved at recievers end.
