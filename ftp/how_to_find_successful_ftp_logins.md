## File Transfer Protocol (FTP)
##### Question : How to find successful ftp logins?
```bash
$ tshark -i "eth0" -Y "ftp.request.code==230"
```

###### REFERENCE:

* [Wikipedia - List of FTP server return codes]
(https://en.wikipedia.org/wiki/List_of_FTP_server_return_codes)
* [Display Filter Reference: File Transfer Protocol (FTP)]
(https://www.wireshark.org/docs/dfref/f/ftp.html)
