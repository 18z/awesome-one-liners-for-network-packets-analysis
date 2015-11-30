## The Internet Control Message Protocol (ICMP)
##### Question 1 : How to filter icmp packet?
```bash
$ tshark -i eth0 -Y "icmp"
```

###### OPTIONS:


__-Y \<displaY filter>__

>Cause the specified filter (which uses the syntax of read/display filters, rather than that of capture filters) to be applied before printing a decoded form of packets or writing packets to a file.

>Packets matching the filter are printed or written to file; packets that the matching packets depend upon (e.g., fragments), are not printed but are written to file; packets not matching the filter nor depended upon are discarded rather than being printed or written.

>Use this instead of -R for filtering using single-pass analysis. If doing two-pass analysis (see -2) then only packets matching the read filter (if there is one) will be checked against this filter.
