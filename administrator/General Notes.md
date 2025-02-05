
# IP
10.10.11.42

# Hostname
admin.htb

# Other Notes:



# Steps to Compromise:
1. AD, FTP is running
2. Olivia doesn't have ftp access
3. look for users, found some
4. run bloodhound
5. we have permissions to change passwords for benjamin and michael, so changed it.
6. Benjamin had ftp access. there was a password safe. we used hashcat to crack it. it had passwords of 3 more users.
7. remoting into target with evil-winrm with emily to find flag.
8. found path to admin from emily
9. generic write to get ethan's hash
	1. crack the hash
10. dcsync w ethan to dump admin hashes