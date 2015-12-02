## The Domain Name System (DNS)
##### Question 4 : How to filter dns traffic which has error conditions?
```bash
$ tshark -i "eth0" -Y "dns.flags.rcode != 0"
```

###### REFERENCE:

* [IANA - DNS RCodes](https://www.iana.org/assignments/dns-parameters/dns-parameters.xhtml#dns-parameters-6)
