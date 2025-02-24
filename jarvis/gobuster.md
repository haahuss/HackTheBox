```
└─$ gobuster dir -u http://jarvis.htb/ --wordlist=/usr/share/seclists/Discovery/Web-Content/raft-medium-directories.txt -t 100
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://jarvis.htb/
[+] Method:                  GET
[+] Threads:                 100
[+] Wordlist:                /usr/share/seclists/Discovery/Web-Content/raft-medium-directories.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/fonts                (Status: 301) [Size: 308] [--> http://jarvis.htb/fonts/]
/phpmyadmin           (Status: 301) [Size: 313] [--> http://jarvis.htb/phpmyadmin/]
/css                  (Status: 301) [Size: 306] [--> http://jarvis.htb/css/]
/images               (Status: 301) [Size: 309] [--> http://jarvis.htb/images/]
/js                   (Status: 301) [Size: 305] [--> http://jarvis.htb/js/]
/server-status        (Status: 403) [Size: 275]
Progress: 23844 / 30001 (79.48%)[ERROR] parse "http://jarvis.htb/error\x1f_log": net/url: invalid control character in URL
Progress: 30000 / 30001 (100.00%)
===============================================================
Finished
===============================================================

```