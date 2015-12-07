## The Internet Control Message Protocol (ICMP)
##### Question : How to find icmp ping request (ping sweep detection) or response?
```bash
$ tshark -i "eth0" -Y "icmp.type==8 || icmp.type==0"
```

##### Experiment:

Environment setup:

```
host machine: IP 10.44.163.217
target machine: IP 8.8.8.8
```

Launch Experiment:

```
## On the host machine: ##

# ping target machine
$ ping 8.8.8.8

    you'll get responses like

64 bytes from 8.8.8.8: icmp_seq=862 ttl=45 time=8.764 ms
64 bytes from 8.8.8.8: icmp_seq=863 ttl=45 time=8.722 ms
64 bytes from 8.8.8.8: icmp_seq=864 ttl=45 time=9.274 ms
64 bytes from 8.8.8.8: icmp_seq=865 ttl=45 time=9.353 ms
64 bytes from 8.8.8.8: icmp_seq=866 ttl=45 time=7.086 ms
64 bytes from 8.8.8.8: icmp_seq=867 ttl=47 time=14.616 ms
64 bytes from 8.8.8.8: icmp_seq=868 ttl=45 time=9.855 ms
...
```
```
## On the host machine: ##

    Execute the oneliner


# Capture Echo (ping) reply packets
$ tshark -i en1 -Y "icmp.type==0"

    and you'll capture echo (ping) reply packets from target machine

0.318873      8.8.8.8  10.44.163.217     Echo (ping) reply    id=0xf010, seq=32/8192, ttl=45 (request in 7)
1.323618      8.8.8.8  10.44.163.217     Echo (ping) reply    id=0xf010, seq=33/8448, ttl=45 (request in 11)
2.328255      8.8.8.8  10.44.163.217     Echo (ping) reply    id=0xf010, seq=34/8704, ttl=47 (request in 13)

# Capture Echo (ping) request packets
$ tshark -i en1 -Y "icmp.type==8"

    and you'll capture echo (ping) request packets from target machine

0.000000 10.44.163.217  8.8.8.8          Echo (ping) request  id=0xf010, seq=15/3840, ttl=64
1.002965 10.44.163.217  8.8.8.8          Echo (ping) request  id=0xf010, seq=16/4096, ttl=64
2.008187 10.44.163.217  8.8.8.8          Echo (ping) request  id=0xf010, seq=17/4352, ttl=64
```

###### REFERENCE:

[1] [IANA - Internet Control Message Protocol (ICMP) Parameters](https://www.iana.org/assignments/icmp-parameters/icmp-parameters.xhtml)
