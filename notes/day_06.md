DNS:
Domain name system
- Resolves domain names to IP addresses.
- If web browser or OS can't find the IP address in its own cache memory, it will send the query to the next level (resolver server - usually ISP).
- ISP will check its own cache memory. If can't find, send the query to next level (root server).
- DNS hierarchy: 3 main evels
+ Root servers
+ TLD (top level domain) servers
+ Authoritative name servers
- Root server is the top of DNS hierarchy.
+ 13 sets of these roots servers strategically place around the world.
+ Operated by 12 different organizations.
+ Each set has their own IP address.
+ The root server doesn't know the IP address is, but it knows where to send the resolver to help it find the IP address.
- The root server will direct the resolver to the TLD (top level domain) server.
- The resolver will now ask the TLD server.
- TLD server stores the address info for top level domains such as .com, .net, .org,...
- TLD direct the resolver to the Authoritative Name server.
- Authoritative Name server is resposible for knowing everything about the domain, inclduing the IP address.
- Once the resolver receives the IP address, it stores in its cache memory for potential future usage.
DNS Records:
- In a DNS database, you have a zone file. This contains the DNS records.
- A record:
+ Resolves domain names to IP addresses (IPv4)
+ TTL (time to live) tells how long each record is valid until the next update.
- AAAA record:
+ Resolves domain names to IP addresses (IPv6)
- CNAME record:
+ The CNAME (canonical) record resolves a domain or subdomain to another domain name.
+ Ex: www.example.com -> example.com (alias)
- Computers read domain names from right to left
+ Subdomains are also often used when a website has different services running on the same server and are using the same IP address.
- MX record:
+ MX (mail exchanger) record is used for email.
+ Points to the server where emails should be delivered for that domain.
+ Generally has 2 entries, along with priority numbers. The lower the number -> primary.
- SOA record:
+ SOA (start of authority) record stores administrative info about a DNS zone.
+ A DNS zone is a section of a domain name space that a certain admin has been delegated control over.
- NS record:
+ NS (name server) provides the name of the authoritative name server within a domain.
+ Generally 2 name servers. Primary and secondary
- SRV record: SRV (service) record points to a server and a service by including a port number.
- PTR record: PTR (pointer) record.
+ Reversed of A or AAAA record -> Resolves IP addresses -> domain names.
+ Attached to emails. Used to prevent email spam.
- TXT record: contains miscellaneous info about a domain. Also used to prevent email spam.

```
dig google.com

; <<>> DiG 9.10.6 <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 19091
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		16	IN	A	142.250.197.110

;; Query time: 11 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Tue Jul 28 21:08:10 +07 2026
;; MSG SIZE  rcvd: 55
```

IP address: 142.250.197.110
Record type: Type A
TTL: 16