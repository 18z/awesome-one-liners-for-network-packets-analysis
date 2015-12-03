## tshark - Dump and analyze network traffic
##### Question : How to capture network traffic with tshark?
```bash
$ tshark -i "eth0"
```

###### OPTIONS:


__-i \<capture interface> | -__

>Set the name of the network interface or pipe to use for live packet capture.

>Network interface names should match one of the names listed in "tshark -D" (described above); a number, as reported by "tshark -D", can also be used. If you're using UNIX, "netstat -i" or "ifconfig -a" might also work to list interface names, although not all versions of UNIX support the -a option to ifconfig.

>If no interface is specified, TShark searches the list of interfaces, choosing the first non-loopback interface if there are any non-loopback interfaces, and choosing the first loopback interface if there are no non-loopback interfaces. If there are no interfaces at all, TShark reports an error and doesn't start the capture.

>Pipe names should be either the name of a FIFO (named pipe) or ``-'' to read data from the standard input. Data read from pipes must be in standard pcap format.

>This option can occur multiple times. When capturing from multiple interfaces, the capture file will be saved in pcap-ng format.

>Note: the Win32 version of TShark doesn't support capturing from pipes!
