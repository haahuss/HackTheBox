Find Open Ports:
```
sudo nmap TARGET -p- -T5 -oA listopenports -Pn -n --disable-arp-ping

# Nmap 7.94SVN scan initiated Sat Feb  1 00:15:24 2025 as: nmap -p- -T5 -oN nmap/listopenports -Pn admin.htb
Warning: 10.10.11.42 giving up on port because retransmission cap hit (2).
Nmap scan report for admin.htb (10.10.11.42)
Host is up (0.041s latency).
Not shown: 65509 closed tcp ports (reset)
PORT      STATE SERVICE
21/tcp    open  ftp
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
47001/tcp open  winrm
49664/tcp open  unknown
49665/tcp open  unknown
49666/tcp open  unknown
49667/tcp open  unknown
49668/tcp open  unknown
51339/tcp open  unknown
57954/tcp open  unknown
57965/tcp open  unknown
57970/tcp open  unknown
57973/tcp open  unknown
57986/tcp open  unknown

# Nmap done at Sat Feb  1 00:17:07 2025 -- 1 IP address (1 host up) scanned in 103.09 seconds

```

List of open ports:
```
cat listopenports.nmap | grep open | grep tcp | cut -d "/" -f1 | tr "\n" ","

21,53,88,135,139,389,445,464,593,636,3268,3269,5985,9389,47001,49664,49665,49666,49667,49668,51339,57954,57965,57970,57973,57986,
```

Full Scan:
```
sudo nmap TARGET -p PORTS -A -oA fullscan -Pn -n --disable-arp-ping

┌──(kali㉿kali)-[~/HackTheBox/administrator]
└─$ cat nmap/fullscan 
# Nmap 7.94SVN scan initiated Sat Feb  1 00:17:38 2025 as: nmap -A -oN nmap/fullscan -Pn -p 21,53,88,135,139,389,445,464,593,636,3268,3269,5985,9389,47001,49664,49665,49666,49667,49668,51339,57954,57965,57970,57973,57986, admin.htb
Nmap scan report for admin.htb (10.10.11.42)
Host is up (0.044s latency).

PORT      STATE SERVICE       VERSION
21/tcp    open  ftp           Microsoft ftpd
| ftp-syst: 
|_  SYST: Windows_NT
53/tcp    open  domain        Simple DNS Plus
88/tcp    open  kerberos-sec  Microsoft Windows Kerberos (server time: 2025-02-01 12:17:40Z)
135/tcp   open  msrpc         Microsoft Windows RPC
139/tcp   open  netbios-ssn   Microsoft Windows netbios-ssn
389/tcp   open  ldap          Microsoft Windows Active Directory LDAP (Domain: administrator.htb0., Site: Default-First-Site-Name)
445/tcp   open  microsoft-ds?
464/tcp   open  kpasswd5?
593/tcp   open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
636/tcp   open  tcpwrapped
3268/tcp  open  ldap          Microsoft Windows Active Directory LDAP (Domain: administrator.htb0., Site: Default-First-Site-Name)
3269/tcp  open  tcpwrapped
5985/tcp  open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
9389/tcp  open  mc-nmf        .NET Message Framing
47001/tcp open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
49664/tcp open  msrpc         Microsoft Windows RPC
49665/tcp open  msrpc         Microsoft Windows RPC
49666/tcp open  msrpc         Microsoft Windows RPC
49667/tcp open  msrpc         Microsoft Windows RPC
49668/tcp open  msrpc         Microsoft Windows RPC
51339/tcp open  msrpc         Microsoft Windows RPC
57954/tcp open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
57965/tcp open  msrpc         Microsoft Windows RPC
57970/tcp open  msrpc         Microsoft Windows RPC
57973/tcp open  msrpc         Microsoft Windows RPC
57986/tcp open  msrpc         Microsoft Windows RPC
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose
Running (JUST GUESSING): Microsoft Windows Vista|10|2022|2016|2012|2019|7|8.1|11|2008 (93%)
OS CPE: cpe:/o:microsoft:windows_vista::sp1 cpe:/o:microsoft:windows_10:1703 cpe:/o:microsoft:windows_server_2022 cpe:/o:microsoft:windows_server_2016 cpe:/o:microsoft:windows_server_2012 cpe:/o:microsoft:windows_7:::ultimate cpe:/o:microsoft:windows_8.1 cpe:/o:microsoft:windows_server_2008::sp2
Aggressive OS guesses: Microsoft Windows Vista SP1 (93%), Microsoft Windows 10 1703 (93%), Windows Server 2022 (93%), Microsoft Windows Server 2016 (93%), Microsoft Windows Server 2016 build 10586 - 14393 (93%), Microsoft Windows 10 1511 (92%), Microsoft Windows Server 2012 (92%), Microsoft Windows Server 2019 (92%), Microsoft Windows 10 1507 - 1607 (91%), Microsoft Windows 7, Windows Server 2012, or Windows 8.1 Update 1 (91%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 2 hops
Service Info: Host: DC; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_clock-skew: 6h59m54s
| smb2-time: 
|   date: 2025-02-01T12:18:52
|_  start_date: N/A
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled and required

TRACEROUTE (using port 445/tcp)
HOP RTT      ADDRESS
1   35.00 ms 10.10.14.1
2   35.41 ms admin.htb (10.10.11.42)

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sat Feb  1 00:19:06 2025 -- 1 IP address (1 host up) scanned in 87.67 seconds

```