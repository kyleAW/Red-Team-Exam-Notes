---
tags: 🔻 🔻/🃏/Passwords password_cracking md5
aliases: Hacking Notes
---
# # **MD5 \$1$ shadow file**
#hashcat 
Hashcat MD5 \$1$ shadow file  
hashcat -m 500 -a 0 hash.txt rockyou.txt --username

# john RAW MD5
#john 
john hashes.txt --format=raw-md5 -w /usr/share/wordlists/rockyou.txt

# MD5 Apache webdav file \$arp1$
#hashcat 
Hashcat MD5 Apache webdav file  
hashcat -m 1600 -a 0 hash.txt rockyou.txt


# Crack MD5 windows
#hashcat 
crack MD5 with hashcat and wordlist. a=0 is straight attack  

Hashcat64.exe -m 0 -a 0 C:\\whereeveritis\\hashuri.txt F:\\wordlist\\realuniq.lst  
oclHashcat64.exe -m 0 -pw-max=8 C:\\whereeveritis\\hashuri.txt  F:\\wordlist\\realuniq.lst