
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
