---
tags: 🔻 🔻/Enumeration/sqlinjection sqlinjection
aliases: Hacking Notes
---

# Boolean based SQL

Determine databsae name with boolean-based blind SQL injection with #substr  
  


and `(substr(database(),<offset>,<character length>))='<character>' --+  `
  
  
Determine databsae name with boolean-based blind SQL injection by observing http response size with combination of substr() and wfuzz, assuming database name does not include special characters  
for i in $(seq 1 x.x.x.x  
  
Determine databsae name with boolean-based blind SQL injection by observing http response size with substr(), ascii() and wfuzz. The below range is the standard ASCII characters (32-127)  
for i in $(seq 1 x.x.x.x  
  
Determine table name with boolean-based blind SQL injection by observing http response size with substr(), ascii(), and wfuzz.The below range is the standard ASCII characters (32-127)  
for i in $(seq 1 x.x.x.x  
  
Determine column name with boolean blind-based SQL injection by observing http response size with substr(), ascii(), and wfuzz. The below range is the standard ASCII characters (32-127)  
for i in $(seq 1