## The Internet Control Message Protocol (ICMP)
##### Question : How to discover icmp destination unreachable response due to a possible firewall reject?
```bash
$ tshark -i "eth0" -Y "icmp.type==3 &&
    (icmp.code==0 || icmp.code==1 || icmp.code==2  || icmp.code==3 ||
    icmp.code==9 || icmp.code==10 || icmp.code==13)"
```

##### Experiment:

Environment setup:

```
Target machine: IP: 10.3.34.148
Client machine: IP: 10.3.34.146


## On the target machine ##
Setup one (and only one) of the following rules on the target machine.

# 0   Net Unreachable     [RFC792]
sudo iptables -I INPUT -p icmp -j REJECT --reject-with icmp-net-unreachable

# 1   Host Unreachable    [RFC792]
sudo iptables -I INPUT -p icmp -j REJECT --reject-with icmp-host-unreachable

# 2   Protocol Unreachable    [RFC792]
sudo iptables -I INPUT -p icmp -j REJECT --reject-with icmp-proto-unreachable

# 3   Port Unreachable    [RFC792]
sudo iptables -I INPUT -p icmp -j REJECT --reject-with icmp-port-unreachable

# 9   Communication with Destination Network is Administratively Prohibited   [RFC1122]
sudo iptables -I INPUT -p icmp -j REJECT --reject-with icmp-net-prohibited

# 10  Communication with Destination Host is Administratively Prohibited  [RFC1122]
sudo iptables -I INPUT -p icmp -j REJECT --reject-with icmp-host-prohibited

# 13  Communication Administratively Prohibited   [RFC1812]
sudo iptables -I INPUT -p icmp -j REJECT --reject-with icmp-admin-prohibited

As mentioned in the article of port scanning techniques [2],
an ICMP unreachable error could be any of icmp type 3, code 0, 1, 2, 3, 9, 10, or 13.

```

Launch Experiment:

```
## On the client machine: ##

# ping the target machine (34.148)
$ ping 10.3.34.148 -c 1

    and you'll get respones like:

PING 10.3.34.148 (10.3.34.148) 56(84) bytes of data.
From 10.3.34.148 icmp_seq=1 Destination Net Unreachable

--- 10.3.34.148 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms
```

```
## On the Target machine: ##

    Execute the oneliner

$  tshark -i "eth0" -Y "icmp.type==3 &&
    (icmp.code==0 || icmp.code==1 || icmp.code==2  || icmp.code==3 ||
    icmp.code==9 || icmp.code==10 || icmp.code==13)"

and you'll capture packets like:

10.3.34.148 -> 10.3.34.146  Destination unreachable (Network unreachable)
1  10.3.34.148 -> 10.3.34.146  Destination unreachable (Network unreachable)
2  10.3.34.148 -> 10.3.34.146  Destination unreachable (Network unreachable)

yeah! the target machine (34.148)
responeses destination unreachable packets to the client machine (34.146).
```

###### REFERENCE:

[1] [IANA - ICMP Type 3 — Destination Unreachable](https://www.iana.org/assignments/icmp-parameters/icmp-parameters.xhtml#icmp-parameters-codes-3)

[2] [NMAP - Port Scanning Techniques](https://nmap.org/book/man-port-scanning-techniques.html)
