Subnet Mask:
- Subnetting: Taking a network and dividing it into sub-networks.
- An IP Address consists of two parts: Network address and host address.
- Every network has a unique address.
- To tell which portion of the IP address is network or host -> subnet mask.
- A subnet mask reveals how many bits in the IP address are used for the network by masking the network portion of the IP address.
- Subnet mask's binary digit is 1 -> Network portion.
Ex:
192.168.1.0--->(11000000.10101000.00000001).00000000
255.255.255.0->(11111111.11111111.11111111).00000000
-> First 3 octets: Network portion. Last one: Host portion
255.255.0.0-> First 2 octets: Network portion. Last 2: Host portion
255.255.224.0->11111111.11111111.11100000.00000000
-> First 2 oclets and next 3 bits for network portion. Last 13 bits for host portion.
- IP addresses have a network and a host part so networks can be logically broken down into smaller networks -> subnetting (remember ARP protocol from day 4)
- Subnetting is done by changing the default subnet mask by borrowing some of the bits from the host portion.
- If we leave the subnet mask the way it is, it will give us 1 network with (256-2=254) hosts (All 1's and 0's are reserved for broadcast and network address respectively).
- If we borrow the first bit -> 255.255.255.128 -> 2 sub-networks with (256/2 - 2 = 126) hosts.
- (first two bits): 255.255.255.192 -> 4 sub-networks with 62 hosts.
- (first 3 bits): 255.255.255.224 -> 8 sub-networks with 30 hosts.
- 4 bits: 255.255.255.240 -> 16 sub-networks with 14 hosts.
- 5 bits: 255.255.255.248 -> 32 sub-networks with 6 hosts.
- 6 bits: 255.255.255.252 -> 64 sub-networks with 2 hosts (limit).
- Ex: Divide into 3 networks -> Borrow 2 bits
- Class A: Private IP starts with 10.
+ IP address range: 10.0.0.0 - 10.255.255.255
+ First octet address: 1-126
+ Default subnet mask: 255.0.0.0
+ Can provide up to 16 million hosts.
- Class B: Starts with 172
+ IP address range: 172.16.0.0-172.31.255.255
+ First octet address: 128-191
+ Default subnet mask: 255.255.0.0
+ Can provide up to 65000 hosts.
- Class C: Starts with 192
+ IP address range: 192.168.0.0-192.168.255.255
+ First octet address: 192-223
+ Default subnet mask: 255.255.255.0
+ Can provide up to 254 hosts.
- CIDR (slash notation): "/" + number of 1's in the subnet mask
Ex: 192.168.1.0 /24 -> Subnet mask: 255.255.255.0
/25 -> 255.255.255.128
/26 -> 255.255.255.192
/8 -> 255.0.0.0
-> /24 can be divided into 2 /25. Can also be divided into 1 /25, 1 /26, 2 /27.
- Network ID: First IP address in each sub-net
- Broadcast IP: Last IP address in each sub-net
- First Host IP: IP address after the Network ID
- Last Host IP: IP address before the Broadcast IP
- Next Network: Network ID of the next Sub-net.
- Number of IP addresses.
- CIDR/Subnet converting

Public vs Private Address:
Public IP addresses:
- Publicly registered. What gives access to the Internet. 
- Unique.
- Used externally.
- Assigned by an Internet service provider (ISP).
- Not free.
- Traceable (not secure).
- When IP addresses were first created, engineers didn't realize how big the Internet would become. Over 4 billion IPv4 addresses available
-> Private IP address.
- Not publicly registered on the Internet.
- Not unique. Can be used on other private networks.
- Used internally.
- DHCP is a service used in routers to assign Private IP.
- Private IP must be converted into Public IP to access the Internet. This is because Private IP addresses are only used internally.
- NAT is what translates a set of IP addresses to another set of IP addresses (Private->Public and Public->Private).
- More secure (used internally).
- Class A, B, C