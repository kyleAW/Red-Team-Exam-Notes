---
tags: 🔻 🔻/🃏 Passwords john bruteforce
aliases: Hacking Notes
---

## John the Ripper

*pain in the arse to use sometimes!*

Variety of 2john tools to test and try to crack. for instance ssh2john. google to find the different ones



Wordlist Mode (dictionary attack) 
./john --wordlist=password.lst hashfile 
Mangling Rules Mode (hybrid)
./john --wordlist=password.lst – rules: hashfile 
Incremental mode (Brute Force) 
./john --incremental hashfile 
External mode (use a program to generate guesses) 
./john --external: hashfile 
Loopback mode (use POT as wordlist)
./john --loopback hashfile 
Mask mode (read MASK under /doc) 
./john --mask=?1?1?1?1?1?1?1?1 -1=\[A-Z\] hashfile -min-len=8 
Hybrid Mask mode 
./john -w=password.lst - mask='?l?l?w?l?l' hashfile 
Markov mode (Read MARKOV under /doc). 
First generate Markov stats: ./calc\_stat wordlist markovstats Then run: 
./john -markov:200 -max-len:12 hashfile --mkv-stats=markovstats 
Prince mode (Read PRINCE under /doc) 
./john --prince=wordlist hashfile

### Example uses

john $ip.pwdump  
john --wordlist=/usr/share/wordlists/rockyou.txt hashes  
john --rules --wordlist=/usr/share/wordlists/rockyou.txt  
john --rules --wordlist=/usr/share/wordlists/rockyou.txt unshadowed.txt  
  
JTR forced descrypt cracking with wordlist  

john --format=descrypt --wordlist /usr/share/wordlists/rockyou.txt hash.txt  
  
JTR forced descrypt brute force cracking  

john --format=descrypt hash --show  
  
  
python 7z2ctf.py arjun.7z > hash  
john --wordlist=/usr/share/wordlists/rockyou.txt hash  
  
john -w=/usr/share/wordlists/rockyou.txt -form=raw-md5 hashes  
  
john --wordlist=wordlist.txt dump.txt  
  
john --rules --wordlist=wordlist.txt dump.txt  
  
unshadow passwd-file.txt shadow-file.txt > unshadowed.txt  
`john --rules --wordlist=wordlist.txt unshadowed.txt ` 
  
`john --wordlist=/usr/share/wordlists/rockyou.txt keepass-hash.txt ` 

`john --wordlist=/usr/share/wordlists/sqlmap.txt passwords.txt`  
  
ssh2john   id\_rsa > id\_john​ and then ​john id\_john --wordlist=/usr/share/wordlists/rockyou.txt