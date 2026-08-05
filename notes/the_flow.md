# What happens when you type google.com?

This is a step-by-step breakdown of how data moves from my computer to a server, based on my Week 1 networking knowledge.

## 1. DNS Resolution (Finding the IP)
Before my computer can connect to Google, it needs the IP address.
* The OS and browser first check their local cache memory.
* If it's not there, the request goes to the Resolver Server (usually the ISP).
* The ISP asks the Root Servers. They don't know the IP, but they guide the resolver to the TLD (.com) server.
* The TLD server points to Google's Authoritative Name Server, which finally returns the correct IP address.

## 2. Local Routing & ARP (Layer 2 & 3)
Because my computer and Google's server are not on the same local network, my computer needs to send the packet to my router (the default gateway).
* It uses the ARP protocol to find the router's MAC address.
* It sends a broadcast request to the router, and the router takes over the job of passing the packet along the internet.

## 3. The TCP 3-Way Handshake (Layer 4)
Once the IP is found and the packet is routed, the two machines establish a reliable, service-to-service connection using TCP.
* **SYN:** My computer sends a SYNchronize request (Sequence X).
* **SYN-ACK:** The server acknowledges it is ready for X+1 and sends its own SYNchronize request (Sequence Y).
* **ACK:** My computer sends an ACKnowledgement for Y+1. 
*(Note: When the connection eventually closes, it uses a similar FIN/ACK process: FIN(X), ACK(X+1), FIN(Y), ACK(Y+1)).*

## 4. Transport and Decapsulation (L1 to L3)
* **Layer 1:** The data is physically transported across the internet as bits (via fiber optic cables, etc.).
* **Decapsulation:** When the packet arrives at the server, the server checks the L2 (MAC) and L3 (IP) tags. If the IP address is correct, it removes the L3 tag. Then it checks and removes the L2 tag. What is left is the actual data payload.

## 5. The Application Layer (Current knowledge gap)
Once the TCP connection is established, an HTTP request is sent through that pipe. The server responds with raw HTML. Right now, my knowledge on how the browser actually parses that HTML, builds the DOM, and renders the visual webpage is lacking.