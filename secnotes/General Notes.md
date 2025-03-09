
# IP
10.10.10.97

# Hostname
secnotes.htb

# Other Notes:



# Steps to Compromise:
1. register and login to secnotes
2. send change_pass w/ new creds to tyler on contact_us page **OR** try SQLi on login page
3. login as tyler on secnotes
4. get smb creds and login
5. tyler has access to new-site share
	1. this share is the web directory for port 8808 website
6. upload php, PHP works! get a rev shell for **USER ACCESS**
7. winPEAS shows WSL and the rootfs dir
8. navigate and enumerate WSL rootfs dir
9. see that bash_history has admin creds stored in it
10. use the creds with nxc, **GOT ADMIN ACCESS**
	1. login with PSEXEC (psexec gives )