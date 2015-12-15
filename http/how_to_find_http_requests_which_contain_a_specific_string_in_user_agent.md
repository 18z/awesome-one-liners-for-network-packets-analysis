## Hypertext Transfer Protocol (HTTP)
##### Question : How to find http requests which contain a specific string in user agent?
```bash
$ tshark -i "eth0" -Y 'http.user_agent contains "Chrome"'
```

###### REFERENCE:

* [Wikipedia - List of HTTP header fields]
(https://en.wikipedia.org/wiki/List_of_HTTP_header_fields)
* [UserAgentString.com - List of User Agent Strings]
(http://www.useragentstring.com/pages/useragentstring.php)
