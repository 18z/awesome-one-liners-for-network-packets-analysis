## Transport Layer Security (TLS)/ Secure Socket Layer (SSL) Protocol
##### Question : How to find tls/ssl handshake traffic?
```bash
$ tshark -i "eth0" -Y "ssl.record.content_type==22"
```

###### REFERENCE:

* [Wireshark Wiki - Secure Socket Layer (SSL)]
(https://wiki.wireshark.org/SSL)
