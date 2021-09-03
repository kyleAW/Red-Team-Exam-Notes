---
tags: 🔻 🔻/🃏 Passwords hashcat bruteforce
aliases: Hacking Notes
---

#### Tool is actually on the windows machine not on the Kali box

https://www.blackhillsinfosec.com/wp-content/uploads/2020/09/HashcatCheatSheet.v2018.1b.pdf
*handy cheat sheet to have open when using hashcat*

##### List of Hash Modes 
https://hashcat.net/wiki/doku.php?id=example_hashes
*too big to put on a note follow link for table of different modes*


##### Attack Modes 
-a 0 Straight \[hash\] \[dictionary\] 
-a 1 Combination \[hash\] \[dictionary\] \[dictionary\] 
-a 3 Brute-Force \[hash\] \[mask\] 
-a 6 Hybrid Wordlist + Mask \[hash\] \[dictionary\] \[mask\] 
-a 7 Hybrid Mask + Wordlist \[hash\] \[dictionary\] \[mask\] 

##### Character Sets (Default) \[?\] 
?l abcdefghijklmnopqrstuvwxyz \[26\] 
?u ABCDEFGHIJKLMNOPQRSTUVWXYZ \[26\] 
?d 0123456789 \[10\] 
?h 0123456789abcdef \[16\] 
?H 0123456789ABCDEF \[16\] 
?s !"#$%&'()\*+,-./:;<=>?@\[\\\]^\_\`{|}~ \[33\] 
?a ?l?u?d?s \[95\] ?b 0x00 - 0xff \[255\] 

##### Device Types (-D) 
-D 1 CPU 
-D 2 GPU 
-D 3 FPGA, DSP, Co-Proc 

##### Options 
-m \[#\] Hash Type (mode) 
-a \[#\] Attack Mode 
-r \[file\] Rules file 
-V Version 
--status Keep screen updated 
-b Benchmark 
--runtime \[#\] Abort after x seconds 
--session \[text\] Set session name (resumeable) 
--restore Restore/Resume session 
-o \[filename\] Define output/potfile 
--username Ignore username field in hashfile 
--potfile-disable Ignore potfile and do not write 
-d \[#\] Specify an OpenCL Device 
-D \[#\] Specify an OpenCL Device type 
-I List OpenCL Devices & Types 
-O Optimized Kernel, Passwords <32 char 
-i Increment (brute force) 
--increment-min \[#\] Start increment at \[#\] of chars 
--increment-max \[#\] Stop increment at \[#\[ of chars

### Examples 

\# Hashcat SHA512 $6$ shadow file  
hashcat -m 1800 -a 0 hash.txt rockyou.txt --username  
  
#Hashcat MD5 $1$ shadow file  
hashcat -m 500 -a 0 hash.txt rockyou.txt --username  
  
\# Hashcat MD5 Apache webdav file  
hashcat -m 1600 -a 0 hash.txt rockyou.txt  
  
\# Hashcat SHA1  
hashcat -m x.x.x.x  
  
\# Hashcat Wordpress  
hashcat -m 400 -a 0 --remove hash.txt rockyou.txt  
  
hashcat --force -m 500 -a 0 -o found1.txt --remove puthasheshere.hash /usr/share/wordlists/rockyou.txt  
  
Wordpress hash  
hashcat --force -m 400 -a 0 -o found1.txt --remove wphash.hash /usr/share/wordlists/rockyou.txt  
  
hashcat -m 2500 -a 0 ctf.hccapx x.x.x.x  
  
hashcat -m 11 -a 0 -o found.txt admin.hash /usr/share/hashcat/rules/rockyou-30000.rule  
  
`hashcat -m 500 -a 0 -o cracked.txt hashes.txt /u`


