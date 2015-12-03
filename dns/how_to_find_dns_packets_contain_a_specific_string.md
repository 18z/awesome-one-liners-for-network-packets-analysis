## The Domain Name System (DNS)
##### Question : How to find dns packets contain a specific string?
```bash
$ tshark -i "eth0" -Y 'dns contains "example"'
```

###### REFERENCE:

* [ Wireshark DisplayFilters](https://wiki.wireshark.org/DisplayFilters)
