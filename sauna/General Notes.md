
# IP
10.10.10.175

# Hostname
egotistical-bank.local

# Other Notes:



# Steps to Compromise:
1. found users of team on webserver
2. create list of usernames using `username-anarchy`
3. validate with Kerbrute
4. asreproast the usernames using `nxc` or `impacket-GetMPUsers`
5. get and crack fsmith hash
6. run bloodhound, 
	1. find svc_loanmgr has 
7. run winPEAS on fsmith winrm session
8. get password of svc_loanmgr, do DCsync with impacket-secretsdump
9. got admin hash
	1. got admin session with winRM

