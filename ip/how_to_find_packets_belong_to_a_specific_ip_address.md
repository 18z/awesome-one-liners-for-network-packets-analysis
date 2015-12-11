## The Internet Protocol (IP)
##### Question : How to find packets belong to a specific ip address?
Answer 1: find specific source IPv4 address

```bash
$ tshark -i "eth0" -Y "ip.src==8.8.8.8"
```

Answer 2: find specific destination IPv4 address

```bash
$ tshark -i "eth0" -Y "ip.dst==8.8.8.8"
```

Answer 3: find either the source or destination IPv4 address


```bash
$ tshark -i "eth0" -Y "ip.addr==8.8.8.8"
```

Just replace ip with ipv6 in the filter for looking IPv6 address.

###### REFERENCE:

* [Display Filter Reference: Internet Protocol Version 4]
(https://www.wireshark.org/docs/dfref/i/ip.html)
* [Display Filter Reference: Internet Protocol Version 6]
(https://www.wireshark.org/docs/dfref/i/ipv6.html2)
