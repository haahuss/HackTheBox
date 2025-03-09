# Services
```
80 
	HTTP server
	Microsoft IIS httpd 10.0
	
445
	SMB
	--> do SMB enum

8808
	HTTP Server
	Microsoft IIS httpd 10.0
	
```

Find Open Ports:
```
sudo nmap 10.10.10.97 -p- -T5 -oA nmap/listopenports -Pn -n --disable-arp-ping

PORT     STATE SERVICE
80/tcp   open  http
445/tcp  open  microsoft-ds
8808/tcp open  ssports-bcast

```

List of open ports:
```
cat listopenports.nmap | grep open | grep tcp | cut -d "/" -f1 | tr "\n" ","

80,445,8808,
```

Full Scan:
```
sudo nmap 10.10.10.97 -p 80,445,8808, -A -oA fullscan 

PORT     STATE SERVICE      VERSION
80/tcp   open  http         Microsoft IIS httpd 10.0

445/tcp  open  microsoft-ds Microsoft Windows 7 - 10 microsoft-ds (workgroup: HTB)

8808/tcp open  http         Microsoft IIS httpd 10.0



Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose
Running (JUST GUESSING): Microsoft Windows 10|2019 (97%)
OS CPE: cpe:/o:microsoft:windows_10 cpe:/o:microsoft:windows_server_2019
Aggressive OS guesses: Microsoft Windows 10 1903 - 21H1 (97%), Windows Server 2019 (91%), Microsoft Windows 10 1803 (89%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 2 hops
Service Info: Host: SECNOTES; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_smb2-time: Protocol negotiation failed (SMB2)

TRACEROUTE (using port 80/tcp)
HOP RTT      ADDRESS
1   43.63 ms 10.10.14.1
2   43.81 ms 10.10.10.97

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 131.17 seconds

```


