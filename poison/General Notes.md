
# IP
10.10.10.84

# Hostname
poison.htb

# Other Notes:



# Steps to Compromise:
1. We can browse files from the web page. We found a `pwdbackup.txt` and `/etc/passwd`
2. From this we got access to `charix`
3. We found a `secret.zip` file in `/home/charix`
4. We found a VNC service running as `root` on the local interface
5. We port forward the VNC service and access it to get a `root` shell.