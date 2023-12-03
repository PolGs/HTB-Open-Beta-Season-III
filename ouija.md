# Ouija
![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/c61df0d2-899d-4906-860d-8b2bd12e8e57)


------------------------------
RECON

NMAP
```s
┌──(kali㉿kali)-[~/Documents/htb_os3/ouija]
└─$ nmap -Pn -sV -sC 10.10.11.244                
Starting Nmap 7.93 ( https://nmap.org ) at 2023-12-03 07:13 EST
Nmap scan report for 10.10.11.244
Host is up (0.12s latency).
Not shown: 997 closed tcp ports (conn-refused)
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 8.9p1 Ubuntu 3ubuntu0.4 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   256 6ff2b4ed1a918d6ec9105171d57c49bb (ECDSA)
|_  256 dfddbcdc570d98af0f882f73334862e8 (ED25519)
80/tcp   open  http    Apache httpd 2.4.52
|_http-title: Apache2 Ubuntu Default Page: It works
|_http-server-header: Apache/2.4.52 (Ubuntu)
3000/tcp open  http    Node.js Express framework
|_http-title: Site doesn't have a title (application/json; charset=utf-8).
Service Info: Host: localhost; OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 23.32 seconds
```
![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/1bdfe553-eae1-42d2-b8c0-52e9f6c7415a)
![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/2ec1d05a-b314-4904-808f-e18dc1ab7fc4)

Found login endpoint by luck looks like a od API
![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/222c3d86-72fc-4902-baac-9eea6bd33a3c)


