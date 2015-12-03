## The Internet Control Message Protocol (ICMP)
##### Question : How to detect OS fingerprinting?
```bash
$ tshark -i "eth0" -Y "icmp.type==13 || icmp.type==15 || icmp.type==17"
```

###### REFERENCE:

* [SANS - How can attacker use ICMP for reconnaissance?](https://www.sans.org/security-resources/idfaq/icmp_misuse.php)
