## The Domain Name System (DNS)
##### Question : How to filter dns query packets?
```bash
$ tshark -i "eth0" -Y "dns.flags.response==0"
```

###### REFERENCE:

* [IANA - Domain Name System (DNS) Parameters](https://www.iana.org/assignments/dns-parameters/dns-parameters.xhtml)
