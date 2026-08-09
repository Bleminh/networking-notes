# Port
* Logical connection used to exchange info
* Determines which program or service that is going to be used
* Have a unique number that identifies them (0-65535)
* 80: HTTP
* 443: HTTPS
* 21: FTP (File transfer protocol)
* 25: Email (SMTP)
* 22: SSH (Remote terminal access)
* 53: DNS
* Always associated with an IP address
* IP address is used to determine the geographical location
* Port number determines which serevice or program on that server is used
* 0-1023: System/Well-known ports
* 1024-49151: User/registered ports
* 49152-65535: Dynamic/private ports. Computer assigns temporarily to itself during a session
* First two are used on servers. Last one used on clients