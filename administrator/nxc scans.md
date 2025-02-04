```
└─$ nxc smb administrator.htb -u 'Olivia' -p 'ichliebedich' --shares --log nxc-logs
SMB         10.10.11.42     445    DC               [*] Windows Server 2022 Build 20348 x64 (name:DC) (domain:administrator.htb) (signing:True) (SMBv1:False)
SMB         10.10.11.42     445    DC               [+] administrator.htb\Olivia:ichliebedich 
SMB         10.10.11.42     445    DC               [*] Enumerated shares
SMB         10.10.11.42     445    DC               Share           Permissions     Remark
SMB         10.10.11.42     445    DC               -----           -----------     ------
SMB         10.10.11.42     445    DC               ADMIN$                          Remote Admin
SMB         10.10.11.42     445    DC               C$                              Default share
SMB         10.10.11.42     445    DC               IPC$            READ            Remote IPC
SMB         10.10.11.42     445    DC               NETLOGON        READ            Logon server share 
SMB         10.10.11.42     445    DC               SYSVOL          READ            Logon server share 

```

```
└─$ nxc smb administrator.htb -u 'Olivia' -p 'ichliebedich' --users --log nxc-logs 
SMB         10.10.11.42     445    DC               [*] Windows Server 2022 Build 20348 x64 (name:DC) (domain:administrator.htb) (signing:True) (SMBv1:False)
SMB         10.10.11.42     445    DC               [+] administrator.htb\Olivia:ichliebedich 
SMB         10.10.11.42     445    DC               -Username-                    -Last PW Set-       -BadPW- -Description-                                 
SMB         10.10.11.42     445    DC               Administrator                 2024-10-22 18:59:36 0       Built-in account for administering the computer/domain
SMB         10.10.11.42     445    DC               Guest                         <never>             0       Built-in account for guest access to the computer/domain
SMB         10.10.11.42     445    DC               krbtgt                        2024-10-04 19:53:28 0       Key Distribution Center Service Account 
SMB         10.10.11.42     445    DC               olivia                        2024-10-06 01:22:48 0        
SMB         10.10.11.42     445    DC               michael                       2024-10-06 01:33:37 0        
SMB         10.10.11.42     445    DC               benjamin                      2024-10-06 01:34:56 0        
SMB         10.10.11.42     445    DC               emily                         2024-10-30 23:40:02 0        
SMB         10.10.11.42     445    DC               ethan                         2024-10-12 20:52:14 0        
SMB         10.10.11.42     445    DC               alexander                     2024-10-31 00:18:04 0        
SMB         10.10.11.42     445    DC               emma                          2024-10-31 00:18:35 0        
SMB         10.10.11.42     445    DC               [*] Enumerated 10 local users: ADMINISTRATOR

```

```

```

```

```

