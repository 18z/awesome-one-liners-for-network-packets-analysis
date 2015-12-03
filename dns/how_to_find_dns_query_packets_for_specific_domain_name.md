## The Domain Name System (DNS)
##### Question : How to find dns query packets for specific domain name?
```bash
$ tshark -i "eth0" -Y 'dns.qry.name=="www.example.com"'
```

###### REFERENCE:

* [Wireshark - Display Filter Reference: Domain Name System](https://www.wireshark.org/docs/dfref/d/dns.html)
