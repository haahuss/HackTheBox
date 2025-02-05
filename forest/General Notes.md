
# IP
10.10.10.161

# Hostname
htb.local
FOREST.htb.local

# Other Notes:



# Steps to Compromise:
1. use msrpc to enumerate users
2. asreproast to get users with kerberos pre auth required
3. got user svc-alfresco hash, cracked with hashcat (got user flag)
4. used svc-alfresco to run bloodhound
5. found attack path: svc-alfresco owns john that has dcsync on the domain
6. owned john and did dcsync w/ secretsdump
7. got admin hash and got admin flag