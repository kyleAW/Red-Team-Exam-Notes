---
tags: 🔻 🔻/shell
aliases: Hacking Notes
---

# TTY
## used to sure up a shell to something we can actually use

python -c 'import pty;pty.spawn("/bin/bash")'  
  
### method 1  
  
python -c 'import pty; pty.spawn("/bin/bash")' -> stty raw -echo -> fg -> export TERM=xterm  
  
### method 2
 
echo os.system('/bin/bash')  
/bin/sh -i  
  
 
\# Enter while in reverse shell  
$ python -c 'import pty; pty.spawn("/bin/bash")'  
  
Ctrl-Z  
  
\# In Kali  
$ stty raw -echo  
$ fg  
  
\# In reverse shell  
$ reset  
$ export SHELL=bash  
$ export TERM=xterm-256color  
$ stty rows <num> columns <cols>