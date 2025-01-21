Find Open Ports:
```
sudo nmap TARGET -p- -T5 -oA listopenports -Pn -n --disable-arp-ping

Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-01-20 14:17 EST
Warning: 10.10.11.28 giving up on port because retransmission cap hit (2).
Stats: 0:00:55 elapsed; 0 hosts completed (1 up), 1 undergoing Connect Scan
Connect Scan Timing: About 67.95% done; ETC: 14:18 (0:00:26 remaining)
Nmap scan report for sea.htb (10.10.11.28)
Host is up (0.043s latency).
Not shown: 65023 closed tcp ports (conn-refused), 510 filtered tcp ports (no-response)
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http

Nmap done: 1 IP address (1 host up) scanned in 82.11 seconds

```

List of open ports:
```
cat listopenports.nmap | grep open | grep tcp | cut -d "/" -f1 | tr "\n" ","

22,80

```

Full Scan:
```
sudo nmap TARGET -p PORTS -A -oA fullscan -Pn -n --disable-arp-ping

Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-01-20 14:19 EST
Nmap scan report for sea.htb (10.10.11.28)
Host is up (0.040s latency).

PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.11 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 e3:54:e0:72:20:3c:01:42:93:d1:66:9d:90:0c:ab:e8 (RSA)
|   256 f3:24:4b:08:aa:51:9d:56:15:3d:67:56:74:7c:20:38 (ECDSA)
|_  256 30:b1:05:c6:41:50:ff:22:a3:7f:41:06:0e:67:fd:50 (ED25519)
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
|_http-title: Sea - Home
|_http-server-header: Apache/2.4.41 (Ubuntu)
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Aggressive OS guesses: Linux 5.0 (97%), Linux 4.15 - 5.8 (96%), Linux 5.3 - 5.4 (95%), Linux 2.6.32 (95%), Linux 5.0 - 5.5 (95%), Linux 3.1 (95%), Linux 3.2 (95%), AXIS 210A or 211 Network Camera (Linux 2.6.17) (95%), ASUS RT-N56U WAP (Linux 3.4) (93%), Linux 3.16 (93%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 2 hops
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 22/tcp)
HOP RTT      ADDRESS
1   44.31 ms 10.10.14.1
2   44.85 ms sea.htb (10.10.11.28)

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 24.93 seconds

```