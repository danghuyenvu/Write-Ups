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