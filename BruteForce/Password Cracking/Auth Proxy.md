---
tags: 🔻 🔻/🃏/Passwords password_cracking auth-proxy
aliases: Hacking Notes
---

# Auth Proxy

wfuzz -c --hc 404,400,401 -z file,/root/Documents/Audits/ActivosProduban/names.txt -z file,/root/Documents/Audits/ActivosProduban/names.txt --basic "FUZZ:FUZ2Z" -p x.x.x.x:8080

