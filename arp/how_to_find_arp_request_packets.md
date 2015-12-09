## The Address Resolution Protocol (ARP)
##### Question : How to find arp request packets?
```bash
$ tshark -i "eth0" -Y "arp.opcode==0x0001"
```

###### REFERENCE:

* [IANA - Address Resolution Protocol (ARP) Parameters]
(https://www.iana.org/assignments/arp-parameters/arp-parameters.xhtml)
