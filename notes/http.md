HTTP:
- Continents are connected via physical cables that lie on the bottom of the ocean floor.
- Fiber optic cables made of glass fibers.
- Hyper Text Transfer Protocol.
- Servers always respond with status code. Three-digit numbers.
- 1xx: Info
- 2xx: Success (200 Success)
- 3xx: Redirection
- 4xx: Client Error (404 Page Not Found)
- 5xx: Server Error
- HTTP Requests go through a header. 3 parts:
+ Start Line: starts with a method, usually either GET or POST. Next is target - which file I'm trying to locate. Third parameter is HTTP version (Method - Target - Version).
+ Headers: Additional info about the request.
+ Body: Typically nothing for request. What servers use to send back the files that are requested.
- HTTP Response:
+ Start Line: Version - Status Code (1xx-5xx) - Status Text
+ Headers
+ Body: The actual content being transfered - raw HTML, image data, or JSON.
- HTTP 1.0 is stateless (After the response is sent back, the connection is broken)
- Based on TCP/IP
- 3 parts to the request/response message

```
curl -I https://github.com
```

HTTP/2 200 (status - success)
content-type: text/html (tells the client how to interpret the response)
server: github.com (the web server GitHub uses)

```
curl -I https://github.com/something-random-for-error
```
HTTP/2 404 -> Error

```
curl -v https://example.com
```
-v verbose mode
``` IPv4: 104.20.23.154, 172.66.147.243
*   Trying 104.20.23.154:443...
* Connected to example.com (104.20.23.154) port 443 ```
DNS: example.com->IPv4
TCP connection establised

> GET / HTTP/2
> Host: example.com
> User-Agent: curl/8.7.1
> Accept: */*
>
* Request completely sent off

-> client request

< HTTP/2 200
< date: Wed, 29 Jul 2026 20:29:59 GMT
< content-type: text/html
< server: cloudflare
< last-modified: Tue, 21 Jul 2026 07:16:00 GMT
< allow: GET, HEAD
< accept-ranges: bytes
< age: 9398
< cf-cache-status: HIT
< cf-ray: a22ee0fcda026e4f-HKG
<
<!doctype html><html lang="en"><head><title>Example Domain</title><link rel="icon" href="data:,"><meta name="viewport" content="width=device-width, initial-scale=1"><style>body{background:#eee;width:60vw;margin:15vh auto;font-family:system-ui,sans-serif}h1{font-size:1.5em}div{opacity:0.8}a:link,a:visited{color:#348}</style></head><body><div><h1>Example Domain</h1><p>This domain is for use in documentation examples without needing permission. Avoid use in operations.</p><p><a href="https://iana.org/domains/example">Learn more</a></p></div></body></html>
* Connection #0 to host example.com left intact

Server response