# Services
```
88          kerberos, DC
139/445     SMB share, enumerate everything users and shares
3269        maybe open no information, probably nothing but scan anyway when stuck
5986        allows winrm over HTTPS, research how to do that when we get creds. (remember to use -S flag because this is over HTTPS) 


clock skew exists, use "sudo ntpdate DCIP" later if clock skew error comes up
```

Find Open Ports:
```
sudo nmap TARGET -p- -T5 -oA nmap/listopenports -Pn

# Nmap 7.95 scan initiated Sun Mar  9 22:22:59 2025 as: /usr/lib/nmap/nmap -p- -T5 -oN nmap/listopenports -Pn 10.10.11.152
Nmap scan report for 10.10.11.152
Host is up (0.042s latency).
Not shown: 65518 filtered tcp ports (no-response)
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
5986/tcp  open  wsmans
9389/tcp  open  adws
49667/tcp open  unknown
49673/tcp open  unknown
49674/tcp open  unknown
49693/tcp open  unknown

# Nmap done at Sun Mar  9 22:24:19 2025 -- 1 IP address (1 host up) scanned in 79.94 seconds

```

List of open ports:
```
cat listopenports.nmap | grep open | grep tcp | cut -d "/" -f1 | tr "\n" ","


```

Full Scan:
```
sudo nmap TARGET -p PORTS -A -oA nmap/fullscan -Pn

# Nmap 7.95 scan initiated Sun Mar  9 22:26:01 2025 as: /usr/lib/nmap/nmap -A -oN nmap/fullscan -Pn -p 53,88,135,139,389,445,464,593,636,3268,3269,5986,9389,49667,49673,49674,49693, 10.10.11.152
Nmap scan report for timelapse.htb (10.10.11.152)
Host is up (0.12s latency).

PORT      STATE SERVICE           VERSION
53/tcp    open  domain            Simple DNS Plus
88/tcp    open  kerberos-sec      Microsoft Windows Kerberos (server time: 2025-03-10 10:26:07Z)
135/tcp   open  msrpc             Microsoft Windows RPC
139/tcp   open  netbios-ssn       Microsoft Windows netbios-ssn
389/tcp   open  ldap              Microsoft Windows Active Directory LDAP (Domain: timelapse.htb0., Site: Default-First-Site-Name)
445/tcp   open  microsoft-ds?
464/tcp   open  kpasswd5?
593/tcp   open  ncacn_http        Microsoft Windows RPC over HTTP 1.0
636/tcp   open  ldapssl?
3268/tcp  open  ldap              Microsoft Windows Active Directory LDAP (Domain: timelapse.htb0., Site: Default-First-Site-Name)
3269/tcp  open  globalcatLDAPssl?
5986/tcp  open  ssl/http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-title: Not Found
|_http-server-header: Microsoft-HTTPAPI/2.0
| tls-alpn: 
|_  http/1.1
| ssl-cert: Subject: commonName=dc01.timelapse.htb
| Not valid before: 2021-10-25T14:05:29
|_Not valid after:  2022-10-25T14:25:29
|_ssl-date: 2025-03-10T10:27:55+00:00; +7h59m58s from scanner time.
9389/tcp  open  mc-nmf            .NET Message Framing
49667/tcp open  msrpc             Microsoft Windows RPC
49673/tcp open  ncacn_http        Microsoft Windows RPC over HTTP 1.0
49674/tcp open  msrpc             Microsoft Windows RPC
49693/tcp open  msrpc             Microsoft Windows RPC
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose
Running (JUST GUESSING): Microsoft Windows 2019|10 (97%)
OS CPE: cpe:/o:microsoft:windows_server_2019 cpe:/o:microsoft:windows_10
Aggressive OS guesses: Windows Server 2019 (97%), Microsoft Windows 10 1903 - 21H1 (91%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 2 hops
Service Info: Host: DC01; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled and required
|_clock-skew: mean: 7h59m57s, deviation: 0s, median: 7h59m57s
| smb2-time: 
|   date: 2025-03-10T10:27:18
|_  start_date: N/A

TRACEROUTE (using port 445/tcp)
HOP RTT       ADDRESS
1   74.20 ms  10.10.16.1
2   161.53 ms timelapse.htb (10.10.11.152)

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sun Mar  9 22:27:58 2025 -- 1 IP address (1 host up) scanned in 116.89 seconds

```


