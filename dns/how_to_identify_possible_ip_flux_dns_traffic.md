## The Domain Name System (DNS)
##### Question : How to identify possible ip-flux(Fast-flux) response traffic?
```bash
$ tshark -i "eth0" -Y "(dns.flags.response==1) && (dns.count.answers>=5) && 
    (dns.resp.ttl<3600 || dns.resp.ttl<86400 || dns.resp.ttl<259200)"
```

###### REFERENCE:

* [Wikipideia - Fast flux](https://en.wikipedia.org/wiki/Fast_flux)
* [RFC Draft - Double Flux Defense in the DNS Protocol](https://tools.ietf.org/html/draft-bambenek-doubleflux-01)
