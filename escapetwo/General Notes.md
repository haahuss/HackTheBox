
# IP
10.10.11.51

# Hostname
sequel.htb

# Other Notes




# Steps to Compromise:
1. got credentials in smb using rose (accounting department)
2. use `sa` user to find SQL ini config file
3. ryan has same password as sql_svc
4. ryan has writeowner perm on ca_svc
	1. change pw of ca_svc
5. ca_svc creds detect ESC4
	1. get admin cert via ESC4