## Hypertext Transfer Protocol (HTTP)
##### Question : How to find http client or server errors?
```bash
$ tshark -i "eth0" -Y "http.response.code > 399"
```

###### REFERENCE:

* [Wikipedia - List of HTTP status codes]
(https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)
