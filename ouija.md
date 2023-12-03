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
fuzzing API endpoints
```s
┌──(kali㉿kali)-[~/Documents/htb_os3/ouija]
└─$ wfuzz -c -w /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt -u "http://10.10.11.244:3000/FUZZ" --hw 7
 /usr/lib/python3/dist-packages/wfuzz/__init__.py:34: UserWarning:Pycurl is not compiled against Openssl. Wfuzz might not work correctly when fuzzing SSL sites. Check Wfuzz's documentation for more information.
********************************************************
* Wfuzz 3.1.0 - The Web Fuzzer                         *
********************************************************

Target: http://10.10.11.244:3000/FUZZ
Total requests: 220560

=====================================================================
ID           Response   Lines    Word       Chars       Payload          
=====================================================================

000000053:   200        0 L      5 W        42 Ch       "login"          
000000065:   200        0 L      1 W        26 Ch       "register"       
000000202:   200        0 L      4 W        25 Ch       "users"          
000000825:   200        0 L      5 W        42 Ch       "Login"          
000002712:   200        0 L      1 W        26 Ch       "Register"
```
users endpoint
![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/69ce3153-a629-42fd-87e7-cd502529d013)
register
![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/ae5f6cd7-87e8-4b21-a7e8-c60415c73000)

gobuster on apache site
```s
┌──(kali㉿kali)-[~/Documents/htb_os3/ouija]
└─$ gobuster dir -u http://10.10.11.244/ -w /usr/share/wordlists/SecLists/Discovery/Web-Content/common.txt 
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.10.11.244/
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/SecLists/Discovery/Web-Content/common.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/.htaccess            (Status: 403) [Size: 279]
/.hta                 (Status: 403) [Size: 279]
/.htpasswd            (Status: 403) [Size: 279]
/index.php            (Status: 302) [Size: 0] [--> http://ouija.htb/]
/index.html           (Status: 200) [Size: 10671]
/server-status        (Status: 200) [Size: 19019]
Progress: 4727 / 4727 (100.00%)
===============================================================
Finished
===============================================================

```

![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/1430bfe8-1b19-4da2-9058-fc5701de68f9)

Adding domain to hosts
http://ouija.htb/
![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/6de3ef97-d4a7-44d9-96d6-425a1cf9e85a)


Subdomain enumeration
```s
┌──(kali㉿kali)-[~/Documents/htb_os3/ouija]
└─$ wfuzz -c -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-110000.txt -u "http://ouija.htb/" -H "Host: FUZZ.ouija.htb" --hl 363
 /usr/lib/python3/dist-packages/wfuzz/__init__.py:34: UserWarning:Pycurl is not compiled against Openssl. Wfuzz might not work correctly when fuzzing SSL sites. Check Wfuzz's documentation for more information.
********************************************************
* Wfuzz 3.1.0 - The Web Fuzzer                         *
********************************************************

Target: http://ouija.htb/
Total requests: 114441

=====================================================================
ID           Response   Lines    Word       Chars       Payload          
=====================================================================

000000019:   403        3 L      8 W        93 Ch       "dev"            
000000171:   403        3 L      8 W        93 Ch       "dev2"           
000000302:   403        3 L      8 W        93 Ch       "devel"          
000000341:   403        3 L      8 W        93 Ch       "development"    
000000466:   403        3 L      8 W        93 Ch       "dev1"           
000000612:   403        3 L      8 W        93 Ch       "develop"        
000000643:   403        3 L      8 W        93 Ch       "dev3"           
000000804:   403        3 L      8 W        93 Ch       "developer"      
000001492:   403        3 L      8 W        93 Ch       "dev01"          
000001629:   403        3 L      8 W        93 Ch       "dev4"
```
![imagen](https://github.com/PolGs/HTB-Open-Beta-Season-III/assets/19478700/7bbdc405-cdff-47c9-baf4-35fe88b18a8e)



