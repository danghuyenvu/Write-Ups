[Support](https://app.hackthebox.com/machines/Support) is an Easy rated machine on HackTheBox
## Reconnaissance
```bash

```

```bash
smbclient --user=support.htb/anonymous --no-pass -L 10.129.31.87
```
![](../Images/Pasted%20image%2020260428093024.png)
![](../Images/Pasted%20image%2020260428093349.png)
```bash
nxc ldap IP -u ldap -p ldap_pass --users
```
Enumerate all users in the domain
![](../Images/Pasted%20image%2020260428140050.png)
```bash
ldapsearch -H LDAP://support.htb -x -b "dc=support,dc=htb" -D "ldap@support.htb" -W "*"
```
![](../Images/Pasted%20image%2020260428140956.png)
## Privilege Escalation