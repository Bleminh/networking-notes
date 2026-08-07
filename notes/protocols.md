# Protocols
* Protocols: Set of rules and messages that defines how two hosts communicate.
* ARP: Resolves IP to MAC mappings.
* FTP: File Transfer Protocol
- Request : RETR (retrieve) file.pdf
- Response: file.pdf
* SMTP: Simple Mail Transfer Protocol
- Request: HELO client.com
- Response: 250 email.com
* HTTP: Hyper Text Transfer Protocol
- Use when communicating with web server
- Web servers host many websites written in HTML
- Request: GET /index.html
```
GET / HTTP/1.1
Host: example.com
```
- Response: 200 OK
```
HTTP/1.1 200 OK
Content-Type: text/html (info needed to render)
```
- GET: Read
- POST: Create new resources
- PUT: Edit an existing resource
- DELETE: Delete an existing resource
* SSL: Secure Sockets Layer (depreciated)
* TLS: Transport Layer Security (used today)
- Both allow the hosts to build a secure tunnel between themselves.
* HTTPS: HTTP secured with SSL/TLS
* Every host needs 4 items for Internet Connectivity:
- IP address.
- Subnet mask (size of host's network. The first 2 will allow for connection within the same network)
- Default Gateway (Router's IP address)
- DNS Server IP
* DHCP: Dynamic Host Configuration Protocol
- DHCP Server provides IP, subnet mask, default gateway, DNS for clients.