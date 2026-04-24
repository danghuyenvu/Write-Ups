[AirTouch](https://app.hackthebox.com/machines/AirTouch) is a medium rated machine on HackTheBox.
## Reconnaissance
Start with an Nmap SYN scan on every port:
```bash
sudo nmap -sSVC -vv -p- <IP> -T4 -oN nmap-full
```
![](../Images/Pasted%20image%2020260421224116.png)
The Nmap TCP scan shows one port open. Tried fuzzing with some default credentials but failed. So we move on to UDP scan:
```bash
sudo nmap -sUV -vv <IP> -oN nmap-UDP
```
![](../Images/Pasted%20image%2020260421230614.png)
The UDP scans show 2 open ports:
- On port 68 is a DHCP client process.
- On port 161 is SNMP.
I think we gonna focus on the SNMP cause the DHCP one is not responding.
