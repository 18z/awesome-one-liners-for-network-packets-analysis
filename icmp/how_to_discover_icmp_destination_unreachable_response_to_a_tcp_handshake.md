## The Internet Control Message Protocol (ICMP)
##### Question 3 : How to discover icmp destination unreachable response to a tcp handshake (possible firewall-protected target)? 
```bash
$ tshark -i "eth0" -Y "icmp.type==3 && 
    (icmp.code==1 || icmp.code ==2 || icmp.code==3 || 
    icmp.code==9  || icmp.code==10 || icmp.code==13)"
```

###### REFERENCE:

* [IANA - ICMP Type 3 — Destination Unreachable](https://www.iana.org/assignments/icmp-parameters/icmp-parameters.xhtml#icmp-parameters-codes-3)
