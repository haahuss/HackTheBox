```
nmap <TARGET> -Pn -T5 -o quicknmapscan
nmap <TARGET> -Pn -T5 -p- -o allportscan
sudo nmap <TARGET> -Pn -T5 -p<PORTS> -sC -sV -O -o fullnmapscan
```

```
┌──(kali㉿kali)-[~/htb/cicada]
└─$ nmap cicada.htb -Pn -T5                    
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-11-21 22:18 EST
Nmap scan report for cicada.htb (10.10.11.35)
Host is up (0.042s latency).
Not shown: 989 filtered tcp ports (no-response)
PORT     STATE SERVICE
53/tcp   open  domain
88/tcp   open  kerberos-sec
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
389/tcp  open  ldap
445/tcp  open  microsoft-ds
464/tcp  open  kpasswd5
593/tcp  open  http-rpc-epmap
636/tcp  open  ldapssl
3268/tcp open  globalcatLDAP
3269/tcp open  globalcatLDAPssl

Nmap done: 1 IP address (1 host up) scanned in 3.47 seconds

```

```
┌──(kali㉿kali)-[~/htb/cicada]
└─$ nmap cicada.htb -Pn -T5 -p-
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-11-21 22:18 EST
Nmap scan report for cicada.htb (10.10.11.35)
Host is up (0.047s latency).
Not shown: 65522 filtered tcp ports (no-response)
PORT      STATE SERVICE
53/tcp    open  domain
88/tcp    open  kerberos-sec
135/tcp   open  msrpc
139/tcp   open  netbios-ssn
389/tcp   open  ldap
445/tcp   open  microsoft-ds
464/tcp   open  kpasswd5
593/tcp   open  http-rpc-epmap
636/tcp   open  ldapssl
3268/tcp  open  globalcatLDAP
3269/tcp  open  globalcatLDAPssl
5985/tcp  open  wsman
54890/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 88.05 seconds

```

```
┌──(kali㉿kali)-[~/htb/cicada]
└─$ nmap cicada.htb -Pn -T5 -p53,88,135,139,445,464,593,636,3268,3269,5895,54890 -sC -sV
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-11-21 22:24 EST
Nmap scan report for cicada.htb (10.10.11.35)
Host is up (0.042s latency).

PORT      STATE    SERVICE       VERSION
53/tcp    open     domain?
88/tcp    open     kerberos-sec  Microsoft Windows Kerberos (server time: 2024-11-22 10:24:40Z)
135/tcp   open     msrpc         Microsoft Windows RPC
139/tcp   open     netbios-ssn   Microsoft Windows netbios-ssn
445/tcp   open     microsoft-ds?
464/tcp   open     kpasswd5?
593/tcp   open     ncacn_http    Microsoft Windows RPC over HTTP 1.0
636/tcp   open     ssl/ldap      Microsoft Windows Active Directory LDAP (Domain: cicada.htb0., Site: Default-First-Site-Name)
| ssl-cert: Subject: commonName=CICADA-DC.cicada.htb
| Subject Alternative Name: othername: 1.3.6.1.4.1.311.25.1::<unsupported>, DNS:CICADA-DC.cicada.htb
| Not valid before: 2024-08-22T20:24:16
|_Not valid after:  2025-08-22T20:24:16
|_ssl-date: TLS randomness does not represent time
3268/tcp  open     ldap          Microsoft Windows Active Directory LDAP (Domain: cicada.htb0., Site: Default-First-Site-Name)
| ssl-cert: Subject: commonName=CICADA-DC.cicada.htb
| Subject Alternative Name: othername: 1.3.6.1.4.1.311.25.1::<unsupported>, DNS:CICADA-DC.cicada.htb
| Not valid before: 2024-08-22T20:24:16
|_Not valid after:  2025-08-22T20:24:16
|_ssl-date: TLS randomness does not represent time
3269/tcp  open     ssl/ldap      Microsoft Windows Active Directory LDAP (Domain: cicada.htb0., Site: Default-First-Site-Name)
|_ssl-date: TLS randomness does not represent time
| ssl-cert: Subject: commonName=CICADA-DC.cicada.htb
| Subject Alternative Name: othername: 1.3.6.1.4.1.311.25.1::<unsupported>, DNS:CICADA-DC.cicada.htb
| Not valid before: 2024-08-22T20:24:16
|_Not valid after:  2025-08-22T20:24:16
5895/tcp  filtered unknown
54890/tcp open     msrpc         Microsoft Windows RPC
Service Info: Host: CICADA-DC; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb2-time: 
|   date: 2024-11-22T10:27:03
|_  start_date: N/A
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled and required
|_clock-skew: 7h00m01s

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 188.21 seconds

```

```
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose
Running (JUST GUESSING): Microsoft Windows 2022 (89%)
Aggressive OS guesses: Microsoft Windows Server 2022 (89%)
No exact OS matches for host (test conditions non-ideal).

OS detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 9.45 seconds

```

