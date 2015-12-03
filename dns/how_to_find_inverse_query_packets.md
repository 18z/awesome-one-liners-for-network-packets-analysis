## The Domain Name System (DNS)
##### Question : How to find inverse query packets?
```bash
$ tshark -i "eth0" -Y "dns.qry.type==0x000c"
```

###### REFERENCE:

* [RFC 1035 -  Domain Names - Implementation And Specification](https://tools.ietf.org/html/rfc1035)
