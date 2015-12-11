## The Internet Protocol (IP)
##### Question : How to find fragmented ip packets?
```bash
$ tshark -i "eth0" -Y "ip.flags.mf == 1 || ip.frag_offset > 0"
```

###### REFERENCE:

* [Wireshark filter on IP fragmentation]
(https://www.ibm.com/developerworks/community/blogs/f0c70e7a-14af-46c2-91b8-4d90b35f19da/entry/wireshark_filter_on_ip_fragmentation?lang=en)
* [Wikipedia - IPv4 flags field]
(https://en.wikipedia.org/wiki/IPv4#Flags)
* [Wikipedia - IPv4 fragment offset field]
(https://en.wikipedia.org/wiki/IPv4#Fragment_Offset)
