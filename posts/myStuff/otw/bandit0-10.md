https://overthewire.org/wargames/bandit/bandit0.html


# Level 0 
user: bandit0
host: bandit.labs.overthewire.org
port: 2220
pw: bandit0



# Level 1
1. once logged in, I wanted to see what files there were. I did a `ls -la`
2. i saw the file `readme`
3. did `cat readme`
4. pw found `NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL`
5. NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL



# Level 2
login: ssh bandit1@bandit.labs.overthewire.org -p 2220
pw: NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL

1. After logging in, did the command `ls -la`
2. saw the file titled `-`
3. to be able to cat the file, i did `cat ./"-"`
4. pw found `rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi`
5. rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi



# Level 3
login: ssh bandit2@bandit.labs.overthewire.org -p 2220
pw: rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi

1. to cat a file with spaces do `./spaces\ in\ file\ name`
2. aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG



# level 4
login: ssh bandit3@bandit.labs.overthewire.org -p 2220
pw: aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG

```
1. whoami
2. pwd
3. ls
4. saw a filed named `inhere`
5. cd inhere/
6. ls -la
7. foud a file called `.hidden`
8. cat .hidden
9. 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
```



# level 5
login: ssh bandit4@bandit.labs.overthewire.org -p 2220
pw: 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe


1. whoami
2. pwd
3. ls -la
4. found a folder called `inhere`
5. ls -la inhere
6. after doing `cat inhere/-file0*` and going through all the files, file `-file07` was the only human-readable file 
7. lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR



# level 6
login: ssh bandit5@bandit.labs.overthewire.org -p 2220
pw: lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR

1. whoami
    bandit5
2. pwd
    /home/bandit5
3. ls -la
    total 24
    drwxr-xr-x  3 root root    4096 Oct  5 06:19 .
    drwxr-xr-x 70 root root    4096 Oct  5 06:20 ..
    -rw-r--r--  1 root root     220 Jan  6  2022 .bash_logout
    -rw-r--r--  1 root root    3771 Jan  6  2022 .bashrc
    drwxr-x--- 22 root bandit5 4096 Oct  5 06:19 inhere
    -rw-r--r--  1 root root     807 Jan  6  2022 .profile
4. cd inhere/
5. ls -la
    total 88   
    drwxr-x--- 22 root bandit5 4096 Oct  5 06:19 . 
    drwxr-xr-x  3 root root    4096 Oct  5 06:19 ..
    drwxr-x---  2 root bandit5 4096 Oct  5 06:19 maybehere00   
    drwxr-x---  2 root bandit5 4096 Oct  5 06:19 maybehere01   
    drwxr-x---  2 root bandit5 4096 Oct  5 06:19 maybehere02   
    drwxr-x---  2 root bandit5 4096 Oct  5 06:19 maybehere03   
    drwxr-x---  2 root bandit5 4096 Oct  5 06:19 maybehere04   
    drwxr-x---  2 root bandit5 4096 Oct  5 06:19 maybehere05   
    drwxr-x---  2 root bandit5 4096 Oct  5 06:19 maybehere06   
    drwxr-x---  2 root bandit5 4096 Oct  5 06:19 maybehere07   
    drwxr-x---  2 root bandit5 4096 Oct  5 06:19 maybehere08   
    drwxr-x---  2 root bandit5 4096 Oct  5 06:19 maybehere09   
    drwxr-x---  2 root bandit5 4096 Oct  5 06:19 maybehere10   
    drwxr-x---  2 root bandit5 4096 Oct  5 06:19 maybehere11   
    drwxr-x---  2 root bandit5 4096 Oct  5 06:19 maybehere12   
    drwxr-x---  2 root bandit5 4096 Oct  5 06:19 maybehere13   
    drwxr-x---  2 root bandit5 4096 Oct  5 06:19 maybehere14   
    drwxr-x---  2 root bandit5 4096 Oct  5 06:19 maybehere15   
    drwxr-x---  2 root bandit5 4096 Oct  5 06:19 maybehere16   
    drwxr-x---  2 root bandit5 4096 Oct  5 06:19 maybehere17   
    drwxr-x---  2 root bandit5 4096 Oct  5 06:19 maybehere18   
    drwxr-x---  2 root bandit5 4096 Oct  5 06:19 maybehere19

6. ls -la maybehere* | less
7. within `less`, enter the following to search through the output. `/1033`
8. found a match in maybehere07/.file2
9. cat maybehere07/.file2
10. P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU

19 AAAAC3NzaC1l
19 AAAAC3NzaC1l
# Level 7
login: ssh bandit6@bandit.labs.overthewire.org -p 2220
pw: P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU

1. whoami
2. pwd
3. ls -la
4. i am given the follwoing:
```
   The password for the next level is stored somewhere on the server and has all of the following properties:

    owned by user bandit7
    owned by group bandit6
    33 bytes in size
```

5. find / -type f -user bandit7 -group6 -print 2>&1 | grep -v "Permission denied"
    - what does the 2>&1 mean ?
6. found `/var/lib/dpkg/info/bandit7.password`
7. cat /var/lib/dpkg/info/bandit7.password
8. z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S



# level 8
login: ssh bandit7@bandit.labs.overthewire.org -p 2220
pw: z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S

```text
1. pwd
2. ls -la
3. `cat data.txt` will output a lot of info in a dictionary style
4. sort data.txt | uniq | grep millionth
5. TESKZC0XvTetK0S9xNwm25STk5iWrBvP
```



# Level 9
login: ssh bandit8@bandit.labs.overthewire.org -p 2220
pw: TESKZC0XvTetK0S9xNwm25STk5iWrBvP

```text
1. pwd
2. ls -la
```


# Level 10
