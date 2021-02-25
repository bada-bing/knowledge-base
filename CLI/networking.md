
# wget
- `wget <url>` - download a web page and read the downloaded page as a local file using a graphical or non-graphical browser.
- `wget` handles the following types of downloads:
* retrieve **files** using HTTP, HTTPS, FTP, FTPS
* Large file downloads
* Recursive downloads, where a web page refers to other web pages and all are downloaded at once
* Password-required downloads
* Multiple file downloads.

# curl
* `curl` can be used from the command line or a script to make requests. curl also allows you to save the contents of a web page to a file, as does wget.
* You can read a URL using `curl <URL>`. (`curl http://www.linuxfoundation.org`)
* Store the contents of a web page (the main index file) to a (saved.html) file `curl -o saved.html http://www.mysite.com`.
- ⭐ https://catonmat.net/cookbooks/curl
- ⭐ test this really good alternative: https://httpie.org/

# netstat
- https://www.howtogeek.com/513003/how-to-use-netstat-on-linux/
- nmap - port scanner
  - https://www.techrepublic.com/article/how-to-listen-to-port-traffic-on-a-linux-server/
- ping vs traceroute (traceroute gives the number and more details about hops to certain IP address)
- `ping -c 5 -n 8.8.8.8`
  - -c 5 - only send 5 packages
  - -n do not transform ip addresses into host names
  - 8.8.8.8. googles DNS


- Packets are essentially base unit of information that everybody in the network know how to use (knows how to communicate with)
- Nginx is read as (engine-x) is a more than just  http server (a load balancer or UI gateway)
- Opposite of Cloud Service (SAAS) is on-premise software (installed at user's place)
- DNS Records - A record - map name to ip adress or CNAME (map name to another name)
- you can check it using dig command
- certificate authority - entity that issues Digital Certificates

What is the difference between subdomains and paths
- e.g., www.milan.com/blog vs www.blog.milan.com
- more or less it should be something like semantical difference
- to emphasize that subdomain represents different app in the ecosystem… something like that, but google that more

# Web Protocols
In general, use WebSockets whenever you need a truly low-latency, near realtime connection between the client and the server.
If your use case requires displaying real-time market news, market data, chat applications, etc., relying on HTTP/2 + SSE will provide you with an efficient bidirectional communication channel while reaping the benefits from staying in the HTTP world:

HTTPS
TCP - it is called error correcting
	- it uses checksums to ensure that it collects data from all packets
	- if necessary it knows which packets which were lost and should be sent again
SMTP - (Simple Mail) resembles HTTP
	- it also have status codes, body
WebRTC - peer to peer

HTTP 1.1 vs 2
HTTP /2
	- HTTP/2 is about improving the efficiency of the way data is transferred on the wire.
	- SSE (Server-Sent Events)

Cookies
First-party cookies - store your preferences for a particular site
Third-party (cross-site tracking) cookies - follow your online activity across sites

fingerprinting - a certain form of tracking that uses data about your system configuration to identify you
