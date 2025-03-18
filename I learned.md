# 🟩Active
- [ ] Look for SPN-enabled users when you get first set of credentials
- [ ] XML files was Windows' old way of handling local accounts in group policy. Not allowed in recent boxes (Groups.xml)
- [ ] Evil-winrm works on port 5985 (over HTTP)
	- [ ] use psexec if it doesn't work!
- [ ] if you get a non admin user, you can't get remote shell access with psexec, evil-winrm, etc. SO, use `/netonly` on windows to run commands as that user 
	- [ ] this is useful in listing shares and in running bloodhound ingestor!

# 🟨Busqueda
- [ ] if you find credentials or password. Use it on multiple users on multiple platforms. it could be the same person under the guise of different users.
- [ ] use `ls -la` FFS!!!!!! (after getting shell access)
- [ ] look at service related folders (after getting shell access)
	- [ ] apache folders
	- [ ] git folders
- [ ] look at services running internally!!!!! after getting shell access
- [ ] Since RAM is significantly faster than disk storage, you can use `/dev/shm` instead of `/tmp` for the performance boost

# 🟦ServMon
- [ ] use searchsploit on every service you find!
- [ ] use `https://` for https ports man!! come on 

# 🟩Administrator
- [ ] enumerate everything with every user
- [ ] use bloodhound asap!
- [ ] look for pathways to other users as well not just admin
- [ ] right click on user links in bloodhound to understand how to do that attack
- [ ] psexec will only work for admin level users
	- [ ] use (Evil-)WinRM for normal users

# 🟩 Forest
- [ ] msrpc service hints using rpcclient
- [ ] use rpcclient to enumerate when port 445 is open
- [ ] asreproast is an enum tactic to find users with pre-auth disabled
	- [ ] this can lead to dumping a hash and cracking it!!
- [ ] look at LDAP protocol in the nxc docs when dealing with LDAP
- [ ] find multiple ways to enumerate users
	- [ ] ldap
	- [ ] msrpc

# 🟨 Solidstate
- [ ] always google and understand all the services running
- [ ] use pspy to see what's running in the background

# 🟦 Chatterbox
**I HATE THIS BOX**


# 🟨 Poison
- [ ] use `ps auxw`
- [ ] use `netstat -an` on freebsd


# 🟩 Escape
- [ ] what is smb/ntlm relay attack
- [ ] xp_dirtree can be used to do an smb/ntlm relay attack
- [ ] impacket's responder AND smbserver can both be used to grab NTLM hash
- [ ] check out the logs of running services after getting access
- [ ] when SSL/LDAP (3269) is open, test for Certificate services
	- [ ] it's most likely a CA.

# 🟨 Jarvis
- [ ] use special chars fuzzing to find sql injection
- [ ] what is information schema
- [ ] using `limit` in sql injection to get information
- [ ] `group_concat` used to print multiple lines in sql injection
- [ ] `LOAD_FILE()` function to read files
- [ ] try switching up single/double quotations
- [ ] write files using SQLi (see INTO OUTFILE )
- [ ] `systemctl` doesn't like the `/tmp` directory
- [ ] command injection with `$(COMAMND)`

# 🟦 Heist
- [ ] if you come accross a cisco config file, check the password types
- [ ] manually enumerate the User's directories 
- [ ] how rpcclient does RID bruteforcing

# 🟦 Mailing
- [ ] look at Program Files (x86) as well (not just Program Files)
- [ ] use smtplib/swaks with smtp creds
- [ ] assume someone will click a link (if email service is running)

# 🟩 EscapeTwo
- [ ] learn what an xlsx file is like if it's not opening(with the xml stuff) 
	- [ ] it's just a zipped archive of xml files
- [ ] use xp_dirtree, xp_cmdshell in impacket-mssql
- [ ] use nxc with all services such as mssql, smb, winrm, etc

# 🟩 Certified
- [ ] learned shadow credential attack if you have `GenericWrite` over another user
- [ ] Gotta learn more about AD CS in depth
	- [ ] how certipy functions work
	- [ ] functions of pywhisker
	- [ ] what do pfx files entail
- [ ] 

# 🟩 Sauna
- [ ] use `username-anarchy` to create usernames (firstname lastname)
- [ ] what is kerbrute
- [ ] what is asreproast
- [ ] use winPEAS.ps1 to run winpeas on a target system to get creds
	- [ ] use winPEAS to see stored credentials because without local admin, can't run mimikatz
	- [ ] sensitive stuff on winpeas will be Red Highlight, Yellow Font!

# 🟩 Monteverde
**WATCH IPPSEC VIDEO AGAIN FOR FULL PRIVESC METHODOLOGY**
- [ ] do rpc null auth manually (try anon/null auth in a number of ways)
- [ ] use ldapsearch if absolutely no users, or try to list users with empty user/pass
- [ ] learned to use sqlcmd on powershell and PowerUpSQL
- [ ] learn to read and research well on what to do with exploit poc scripts
- [ ] look for identifiers of using Azure AD (Connect)
- [ ] learn to read ADSync database to get creds


# 🟦 Secnotes
- [ ] on a website if you see a contact us page or some field to send an "email", PHISH
	- [ ] put a test link and see if you get a hit on your python webserver
	- [ ] try change_pass.php with new passowrd parameters (use get instead of post request)
	- [ ] maybe upload a shell and send the link to get a hit?
	- [ ] *basically try to give a malicious link*
- [ ] if you can upload files to the webroot, try different ways to get a reverse shell
	- [ ] php-reverse-shell 
		- [ ] works if the webserver parses php
		- [ ] test it with a test php file
	- [ ] invoke-powershelltcp
	- [ ] webshell then nc.exe
- [ ] use `sudo rlwrap nc -lvnp LPORT` instead of `nc -lvnp LPORT`
- [ ] use manual and automated enumeration in Windows
	- [ ] build methodology for manual enum
	- [ ] look at WinPeas CAREFULLY (the colors have meaning bruh!)
	- [ ] there's def an interesting finding
- [ ] if you find WSL, enumerate the rootfs w/ Linux enum methodology
	- [ ] look at `.bash_history`


# 🟩 Timelapse
- [ ] don't provide any password when trying listing shares as Anonymous
	- [ ] you'll verify the anon/guest account exists but it won't list shares. Password could also be empty!
	- [ ] so try all permutations empty user, empty password, both empty, both random. 
- [ ] use Anonymous user for smb shares, other Guest users won't work even though nxc shows that they work
- [ ] USE `-S` FLAG IN evil-winRM command if it's over winRM over HTTPS!!!
- [ ] learned ReadLAPSPassword permission abuse, very easy on both windows and linux
	- [ ] even though the output will say something like DC01$, try the password shown with Administrator to verify. It actually was Administrator password smh bruhhhh
- [ ] 

# 🟩 Flight
- [ ] subdomain enum with different tools, try them all, be aware of the command args it's easy to mess up and waste time
- [ ] remember what OS you are using when doing LFI or whatevs. Different OS have different standard files and dirs
- [ ] on windows, if you can do an LFI or RFI, then the service will authenticate if you're asking it to include a file from SMB!
- [ ] when we can write to a share, we can try to put a malicous file that gives us a hash
	- [ ] use `ntlm_theft` from github
- [ ] use nc with webshell for windows, best results!
- [ ] using runasCs.exe instead of normal runas
	- [ ] runas normally prompts for password, can't do that in a reverse shell
	- [ ] RunasCs.exe will let you spawn a totally new shell with the new user you want
- [ ] TGT Delegation
	- [ ] what the flip is this even???

🟨 Dog
- [ ] use git-dumper to get all files and read them araam se
- [ ] use grep to look for some juicy creds or files
- [ ] read files from a code editor instead of using cat
- [ ] 