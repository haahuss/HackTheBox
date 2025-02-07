
# IP
10.10.10.51

# Hostname
solidstate.htb

# Other Notes:



# Steps to Compromise:
1. nmap scan reveals a James Server running
2. change mindy user's mail passwords in RPIC service (4555)
3. log in as mindy in pop3 service (110)
4. find credentials
5. get user access; escape rbash using -t option while ssh'ing
6. look for sensitive file /opt/tmp.py
7. mod