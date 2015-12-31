## The Internet Control Message Protocol (ICMP)
##### Question : How to discover icmp destination unreachable response due to a possible firewall reject?
```bash
$ tshark -i "eth0" -Y "icmp.type==3 &&
    (icmp.code==0 || icmp.code==1 || icmp.code==2  || icmp.code==3 ||
    icmp.code==9 || icmp.code==10 || icmp.code==13)"
```

##### Experiment:

* [Experiment Setup](S_how_to_discover_icmp_destination_unreachable_response_due_to_a_possible_firewall_reject.md)

* [Experiment Evaluation](E_how_to_discover_icmp_destination_unreachable_response_due_to_a_possible_firewall_reject.md)

###### REFERENCE:

[1] [IANA - ICMP Type 3 — Destination Unreachable](https://www.iana.org/assignments/icmp-parameters/icmp-parameters.xhtml#icmp-parameters-codes-3)

[2] [NMAP - Port Scanning Techniques](https://nmap.org/book/man-port-scanning-techniques.html)
