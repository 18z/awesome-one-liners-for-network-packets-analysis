## The Address Resolution Protocol (ARP)
##### Question : How to find arp reply packets?
```bash
$ tshark -i "eth0" -Y "arp.opcode==0x0002"
```

###### REFERENCE:

* [IANA - Address Resolution Protocol (ARP) Parameters]
(https://www.iana.org/assignments/arp-parameters/arp-parameters.xhtml)
