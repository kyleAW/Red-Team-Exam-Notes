---
tags: 🔻 🔻/Enumeration/smb
aliases: Hacking Notes
---

# SMB

\# mount SMB share to a afolder  
mount -t auto --source //x.x.x.x  
  
  
Note
note the comments which get listed while listing smb share like smbclient //*ip*/share exist in /etc/  
Follow the file mapping based on http files & smb files listing becuase putting file in a certain folder might get accessible from LFI in webbrowser   
  
  
Note if get access with creds to a certain domain then tryupload there

# smbclient
#smbclient


List shares on a machine using NULL Session

smbclient -


smbclient -L *TargetIP* -U username%password

Connect to a valid share with username + password

smbclient //*TargetIP*/*share$* -U username%password

List files on a specific share

smbclient //*TargetIP*/*share$* -c 'ls' password -U username

List files on a specific share folder inside the share

smbclient //*TargetIP*/*share$* -c 'cd folder; ls' password -U username

Download a file from a specific share folder

smbclient //*TargetIP*/*share$* -c 'cd folder;get desired\_file\_name' password -U username

Copy a file to a specific share folder

smbclient //*TargetIP*/*share$* -c 'put /var/www/my\_local\_file.txt .\\target\_folder\\target\_file.txt' password -U username

Create a folder in a specific share folder

smbclient //*TargetIP*/*share$* -c 'mkdir .\\target\_folder\\new\_folder' password -U username

)Rename a file in a specific share folder

smbclient //*TargetIP*/*share$* -c 'rename current\_file.txt new\_file.txt' password -U username
	

## SMB NETBIOS
#enum4linux
enum4linux x.x.x.x  
nmap -v -p 139,445 -oG smb.txt x.x.x.x  
nbtscan -r x.x.x.x  
nmblookup -A target  
smbclient //x.x.x.x  
rpcclient -U "" target // connect as blank user /nobody  
smbmap -u "" -p "" -d MYGROUP -H *targetIP* 
  
  
\== NetBIOS NullSession enumeration ==  
\# This feature exists to allow unauthenticated machines to obtain browse lists from other  
\# Microsoft servers. Enum4linux is a wrapper built on top of smbclient,rpcclient, net and nmblookup  
enum4linux -a x.x.x.x  
  
\## upload file  
smbclient //x.x.x.x  

  

## Windows null session:  
#acccheck
C:\\>net use \\\\TARGET\\IPC$ “” /u:””  
Use acccheck for getting user pass using smb  
acccheck -v -t x.x.x.x  
acccheck -t x.x.x.x  

Once you got user creds we will use the creds to see the shares using 

#smbmap  

smbmap -u *username* -p *password* -d *domain* -H *ip*
smbmap -u user -p pass -d workgroup -H x.x.x.x  
smbmap -L -u user -p pass -d workgroup -H x.x.x.x  
If you have only read privilege read the shares  
smbmap -r -u user -p pass -d workgroup -H