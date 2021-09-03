---
tags: 🔻 🔻/🃏/Passwords password_cracking zip
aliases: Hacking Notes
---
# zip

`fcrackzip -u -D -p /usr/share/wordlists/rockyou.txt file.zip`

    
----------  
  
unzip fails with error 99  
then try  
7z x <file.zip> {7z l -slt <file.zip> //to get encrpted method}  
‬zip2john <filename>  
john Access\\ control.hash --worlist=wordlist  
  
string -n 8 <backup.mdb> > wordlist