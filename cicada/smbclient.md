
```
┌──(kali㉿kali)-[~/htb/cicada]
└─$ smbclient \\\\cicada.htb\\hr  
Password for [WORKGROUP\kali]:
Try "help" to get a list of possible commands.
smb: \> ls
  .                                   D        0  Thu Mar 14 08:29:09 2024
  ..                                  D        0  Thu Mar 14 08:21:29 2024
  Notice from HR.txt                  A     1266  Wed Aug 28 13:31:48 2024

		4168447 blocks of size 4096. 0 blocks available
smb: \> 


```

```
smbclient -I 10.10.11.35 -L cicada.htb -U cicada.htb\michael.wrightson%'Cicada$M6Corpb*@Lp#nZp!8'
```