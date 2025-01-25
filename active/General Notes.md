
# IP
10.10.10.100

# Hostname
active.htb

# Other Notes:



# Steps to Compromise:
1. find anon access to replciation share
2. found a groups.xml file with user creds
3. cracked password using gpp-decrypt
4. used user creds to enumerate spn users
5. admin is spn user
6. kerberoast admin to get hash
7. hashcat to crack hash
