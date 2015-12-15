## Transport Layer Security (TLS)/ Secure Socket Layer (SSL) Protocol
##### Question : How to find tls/ssl client hello message?
```bash
$ tshark -i "eth0" -Y "ssl.handshake.type==1"
```

###### REFERENCE:

* [Wikipedia -  Transport Layer Security]
(https://en.wikipedia.org/wiki/Transport_Layer_Security)
* [Wireshark Wiki - Secure Socket Layer (SSL)]
(https://wiki.wireshark.org/SSL)
* [Display Filter Reference: Secure Sockets Layer]
(https://www.wireshark.org/docs/dfref/s/ssl.html)
