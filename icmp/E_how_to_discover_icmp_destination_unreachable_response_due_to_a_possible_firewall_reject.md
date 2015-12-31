## Experiment Evaluation

### Three stages in this experiment:

1. Packet Sending
2. Verify whether received or not
3. Packet Forensics

### Steps in experiment:

1. On receiver side, setup filrewall rules for ICMP response and firewall logging. 
3. On receiver side, use tshark to capture the packets
4. On sender side, send ICMP packet with ping command.
4. On receiver side, check firewall log to see whether received or not
6. On forensic side, use tshark to analyze packets.

### Steps in detail:

1. Receiver side - setup filrewall rules for ICMP response and firewall logging.

	```bash
	# Set up the iptables rule
	$ sudo iptables -I INPUT -p icmp -j REJECT --reject-with icmp-net-unreachable
	
	# Set up firewall logging
	$ sudo iptables -I INPUT -p icmp -j LOG --log-prefix='[net-unreachable ICMP]'

	# Make sure the rule is set up
	$ sudo iptables -L -n
	Chain INPUT (policy ACCEPT)
	target     prot opt source               destination         
	LOG        icmp --  0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 4 prefix "[net-unreachable ICMP]"
	REJECT     icmp --  0.0.0.0/0            0.0.0.0/0            reject-with icmp-net-unreachable

	Chain FORWARD (policy ACCEPT)
	target     prot opt source               destination         

	Chain OUTPUT (policy ACCEPT)
	target     prot opt source               destination 
	```

2. Receiver side - use tshark to capture the packets

	```bash
	$ sudo tshark -i eth0 -w icmp.pcap
	```

3. Sender side - send ICMP packet with ping command

	```bash
	$ ping 10.3.34.148 -c 1
	PING 10.3.34.148 (10.3.34.148) 56(84) bytes of data.
	From 10.3.34.148 icmp_seq=1 Destination Net Unreachable

	--- 10.3.34.148 ping statistics ---
	1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms
	```

4. Receiver side - check firewall log to see whether received or not

	```bash
	$ tail -f /var/log/syslog|grep ICMP                           
Dec 31 11:56:36 RedBull kernel: [ 9328.099109] [net-unreachable ICMP]IN=eth0 OUT= MAC=00:0f:fe:e1:73:25:00:21:5e:4d:ce:1d:08:00 SRC=10.3.34.146 DST=10.3.34.148 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=60079 DF PROTO=ICMP TYPE=8 CODE=0 ID=16115 SEQ=1
	```

5. Forensic side - use tshark to analyze packets

	```bash
	$ sudo tshark -i "eth0" -Y "icmp.type==3 &&
	    (icmp.code==0 || icmp.code==1 || icmp.code==2  || icmp.code==3 ||
	    icmp.code==9 || icmp.code==10 || icmp.code==13)" -r icmp.pcap
	10.3.34.148 -> 10.3.34.146  Destination unreachable (Network unreachable)
	1  10.3.34.148 -> 10.3.34.146  Destination unreachable (Network unreachable)
	2  10.3.34.148 -> 10.3.34.146  Destination unreachable (Network unreachable)
	```
