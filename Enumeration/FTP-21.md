---
tags: 🔻 🔻/Enumeration/ftp
aliases: Hacking Notes
---

## nmap scans
#nmap #Enumeration 

nmap –script ftp-anon,ftp-bounce,ftp-libopie,ftp-proftpd-backdoor,ftp-vsftpd-backdoor,ftp-vuln-cve20 *target ip*


nmap --script=\*ftp\* --script-args=unsafe=1 -p 20,21 *target ip*

## Download files from ftp
wget -m ftp://anonymous:anonymous@ip
wget -m --no-passive ftp://anonymous:anonymous@ip {if above fail}



	