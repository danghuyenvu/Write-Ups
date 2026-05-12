Writeups for Labs in HTB Academy's Footprinting Module
# Easy Lab
Nmap scan result:
```bash
└──╼ [★]$ cat nmap-full 
# Nmap 7.94SVN scan initiated Wed May  6 10:34:10 2026 as: nmap -sVC -vv -p- -oN nmap-full 10.129.75.16
Nmap scan report for 10.129.75.16
Host is up, received reset ttl 63 (0.23s latency).
Scanned at 2026-05-06 10:34:10 CDT for 469s
Not shown: 65531 closed tcp ports (reset)
PORT     STATE SERVICE REASON         VERSION
21/tcp   open  ftp     syn-ack ttl 63
| fingerprint-strings: 
|   GenericLines: 
|     220 ProFTPD Server (ftp.int.inlanefreight.htb) [10.129.75.16]
|     Invalid command: try being more creative
|     Invalid command: try being more creative
|   NULL: 
|_    220 ProFTPD Server (ftp.int.inlanefreight.htb) [10.129.75.16]
22/tcp   open  ssh     syn-ack ttl 63 OpenSSH 8.2p1 Ubuntu 4ubuntu0.2 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 3f:4c:8f:10:f1:ae:be:cd:31:24:7c:a1:4e:ab:84:6d (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDa9RJRoAShv6FzLx23WYUh5z5vpaC1W0jTGGJuVfOVmOiwXu7d+eLRcf51dFwqe2J4OZ7z70w6Lrbm3RyKjNSZmY0ekPqbXyP0P6KqYn4eFdJkYp74zPUEvC/Y5U9gYmvCpoQ8gvqgAImYwhBXAlAmGDptcfRWRJ3KaRG/bbmfg0vsWqwYvDVfxEcCfbO1m7v6a9EiWELRTynHS26+oJbjY7tX5X05XMvj6L53JMWodHVsFf/vD4/qP2Ic0lafSBXuyKOcN5Tnx0DpExUwqj7GPLaM/ljG5LjF8y2yqZ85GeNQsgnsSxIL6dHiWkbUP4RXogUVI/prXLDU8307Wn/LWJQl3hxjJmunJfC5qw4a/JPLd9ydFSwadjYhztQoYIsSp41mr/wEVns8owxcKzBju74T9FptZ4I4UAzZLIWg1RJzpnJ7wpnFSUXFbvOa6V+nzeMesjYvKK1vx+UuNtrUuXPJm3BoYKjRJd2msog1KX4CguQNGZMS6LegiRIGde0=
|   256 7b:30:37:67:50:b9:ad:91:c0:8f:f7:02:78:3b:7c:02 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBNAdY+PFLa0XBlXCp3lL+mrrQKkU6bxWjDVEsljltzBYtugbDuER3AyIq1igFdgQPn+uKh5RtNQvPvX1Al8pA0Y=
|   256 88:9e:0e:07:fe:ca:d0:5c:60:ab:cf:10:99:cd:6c:a7 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIGKKM5saOYH/Fq3lWY1P4fchdWaH60Ib5/VQk6A00nAP
53/tcp   open  domain  syn-ack ttl 63 ISC BIND 9.16.1 (Ubuntu Linux)
| dns-nsid: 
|_  bind.version: 9.16.1-Ubuntu
2121/tcp open  ftp     syn-ack ttl 63
| fingerprint-strings: 
|   GenericLines: 
|     220 ProFTPD Server (Ceil\'s FTP) [10.129.75.16]
|     Invalid command: try being more creative
|     Invalid command: try being more creative
|   NULL: 
|_    220 ProFTPD Server (Ceil\'s FTP) [10.129.75.16]
2 services unrecognized despite returning data. If you know the service/version, please submit the following fingerprints at https://nmap.org/cgi-bin/submit.cgi?new-service :
==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============
SF-Port21-TCP:V=7.94SVN%I=7%D=5/6%Time=69FB60EC%P=x86_64-pc-linux-gnu%r(NU
SF:LL,3F,"220\x20ProFTPD\x20Server\x20\(ftp\.int\.inlanefreight\.htb\)\x20
SF:\[10\.129\.75\.16\]\r\n")%r(GenericLines,9B,"220\x20ProFTPD\x20Server\x
SF:20\(ftp\.int\.inlanefreight\.htb\)\x20\[10\.129\.75\.16\]\r\n500\x20Inv
SF:alid\x20command:\x20try\x20being\x20more\x20creative\r\n500\x20Invalid\
SF:x20command:\x20try\x20being\x20more\x20creative\r\n");
==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============
SF-Port2121-TCP:V=7.94SVN%I=7%D=5/6%Time=69FB60EC%P=x86_64-pc-linux-gnu%r(
SF:NULL,30,"220\x20ProFTPD\x20Server\x20\(Ceil's\x20FTP\)\x20\[10\.129\.75
SF:\.16\]\r\n")%r(GenericLines,8C,"220\x20ProFTPD\x20Server\x20\(Ceil's\x2
SF:0FTP\)\x20\[10\.129\.75\.16\]\r\n500\x20Invalid\x20command:\x20try\x20b
SF:eing\x20more\x20creative\r\n500\x20Invalid\x20command:\x20try\x20being\
SF:x20more\x20creative\r\n");
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Wed May  6 10:41:59 2026 -- 1 IP address (1 host up) scanned in 468.77 seconds
```
Tried SSH using given credentials:
```bash
└──╼ [★]$ ssh ceil@10.129.75.16
ceil@10.129.75.16: Permission denied (publickey).
```
So maybe the server requires publickey authentication.
Attempts to login to ftp using that credentials:
First attempt to login to ftp on default port using given credentials succeed, but `ls` shows nothing:
```bash
└──╼ [★]$ ftp ceil@10.129.75.16
Connected to 10.129.75.16.
220 ProFTPD Server (ftp.int.inlanefreight.htb) [10.129.75.16]
331 Password required for ceil
Password: 
230 User ceil logged in
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls -la
229 Entering Extended Passive Mode (|||20888|)
150 Opening ASCII mode data connection for file list
drwxr-xr-x   2 root     root         4096 Nov 10  2021 .
drwxr-xr-x   2 root     root         4096 Nov 10  2021 ..
226 Transfer complete
```
So I moved onto the ftp running on port 2121:
```bash
└──╼ [★]$ ftp
ftp> open 10.129.75.16 2121
Connected to 10.129.75.16.
220 ProFTPD Server (Ceil\'s FTP) [10.129.75.16]
Name (10.129.75.16:root): ceil
331 Password required for ceil
Password: 
230 User ceil logged in
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls -la
229 Entering Extended Passive Mode (|||49921|)
150 Opening ASCII mode data connection for file list
drwxr-xr-x   4 ceil     ceil         4096 Nov 10  2021 .
drwxr-xr-x   4 ceil     ceil         4096 Nov 10  2021 ..
-rw-------   1 ceil     ceil          294 Nov 10  2021 .bash_history
-rw-r--r--   1 ceil     ceil          220 Nov 10  2021 .bash_logout
-rw-r--r--   1 ceil     ceil         3771 Nov 10  2021 .bashrc
drwx------   2 ceil     ceil         4096 Nov 10  2021 .cache
-rw-r--r--   1 ceil     ceil          807 Nov 10  2021 .profile
drwx------   2 ceil     ceil         4096 Nov 10  2021 .ssh
-rw-------   1 ceil     ceil          759 Nov 10  2021 .viminfo
226 Transfer complete
```
So it's likely I'm in the home directory of user ceil. Maybe I can get ceil's privatekey then ssh into the machine.
```bash
ftp> get id_rsa
local: id_rsa remote: id_rsa
229 Entering Extended Passive Mode (|||2623|)
150 Opening BINARY mode data connection for id_rsa (3381 bytes)
100% |***********************************|  3381        1.45 MiB/s    00:00 ETA
226 Transfer complete
3381 bytes received in 00:00 (14.00 KiB/s)
```
SSH into the machine and get the flag in `/home/flag/flag.txt`:
```bash
ceil@NIXEASY:/home$ cd flag
ceil@NIXEASY:/home/flag$ cat flag.txt
HTB{7nrzise7hednrxihskjed7nzrgkweunj47zngrhdbkjhgdfbjkc7hgj}
```
# Medium Lab
Nmap scan result:
```bash
└──╼ [★]$ cat nmap-full 
# Nmap 7.94SVN scan initiated Wed May  6 20:59:02 2026 as: nmap -sV -sC -vv -p- --min-rate 5000 -oN nmap-full 10.129.202.41
Nmap scan report for 10.129.202.41
Host is up, received reset ttl 127 (0.24s latency).
Scanned at 2026-05-06 20:59:03 CDT for 130s
Not shown: 65519 closed tcp ports (reset)
PORT      STATE SERVICE       REASON          VERSION
111/tcp   open  rpcbind       syn-ack ttl 127 2-4 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2,3,4        111/tcp   rpcbind
|   100000  2,3,4        111/tcp6  rpcbind
|   100000  2,3,4        111/udp   rpcbind
|   100000  2,3,4        111/udp6  rpcbind
|   100003  2,3         2049/udp   nfs
|   100003  2,3         2049/udp6  nfs
|   100003  2,3,4       2049/tcp   nfs
|   100003  2,3,4       2049/tcp6  nfs
|   100005  1,2,3       2049/tcp   mountd
|   100005  1,2,3       2049/tcp6  mountd
|   100005  1,2,3       2049/udp   mountd
|   100005  1,2,3       2049/udp6  mountd
|   100021  1,2,3,4     2049/tcp   nlockmgr
|   100021  1,2,3,4     2049/tcp6  nlockmgr
|   100021  1,2,3,4     2049/udp   nlockmgr
|   100021  1,2,3,4     2049/udp6  nlockmgr
|   100024  1           2049/tcp   status
|   100024  1           2049/tcp6  status
|   100024  1           2049/udp   status
|_  100024  1           2049/udp6  status
135/tcp   open  msrpc         syn-ack ttl 127 Microsoft Windows RPC
139/tcp   open  netbios-ssn   syn-ack ttl 127 Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds? syn-ack ttl 127
2049/tcp  open  nlockmgr      syn-ack ttl 127 1-4 (RPC #100021)
3389/tcp  open  ms-wbt-server syn-ack ttl 127 Microsoft Terminal Services
|_ssl-date: 2026-05-07T02:00:25+00:00; 0s from scanner time.
| rdp-ntlm-info: 
|   Target_Name: WINMEDIUM
|   NetBIOS_Domain_Name: WINMEDIUM
|   NetBIOS_Computer_Name: WINMEDIUM
|   DNS_Domain_Name: WINMEDIUM
|   DNS_Computer_Name: WINMEDIUM
|   Product_Version: 10.0.17763
|_  System_Time: 2026-05-07T02:00:16+00:00
| ssl-cert: Subject: commonName=WINMEDIUM
| Issuer: commonName=WINMEDIUM
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2026-05-06T00:47:11
| Not valid after:  2026-11-05T00:47:11
| MD5:   f4cf:5e75:3307:0df6:9801:49e0:3785:1604
| SHA-1: a582:57a6:1042:8b25:56fe:ee1f:9b12:8122:517c:9fd6
| -----BEGIN CERTIFICATE-----
| MIIC1jCCAb6gAwIBAgIQYxps+aM+wK1As7xTGRFP1zANBgkqhkiG9w0BAQsFADAU
| MRIwEAYDVQQDEwlXSU5NRURJVU0wHhcNMjYwNTA2MDA0NzExWhcNMjYxMTA1MDA0
| NzExWjAUMRIwEAYDVQQDEwlXSU5NRURJVU0wggEiMA0GCSqGSIb3DQEBAQUAA4IB
| DwAwggEKAoIBAQDKSZOaj2/Ulx4zAJ8hf/6eJSEhQcwI5hYgjDbpBBRE1yxH/V5E
| RSpFpjBaJA1rXuEd/+pmp/ntboNQ8I53mEnDhGaQ76RwWJQFoZA7bB+mpu63gn/g
| N8AbU6iVtcjikZ+cFeBVwE1LFpCobkiX/B/kTM56KQMTN3e0YZGahjcSgZsEnEwy
| HY+A7nOsq2vGFK0uKwBeLFXoDnGBvm/1XPn+nFMFx0/fp0eLs2Z1ijlyHFmJAO/Z
| vum8IsFzmeG8NuafTmKiR/bf6sKHfU2Ab2BocfNiKsU4xxl9JPsoUUzY4Ezt5bgz
| d959voZLEa8WnoxcNBWRJXRBqu9AxO3d2PrJAgMBAAGjJDAiMBMGA1UdJQQMMAoG
| CCsGAQUFBwMBMAsGA1UdDwQEAwIEMDANBgkqhkiG9w0BAQsFAAOCAQEAZYi47P1X
| sDLewv9fxyS14UX4VB5gpH8f5LhKirP1YFGxJ2RrBfVATpyWJs4U/Ui/CqTnZs5l
| MAaI5TT9qhUL0Olu0syjo/UNjzko0zovfb/mzhlDhaZxECUcBUSpelR1AgsSQA/j
| Pmt8MpYctzcXVueZKWniGE/SMXl8MkYUmfsXiMg5OeU37hvD3a6jHfHfdjVzp5OE
| bIHXPSqxmbjXbjn40luKgZysRDq01N3b6+uhlMESTmuuo+tVZ9OjverBFGdZbnmy
| NvLcT97gupj0Uvx5e8lKozZRJ2FR3DfSULMAPJB35B2pWkI35lsZSdEUxntGHW1q
| cIcNh25ya2fDSQ==
|_-----END CERTIFICATE-----
5985/tcp  open  http          syn-ack ttl 127 Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-title: Not Found
|_http-server-header: Microsoft-HTTPAPI/2.0
47001/tcp open  http          syn-ack ttl 127 Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-title: Not Found
|_http-server-header: Microsoft-HTTPAPI/2.0
49664/tcp open  msrpc         syn-ack ttl 127 Microsoft Windows RPC
49665/tcp open  msrpc         syn-ack ttl 127 Microsoft Windows RPC
49666/tcp open  msrpc         syn-ack ttl 127 Microsoft Windows RPC
49667/tcp open  msrpc         syn-ack ttl 127 Microsoft Windows RPC
49668/tcp open  msrpc         syn-ack ttl 127 Microsoft Windows RPC
49679/tcp open  msrpc         syn-ack ttl 127 Microsoft Windows RPC
49680/tcp open  msrpc         syn-ack ttl 127 Microsoft Windows RPC
49681/tcp open  msrpc         syn-ack ttl 127 Microsoft Windows RPC
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2026-05-07T02:00:16
|_  start_date: N/A
| p2p-conficker: 
|   Checking for Conficker.C or higher...
|   Check 1 (port 47689/tcp): CLEAN (Couldn\'t connect)
|   Check 2 (port 32042/tcp): CLEAN (Couldn\'t connect)
|   Check 3 (port 28088/udp): CLEAN (Failed to receive data)
|   Check 4 (port 51367/udp): CLEAN (Timeout)
|_  0/4 checks are positive: Host is CLEAN or ports are blocked
|_clock-skew: mean: 0s, deviation: 0s, median: 0s

Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Wed May  6 21:01:13 2026 -- 1 IP address (1 host up) scanned in 130.82 seconds
```
Checking the NFS service:
```bash
└──╼ [★]$ showmount -e 10.129.81.113
Export list for 10.129.81.113:
/TechSupport (everyone)
```
Create mount point and mount the share:
```bash
sudo mount -t nfs <IP>:/TechSupport mnt-point -o nolock
```
In order to access the share, `su` to root.
![](../Images/Pasted%20image%2020260512104236.png)
Inspect the only file that is larger than 0:
![](../Images/Pasted%20image%2020260512104322.png)
Got the credentials for user alex. Try use this to list smb shares since the previous nmap scan reveals smb on this machine too:
```bash
└──╼ [★]$ nxc smb 10.129.202.41 -u 'alex' -p 'lol123!mD' --shares
SMB         10.129.202.41   445    WINMEDIUM        [*] Windows 10 / Server 2019 Build 17763 x64 (name:WINMEDIUM) (domain:WINMEDIUM) (signing:False) (SMBv1:False)
SMB         10.129.202.41   445    WINMEDIUM        [+] WINMEDIUM\alex:lol123!mD
SMB         10.129.202.41   445    WINMEDIUM        [*] Enumerated shares
SMB         10.129.202.41   445    WINMEDIUM        Share           Permissions     Remark
SMB         10.129.202.41   445    WINMEDIUM        -----           -----------     ------
SMB         10.129.202.41   445    WINMEDIUM        ADMIN$                          Remote Admin
SMB         10.129.202.41   445    WINMEDIUM        C$                              Default share
SMB         10.129.202.41   445    WINMEDIUM        devshare        READ,WRITE  
SMB         10.129.202.41   445    WINMEDIUM        IPC$            READ            Remote IPC
SMB         10.129.202.41   445    WINMEDIUM        Users           READ
```
There is an unusual share called `devshare` let's access it and see what's in there
```bash
└──╼ [★]$ smbclient //10.129.202.41/devshare -U 'alex'
Password for [WORKGROUP\alex]:
Try "help" to get a list of possible commands.
smb: \> ls 
  .                                   D        0  Mon May 11 22:49:30 2026
  ..                                  D        0  Mon May 11 22:49:30 2026
  important.txt                       A       16  Wed Nov 10 10:12:55 2021

		6367231 blocks of size 4096. 2590138 blocks available
smb: \>
```
There's a file called `important.txt`, checking the content, I see a credential for user `sa`:
```
sa:87N1ns@slls83
```
Now that I've found 2 credentials (alex and sa), I tried rdp to the machine but only alex account succeed:
```bash
xfreerdp /v:10.129.81.113 /u:alex /p:'lol123!mD'
```
![](../Images/Pasted%20image%2020260512110751.png)
Here I saw an SSMS instance, let's try access it.
![](../Images/Pasted%20image%2020260512110907.png)
Used the password for user `sa`, but login failed. Then I tried run the SSMS as administrator:
![](../Images/Pasted%20image%2020260512111226.png)
Found an interesting table inside `accounts` database.
We can try if HTB is inside by executing a simple query:
![](../Images/Pasted%20image%2020260512111448.png)
# Hard Lab
Nmap scan:
```bash
nmap -sVC -vv -p- <IP> -oN nmap-full
└──╼ [★]$ cat nmap-full
# Nmap 7.94SVN scan initiated Tue May 12 08:05:26 2026 as: nmap -sVC -vv -p- -oN nmap-full 10.129.202.20
Nmap scan report for 10.129.202.20
Host is up, received echo-reply ttl 63 (0.24s latency).
Scanned at 2026-05-12 08:05:27 CDT for 237s
Not shown: 65530 closed tcp ports (reset)
PORT    STATE SERVICE  REASON         VERSION
22/tcp  open  ssh      syn-ack ttl 63 OpenSSH 8.2p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 3f:4c:8f:10:f1:ae:be:cd:31:24:7c:a1:4e:ab:84:6d (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDa9RJRoAShv6FzLx23WYUh5z5vpaC1W0jTGGJuVfOVmOiwXu7d+eLRcf51dFwqe2J4OZ7z70w6Lrbm3RyKjNSZmY0ekPqbXyP0P6KqYn4eFdJkYp74zPUEvC/Y5U9gYmvCpoQ8gvqgAImYwhBXAlAmGDptcfRWRJ3KaRG/bbmfg0vsWqwYvDVfxEcCfbO1m7v6a9EiWELRTynHS26+oJbjY7tX5X05XMvj6L53JMWodHVsFf/vD4/qP2Ic0lafSBXuyKOcN5Tnx0DpExUwqj7GPLaM/ljG5LjF8y2yqZ85GeNQsgnsSxIL6dHiWkbUP4RXogUVI/prXLDU8307Wn/LWJQl3hxjJmunJfC5qw4a/JPLd9ydFSwadjYhztQoYIsSp41mr/wEVns8owxcKzBju74T9FptZ4I4UAzZLIWg1RJzpnJ7wpnFSUXFbvOa6V+nzeMesjYvKK1vx+UuNtrUuXPJm3BoYKjRJd2msog1KX4CguQNGZMS6LegiRIGde0=
|   256 7b:30:37:67:50:b9:ad:91:c0:8f:f7:02:78:3b:7c:02 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBNAdY+PFLa0XBlXCp3lL+mrrQKkU6bxWjDVEsljltzBYtugbDuER3AyIq1igFdgQPn+uKh5RtNQvPvX1Al8pA0Y=
|   256 88:9e:0e:07:fe:ca:d0:5c:60:ab:cf:10:99:cd:6c:a7 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIGKKM5saOYH/Fq3lWY1P4fchdWaH60Ib5/VQk6A00nAP
110/tcp open  pop3     syn-ack ttl 63 Dovecot pop3d
|_pop3-capabilities: CAPA USER UIDL RESP-CODES STLS SASL(PLAIN) PIPELINING TOP AUTH-RESP-CODE
|_ssl-date: TLS randomness does not represent time
| ssl-cert: Subject: commonName=NIXHARD
| Subject Alternative Name: DNS:NIXHARD
| Issuer: commonName=NIXHARD
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2021-11-10T01:30:25
| Not valid after:  2031-11-08T01:30:25
| MD5:   2b45:ec3c:508f:3cfb:9f6a:750c:63f8:2077
| SHA-1: ed43:7d5a:3c46:54ac:9902:8dc4:9d86:6efb:2ae3:357c
| -----BEGIN CERTIFICATE-----
| MIIC0zCCAbugAwIBAgIUC6tYfrtqQqCrhjYv11bUtaKet3EwDQYJKoZIhvcNAQEL
| BQAwEjEQMA4GA1UEAwwHTklYSEFSRDAeFw0yMTExMTAwMTMwMjVaFw0zMTExMDgw
| MTMwMjVaMBIxEDAOBgNVBAMMB05JWEhBUkQwggEiMA0GCSqGSIb3DQEBAQUAA4IB
| DwAwggEKAoIBAQDEBpDfkH4Ro5ZXW44NvnF3N9lKz27V1hgRppyUk5y/SEPKt2zj
| EU+r2tEHUeHoJHQZBbW0ybxh+X2H3ZPNEG9nV1GtFQfTBVcrUEpN5VV15aIbdh+q
| j53pp/wcL/d8+Zg2ZAaVYWvQHVqtsAudQmynrV1MHA39A44fG3/SutKlurY8AKR0
| MW5zMPtflMc/N3+lH8UUMBf2Q+zNSyZLiBEihxK3kfMW92HqWeh016egSIFuxUsH
| kk4xpGmyG9NDYna47dQzoHCg+42KgqFvWrGw2nIccaEIX5XA8rU9u53C7EQzDzmQ
| vAtHpKWBwNmiivxAz/QC7MPExWIWtZtOqxmfAgMBAAGjITAfMAkGA1UdEwQCMAAw
| EgYDVR0RBAswCYIHTklYSEFSRDANBgkqhkiG9w0BAQsFAAOCAQEAG+Dm9pLJgNGC
| X1YmznmtBUekhXMrU67tQl745fFasJQzIrDgVtK27fjAtQRwvIbDruSwTj47E7+O
| XdS7qyjFNBerklWNq4fEAVI7BmkxnTS9542okA/+UmeG70LdKjzFS+LjjOnyWzTh
| YwU8uUjLfnRca74kY0DkVHOIkwZQha0J+BrKSADq/zDjkG0g4v0vzHINOmHx9eiE
| 67NoJKJPY5S3RYWxl/4x8Kphx7PNJBPC75gYjlxxDhxdYu9a3daqJUa58/qOm6P8
| w1P9nA6lkg7NopyqepulLAzIcqnTjb/nMD2Pd9b6vgWc3IqSfFreqjzshZ+FjNZo
| zR+tR6z4TQ==
|_-----END CERTIFICATE-----
143/tcp open  imap     syn-ack ttl 63 Dovecot imapd (Ubuntu)
|_imap-capabilities: more ENABLE have SASL-IR LOGIN-REFERRALS post-login AUTH=PLAINA0001 listed LITERAL+ ID Pre-login IMAP4rev1 capabilities IDLE OK STARTTLS
| ssl-cert: Subject: commonName=NIXHARD
| Subject Alternative Name: DNS:NIXHARD
| Issuer: commonName=NIXHARD
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2021-11-10T01:30:25
| Not valid after:  2031-11-08T01:30:25
| MD5:   2b45:ec3c:508f:3cfb:9f6a:750c:63f8:2077
| SHA-1: ed43:7d5a:3c46:54ac:9902:8dc4:9d86:6efb:2ae3:357c
| -----BEGIN CERTIFICATE-----
| MIIC0zCCAbugAwIBAgIUC6tYfrtqQqCrhjYv11bUtaKet3EwDQYJKoZIhvcNAQEL
| BQAwEjEQMA4GA1UEAwwHTklYSEFSRDAeFw0yMTExMTAwMTMwMjVaFw0zMTExMDgw
| MTMwMjVaMBIxEDAOBgNVBAMMB05JWEhBUkQwggEiMA0GCSqGSIb3DQEBAQUAA4IB
| DwAwggEKAoIBAQDEBpDfkH4Ro5ZXW44NvnF3N9lKz27V1hgRppyUk5y/SEPKt2zj
| EU+r2tEHUeHoJHQZBbW0ybxh+X2H3ZPNEG9nV1GtFQfTBVcrUEpN5VV15aIbdh+q
| j53pp/wcL/d8+Zg2ZAaVYWvQHVqtsAudQmynrV1MHA39A44fG3/SutKlurY8AKR0
| MW5zMPtflMc/N3+lH8UUMBf2Q+zNSyZLiBEihxK3kfMW92HqWeh016egSIFuxUsH
| kk4xpGmyG9NDYna47dQzoHCg+42KgqFvWrGw2nIccaEIX5XA8rU9u53C7EQzDzmQ
| vAtHpKWBwNmiivxAz/QC7MPExWIWtZtOqxmfAgMBAAGjITAfMAkGA1UdEwQCMAAw
| EgYDVR0RBAswCYIHTklYSEFSRDANBgkqhkiG9w0BAQsFAAOCAQEAG+Dm9pLJgNGC
| X1YmznmtBUekhXMrU67tQl745fFasJQzIrDgVtK27fjAtQRwvIbDruSwTj47E7+O
| XdS7qyjFNBerklWNq4fEAVI7BmkxnTS9542okA/+UmeG70LdKjzFS+LjjOnyWzTh
| YwU8uUjLfnRca74kY0DkVHOIkwZQha0J+BrKSADq/zDjkG0g4v0vzHINOmHx9eiE
| 67NoJKJPY5S3RYWxl/4x8Kphx7PNJBPC75gYjlxxDhxdYu9a3daqJUa58/qOm6P8
| w1P9nA6lkg7NopyqepulLAzIcqnTjb/nMD2Pd9b6vgWc3IqSfFreqjzshZ+FjNZo
| zR+tR6z4TQ==
|_-----END CERTIFICATE-----
|_ssl-date: TLS randomness does not represent time
993/tcp open  ssl/imap syn-ack ttl 63 Dovecot imapd (Ubuntu)
|_ssl-date: TLS randomness does not represent time
|_imap-capabilities: more ENABLE SASL-IR LOGIN-REFERRALS LITERAL+ AUTH=PLAINA0001 post-login listed ID Pre-login IMAP4rev1 capabilities IDLE OK have
| ssl-cert: Subject: commonName=NIXHARD
| Subject Alternative Name: DNS:NIXHARD
| Issuer: commonName=NIXHARD
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2021-11-10T01:30:25
| Not valid after:  2031-11-08T01:30:25
| MD5:   2b45:ec3c:508f:3cfb:9f6a:750c:63f8:2077
| SHA-1: ed43:7d5a:3c46:54ac:9902:8dc4:9d86:6efb:2ae3:357c
| -----BEGIN CERTIFICATE-----
| MIIC0zCCAbugAwIBAgIUC6tYfrtqQqCrhjYv11bUtaKet3EwDQYJKoZIhvcNAQEL
| BQAwEjEQMA4GA1UEAwwHTklYSEFSRDAeFw0yMTExMTAwMTMwMjVaFw0zMTExMDgw
| MTMwMjVaMBIxEDAOBgNVBAMMB05JWEhBUkQwggEiMA0GCSqGSIb3DQEBAQUAA4IB
| DwAwggEKAoIBAQDEBpDfkH4Ro5ZXW44NvnF3N9lKz27V1hgRppyUk5y/SEPKt2zj
| EU+r2tEHUeHoJHQZBbW0ybxh+X2H3ZPNEG9nV1GtFQfTBVcrUEpN5VV15aIbdh+q
| j53pp/wcL/d8+Zg2ZAaVYWvQHVqtsAudQmynrV1MHA39A44fG3/SutKlurY8AKR0
| MW5zMPtflMc/N3+lH8UUMBf2Q+zNSyZLiBEihxK3kfMW92HqWeh016egSIFuxUsH
| kk4xpGmyG9NDYna47dQzoHCg+42KgqFvWrGw2nIccaEIX5XA8rU9u53C7EQzDzmQ
| vAtHpKWBwNmiivxAz/QC7MPExWIWtZtOqxmfAgMBAAGjITAfMAkGA1UdEwQCMAAw
| EgYDVR0RBAswCYIHTklYSEFSRDANBgkqhkiG9w0BAQsFAAOCAQEAG+Dm9pLJgNGC
| X1YmznmtBUekhXMrU67tQl745fFasJQzIrDgVtK27fjAtQRwvIbDruSwTj47E7+O
| XdS7qyjFNBerklWNq4fEAVI7BmkxnTS9542okA/+UmeG70LdKjzFS+LjjOnyWzTh
| YwU8uUjLfnRca74kY0DkVHOIkwZQha0J+BrKSADq/zDjkG0g4v0vzHINOmHx9eiE
| 67NoJKJPY5S3RYWxl/4x8Kphx7PNJBPC75gYjlxxDhxdYu9a3daqJUa58/qOm6P8
| w1P9nA6lkg7NopyqepulLAzIcqnTjb/nMD2Pd9b6vgWc3IqSfFreqjzshZ+FjNZo
| zR+tR6z4TQ==
|_-----END CERTIFICATE-----
995/tcp open  ssl/pop3 syn-ack ttl 63 Dovecot pop3d
|_ssl-date: TLS randomness does not represent time
| ssl-cert: Subject: commonName=NIXHARD
| Subject Alternative Name: DNS:NIXHARD
| Issuer: commonName=NIXHARD
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2021-11-10T01:30:25
| Not valid after:  2031-11-08T01:30:25
| MD5:   2b45:ec3c:508f:3cfb:9f6a:750c:63f8:2077
| SHA-1: ed43:7d5a:3c46:54ac:9902:8dc4:9d86:6efb:2ae3:357c
| -----BEGIN CERTIFICATE-----
| MIIC0zCCAbugAwIBAgIUC6tYfrtqQqCrhjYv11bUtaKet3EwDQYJKoZIhvcNAQEL
| BQAwEjEQMA4GA1UEAwwHTklYSEFSRDAeFw0yMTExMTAwMTMwMjVaFw0zMTExMDgw
| MTMwMjVaMBIxEDAOBgNVBAMMB05JWEhBUkQwggEiMA0GCSqGSIb3DQEBAQUAA4IB
| DwAwggEKAoIBAQDEBpDfkH4Ro5ZXW44NvnF3N9lKz27V1hgRppyUk5y/SEPKt2zj
| EU+r2tEHUeHoJHQZBbW0ybxh+X2H3ZPNEG9nV1GtFQfTBVcrUEpN5VV15aIbdh+q
| j53pp/wcL/d8+Zg2ZAaVYWvQHVqtsAudQmynrV1MHA39A44fG3/SutKlurY8AKR0
| MW5zMPtflMc/N3+lH8UUMBf2Q+zNSyZLiBEihxK3kfMW92HqWeh016egSIFuxUsH
| kk4xpGmyG9NDYna47dQzoHCg+42KgqFvWrGw2nIccaEIX5XA8rU9u53C7EQzDzmQ
| vAtHpKWBwNmiivxAz/QC7MPExWIWtZtOqxmfAgMBAAGjITAfMAkGA1UdEwQCMAAw
| EgYDVR0RBAswCYIHTklYSEFSRDANBgkqhkiG9w0BAQsFAAOCAQEAG+Dm9pLJgNGC
| X1YmznmtBUekhXMrU67tQl745fFasJQzIrDgVtK27fjAtQRwvIbDruSwTj47E7+O
| XdS7qyjFNBerklWNq4fEAVI7BmkxnTS9542okA/+UmeG70LdKjzFS+LjjOnyWzTh
| YwU8uUjLfnRca74kY0DkVHOIkwZQha0J+BrKSADq/zDjkG0g4v0vzHINOmHx9eiE
| 67NoJKJPY5S3RYWxl/4x8Kphx7PNJBPC75gYjlxxDhxdYu9a3daqJUa58/qOm6P8
| w1P9nA6lkg7NopyqepulLAzIcqnTjb/nMD2Pd9b6vgWc3IqSfFreqjzshZ+FjNZo
| zR+tR6z4TQ==
|_-----END CERTIFICATE-----
|_pop3-capabilities: CAPA SASL(PLAIN) USER UIDL AUTH-RESP-CODE RESP-CODES TOP PIPELINING
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Tue May 12 08:09:24 2026 -- 1 IP address (1 host up) scanned in 238.13 seconds
```
I see SSH, IMAP, POP3. currently I have no creds to interact.
Run Nmap to check for UDP ports:
```bash
nmap -sU -vv -p- <IP> -oN nmap-udp
└──╼ [★]$ cat nmap-udp
# Nmap 7.94SVN scan initiated Tue May 12 08:15:52 2026 as: nmap -sU -vv -p- -oN nmap-udp --min-rate 5000 10.129.202.20
Warning: 10.129.202.20 giving up on port because retransmission cap hit (10).
Nmap scan report for 10.129.202.20
Host is up, received echo-reply ttl 63 (0.24s latency).
Scanned at 2026-05-12 08:15:52 CDT for 146s
Not shown: 65383 open|filtered udp ports (no-response), 151 closed udp ports (port-unreach)
PORT    STATE SERVICE REASON
161/udp open  snmp    udp-response ttl 63

Read data files from: /usr/bin/../share/nmap
# Nmap done at Tue May 12 08:18:19 2026 -- 1 IP address (1 host up) scanned in 146.67 seconds
```
Got SNMP open on port 161. I can try some enumeration for community strings using onesixtyone:
```bash
└──╼ [★]$ onesixtyone 10.129.202.20 -c /usr/share/wordlists/seclists/Discovery/SNMP/snmp-onesixtyone.txt 
Scanning 1 hosts, 3218 communities
10.129.202.20 [backup] Linux NIXHARD 5.4.0-90-generic #101-Ubuntu SMP Fri Oct 15 20:00:55 UTC 2021 x86_64
```
Use this community strings with snmpwalk:
```bash
└──╼ [★]$ snmpwalk -c backup 10.129.202.20 -v2c
iso.3.6.1.2.1.1.1.0 = STRING: "Linux NIXHARD 5.4.0-90-generic #101-Ubuntu SMP Fri Oct 15 20:00:55 UTC 2021 x86_64"
iso.3.6.1.2.1.1.2.0 = OID: iso.3.6.1.4.1.8072.3.2.10
iso.3.6.1.2.1.1.3.0 = Timeticks: (471889) 1:18:38.89
iso.3.6.1.2.1.1.4.0 = STRING: "Admin <tech@inlanefreight.htb>"
iso.3.6.1.2.1.1.5.0 = STRING: "NIXHARD"
iso.3.6.1.2.1.1.6.0 = STRING: "Inlanefreight"
iso.3.6.1.2.1.1.7.0 = INTEGER: 72
iso.3.6.1.2.1.1.8.0 = Timeticks: (21) 0:00:00.21
iso.3.6.1.2.1.1.9.1.2.1 = OID: iso.3.6.1.6.3.10.3.1.1
iso.3.6.1.2.1.1.9.1.2.2 = OID: iso.3.6.1.6.3.11.3.1.1
iso.3.6.1.2.1.1.9.1.2.3 = OID: iso.3.6.1.6.3.15.2.1.1
iso.3.6.1.2.1.1.9.1.2.4 = OID: iso.3.6.1.6.3.1
iso.3.6.1.2.1.1.9.1.2.5 = OID: iso.3.6.1.6.3.16.2.2.1
iso.3.6.1.2.1.1.9.1.2.6 = OID: iso.3.6.1.2.1.49
iso.3.6.1.2.1.1.9.1.2.7 = OID: iso.3.6.1.2.1.4
iso.3.6.1.2.1.1.9.1.2.8 = OID: iso.3.6.1.2.1.50
iso.3.6.1.2.1.1.9.1.2.9 = OID: iso.3.6.1.6.3.13.3.1.3
iso.3.6.1.2.1.1.9.1.2.10 = OID: iso.3.6.1.2.1.92
iso.3.6.1.2.1.1.9.1.3.1 = STRING: "The SNMP Management Architecture MIB."
iso.3.6.1.2.1.1.9.1.3.2 = STRING: "The MIB for Message Processing and Dispatching."
iso.3.6.1.2.1.1.9.1.3.3 = STRING: "The management information definitions for the SNMP User-based Security Model."
iso.3.6.1.2.1.1.9.1.3.4 = STRING: "The MIB module for SNMPv2 entities"
iso.3.6.1.2.1.1.9.1.3.5 = STRING: "View-based Access Control Model for SNMP."
iso.3.6.1.2.1.1.9.1.3.6 = STRING: "The MIB module for managing TCP implementations"
iso.3.6.1.2.1.1.9.1.3.7 = STRING: "The MIB module for managing IP and ICMP implementations"
iso.3.6.1.2.1.1.9.1.3.8 = STRING: "The MIB module for managing UDP implementations"
iso.3.6.1.2.1.1.9.1.3.9 = STRING: "The MIB modules for managing SNMP Notification, plus filtering."
iso.3.6.1.2.1.1.9.1.3.10 = STRING: "The MIB module for logging SNMP Notifications."
iso.3.6.1.2.1.1.9.1.4.1 = Timeticks: (11) 0:00:00.11
iso.3.6.1.2.1.1.9.1.4.2 = Timeticks: (11) 0:00:00.11
iso.3.6.1.2.1.1.9.1.4.3 = Timeticks: (11) 0:00:00.11
iso.3.6.1.2.1.1.9.1.4.4 = Timeticks: (11) 0:00:00.11
iso.3.6.1.2.1.1.9.1.4.5 = Timeticks: (11) 0:00:00.11
iso.3.6.1.2.1.1.9.1.4.6 = Timeticks: (11) 0:00:00.11
iso.3.6.1.2.1.1.9.1.4.7 = Timeticks: (11) 0:00:00.11
iso.3.6.1.2.1.1.9.1.4.8 = Timeticks: (11) 0:00:00.11
iso.3.6.1.2.1.1.9.1.4.9 = Timeticks: (19) 0:00:00.19
iso.3.6.1.2.1.1.9.1.4.10 = Timeticks: (21) 0:00:00.21
iso.3.6.1.2.1.25.1.1.0 = Timeticks: (473414) 1:18:54.14
iso.3.6.1.2.1.25.1.2.0 = Hex-STRING: 07 EA 05 0C 0E 10 2A 00 2B 00 00 
iso.3.6.1.2.1.25.1.3.0 = INTEGER: 393216
iso.3.6.1.2.1.25.1.4.0 = STRING: "BOOT_IMAGE=/vmlinuz-5.4.0-90-generic root=/dev/mapper/ubuntu--vg-ubuntu--lv ro ipv6.disable=1 maybe-ubiquity
"
iso.3.6.1.2.1.25.1.5.0 = Gauge32: 1
iso.3.6.1.2.1.25.1.6.0 = Gauge32: 148
iso.3.6.1.2.1.25.1.7.0 = INTEGER: 0
iso.3.6.1.2.1.25.1.7.1.1.0 = INTEGER: 1
iso.3.6.1.2.1.25.1.7.1.2.1.2.6.66.65.67.75.85.80 = STRING: "/opt/tom-recovery.sh"
iso.3.6.1.2.1.25.1.7.1.2.1.3.6.66.65.67.75.85.80 = STRING: "tom NMds732Js2761"
iso.3.6.1.2.1.25.1.7.1.2.1.4.6.66.65.67.75.85.80 = ""
iso.3.6.1.2.1.25.1.7.1.2.1.5.6.66.65.67.75.85.80 = INTEGER: 5
iso.3.6.1.2.1.25.1.7.1.2.1.6.6.66.65.67.75.85.80 = INTEGER: 1
iso.3.6.1.2.1.25.1.7.1.2.1.7.6.66.65.67.75.85.80 = INTEGER: 1
iso.3.6.1.2.1.25.1.7.1.2.1.20.6.66.65.67.75.85.80 = INTEGER: 4
iso.3.6.1.2.1.25.1.7.1.2.1.21.6.66.65.67.75.85.80 = INTEGER: 1
iso.3.6.1.2.1.25.1.7.1.3.1.1.6.66.65.67.75.85.80 = STRING: "chpasswd: (user tom) pam_chauthtok() failed, error:"
iso.3.6.1.2.1.25.1.7.1.3.1.2.6.66.65.67.75.85.80 = STRING: "chpasswd: (user tom) pam_chauthtok() failed, error:
Authentication token manipulation error
chpasswd: (line 1, user tom) password not changed
Changing password for tom."
iso.3.6.1.2.1.25.1.7.1.3.1.3.6.66.65.67.75.85.80 = INTEGER: 4
iso.3.6.1.2.1.25.1.7.1.3.1.4.6.66.65.67.75.85.80 = INTEGER: 1
iso.3.6.1.2.1.25.1.7.1.4.1.2.6.66.65.67.75.85.80.1 = STRING: "chpasswd: (user tom) pam_chauthtok() failed, error:"
iso.3.6.1.2.1.25.1.7.1.4.1.2.6.66.65.67.75.85.80.2 = STRING: "Authentication token manipulation error"
iso.3.6.1.2.1.25.1.7.1.4.1.2.6.66.65.67.75.85.80.3 = STRING: "chpasswd: (line 1, user tom) password not changed"
iso.3.6.1.2.1.25.1.7.1.4.1.2.6.66.65.67.75.85.80.4 = STRING: "Changing password for tom."
iso.3.6.1.2.1.25.1.7.1.4.1.2.6.66.65.67.75.85.80.4 = No more variables left in this MIB View (It is past the end of the MIB tree)
```
Here I see credential for user `tom:NMds732Js2761`. Maybe I can use this on IMAP and POP3.
```bash
└──╼ [★]$ telnet 10.129.202.20 110
Trying 10.129.202.20...
Connected to 10.129.202.20.
Escape character is '^]'.
+OK Dovecot (Ubuntu) ready.
user tom
+OK
pass NMds732Js2761
+OK Logged in.
stat
+OK 1 3661
retr 1
+OK 3661 octets
HELO dev.inlanefreight.htb
MAIL FROM:<tech@dev.inlanefreight.htb>
RCPT TO:<bob@inlanefreight.htb>
DATA
From: [Admin] <tech@inlanefreight.htb>
To: <tom@inlanefreight.htb>
Date: Wed, 10 Nov 2010 14:21:26 +0200
Subject: KEY

-----BEGIN OPENSSH PRIVATE KEY-----
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
-----END OPENSSH PRIVATE KEY-----
.
```
Got some private key here. Let's try use it to ssh as tom.
```bash
tom@NIXHARD:~$ ls -la
total 48
drwxr-xr-x 6 tom  tom  4096 Nov 10  2021 .
drwxr-xr-x 5 root root 4096 Nov 10  2021 ..
-rw------- 1 tom  tom   532 Nov 10  2021 .bash_history
-rw-r--r-- 1 tom  tom   220 Nov 10  2021 .bash_logout
-rw-r--r-- 1 tom  tom  3771 Nov 10  2021 .bashrc
drwx------ 2 tom  tom  4096 Nov 10  2021 .cache
drwx------ 3 tom  tom  4096 Nov 10  2021 mail
drwx------ 8 tom  tom  4096 May 12 14:18 Maildir
-rw------- 1 tom  tom   169 Nov 10  2021 .mysql_history
-rw-r--r-- 1 tom  tom   807 Nov 10  2021 .profile
drwx------ 2 tom  tom  4096 Nov 10  2021 .ssh
-rw------- 1 tom  tom  2018 Nov 10  2021 .viminfo
tom@NIXHARD:~$ cat .mysql_history 
_HiStOrY_V2_
show\040databases;
select\040*\040from\040users;
use\040users;
select\040*\040from\040users;
show\040databases;
use\040users;
select\040*\040from\040users;
```
Inside tom's root directory, I saw a `.mysql_history` querying from a database called `users`. It could be that this machine is running a mysql service but not exposing it publicy.
Since the default port of mysql is 3306, let's check for listening ports on this machine to see if anything listening on 3306:
```bash
tom@NIXHARD:~$ ss -tuln
Netid  State   Recv-Q  Send-Q   Local Address:Port    Peer Address:Port Process 
udp    UNCONN  0       0        127.0.0.53%lo:53           0.0.0.0:*            
udp    UNCONN  0       0              0.0.0.0:68           0.0.0.0:*            
udp    UNCONN  0       0              0.0.0.0:161          0.0.0.0:*            
tcp    LISTEN  0       4096     127.0.0.53%lo:53           0.0.0.0:*            
tcp    LISTEN  0       128            0.0.0.0:22           0.0.0.0:*            
tcp    LISTEN  0       100            0.0.0.0:993          0.0.0.0:*            
tcp    LISTEN  0       100            0.0.0.0:995          0.0.0.0:*            
tcp    LISTEN  0       70           127.0.0.1:33060        0.0.0.0:*            
tcp    LISTEN  0       151          127.0.0.1:3306         0.0.0.0:*            
tcp    LISTEN  0       100            0.0.0.0:110          0.0.0.0:*            
tcp    LISTEN  0       100            0.0.0.0:143          0.0.0.0:*
```
Okay so there is something listening to loopback traffic on 3306. Let's try using mysql to confirm.
```bash
tom@NIXHARD:~$ mysql -u tom -p -h localhost
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 9
Server version: 8.0.27-0ubuntu0.20.04.1 (Ubuntu)

Copyright (c) 2000, 2021, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases
    -> ;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
| users              |
+--------------------+
5 rows in set (0.00 sec)
```
By using the same credential I've found for tom, I was able to authenticate as tom. Now let's check for users database to see if I can find the target.
```bash
mysql> use users
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show columns from users;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| id       | int         | YES  |     | NULL    |       |
| username | varchar(50) | YES  |     | NULL    |       |
| password | varchar(50) | YES  |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+
3 rows in set (0.01 sec)

mysql> select * from users where username = 'HTB';
+------+----------+------------------------------+
| id   | username | password                     |
+------+----------+------------------------------+
|  150 | HTB      | cr3n4o7rzse7rzhnckhssncif7ds |
+------+----------+------------------------------+
1 row in set (0.00 sec)
```