# Services
```

```

Find Open Ports:
```
sudo nmap TARGET -p- -T5 -oA listopenports -Pn -n --disable-arp-ping

# Nmap 7.95 scan initiated Fri Mar  7 04:31:47 2025 as: /usr/lib/nmap/nmap -p- -T5 -oN nmap/listopenports -Pn -v 10.10.10.172
Nmap scan report for 10.10.10.172
Host is up (0.039s latency).
Not shown: 65516 filtered tcp ports (no-response)
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
9389/tcp  open  adws
49667/tcp open  unknown
49673/tcp open  unknown
49674/tcp open  unknown
49676/tcp open  unknown
49696/tcp open  unknown
49748/tcp open  unknown

Read data files from: /usr/share/nmap
# Nmap done at Fri Mar  7 04:32:47 2025 -- 1 IP address (1 host up) scanned in 60.21 seconds

```

List of open ports:
```
cat listopenports.nmap | grep open | grep tcp | cut -d "/" -f1 | tr "\n" ","


```

Full Scan:
```
sudo nmap TARGET -p PORTS -A -oA fullscan -Pn -n --disable-arp-ping

# Nmap 7.95 scan initiated Fri Mar  7 04:33:22 2025 as: /usr/lib/nmap/nmap -A -oN nmap/fullscan -Pn -p 53,88,135,139,389,445,464,593,636,3268,3269,5985,9389,49667,49673,49674,49676,49696,49748 10.10.10.172
Nmap scan report for 10.10.10.172
Host is up (0.033s latency).

PORT      STATE SERVICE       VERSION
53/tcp    open  domain        Simple DNS Plus
88/tcp    open  kerberos-sec  Microsoft Windows Kerberos (server time: 2025-03-07 07:25:38Z)
135/tcp   open  msrpc         Microsoft Windows RPC
139/tcp   open  netbios-ssn   Microsoft Windows netbios-ssn
389/tcp   open  ldap          Microsoft Windows Active Directory LDAP (Domain: MEGABANK.LOCAL0., Site: Default-First-Site-Name)
445/tcp   open  microsoft-ds?
464/tcp   open  kpasswd5?
593/tcp   open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
636/tcp   open  tcpwrapped
3268/tcp  open  ldap          Microsoft Windows Active Directory LDAP (Domain: MEGABANK.LOCAL0., Site: Default-First-Site-Name)
3269/tcp  open  tcpwrapped
5985/tcp  open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
9389/tcp  open  mc-nmf        .NET Message Framing
49667/tcp open  msrpc         Microsoft Windows RPC
49673/tcp open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
49674/tcp open  msrpc         Microsoft Windows RPC
49676/tcp open  msrpc         Microsoft Windows RPC
49696/tcp open  msrpc         Microsoft Windows RPC
49748/tcp open  msrpc         Microsoft Windows RPC
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose
Running (JUST GUESSING): Microsoft Windows 2019|10 (97%)
OS CPE: cpe:/o:microsoft:windows_server_2019 cpe:/o:microsoft:windows_10
Aggressive OS guesses: Windows Server 2019 (97%), Microsoft Windows 10 1903 - 21H1 (91%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 2 hops
Service Info: Host: MONTEVERDE; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled and required
|_clock-skew: -2h07m45s
| smb2-time: 
|   date: 2025-03-07T07:26:53
|_  start_date: N/A

TRACEROUTE (using port 135/tcp)
HOP RTT      ADDRESS
1   33.68 ms 10.10.14.1
2   32.86 ms 10.10.10.172

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Fri Mar  7 04:35:16 2025 -- 1 IP address (1 host up) scanned in 114.10 seconds

```


