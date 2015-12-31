## Experiment Setup

### Three roles in this experiment :

1. Packet Sender aka Attacker
2. Packet Reveiver aka Defender
3. Packet Analyzer aka Forensic Specialist

### Experiment setup for each role :

1. OS version

	* Packet Sender

	```bash
	$ sudo cat /etc/*-release
	PRETTY_NAME="Debian GNU/Linux 7 (wheezy)"
	```

	* Packet Reiceiver

	```bash
	$ sudo cat /etc/*-release
	DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"
	```

2. Network Settings

	* Packet Sender

	```bash
	$ sudo ifconfig
	eth1      Link encap:Ethernet  HWaddr 00:21:5e:4d:ce:1d
          inet addr:10.3.34.146  Bcast:10.3.255.255  Mask:255.255.0.0
	```

	* Packet Receiver

	```bash
	$ sudo ifconfig
	eth0      Link encap:Ethernet  HWaddr 00:0f:fe:e1:73:25
	          inet addr:10.3.34.148  Bcast:10.3.255.255  Mask:255.255.0.0
	```

3. Tool used and Tool version

	* Packet Sender：Tools that generate packets or launch attacks

	```bash
	# --= Packets Sending =--
	$ ping -V
	ping utility, iputils-s20121221
	```

	* Packet Receiver: Tools that record, verify packets or Tools that customize packets for responding.

	```	bash
	# --= Response Message Configuration ==-
	$ sudo iptables -V
	iptables v1.4.21


	# --= Verification of Packets Received =--
	$ sudo tcpdump -V
	tcpdump: invalid option -- '-'
	tcpdump version 4.5.1
	libpcap version 1.5.3

	# --= Packets Recording =--
	$ sudo tshark -h
	TShark 1.10.6 (v1.10.6 from master-1.10)
	```

	* Packet Analyzer: Forensic tools

	```bash
	# --= Forensic =--
	$ sudo tshark -h
	TShark 1.10.6 (v1.10.6 from master-1.10)
	```

4. Tool settings

	* Packet Sender

	```bash
	# --= Packets Sending =--
	$ ping 10.3.34.148 -c 1
	```

	* Packet Receiver

	```bash
	# --= Response Message Configuration =--
	# Setup one (and only one) of the following rules on the target machine.
	# In this experiment, we set up a net unreachable rule on the packets receiver side.

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

	# As mentioned in the article of port scanning techniques [2],
	# an ICMP unreachable error could be any of icmp type 3, code 0, 1, 2, 3, 9, 10, or 13.

	# --= Verification =-
	# We use iptables to verify
	# if the icmp packets had been received
	# "[net-unreachable ICMP]" will be shown in the firewall log.

		$ sudo iptables -I INPUT -p icmp -j LOG --log-prefix='[net-unreachable ICMP]'

	# --= Packets Recording =--
	# We use tshark to record packets.

		$ sudo tshark -i eth0 -w icmp.pcap
	```

	* Packet Analyzer

	```bash
	# --= Forensic and Analysis =--
	$ sudo tshark -i "eth0" -Y "icmp.type==3 &&
    (icmp.code==0 || icmp.code==1 || icmp.code==2  || icmp.code==3 ||
    icmp.code==9 || icmp.code==10 || icmp.code==13)" -r icmp.pcap
	```
