## Hypertext Transfer Protocol (HTTP)
##### Question : How to filter http packets?
Answer 1: Directly use HTTP display filter

```bash
$ tshark -i "eth0" -Y "http"
```

Answer 2: Use the capture filter tcp port X where X denotes the port HTTP or
HTTPS are using

```bash
$ tshark -i "eth0" -f "tcp.port==80"
```

###### REFERENCE:

* [Wikipedia -  Hypertext Transfer Protocol]
(https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol)
