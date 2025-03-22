
# IP
10.10.10.172

# Hostname
MEGABANK.LOCAL

# Other Notes:



# Steps to Compromise:
1. Use `ldapsearch` or `nxc` to list users 
2. Found SABatchJobs creds (trying same user/pass combo)
	1. Enumerated shares, found a file with `mhope` creds
3. Got user.txt with `mhope`
4. Enumerate box to find Azure ADSync is running
5. Found `mhope` was part of Azure Admins group
6. Found ADSync database
7. Follow this POC to get domain admin credentials: https://www.sqlshack.com/connecting-powershell-to-sql-server/
8. Got shell and root.txt as domain admin