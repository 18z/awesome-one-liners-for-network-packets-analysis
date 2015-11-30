## tshark - Dump and analyze network traffic
##### Question 4 : How to write raw packet data to file?
```bash
$ tshark -i eth0 -w "filename" 
```

###### OPTIONS:


__-w \<outfile> | -__

>Write raw packet data to outfile or to the standard output if outfile is '-'.

>NOTE: -w provides raw packet data, not text. If you want text output you need to redirect stdout (e.g. using '>'), don't use the -w option for this.
