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


