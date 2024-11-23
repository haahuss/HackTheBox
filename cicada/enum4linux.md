```
enum4linux <TARGET>
```
nothing found

```
─(kali㉿kali)-[~/htb/cicada]
└─$ enum4linux cicada.htb
Starting enum4linux v0.9.1 ( http://labs.portcullis.co.uk/application/enum4linux/ ) on Thu Nov 21 22:35:19 2024

 =========================================( Target Information )=========================================

Target ........... cicada.htb
RID Range ........ 500-550,1000-1050
Username ......... ''
Password ......... ''
Known Usernames .. administrator, guest, krbtgt, domain admins, root, bin, none


 =============================( Enumerating Workgroup/Domain on cicada.htb )=============================


[E] Can't find workgroup/domain



 =================================( Nbtstat Information for cicada.htb )=================================

Looking up status of 10.10.11.35
No reply from 10.10.11.35

 ====================================( Session Check on cicada.htb )====================================


[+] Server cicada.htb allows sessions using username '', password ''


 =================================( Getting domain SID for cicada.htb )=================================

Domain Name: CICADA
Domain Sid: S-1-5-21-917908876-1423158569-3159038727

[+] Host is part of a domain (not a workgroup)


 ====================================( OS information on cicada.htb )====================================


[E] Can't get OS info with smbclient


[+] Got OS info for cicada.htb from srvinfo: 
do_cmd: Could not initialise srvsvc. Error was NT_STATUS_ACCESS_DENIED


 ========================================( Users on cicada.htb )========================================


[E] Couldn't find users using querydispinfo: NT_STATUS_ACCESS_DENIED



[E] Couldn't find users using enumdomusers: NT_STATUS_ACCESS_DENIED


 ==================================( Share Enumeration on cicada.htb )==================================

do_connect: Connection to cicada.htb failed (Error NT_STATUS_RESOURCE_NAME_NOT_FOUND)

	Sharename       Type      Comment
	---------       ----      -------
Reconnecting with SMB1 for workgroup listing.
Unable to connect with SMB1 -- no workgroup available

[+] Attempting to map shares on cicada.htb


 =============================( Password Policy Information for cicada.htb )=============================


[E] Unexpected error from polenum:



[+] Attaching to cicada.htb using a NULL share

[+] Trying protocol 139/SMB...

	[!] Protocol failed: Cannot request session (Called Name:CICADA.HTB)

[+] Trying protocol 445/SMB...

	[!] Protocol failed: SAMR SessionError: code: 0xc0000022 - STATUS_ACCESS_DENIED - {Access Denied} A process has requested access to an object but has not been granted those access rights.



[E] Failed to get password policy with rpcclient



 ========================================( Groups on cicada.htb )========================================


[+] Getting builtin groups:


[+]  Getting builtin group memberships:


[+]  Getting local groups:


[+]  Getting local group memberships:


[+]  Getting domain groups:


[+]  Getting domain group memberships:


 ===================( Users on cicada.htb via RID cycling (RIDS: 500-550,1000-1050) )===================


[E] Couldn't get SID: NT_STATUS_ACCESS_DENIED.  RID cycling not possible.


 ================================( Getting printer info for cicada.htb )================================

do_cmd: Could not initialise spoolss. Error was NT_STATUS_ACCESS_DENIED


enum4linux complete on Thu Nov 21 22:35:48 2024


```