Recon:
- nmap scans
- identify language of website
- feroxbuster, gobuster (recursive mode?), include extensions of website language
- find version, is there a CMS?

Initial Access
- find the CVE of the CMS version x.y.z
- execute the cve, make tweaks to the exploit
- get shell

Priv esc
- run linpeas
- look for local services running on local ports
- port forward the service to open on attacker browser
- inspect traffic with burp on attacker vm