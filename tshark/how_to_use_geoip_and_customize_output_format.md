## tshark - Dump and analyze network traffic
##### Question : How to use geoip and customize output format?
```bash
$ tshark -r "pcap" -T fields -e ip.src -e tcp.srcport -e \ 
ip.geoip.src_country -e ip.geoip.src_lat -e ip.geoip.src_lon \
-E separator=, -E quote=d
```
This script customize the pcap file into the ip source,ip source port,ip source country,ip source latitude and longitude in CSV format.

How To Use GeoIP With Wireshark
MaxMind produces databases and software for geolocation. Wireshark 1.1.2 and later can use MaxMind's GeoIP (purchase) and GeoLite (free) databases to look up the city, country, AS number, and other information for an IP address. 

Download the databases in binary format
GeoLite City, Country, and ASNum: http://geolite.maxmind.com/download/geoip/database/ (free download)

It's more convenient if you put all of the databases in the same directory. Once you've downloaded your databases, you must tell Wireshark where they are. Go to Edit¡÷Preferences¡÷Name Resolution and select GeoIP database directories. Add the full path of each database directory. 

Restart Wireshark. At this point you should be able to load a capture file, select Statistics¡÷Endpoints, and see GeoIP information in any tab that contains IP addresses (IP, TCP, UDP, etc). 
You can optionally see GeoIP data in the IP packet detail tree. To enable this, go to Edit¡÷Preferences¡÷Protocols¡÷IP and make sure Enable GeoIP lookups is checked.

Filtering Traffic
You can use the ip.geoip display filters to filter traffic.
Exclude U.S.-based traffic:
 ip and not ip.geoip.country == "United States" 
Show address above the arctic circle:
 ip.geoip.lat > "66.5" 

###### REFERENCE:
[1] [How To Use GeoIp](https://wiki.wireshark.org/HowToUseGeoIP)

