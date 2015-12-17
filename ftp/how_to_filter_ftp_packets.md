## File Transfer Protocol (FTP)
##### Question : How to filter ftp packets?
```bash
$ tshark -i "eth0" -Y "ftp || ftp-data"
```

###### REFERENCE:

* [Wikipedia -  File Transfer Protocol]
(https://en.wikipedia.org/wiki/File_Transfer_Protocol)
* [Display Filter Reference: File Transfer Protocol (FTP)]
(https://www.wireshark.org/docs/dfref/f/ftp.html)
