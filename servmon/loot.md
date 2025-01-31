nadine
```
└─$ cat FTPcontent/Users/Nadine/Confidential.txt 
Nathan,

I left your Passwords.txt file on your Desktop.  Please remove this once you have edited it yourself and place it back into the secure folder.

Regards

Nadine                                                                               

```


nathan
```
└─$ cat FTPcontent/Users/Nathan/Notes\ to\ do.txt 
1) Change the password for NVMS - Complete
2) Lock down the NSClient Access - Complete
3) Upload the passwords
4) Remove public access to NVMS
5) Place the secret files in SharePoint                                                                               

```

```
──(kali㉿kali)-[~/HTB/servmon]
└─$ cat nathansPasswords 
1nsp3ctTh3Way2Mars!
Th3r34r3To0M4nyTrait0r5!
B3WithM30r4ga1n5tMe
L1k3B1gBut7s@W0rk
0nly7h3y0unGWi11F0l10w
IfH3s4b0Utg0t0H1sH0me
Gr4etN3w5w17hMySk1Pa5$

```

bruteforce hydra on ssh and ftp

# ssh creds:
nadine:L1k3B1gBut7s@W0rk