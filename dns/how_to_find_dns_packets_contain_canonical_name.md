## The Domain Name System (DNS)
##### Question : How to find dns packets contain canonical name (redirection)?
```bash
$ tshark -i "eth0" -Y "dns.resp.type==0x0005"
```

###### REFERENCE:

* [ Wikipedia - CNAME record](https://en.wikipedia.org/wiki/CNAME_record)
* [RFC 1035 -  Domain Names - Implementation And Specification](https://tools.ietf.org/html/rfc1035)