## The Address Resolution Protocol (ARP)
##### Question : How to detect arp poisoning (spoofing)?
```bash
$ tshark -i "eth0" -Y "arp.duplicate-address-detected"
```

###### REFERENCE:

* [Display Filter Reference: Address Resolution Protocol]
(https://www.wireshark.org/docs/dfref/a/arp.html)
