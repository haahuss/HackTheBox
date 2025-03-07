# Services
```
80
	HTTP server running 
	Microsoft IIS httpd 10.0
	

88
	Kerberos, suggests this is a DC

139/445
	SMB

3269
	possible use of ADCS (not sure tho)

5985
	remote winrm over HTTP
```

Find Open Ports:
```
sudo nmap TARGET -p- -T5 -oA listopenports -Pn -n --disable-arp-ping

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
5985/tcp  open  wsman
9389/tcp  open  adws
49667/tcp open  unknown
49673/tcp open  unknown
49674/tcp open  unknown
49676/tcp open  unknown
49689/tcp open  unknown
49697/tcp open  unknown

```

List of open ports:
```
cat listopenports.nmap | grep open | grep tcp | cut -d "/" -f1 | tr "\n" ","

53,80,88,135,139,389,445,464,593,636,3268,3269,5985,9389,49667,49673,49674,49676,49689,49697,
```

Full Scan:
```
sudo nmap TARGET -p PORTS -A -oA fullscan -Pn -n --disable-arp-ping

PORT      STATE SERVICE       VERSION
53/tcp    open  domain        Simple DNS Plus

80/tcp    open  http          Microsoft IIS httpd 10.0
|_http-server-header: Microsoft-IIS/10.0
|_http-title: Egotistical Bank :: Home
| http-methods: 
|_  Potentially risky methods: TRACE

88/tcp    open  kerberos-sec  Microsoft Windows Kerberos (server time: 2025-03-07 03:38:33Z)

135/tcp   open  msrpc         Microsoft Windows RPC

139/tcp   open  netbios-ssn   Microsoft Windows netbios-ssn

389/tcp   open  ldap          Microsoft Windows Active Directory LDAP (Domain: EGOTISTICAL-BANK.LOCAL0., Site: Default-First-Site-Name)

445/tcp   open  microsoft-ds?

464/tcp   open  kpasswd5?

593/tcp   open  ncacn_http    Microsoft Windows RPC over HTTP 1.0

636/tcp   open  tcpwrapped

3268/tcp  open  ldap          Microsoft Windows Active Directory LDAP (Domain: EGOTISTICAL-BANK.LOCAL0., Site: Default-First-Site-Name)

3269/tcp  open  tcpwrapped

5985/tcp  open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found

9389/tcp  open  mc-nmf        .NET Message Framing
49667/tcp open  msrpc         Microsoft Windows RPC
49673/tcp open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
49674/tcp open  msrpc         Microsoft Windows RPC
49676/tcp open  msrpc         Microsoft Windows RPC
49689/tcp open  msrpc         Microsoft Windows RPC
49697/tcp open  msrpc         Microsoft Windows RPC

```


