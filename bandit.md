# https://overthewire.org/wargames/bandit/

## Level 0
#### ssh bandit0@bandit.labs.overthewire.org -p 2220
#### ls
#### cat readme 
### Password - boJ9jbbUNNfktd78OOpsqOltutMc3MY1

## Level 1-2
#### ssh bandit@bandit.labs.overthewire.org -p 2220
#### ls
#### cat ./-
### The dashed file can be accesses by using ./ as a prefix
### Password - CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9

## Level 2-3
#### ls
#### cat ./spaces\ in\ this\ filename
### add backslash for spaces
### Password - UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK

## Level 3-4
#### ls --all
#### cat .hidden
### ls doesn't give all files, so run ls --all and you'll get even the hidden files
### Password - pIwrPrtPN36QITSp3EQaw936yaFoFgAB

## Level 4-5
#### bandit4@bandit:~/inhere$ ls
-file00  -file02  -file04  -file06  -file08
-file01  -file03  -file05  -file07  -file09
#### bandit4@bandit:~/inhere$ file ./-*
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
#### bandit4@bandit:~/inhere$ cat ./-file07
### Password - koReBOKuIDDepwhWk7jZC0RTdopnAYKh
### find the files for ASCII text 


## Level 5-6
#### bandit5@bandit:~$ ls
inhere
#### bandit5@bandit:~$ find -type f -size 1033c
./inhere/maybehere07/.file2
#### bandit5@bandit:~$ cat ./inhere/maybehere07/.file2
### Password - DXjZPULLxYr17uwoI01bNLQbtFemEgo7
### -size finds the matching size where ##c stands for bytes

## Level 6-7
#### bandit6@bandit:~$ ls -l
total 0
#### bandit6@bandit:~$ ls -a
.  ..  .bash_logout  .bashrc  .profile
#### bandit6@bandit:~$ find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
/var/lib/dpkg/info/bandit7.password
#### bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password 
### Password - HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
### / for finding in all server. 
### 2>/dev/null
#### 2 directs the stderr. > is for directing the mentioned output. /dev/null is sort of a dumping place for all error files. Here you will find a lot of files with the error Permission Denied. Command will work even without the error detection
