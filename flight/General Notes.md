
# IP
10.10.11.187

# Hostname


# Other Notes:



# Steps to Compromise:
1. Find an LFI, and do an SMB relay attack
	1. got svc_apache user/pass with Responder
2. Look at shares and users
3. Check password reuse with other users. Found s.moon
4. Enum shares with s.moon
	1. found write access to SHARED share
5. Try an NTLM relay on SHARED share using ntlm_theft scripts
	1. Got user c.bum hash with Responder
6. C.bum can write to a Web share, upload a PHP web shell and nc.exe to spawn a connection
	1. Got a shell as svc_apache
7. Enumerating more to find another internal web server
	1. C.bum can write to the web root of the internal webserver
	2. use runasCs to swith to c.bum user (**user.txt**)
8. Write an aspx shell to the webroot (development dir) of internal webserver
9. use chisel to port forward port 8000
10. spawn a connection with aspx shell
	1. got a shell as defaultapppool
	2. *why this user uses machine account for smb auth, is it builtin?*
	3. *what is this user?*
11. User Responder to get machine account hash
12. use shell with defaultapppool to request TGT (use rubeus too)
13. use TGT for TGT delegation: decode b64, kirbi2ccache, then impacket-secretsdump
14. get Admin hash, use impacket-psexec to get a shell.