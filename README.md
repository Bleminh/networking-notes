# networking-notes

Technical notes tracking my understanding of network engineering, protocols, and the architecture of the Internet. Simple visualization of the concepts learned.

## 🧠 Core Mental Models
*A selection of my hand-drawn network diagrams.*

![OSI Model](./drawings/OSI_Model.png)

![TCP Model](./drawings/TCP_Model.png)

> **Note:** Additional diagrams including the `TLS_Handshake`, `Layer1-2-3` interactions, and hardware components (`Routers`, `Switch`) can be found in the `/drawings` directory.

---

## 📚 Topic Index

### 1. Architecture & The Big Picture
* [The OSI Model](./osi_model.md)
* [The Flow: From DNS to Page Render](./the_flow.md)
* [Network Devices (Routers, Switches, etc.)](./network_devices.md)
* [Subnetting Basics](./subnetting.md)

### 2. Transport & Network Layers (TCP/IP)
* [TCP vs. UDP](./tcp_udp.md)
* [Public vs. Private IP Addresses](./public_private.md)
* [Ports & Sockets](./ports.md)
* [TCP & ARP Interactions](./tcp_arp.md)

### 3. Application Layer & Security
* [DNS (Domain Name System)](./dns.md)
* [HTTP / HTTPS](./http.md)
* [TLS & Encryption](./tls.md)
* [General Application Protocols](./protocols.md)

### 4. Packet Analysis
* [Wireshark Observations](./wireshark.md)