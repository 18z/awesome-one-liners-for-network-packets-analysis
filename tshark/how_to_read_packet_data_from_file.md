## tshark - Dump and analyze network traffic
##### Question : How to read packet data from file?
```bash
$ tshark -r "filename" 
```

###### OPTIONS:


__-r \<infile>__

>Read packet data from infile, can be any supported capture file format (including gzipped files). It is possible to use named pipes or stdin (-) here but only with certain (not compressed) capture file formats (in particular: those that can be read without seeking backwards).
