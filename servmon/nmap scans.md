Find Open Ports:
```
sudo nmap TARGET -p- -T5 -oA listopenports -Pn -n --disable-arp-ping

┌──(kali㉿kali)-[~/HTB/servmon.htb]
└─$ cat nmap/listopenports 
# Nmap 7.94 scan initiated Wed Jan 29 11:29:23 2025 as: nmap -p- -T5 -oN nmap/listopenports -Pn servmon.htb
Nmap scan report for servmon.htb (10.10.10.184)
Host is up (0.020s latency).
Not shown: 65518 closed tcp ports (reset)
PORT      STATE SERVICE
21/tcp    open  ftp
22/tcp    open  ssh
80/tcp    open  http
135/tcp   open  msrpc
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
5666/tcp  open  nrpe
6063/tcp  open  x11
6699/tcp  open  napster
8443/tcp  open  https-alt
49664/tcp open  unknown
49665/tcp open  unknown
49666/tcp open  unknown
49667/tcp open  unknown
49668/tcp open  unknown
49669/tcp open  unknown
49670/tcp open  unknown

# Nmap done at Wed Jan 29 11:29:44 2025 -- 1 IP address (1 host up) scanned in 20.12 seconds
                
```

List of open ports:
```
cat listopenports.nmap | grep open | grep tcp | cut -d "/" -f1 | tr "\n" ","

21,22,80,135,139,445,5666,6063,6699,8443,49664,49665,49666,49667,49668,49669,49670,
```

Full Scan:
```
sudo nmap TARGET -p PORTS -A -oA fullscan -Pn -n --disable-arp-ping

┌──(kali㉿kali)-[~/HTB/servmon.htb]
└─$ fullscan 21,22,80,135,139,445,5666,6063,6699,8443,49664,49665,49666,49667,49668,49669,49670, servmon.htb  
Starting Nmap 7.94 ( https://nmap.org ) at 2025-01-29 11:32 PST
Nmap scan report for servmon.htb (10.10.10.184)
Host is up (0.017s latency).

PORT      STATE SERVICE       VERSION
21/tcp    open  ftp           Microsoft ftpd
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_02-28-22  06:35PM       <DIR>          Users
| ftp-syst: 
|_  SYST: Windows_NT
22/tcp    open  ssh           OpenSSH for_Windows_8.0 (protocol 2.0)
| ssh-hostkey: 
|   3072 c7:1a:f6:81:ca:17:78:d0:27:db:cd:46:2a:09:2b:54 (RSA)
|   256 3e:63:ef:3b:6e:3e:4a:90:f3:4c:02:e9:40:67:2e:42 (ECDSA)
|_  256 5a:48:c8:cd:39:78:21:29:ef:fb:ae:82:1d:03:ad:af (ED25519)
80/tcp    open  http
|_http-title: Site doesn't have a title (text/html).
| fingerprint-strings: 
|   GetRequest, HTTPOptions, RTSPRequest: 
|     HTTP/1.1 200 OK
|     Content-type: text/html
|     Content-Length: 340
|     Connection: close
|     AuthInfo: 
|     <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
|     <html xmlns="http://www.w3.org/1999/xhtml">
|     <head>
|     <title></title>
|     <script type="text/javascript">
|     window.location.href = "Pages/login.htm";
|     </script>
|     </head>
|     <body>
|     </body>
|     </html>
|   NULL: 
|     HTTP/1.1 408 Request Timeout
|     Content-type: text/html
|     Content-Length: 0
|     Connection: close
|_    AuthInfo:
135/tcp   open  msrpc         Microsoft Windows RPC
139/tcp   open  netbios-ssn   Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds?
5666/tcp  open  tcpwrapped
6063/tcp  open  tcpwrapped
6699/tcp  open  napster?
8443/tcp  open  ssl/https-alt
| http-title: NSClient++
|_Requested resource was /index.html
|_ssl-date: TLS randomness does not represent time
| ssl-cert: Subject: commonName=localhost
| Not valid before: 2020-01-14T13:24:20
|_Not valid after:  2021-01-13T13:24:20
| fingerprint-strings: 
|   FourOhFourRequest, HTTPOptions, RTSPRequest, SIPOptions: 
|     HTTP/1.1 404
|     Content-Length: 18
|     Document not found
|   GetRequest: 
|     HTTP/1.1 302
|     Content-Length: 0
|     Location: /index.html
|     iday
|     :Saturday
|     workers
|_    jobs
49664/tcp open  msrpc         Microsoft Windows RPC
49665/tcp open  msrpc         Microsoft Windows RPC
49666/tcp open  msrpc         Microsoft Windows RPC
49667/tcp open  msrpc         Microsoft Windows RPC
49668/tcp open  msrpc         Microsoft Windows RPC
49669/tcp open  msrpc         Microsoft Windows RPC
49670/tcp open  msrpc         Microsoft Windows RPC
2 services unrecognized despite returning data. If you know the service/version, please submit the following fingerprints at https://nmap.org/cgi-bin/submit.cgi?new-service :
==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============
SF-Port80-TCP:V=7.94%I=7%D=1/29%Time=679A8246%P=aarch64-unknown-linux-gnu%
SF:r(NULL,6B,"HTTP/1\.1\x20408\x20Request\x20Timeout\r\nContent-type:\x20t
SF:ext/html\r\nContent-Length:\x200\r\nConnection:\x20close\r\nAuthInfo:\x
SF:20\r\n\r\n")%r(GetRequest,1B4,"HTTP/1\.1\x20200\x20OK\r\nContent-type:\
SF:x20text/html\r\nContent-Length:\x20340\r\nConnection:\x20close\r\nAuthI
SF:nfo:\x20\r\n\r\n\xef\xbb\xbf<!DOCTYPE\x20html\x20PUBLIC\x20\"-//W3C//DT
SF:D\x20XHTML\x201\.0\x20Transitional//EN\"\x20\"http://www\.w3\.org/TR/xh
SF:tml1/DTD/xhtml1-transitional\.dtd\">\r\n\r\n<html\x20xmlns=\"http://www
SF:\.w3\.org/1999/xhtml\">\r\n<head>\r\n\x20\x20\x20\x20<title></title>\r\
SF:n\x20\x20\x20\x20<script\x20type=\"text/javascript\">\r\n\x20\x20\x20\x
SF:20\x20\x20\x20\x20window\.location\.href\x20=\x20\"Pages/login\.htm\";\
SF:r\n\x20\x20\x20\x20</script>\r\n</head>\r\n<body>\r\n</body>\r\n</html>
SF:\r\n")%r(HTTPOptions,1B4,"HTTP/1\.1\x20200\x20OK\r\nContent-type:\x20te
SF:xt/html\r\nContent-Length:\x20340\r\nConnection:\x20close\r\nAuthInfo:\
SF:x20\r\n\r\n\xef\xbb\xbf<!DOCTYPE\x20html\x20PUBLIC\x20\"-//W3C//DTD\x20
SF:XHTML\x201\.0\x20Transitional//EN\"\x20\"http://www\.w3\.org/TR/xhtml1/
SF:DTD/xhtml1-transitional\.dtd\">\r\n\r\n<html\x20xmlns=\"http://www\.w3\
SF:.org/1999/xhtml\">\r\n<head>\r\n\x20\x20\x20\x20<title></title>\r\n\x20
SF:\x20\x20\x20<script\x20type=\"text/javascript\">\r\n\x20\x20\x20\x20\x2
SF:0\x20\x20\x20window\.location\.href\x20=\x20\"Pages/login\.htm\";\r\n\x
SF:20\x20\x20\x20</script>\r\n</head>\r\n<body>\r\n</body>\r\n</html>\r\n"
SF:)%r(RTSPRequest,1B4,"HTTP/1\.1\x20200\x20OK\r\nContent-type:\x20text/ht
SF:ml\r\nContent-Length:\x20340\r\nConnection:\x20close\r\nAuthInfo:\x20\r
SF:\n\r\n\xef\xbb\xbf<!DOCTYPE\x20html\x20PUBLIC\x20\"-//W3C//DTD\x20XHTML
SF:\x201\.0\x20Transitional//EN\"\x20\"http://www\.w3\.org/TR/xhtml1/DTD/x
SF:html1-transitional\.dtd\">\r\n\r\n<html\x20xmlns=\"http://www\.w3\.org/
SF:1999/xhtml\">\r\n<head>\r\n\x20\x20\x20\x20<title></title>\r\n\x20\x20\
SF:x20\x20<script\x20type=\"text/javascript\">\r\n\x20\x20\x20\x20\x20\x20
SF:\x20\x20window\.location\.href\x20=\x20\"Pages/login\.htm\";\r\n\x20\x2
SF:0\x20\x20</script>\r\n</head>\r\n<body>\r\n</body>\r\n</html>\r\n");
==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============
SF-Port8443-TCP:V=7.94%T=SSL%I=7%D=1/29%Time=679A824F%P=aarch64-unknown-li
SF:nux-gnu%r(GetRequest,74,"HTTP/1\.1\x20302\r\nContent-Length:\x200\r\nLo
SF:cation:\x20/index\.html\r\n\r\n\0\0\0\0\0\0\0\0\0\0iday\0\0\0\0:Saturda
SF:y\0\0\x12\x02\x18\0\x1aE\n\x07workers\x12\x0b\n\x04jobs\x12\x03\x18\xe2
SF:W\x12")%r(HTTPOptions,36,"HTTP/1\.1\x20404\r\nContent-Length:\x2018\r\n
SF:\r\nDocument\x20not\x20found")%r(FourOhFourRequest,36,"HTTP/1\.1\x20404
SF:\r\nContent-Length:\x2018\r\n\r\nDocument\x20not\x20found")%r(RTSPReque
SF:st,36,"HTTP/1\.1\x20404\r\nContent-Length:\x2018\r\n\r\nDocument\x20not
SF:\x20found")%r(SIPOptions,36,"HTTP/1\.1\x20404\r\nContent-Length:\x2018\
SF:r\n\r\nDocument\x20not\x20found");
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Aggressive OS guesses: Microsoft Windows Server 2019 (96%), Microsoft Windows 10 1709 - 1909 (93%), Microsoft Windows Server 2012 (93%), Microsoft Windows Vista SP1 (92%), Microsoft Windows Longhorn (92%), Microsoft Windows 10 1709 - 1803 (91%), Microsoft Windows 10 1809 - 2004 (91%), Microsoft Windows Server 2012 R2 (91%), Microsoft Windows Server 2012 R2 Update 1 (91%), Microsoft Windows Server 2016 build 10586 - 14393 (91%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 2 hops
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb2-time: 
|   date: 2025-01-29T19:34:16
|_  start_date: N/A
|_clock-skew: 1s
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled but not required

TRACEROUTE (using port 21/tcp)
HOP RTT      ADDRESS
1   17.24 ms 10.10.14.1
2   17.29 ms servmon.htb (10.10.10.184)

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host
```