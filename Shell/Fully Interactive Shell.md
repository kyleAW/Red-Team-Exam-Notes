---
tags: 🔻 🔻/shell
aliases: Hacking Notes
---

# Magic on netcat

  
  

### In reverse shell  
#tty 

$ python -c 'import pty; pty.spawn("/bin/bash")';  
  
or  
  
$ python3 -c 'import pty; pty.spawn("/bin/bash")'  
  
Ctrl-Z  
  
stty raw -echo;fg;  
  
export SHELL=bash;export TERM=xterm-256color;stty rows 44 columns

211  
export PATH=$PATH:/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin