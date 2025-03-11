# Services
```
22
	SSH
	login with credentials found

80
	HTTP
	try common web exploits
	found Backdrop CMS
	robots.txt
	
```

Find Open Ports:
```
sudo nmap TARGET -p- -T5 -oA nmap/listopenports -Pn

PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http

```

List of open ports:
```
cat listopenports.nmap | grep open | grep tcp | cut -d "/" -f1 | tr "\n" ","


```

Full Scan:
```
sudo nmap TARGET -p PORTS -A -oA nmap/fullscan -Pn


```


