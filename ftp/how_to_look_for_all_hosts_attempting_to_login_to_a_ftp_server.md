## File Transfer Protocol (FTP)
##### Question : How to look for all hosts attempting to login to a ftp server?
```bash
$ tshark -i "eth0" -Y "ftp.request.command==USER || ftp.request.command==PASS"
```

###### REFERENCE:

* [Wikipedia - List of FTP commands]
(https://en.wikipedia.org/wiki/List_of_FTP_commands)
* [Display Filter Reference: File Transfer Protocol (FTP)]
(https://www.wireshark.org/docs/dfref/f/ftp.html)
