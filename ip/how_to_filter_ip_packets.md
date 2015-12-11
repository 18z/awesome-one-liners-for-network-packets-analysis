## The Internet Protocol (IP)
##### Question : How to filter ip packets?
Answer 1: display filter for IPv4 traffic

```bash
$ tshark -i "eth0" -Y "ip"
```

Answer 2: display filter for IPv6 traffic

```bash
$ tshark -i "eth0" -Y "ipv6"
```

###### REFERENCE:

* [Wikipedia - Internet Protocol]
(https://en.wikipedia.org/wiki/Internet_Protocol)
