DCCN_Lecture_4
10/02/2026

# Public IP vs Private IP

- Public Ip is known to the world , and is used for internet.
- Private IP is the IP used for local internet, it is used in local internet, or LAN.
  - Private IP are never used as public IP as there will be conflict of IP.
  - Example Include private ip given to students in PIEAS starts from 10.something and comesat may also start from the same.

# NAT (Network Address Translation)

# Subnet Mask

- It is an IP which is to identify the network part/ network bits of any given network.
- The Value of bit is set to 1. If the corresponding bit of ip address is network bit.
- What will be the subnet mask of 192.168.100.7/24 ?

# Subnetting

- Subnetting is the process of splitting a network into further subnetworks
- Why?
  - For Easy troubleshooting
  - For network segmentation
  - To form a subnet bits will be borrowed from the hostpart. Those borrowed bits will be called subnet bits.
  - Devide 192.168.100.0/24 to two subnets
    - 192.168.100.b1b2b3b4b5b6b7b8 for 2 subnets one will be zeros and one will be ones, or one borrowed bit from host for more subnets or
    - To divide into two subnets we will borrow b1 from host, and now network part will become 25 bits and our cider value is /25 i
    - What if we need 3 subnets instead of subnets in power of 2

# segmentation vs segregatiom
