OSI Model:
- Goal of networking: Allow two hosts to share data.
- Layer 1: Physical - Transporting Bits
+ Goal: Converts bits into physical signals (voltage, light flashes, RF) and send them.
+ Doesn't care about: Sender, receiver, where does a message starts and ends.
-> Crucial limitations: L1 has no concept of boundaries (since it doesn't care about the start and end point). L1 just sends a continuous stream of electricity.
+ Example: Cables, Wi-Fi, Hubs, Repeaters
- Layer 2: Data Link
+ Goal: Take the continuous stream of raw bits from L1, chop it into chunks (called Frames), and add MAC addresses so local device know who is talking to whom.
+ Addressing Scheme - MAC addresses. Every NIC has a unique address (48 bits, represented as 12 hex index).
+ Knows where a message starts and ends.
+ If destination addresses matches MAC address, keep. Else, drop.
+ L2 has a math check (CRC) at the end of the frame -> Corrputed, catches and throws away.
+ Hop to Hop: Take the bits (1's and 0's) from one NIC to another.
+ Ex: NIC (Network Interface Cards), Wi-Fi Access Cards
+ Communication oftern requires multiple hops.
- Layer 3: Network - End to End
+ Addressing Scheme - IP addresses (32 bits, represented as 4 octes from 0 to 255).
+ Routers, Hosts, anything with an IP.
- Distinction between L3 and L2:
+ L2: MAC address: Hard-coded into a host, won't change no matter the physical location (where it is).
+ L3: IP address: change within different networks.
+ L3 is like the starting point and final destination (e.g. from Hanoi to Manchester) -> IP address stays the same from start to finish. Long distances between different networks. L2: Hop to Hop (e.g. Hanoi to Tokyo: hop 1...) -> MAC addresses change at every hop.
- ARP - Address Resolution Protocol. Links L3 with L2.
- Layer 4: Transport - Service to Service
+ Distinguish data streams - make sure the right data goes to the right program/service (e.g. Games, chat,...).
+ Every program on the wire is associated with a port number.
+ Addressing Scheme: Ports.
- TCP: 0-65535. Favours reliability.
- UDP: 0-65535. Favours efficiency.
+ Servers listen to requests to pre-defined Ports.
+ Clients select random Port for each connection.