
# IP
10.10.11.152

# Hostname
timelapse.htb

# Other Notes:



# Steps to Compromise:
1. Anon access to share: SHARES
2. Found a winrm_zip file. Had to crack the password to unzip
	1. Unzipped a password protected .pfx file
3. Cracked the .pfx file. 
4. Extracted the key and cert from pfx
5. WinRM using cert and key , **GOT USER ACCESS**
6. Looked at powershell history, found `svc_deploy` user creds
7. Ran bloodhound: found `svc_deploy` was in LAPS READERS group
8. read the password of the admin account using both linux and windows
9. verify creds and WinRM as Administrator, **GOT ROOT ACCESS!**