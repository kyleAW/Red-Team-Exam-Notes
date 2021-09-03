---
tags: 🔻 🔻/🃏/Passwords password_cracking rsa john
aliases: Hacking Notes
---
# RSA Decrypting


Vigerner Cipher  
  
encrypted id_rsa ....  
key to decrypt  
  
python sshng2john.py id_rsa > id_john {convert John decrpt format}  
  
john id_john --wordlist=/usr/share/wordlists/rockyou.txt  
  
  
  
Decrypting RSA for given p,q,e and ct (cyphertext)  
rsadecrypt.py  
Result - PlainText (Long number)  
  
Convert PT to hex  
python -c "print(PT,'x').decode('hex')"