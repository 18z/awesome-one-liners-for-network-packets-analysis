## tshark - Dump and analyze network traffic
##### Question 1 : How to list your network interfaces?
```bash
$ tshark -D
```

###### OPTIONS:


__-D \<Display>__

>Print a list of the interfaces on which TShark can capture, and exit. For each network interface, a number and an interface name, possibly followed by a text description of the interface, is printed. The interface name or the number can be supplied to the -i option to specify an interface on which to capture.

>This can be useful on systems that don't have a command to list them (e.g., Windows systems, or UNIX systems lacking ifconfig -a); the number can be useful on Windows 2000 and later systems, where the interface name is a somewhat complex string.

>Note that "can capture" means that TShark was able to open that device to do a live capture. Depending on your system you may need to run tshark from an account with special privileges (for example, as root) to be able to capture network traffic. If TShark -D is not run from such an account, it will not list any interfaces.
