25/07/2026
TCP:
- Sequence Numbers: track what is sent
- Acknowledgement Numbers: track what is received
- They measure bytes, not packages.
- TCP caches everything sent for duration of "Retransmission Timeout"
- If no ACK is received, segment is resent.
- Initially, TCP send an ACK after every received segment -> double the amount of packages is put on the wire.
- Delayed Acknowledgements - send acknowledgement every other segment.
- Acknowledgements are cumulative.
- Window Size limits how much unacknowledgement data can be sent.
- Window Size sent in each segment.
- Can be dynamically updated through connection (Flow Control).
- TCP is bidirectional - both peers can send data.
- Both have a SEQ number and an ACK number.
- Initial Sequence Numbers (ISN) are randomly chosen by sender.
- Must be shared at connection established (3-way handshake).
- TCP Connection starts with 3-way handshake; including 4 events:
+ A->B: SYNchronize ISN = X
+ B->A: Received, acknowledge that ready for [X+1]
+ B->A: SYNchronize ISN = Y
+ A->B: Received, acknowledge that ready for [Y+1]
-> 3-way handshake: SYN, SYN-ACK, ACK
- Graceful connection closing: Four-way closure with FIN flags:
+ A->B: FINished, Sequence number = X
+ A<-B: ACKnowledged, Acknowledgement number = [X+1]
+ A<-B: FINished, Sequence number = Y
+ A->B: ACKnowledged, Acknowledgement number = [Y+1]
- Ungraceful conncection closing: One-way with RST flags:
+ A<->B Something went wrong, send a RESET flag.
+ RST is unacknowledged, can be sent by either party.
UDP: Ideal for
- Applications with small requests and responses. Ex: DNS. UDP ~ 2 packets. IDP ~ 11 packets. TCP's additional overhead is unnecessary.
- Applications with built-in Delivery Confirmation System.
- Applications that involve live or streamed content.

Everything Hosts do to speak on the Internet:
DNS converts Domain Name -> IP Address.
Scenario 1: Host A and B are directly connected within a network.
- Both have a MAC address, an IP address and a Subnet Mask
- Host A knows the IP address of Host B (ping, DNS,...)
- Host A can create the L3 (end-to-end) header to attach the Data.
- Host A doesn't know Host B's MAC address -> must use Address Resolution Protocol (ARP) to link a L3 address to a L2 address.
- ARP Request asks for the MAC Address associated with target IP. It also includes sender's MAC and ip addresses.
- ARP Request is a Broadcast - sent to everyone on the network. Destination MAC address: ffff.ffff.ffff
- ARP Mappings are stored in an ARP Cache. Everything that has an IP Address has an ARP.Cache.
- Host B responds by sending an ARP Response. Response is sent Unicast (directly to Host A).
- Host A populates its' ARP cache with Host B's IP/MAC mapping.
Scenario 2: Hosts are connected through a router (foreign network).
- Host A uses ARP to resolve the MAC address of the Router's IP.
- Router IP address is already configured as the Default Gateway.
- Data is sent to the Router. Router takes over the job.
- ARP mapping can be used for any host from a foreign network.
Host A's first step when sending data is always the same:
- Determine if target IP is on local or foreign network
+ Foreign: ARP for Default Gateway IP (Router)
+ Local: ARP for Target IP