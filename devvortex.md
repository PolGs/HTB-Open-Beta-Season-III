# Devvortex
![Devvortex](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/c8f28c35-9ff8-4f1a-af51-b7013934aedb)

Initial nmap scan
```s
──(kali㉿kali)-[~/Documents/htb_os3/devvortex]
└─$ nmap -Pn -sV -sC 10.10.11.242 
Starting Nmap 7.93 ( https://nmap.org ) at 2023-12-02 07:22 EST
Stats: 0:00:22 elapsed; 0 hosts completed (1 up), 1 undergoing Service Scan
Service scan Timing: About 50.00% done; ETC: 07:22 (0:00:06 remaining)
Nmap scan report for 10.10.11.242
Host is up (0.13s latency).
Not shown: 998 closed tcp ports (conn-refused)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.9 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 48add5b83a9fbcbef7e8201ef6bfdeae (RSA)
|   256 b7896c0b20ed49b2c1867c2992741c1f (ECDSA)
|_  256 18cd9d08a621a8b8b6f79f8d405154fb (ED25519)
80/tcp open  http    nginx 1.18.0 (Ubuntu)
|_http-server-header: nginx/1.18.0 (Ubuntu)
|_http-title: Did not follow redirect to http://devvortex.htb/
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 27.98 seconds
```


![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/badd88ee-3076-4613-b7d0-68c9609804d7)

Found dev.devvortex.htb subdomain with enumeration.
![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/7c2a69b4-6f6d-41f2-b044-2e1aa13afa9b)
![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/701bc573-5ad9-45c2-89bd-a08593f3ed10)


Directory enumeration on dev subdomain
![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/213eeafc-5770-4028-b4a3-c16a99d6cf63)
![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/b558310d-83f2-4601-ac23-ddc63aef1241)
![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/e7a5ee19-f346-4495-9014-11f3f12eb4e0)

404
![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/b52bf897-1bfe-48ce-9e0d-26f67b6c4a81)
![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/d851416d-2897-44cc-849d-ecb119651643)


Joomla enumerationg and analysis
https://book.hacktricks.xyz/network-services-pentesting/pentesting-web/joomla#version
![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/e3cff6ed-e3f4-4649-a71e-488afa3b19ad)

"<version>3.0.0</version>"
Possible vulns
![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/a3519557-f24d-4a8f-ac37-bd460b692afb)
![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/2a6b15c8-c267-4c4c-a00a-a5241d7d96e5)
![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/3d20a155-f422-425f-b405-87b8a813d4fa)
![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/8499ed45-d418-453d-96b2-1d3d544f67ea)
Verdsion 4.2.6
Well try CVE-2023-23752
![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/bb0b8e7b-7512-49ee-8500-a82143b54272)
![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/264e5360-7d26-4527-9a71-c261ee248100)
![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/6bd84eaf-ba63-4859-8ee8-589b934b8e53)
![help](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/a6465125-326e-4baf-b833-07ec72587838)
https://www.exploit-db.com/exploits/51334
https://github.com/Acceis/exploit-CVE-2023-23752
![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/48c8d6e5-3982-480d-9251-d05134b25373)
```s
Users
[649] lewis (lewis) - lewis@devvortex.htb - Manager
Administrator
Super Users
[650] logan paul (logan) - logan@devvortex.htb - Registered

Site info
Site name: Development
Editor: tinymce
Captcha: 0
Access: 1
Debug status: false

Database info
DB type: mysqli
DB host: localhost
DB user: lewis
DB password: P4ntherg0t1n5r3c0n##
DB name: joomla
DB prefix: sd4fg_
DB encryption 0
```
Obtained joomla user and pass. No ssh login with pwnd credentials.
![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/ebf0cdb9-cac6-4fd7-baea-b36bf1ebda61)

Now an RCE would be nice. Or just some arbitrary file reads.








