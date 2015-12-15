## Hypertext Transfer Protocol (HTTP)
##### Question : How to filter http get or post requests?
```bash
$ tshark -i "eth0" -Y 'http.request.method=="GET" ||
    http.request.method=="POST"'
```

###### REFERENCE:

* [W3C - HTTP Method Definitions]
(http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html)
