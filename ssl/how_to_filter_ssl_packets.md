## Transport Layer Security (TLS)/ Secure Socket Layer (SSL) Protocol
##### Question : How to filter tls/ssl packets?
Answer 1: Directly use ssl display filter

```bash
$ tshark -i "eth0" -Y "ssl"
```

Answer 2: Use the capture filter tcp port X where X denotes the port SSL are
using

```bash
$ tshark -i "eth0" -f "tcp.port==443"
```

###### REFERENCE:

* [Wikipedia -  Transport Layer Security]
(https://en.wikipedia.org/wiki/Transport_Layer_Security)
