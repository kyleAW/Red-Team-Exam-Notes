---
tags: 🔻 🔻/Enumeration/rdp
aliases: Hacking Notes
---

# RPD
Enable RDP through the command line  
reg add "hklm\\system\\currentControlSet\\Control\\Terminal Server" /v "AllowTSConnections" /t REG\_DWORD /d 0x1 /f  
  
  
if terminal services are disabled:  
sc config TermService start= "demand"  
net start TermService  
    
Mount linux share  
rdesktop -u username -p password -r disk:share=/home//Desktop x.x.x.x  
  
  
Add users  
Windows: net user username password /add  
net localgroup Administrators username /add  
net localgroup "Remote Desktop Users" username /add