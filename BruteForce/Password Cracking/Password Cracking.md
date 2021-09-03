---
tags: 🔻 🔻/🃏/Passwords password_cracking
aliases: Hacking Notes
---

# password Cracking
#john 

$ unshadow passwd shadow > unshadow.db  
$ john unshadow.db  
  
#hashcat 

Hashcat SHA512 $6$ shadow file  
hashcat -m 1800 -a 0 hash.txt rockyou.txt --username  
  
Hashcat MD5 $1$ shadow file  
hashcat -m 500 -a 0 hash.txt rockyou.txt --username  
  
Hashcat MD5 Apache webdav file  
hashcat -m 1600 -a 0 hash.txt rockyou.txt  
  
Hashcat SHA1  
hashcat -m x.x.x.x  
  
Hashcat Wordpress  
hashcat -m 400 -a 0 --remove hash.txt rockyou.txt

  
  


if you are spending more than 20 minutes brute forcing or dictionary attacks then there is another way in. I used SecLists almost exclusively for fuzzing or passwords. #fuzzing #seclists


  
Cracking Linux Hashes - /etc/shadow file  
  
500 | md5crypt $1$, MD5(Unix) | Operating-Systems  
3200 | bcrypt $2\*$, Blowfish(Unix) | Operating-Systems  
7400 | sha256crypt $5$, SHA256(Unix) | Operating-Systems  
1800 | sha512crypt $6$, SHA512(Unix) | Operating-Systems  
  
Cracking Windows Hashes  
  
3000 | LM | Operating-Systems  
x.x.x.x  
  
Cracking Common Application Hashes  
  
900 | MD4 | Raw Hash  
0 | MD5 | Raw Hash  
5x.x.x.x  
x.x.x.x  
x.x.x.x  
1400 | SHA-256 | Raw Hash  
1700 | SHA-512 | Raw Hash  
  
Create a .hash file with all the hashes you want to crack puthasheshere.hash: $1$O3JMY.Tw$AdLnLjQ/5jXF9.MTp3gHv/  
  
Hashcat example cracking Linux md5crypt passwords $1$ using rockyou:  
  
hashcat --force -m 500 -a 0 -o found1.txt --remove puthasheshere.hash /usr/share/wordlists/rockyou.txt