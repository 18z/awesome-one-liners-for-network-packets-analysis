## The Domain Name System (DNS)
##### Question 2 : How to filter dns response packets?
```bash
$ tshark -i "eth0" -Y "dns.flags.response==1"
```

###### REFERENCE:

* [IANA - Domain Name System (DNS) Parameters](https://www.iana.org/assignments/dns-parameters/dns-parameters.xhtml)
