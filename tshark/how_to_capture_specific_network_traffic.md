## tshark - Dump and analyze network traffic
##### Question : How to capture specific network traffic?
```bash
$ tshark -i "eth0" -f "filter"
```

###### OPTIONS:


__-f \<capture filter>__

>Set the capture filter expression.

>This option can occur multiple times. If used before the first occurrence of the -i option, it sets the default capture filter expression. If used after an -i option, it sets the capture filter expression for the interface specified by the last -i option occurring before this option. If the capture filter expression is not set specifically, the default capture filter expression is used if provided.
