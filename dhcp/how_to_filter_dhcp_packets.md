## Dynamic Host Configuration Protocol (DHCP)
##### Question : How to filter dhcp packets?
Answer 1: Since DHCPv4 is based on BOOTP (Bootstrap Protocol), set display filter in "bootp" directly

```bash
$ tshark -i "eth0" -Y "bootp"
```

Answer 2: Set display filter in "dhcpv6" to filter DHCPv6 packets

```bash
$ tshark -i "eth0" -Y "dhcpv6"
```

###### REFERENCE:

* [Wikipedia - Dynamic Host Configuration Protocol]
(https://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol)
