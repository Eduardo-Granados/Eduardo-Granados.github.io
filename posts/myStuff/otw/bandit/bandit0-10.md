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


### Level 1
```text
Continuing on from Level 0:

1. Once logged in, I wanted to see what files there were. I did a `ls -la`
1. I saw the file `readme`
1. Did `cat readme`
1. Found the this in the readme `ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If`
1. ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```



### Level 2
```text
login: ssh bandit1@bandit.labs.overthewire.org -p 2220
pw: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

1. After logging in, did the command `ls -la`
1. saw the file titled `-`
1. to be able to cat the file, i did `cat ./"-"`
1. pw found `263JGJPfgU6LtdEvgfWU1XP5yac29mFx`
1. 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```



### Level 3
```text
login: ssh bandit2@bandit.labs.overthewire.org -p 2220
pw: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

1. to cat a file with spaces do `./spaces\ in\ file\ name`
1. Found 'MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx'
1. MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```



### level 4
```text
login: ssh bandit3@bandit.labs.overthewire.org -p 2220
pw: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

1. whoami
1. pwd
1. ls
1. saw a filed named `inhere`
1. cd inhere/
1. ls -la
1. foud a file called `...Hiding-From-You`
1. cat ./...Hiding-From-You
1. 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```



### level 5
```text
login: ssh bandit4@bandit.labs.overthewire.org -p 2220
pw: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

1. whoami
1. pwd
1. ls -la
1. found a folder called `inhere`
1. ls -la inhere
1. after doing `cat inhere/-file0*` and going through all the files, file `-file07` was the only human-readable file 
1. 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```



### level 6
```text
login: ssh bandit5@bandit.labs.overthewire.org -p 2220
pw: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

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

### Level 7
```text
login: ssh bandit6@bandit.labs.overthewire.org -p 2220
pw: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

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


### level 8
```text
login: ssh bandit7@bandit.labs.overthewire.org -p 2220
pw: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

1. pwd
1. ls -la
1. `cat data.txt` will output a lot of info in a dictionary style
1. sort data.txt | uniq | grep -i "millionth"
1. dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc 
```



### Level 9
```text
login: ssh bandit8@bandit.labs.overthewire.org -p 2220
pw: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

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
