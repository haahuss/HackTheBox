# Services
```

```

Find Open Ports:
```
sudo nmap TARGET -p- -T5 -oA nmap/listopenports -Pn


```

List of open ports:
```
cat listopenports.nmap | grep open | grep tcp | cut -d "/" -f1 | tr "\n" ","


```

Full Scan:
```
sudo nmap TARGET -p PORTS -A -oA nmap/fullscan -Pn


```


