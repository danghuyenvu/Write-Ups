[Lookup]() Is an easy rated room on TryHackMe.
## Reconnaissance
Start with an Nmap scan:
```bash
nmap -sVC -vv -p- <IP> -T4 -oN nmap-full
```
![](../Images/Pasted%20image%2020260425164129.png)
Nmap scan reveals two open ports 22(SSH) and 80(Apache HTTP).
The http server resolves to `lookup.thm`, we add this to `/etc/hosts`.
Then I got dropped in a login page:

Tried fuzzing for some default credentials, I noticed that the error message is different for the user `admin`:
![](../Images/Pasted%20image%2020260425142314.png)
While others got:
![](../Images/Pasted%20image%2020260425142251.png)
This indicating the server has verbose error message vulnerability that exposed a valid credential (admin in this case). Since I've fuzzing for some time without getting blocked, I can use hydra to maybe bruteforce for valid password:
```bash
hydra -v -f -l admin -P /usr/share/wordlists/rockyou.txt lookup.thm http-post-form "/login.php:username=^USER^&password=^PASS^:F=Wrong password"
```
![](../Images/Pasted%20image%2020260425143758.png)
So here I got a pair `admin:password123`.
Tried use that to login, I got 
![](../Images/Pasted%20image%2020260425142251.png)
So for some reason the error message is different for this specific password.
I think this could be the behavior of the server that we got a valid username and valid password but they do not match.
So now I continue fuzzing for another valid username using hydra:
```bash
hydra -v -L /usr/share/wordlists/seclists/Usernames/Honeypot-Captures/multiplesources-users-fabian-fingerle.de.txt -p haha lookup.thm http-post-form "/login.php:username=^USER^&password=^PASS^:F=Wrong username or password" -o usernames.txt
```
![](../Images/Pasted%20image%2020260425151632.png)
Here we got `jose`. Try login with `jose:password123`. We succeed and got redirected to `files.lookup.thm`:
![](../Images/Pasted%20image%2020260425151514.png)
From the url I was able to identify that this is an elFinder instance, there are some known CVEs for it so gotta go find what the actual version is running.
![](../Images/Pasted%20image%2020260425152010.png)
We got elFinder version 2.1.47, searching online gives us CVE-2019-9194.
## [CVE-2019-9194](https://www.rapid7.com/db/modules/exploit/unix/webapp/elfinder_php_connector_exiftran_cmd_injection/)
This vulnerability affects elFinder version prior to 2.1.48.
"The PHP connector component allows unauthenticated users to upload
files and perform file modification operations, such as resizing and
rotation of an image. The file name of uploaded files is not validated,
allowing shell metacharacters.
When performing image operations on JPEG files, the filename is passed
to the `exiftran` utility without appropriate sanitization, causing
shell commands in the file name to be executed, resulting in remote
command injection as the web server user."
## Exploitation
For simplicity we can use Metasploit framework and configure as so:
![](../Images/Pasted%20image%2020260425152540.png)
We got the shell as www-data.
![](../Images/Pasted%20image%2020260425161210.png)
SUID check reveals a suspicious binary `/usr/sbin/pwm`, I cannot find any linux thingy related to this so it might be a user created binary.
We can kinda check the content by 
```bash
strings /usr/sbin/pwm
```
![](../Images/Pasted%20image%2020260425161247.png)
So here we see that it kinda run an id command to get current username and UID, then do something with that user's .passwords file. By checking `/home/think/` directory, I can also locate a `.passwords` file but I don't have read permission. So maybe we can achieve that through exploiting this.
Here we see the user would execute the `id` command, which suggests it might be vulnerable to $PATH injection.
So first I locate a directory I have write permission, in this case is `/var/tmp`.
We inject our shell script with name `id`:
```bash
#!/bin/bash
echo "echo uid=1000(think) gid=1000(think) groups=1000(think)"
```
Provide the execute permission, and then we inject `/var/tmp` into $PATH:
```bash
export PATH=/var/tmp:$PATH
```
Run the `/usr/sbin/pwm` again and I was able to read the content of `/home/think/.passwords`:
![](../Images/Pasted%20image%2020260425162612.png)
We can get this file to our machine and then bruteforce for correct password to ssh as `think`:
![](../Images/Pasted%20image%2020260425163037.png)
By running `sudo -l`, I saw that user `think` can run `/usr/bin/look` as any user:
![](../Images/Pasted%20image%2020260425163229.png)
So this binary allows us to read any files using:
```bash
sudo look '' /path/to/file
```
So I can easily abuse this and read the root flag:
![](../Images/Pasted%20image%2020260425163349.png)
Alternatively, we can use this to get root's sensitive data like private ssh keys to then authenticate as root user on the machine, or just read the `/etc/shadow` and crack the root's password.
