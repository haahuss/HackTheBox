# Active
- [ ] Look for SPN-enabled users when you get first set of credentials
- [ ] XML files was Windows' old way of handling local accounts in group policy. Not allowed in recent boxes (Groups.xml)
- [ ] Evil-winrm works on port 5985 (over HTTP)
	- [ ] use psexec if it doesn't work!
- [ ] if you get a non admin user, you can't get remote shell access with psexec, evil-winrm, etc. SO, use `/netonly` on windows to run commands as that user 
	- [ ] this is useful in listing shares and in running bloodhound ingestor!



