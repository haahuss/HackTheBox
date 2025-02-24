
# IP
10.10.10.149

# Hostname
heist.htb

# Other Notes:
## Services
HTTP

SMB

WSMAN (allows us to remote)

MSRPC (rpclient)


# Steps to Compromise:
1. Found a config file with an md5 hash and two type 7 cisco passwords
2. tried Hazard user first because it was given in the website
3. found hazard password, no winrm access
4. use Hazard to do rid brute-force to find other users
5. check other users against passwords, found chase user
6. chase has remoting access, found user flag
7. there's Firefox process running
8. dump process info with `procdump64.exe`
9. found admin creds