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

# 🟨 Solidstate
- [ ] always google all the services running
- [ ] 