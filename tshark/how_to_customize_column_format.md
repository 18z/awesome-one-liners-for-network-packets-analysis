## tshark - Dump and analyze network traffic
##### Question 8 : How to customize column format?
Answer 1: Directly set preferences with option -o 

```bash
$ tshark -i eth0 \
    -o column.format:' \
    "Source", "%s",
    "Destination", "%d",
    "Info", "%i"'
```

Answer 2: Set the preferences in ~/.wireshark/preferences

```bash
column.format:
    "Source", "%s",
    "Destination", "%d",
    "Info", "%i"
```

###### OPTIONS:


-o  \<preference>:\<value>

> Set a preference value, overriding the default value and any value read from a preference file. The argument to the option is a string of the form prefname:value, where prefname is the name of the preference (which is the same name that would appear in the preference file), and value is the value to which it should be set.


