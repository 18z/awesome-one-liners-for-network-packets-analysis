## The Domain Name System (DNS)
##### Question : How to identify possible domain-flux(DGA) query traffic?
```bash
$ tshark -i "eth0" -Y "dns.flags.rcode==3"
```

###### REFERENCE:

* [Wikipedia -  Domain Generation Algorithm(DGA)](https://en.wikipedia.org/wiki/Domain_generation_algorithm)
* [USENIX - From Throw-Away Traffic to Bots: Detecting the Rise of DGA-Based Malware](https://www.usenix.org/conference/usenixsecurity12/technical-sessions/presentation/antonakakis)
