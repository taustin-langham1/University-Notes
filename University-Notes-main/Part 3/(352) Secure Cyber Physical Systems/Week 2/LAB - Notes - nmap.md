

**identification**
```bash
nmap -sn -T5 - n 10.2.2.0/24
```

10.2.2.20/30/100 up
256 ip addresses (3 hosts up)

sn - No Port scan ! **ping scan**

T5 - timing template


**service scan**

service version
```bash
nmap -sV 10.2.2.30
```
service info: OS: Linux: CPE

service present
```bash
nmao -sC 10.2.2.30 / 20
```
30: 
**title for port 80** 403 Forbidden 
999 closed tcp ports
port 80/tcp open http
20:
1000 ports scanned - 1000 closed tcp ports
6901/tcp open jetstream

async with client ... as client
client.get


gitlab
sccc352