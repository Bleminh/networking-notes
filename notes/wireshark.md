# Wireshark
## 9/8/2026
* Finally seeing how data actually moves
* Saw these actual stuff:
- Frame / Ethernet (Layer 2 - MAC address)
- Internet Protocol (Layer 3 - IP addresses)
- TCP/UDP (Layer 4 - also have port numbers)
* The data actually moves very quick and hectically
* I also noticed a lot of different protocols beside stuff like TCP, UDP, or DNS
## 10/8/2026
**Wireshark Display Filters** are search queries used to hide all background network noise and only show specific packets (like typing `dns` to only see domain requests).
By inspecting the packet layers in Wireshark, I observed the following:
* **Transport Protocol:** DNS uses **UDP**. This makes sense because DNS needs to be incredibly fast. A full TCP handshake would slow down web browsing.
* **Destination Port:** The request was sent to **Port 53**, which is the universal standard port for DNS servers.
* **The Resolution:** The DNS server responded to my query and resolved `hust.edu.vn` to the IP address **202.191.59.13**.
## 11/8/2026
* I used Wireshark with the display filter `tcp.port == 80` and ran `curl http://neverssl.com` in my terminal.
**Observations:**
1. **The 3-Way Handshake:** Before the website downloaded, I saw the exact three packets that establish the connection:
   - `[SYN]`
   - `[SYN, ACK]`
   - `[ACK]`
2. **The 4-Way Teardown:** After the website downloaded, the connection didn't just drop. It closed gracefully using `[FIN]` (Finish) and `[ACK]` packets from both sides.
3. **The Ghost Bytes:** Even though the handshake sends 0 actual payload bytes, the Sequence (Seq) and Acknowledgement (Ack) numbers jump by exactly 1. TCP treats `SYN` and `FIN` flags as if they take up 1 byte of space to keep the math synced!
This is actual identical to what I've learned so far.
## 11/8/2026: TLS Handshake
* As a reminder, TLS is the protocol that wraps regular HTTP trafic in encryption, creating HTTPS.
* How did I test it?
1. Set Wireshark to filter HTTPS traffic: `tcp.port == 443`
2. Triggered a secure connection in the terminal: `curl https://github.com
* Key Observations:
1. The connection still starts with the standard TCP 3-way handshake.
2. The TLS 1.3 Handshake:
+ **Client Hello:** My machine initiated the TLS handshake proposing TLS 1.3 and a list of encryption methods.
* **Server Hello:** GitHub responded and selected the cipher suite. 
* **Cipher Suite Chosen:** `TLS_CHACHA20_POLY1305_SHA256` (ChaCha20 for fast encryption, Poly1305 for integrity, SHA256 for key exchange).
3. **The Missing Certificate:** Unlike older versions of TLS, TLS 1.3 encrypts the server's certificate immediately after the `Server Hello` (labeled as `Change Cipher Spec`).
4. **The Black Box:** After the handshake, Wireshark can no longer read the HTTP requests or HTML. It just shows raw `TCP` packets bouncing between port 443 and my ephemeral port (58989).
5. **TCP Segmentation:** I observed multiple packets with an identical length of `1466`. This is because the encrypted web data is larger than the network's Maximum Transmission Unit (MTU), so TCP chops it into maximum-sized, efficient segments for transport.