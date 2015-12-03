## tshark - Dump and analyze network traffic
##### Question : How to capture a specific number of packets?
```bash
$ tshark -i "eth0" -c "count"
```

###### OPTIONS:


__-c \<capture packet count>__

>Set the maximum number of packets to read when capturing live data. If reading a capture file, set the maximum number of packets to read.
