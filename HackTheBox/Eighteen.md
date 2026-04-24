[Eighteen](https://app.hackthebox.com/machines/Eighteen) is an Easy rated machine on HackTheBox.
## Reconnaissance
Start with an Nmap SYN scan on all ports:
```bash
sudo nmap -sSVC -vv -p- <IP> -T4 -oN nmap-full
```
![](../Images/Pasted%20image%2020260421233326.png)
![](../Images/Pasted%20image%2020260421233342.png)
- On port 80 is a Microsoft IIS which then resolved to `eighteen.htb`.
- On port 1433 is a MSSQL server joined to a domain `EIGHTEEN`
![](../Images/Pasted%20image%2020260421233215.png)
The provided credentials cannot be used to login to this service. We try fuzzing for some credentials but the error message seems consistent.
Let's try create an account.
![](../Images/Pasted%20image%2020260421234757.png)
After login we got into a `/dashboard` page. There's an `Admin` button that then leads to `/admin` but we don't have enough privilege to access.
Moving on to the MSSQL Server on port 1433. We gonna use `Impacket/mssqclient` to interact with the server.
```bash
python3 mssqlclient.py EIGHTEEN/kevin@<IP>
```
And we were able to authenticate using the given credentials.
![](../Images/Pasted%20image%2020260422193222.png)
So by checking the impersonate permission, I know that the current user `kevin` is granted permission to impersonate `appdev`.
Checking out those databases, I noticed that the `financial_planner` database having a table called `users`:
![](../Images/Pasted%20image%2020260422195222.png)
Inside I found credentials for admin account:
![](../Images/Pasted%20image%2020260422195239.png)
The hash format is PBKDF2-HMAC-SHA256, which suggests an attempt to crack it offline using hashcat.
The key seems to be in hexadecimal, we need to convert it to base64 for hashcat to crack:
```bash
echo '0673ad90a0b4afb19d662336f0fce3a9edd0b7b19193717be28ce4d66c887133' | xxd -r -p | base64
```
The formatted string should look like:
![](../Images/Pasted%20image%2020260422224526.png)
```bash
hashcat -a 0 -d 5 pbkdf2-sha256.txt Tools/SecLists/Passwords/Leaked-Databases/rockyou.txt
```
The cracked password is `iloveyou1`:
![](../Images/Pasted%20image%2020260422224637.png)
We then can try bruteforcing RIDs for valid users:
```bash
nxc mssql 10.129.28.21 --local-auth -u kevin -p iNa2we6haRj2gaw! --rid-brute
```
![](../Images/Pasted%20image%2020260423102827.png)
Try password spraying to see if the cracked password matches any of these user's account.
![](../Images/Pasted%20image%2020260423103319.png)
And I were able to log in as user `adam.scott`.
So check group memberships by `whoami /groups`:
![](../Images/Pasted%20image%2020260423110037.png)
By loading `PowerSploit/PowerView` on the current user's Module path, I ran `Invoke-ACLScanner` to check for ACLs.
![](../Images/Pasted%20image%2020260423114012.png)
So adam has the rights to CreateChild in Staff OU. Researching online for some escalation techniques related, I found a technique called 'BadSuccessor'.
