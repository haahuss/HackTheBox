# Services
```
80
	HTTP 

88
	kerberos, this is a DC

139/445
	SMB
	find shares, users


```

Find Open Ports:
```
sudo nmap TARGET -p- -T5 -oA nmap/listopenports -Pn

# Nmap 7.95 scan initiated Tue Mar 11 14:37:03 2025 as: /usr/lib/nmap/nmap -p- -T5 -oN nmap/listopenports -Pn 10.10.11.187
Nmap scan report for 10.10.11.187
Host is up (0.042s latency).
Not shown: 65517 filtered tcp ports (no-response)
PORT      STATE SERVICE
53/tcp    open  domain
80/tcp    open  http
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
9389/tcp  open  adws
49667/tcp open  unknown
49673/tcp open  unknown
49674/tcp open  unknown
49697/tcp open  unknown
49722/tcp open  unknown

# Nmap done at Tue Mar 11 14:38:24 2025 -- 1 IP address (1 host up) scanned in 81.71 seconds

```

List of open ports:
```
cat listopenports.nmap | grep open | grep tcp | cut -d "/" -f1 | tr "\n" ","


```

Full Scan:
```
sudo nmap TARGET -p PORTS -A -oA nmap/fullscan -Pn

# Nmap 7.95 scan initiated Tue Mar 11 14:39:07 2025 as: /usr/lib/nmap/nmap -A -oN nmap/fullscan -Pn -p 53,80,88,135,139,389,445,464,593,636,3268,3269,9389,49667,49673,49674,49697,49722, 10.10.11.187
Nmap scan report for flight.htb (10.10.11.187)
Host is up (0.039s latency).

PORT      STATE SERVICE       VERSION
53/tcp    open  domain        Simple DNS Plus
80/tcp    open  http          Apache httpd 2.4.52 ((Win64) OpenSSL/1.1.1m PHP/8.1.1)
|_http-title: g0 Aviation
| http-methods: 
|_  Potentially risky methods: TRACE
|_http-server-header: Apache/2.4.52 (Win64) OpenSSL/1.1.1m PHP/8.1.1
88/tcp    open  kerberos-sec  Microsoft Windows Kerberos (server time: 2025-03-12 01:39:15Z)
135/tcp   open  msrpc         Microsoft Windows RPC
139/tcp   open  netbios-ssn   Microsoft Windows netbios-ssn
389/tcp   open  ldap          Microsoft Windows Active Directory LDAP (Domain: flight.htb0., Site: Default-First-Site-Name)
445/tcp   open  microsoft-ds?
464/tcp   open  kpasswd5?
593/tcp   open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
636/tcp   open  tcpwrapped
3268/tcp  open  ldap          Microsoft Windows Active Directory LDAP (Domain: flight.htb0., Site: Default-First-Site-Name)
3269/tcp  open  tcpwrapped
9389/tcp  open  mc-nmf        .NET Message Framing
49667/tcp open  msrpc         Microsoft Windows RPC
49673/tcp open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
49674/tcp open  msrpc         Microsoft Windows RPC
49697/tcp open  msrpc         Microsoft Windows RPC
49722/tcp open  msrpc         Microsoft Windows RPC
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose
Running (JUST GUESSING): Microsoft Windows 2019|10 (97%)
OS CPE: cpe:/o:microsoft:windows_server_2019 cpe:/o:microsoft:windows_10
Aggressive OS guesses: Windows Server 2019 (97%), Microsoft Windows 10 1903 - 21H1 (91%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 2 hops
Service Info: Host: G0; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb2-time: 
|   date: 2025-03-12T01:40:24
|_  start_date: N/A
|_clock-skew: 7h00m00s
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled and required

TRACEROUTE (using port 53/tcp)
HOP RTT      ADDRESS
1   37.09 ms 10.10.14.1
2   37.64 ms flight.htb (10.10.11.187)

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Tue Mar 11 14:41:01 2025 -- 1 IP address (1 host up) scanned in 114.47 seconds

```


