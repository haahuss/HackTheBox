
# IP
10.10.11.41

# Hostname
certified.htb

# Other Notes:

judith ***writeowner*** Management Group ***GenericWrite*** management_svc ***GenericAll*** ca_operator

# Steps to Compromise:
1. judith ***writeowner*** Management Group
2. Management Group ***GenericWrite*** management_svc 
3. management_svc ***GenericAll*** ca_operator
4. use `ca_operator` creds to find vuln certificate
5. exploit ESC9