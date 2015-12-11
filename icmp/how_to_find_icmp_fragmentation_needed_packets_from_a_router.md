## The Internet Control Message Protocol (ICMP)
##### Question : How to find icmp fragmentation needed packets from a router?
```bash
$ tshark -i "eth0" -Y "icmp.type==3 && icmp.code==4"
```

###### REFERENCE:

* [Wireshark filter on IP fragmentation]
(https://www.ibm.com/developerworks/community/blogs/f0c70e7a-14af-46c2-91b8-4d90b35f19da/entry/wireshark_filter_on_ip_fragmentation?lang=en)
