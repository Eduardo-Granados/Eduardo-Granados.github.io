# Over the wire
# Bandit

**Link**: https://overthewire.org/wargames/bandit/bandit0.html



### Level 0 
```text
user: bandit0
host: bandit.labs.overthewire.org
port: 2220

bandit0@bandit.labs.overthewire.org -port 2220
pw: bandit0
```


<<<<<<< HEAD
# Level 1
```
1. once logged in, I wanted to see what files there were. I did a `ls -la`
2. i saw the file `readme`
3. did `cat readme`
4. pw found 
=======
### Level 1
```text
Continuing on from Level 0:

1. Once logged in, I wanted to see what files there were. I did a `ls -la`
1. I saw the file `readme`
1. Did `cat readme`
1. Found the this in the readme `ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If`
1. ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
>>>>>>> e7f5110 (2025_1_1 update)
```



### Level 2
```text
login: ssh bandit1@bandit.labs.overthewire.org -p 2220
<<<<<<< HEAD

1. After logging in, did the command `ls -la`
2. saw the file titled `-`
3. to be able to cat the file, i did `cat ./"-"`
4. pw found 
=======
pw: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

1. After logging in, did the command `ls -la`
1. saw the file titled `-`
1. to be able to cat the file, i did `cat ./"-"`
1. pw found `263JGJPfgU6LtdEvgfWU1XP5yac29mFx`
1. 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```
>>>>>>> e7f5110 (2025_1_1 update)



### Level 3
```text
login: ssh bandit2@bandit.labs.overthewire.org -p 2220
<<<<<<< HEAD
=======
pw: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
>>>>>>> e7f5110 (2025_1_1 update)

1. to cat a file with spaces do `./spaces\ in\ file\ name`
<<<<<<< HEAD
=======
1. Found 'MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx'
1. MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```
>>>>>>> e7f5110 (2025_1_1 update)



### level 4
```text
login: ssh bandit3@bandit.labs.overthewire.org -p 2220
<<<<<<< HEAD
=======
pw: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
>>>>>>> e7f5110 (2025_1_1 update)

1. whoami
<<<<<<< HEAD
2. pwd
3. ls
4. saw a filed named `inhere`
5. cd inhere/
6. ls -la
7. foud a file called `.hidden`
8. cat .hidden
=======
1. pwd
1. ls
1. saw a filed named `inhere`
1. cd inhere/
1. ls -la
1. foud a file called `...Hiding-From-You`
1. cat ./...Hiding-From-You
1. 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```
>>>>>>> e7f5110 (2025_1_1 update)



### level 5
```text
login: ssh bandit4@bandit.labs.overthewire.org -p 2220
<<<<<<< HEAD
=======
pw: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
>>>>>>> e7f5110 (2025_1_1 update)

1. whoami
<<<<<<< HEAD
2. pwd
3. ls -la
4. found a folder called `inhere`
5. ls -la inhere
6. after doing `cat inhere/-file0*` and going through all the files, file `-file07` was the only human-readable file 
=======
1. pwd
1. ls -la
1. found a folder called `inhere`
1. ls -la inhere
1. after doing `cat inhere/-file0*` and going through all the files, file `-file07` was the only human-readable file 
1. 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```
>>>>>>> e7f5110 (2025_1_1 update)



### level 6
```text
login: ssh bandit5@bandit.labs.overthewire.org -p 2220
<<<<<<< HEAD
=======
pw: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
>>>>>>> e7f5110 (2025_1_1 update)

1. whoami
1. pwd
1. ls -la
1. cd inhere/
1. ls -la
1. ls -la maybehere* | less
1. within `less`, enter the following to search through the output. `/1033`
1. found a match with maybehere07/.file2
1. OR ls -la | find -type f | find -size 1033c | sort
1. found a match with maybehere07/.file2
1. cat maybehere07/.file2
1. HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```

<<<<<<< HEAD
6. ls -la maybehere* | less
7. within `less`, enter the following to search through the output. `/1033`
8. found a match in maybehere07/.file2
9. cat maybehere07/.file2
```

# Level 7
login: ssh bandit6@bandit.labs.overthewire.org -p 2220
=======
### Level 7
```text
login: ssh bandit6@bandit.labs.overthewire.org -p 2220
pw: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
>>>>>>> e7f5110 (2025_1_1 update)

1. whoami
1. pwd
1. ls -la
1. find / -size 33c -user bandit7 -group6 -print 2>&1 | grep -v "Permission denied" | grep -i "bandit7"
   - what does the 2>&1 mean ? : combies any erroes from find with the strandard output, so all messages (errors and results) appear in the same stream
1. found `/var/lib/dpkg/info/bandit7.password`
1. find / -size 33c -user bandit7 -group6 -print 2>&1 | grep -v "Permission denied" | grep -i "bandit7" | xargs cat
1. OR
1. cat /var/lib/dpkg/info/bandit7.password
1. morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```

<<<<<<< HEAD
5. find / -type f -user bandit7 -group6 -print 2>&1 | grep -v "Permission denied"
    - what does the 2>&1 mean ?
6. found `/var/lib/dpkg/info/bandit7.password`
7. cat /var/lib/dpkg/info/bandit7.password
=======
>>>>>>> e7f5110 (2025_1_1 update)

### level 8
```text
login: ssh bandit7@bandit.labs.overthewire.org -p 2220
<<<<<<< HEAD
=======
pw: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
>>>>>>> e7f5110 (2025_1_1 update)

1. pwd
<<<<<<< HEAD
2. ls -la
3. `cat data.txt` will output a lot of info in a dictionary style
4. sort data.txt | uniq | grep millionth
=======
1. ls -la
1. `cat data.txt` will output a lot of info in a dictionary style
1. sort data.txt | uniq | grep -i "millionth"
1. dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc 
>>>>>>> e7f5110 (2025_1_1 update)
```



### Level 9
```text
login: ssh bandit8@bandit.labs.overthewire.org -p 2220
<<<<<<< HEAD
=======
pw: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
>>>>>>> e7f5110 (2025_1_1 update)

1. pwd
1. ls -la
1. sort data.txt | uniq u
1. 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```


### Level 10

```text
login: ssh bandit8@bandit.labs.overthewire.org -p 2220
pw: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

1. ls -la
1. cat data.txt
1. sort data.txt | strings | grep "="
1. FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```
