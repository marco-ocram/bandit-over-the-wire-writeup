## Level 12-13
#### First, copy the file to a /tmp directory, to make it workable.
#### Reverse a hex dump - xxd -r. file command will tell about the data in the file. DIfferent types of compresson are encountered.
#### For gzip files, extension must be chnaged to gz. Use gunzip command.
#### For bnzip2, extension must be bz2. Use bunzip2 command.
#### For tar,extension isn't compulsory, however it should be tar. Use tar -xvf command
#### At every conversion, run file command to see the content type.
#### Final password is in ASCII Text file data8.bin
### Password - 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL



## Level 13-14
#### Use File command and it's discovered that the sshkey file is the key to next level
> bandit13@bandit:~$ file sshkey.private 
> sshkey.private: PEM RSA private key
> bandit13@bandit:~$ ssh -i sshkey.private bandit14@localhost
#### The password for level 14 is in the directories of level 14 itself
#### Password - 4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e

## Level 14 -15
#### Send files to a specific port of a server using nc command
>bandit14@bandit:~$ nc localhost 30000
>4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
>Correct!
>BfMYroe26WYalil77FoDi9qh59eK5xNr
#### Password -BfMYroe26WYalil77FoDi9qh59eK5xNr

## Level 15-16
#### ssl encryption is anpther way of securing connection with a server
>bandit15@bandit:~$ openssl s_client -connect localhost:30001
CONNECTED(00000003)
.
>BfMYroe26WYalil77FoDi9qh59eK5xNr                                     
Correct!
cluFn7wTiGryunymYOu4RcffSxQluehd
closed
### Password - cluFn7wTiGryunymYOu4RcffSxQluehd

## Level 16-17
#### Use nmap as a port scanner to find ports in the given range. Only 5 ports were found active
#### Use openssl to connect to all different ports with the previous passwords
>bandit16@bandit:~$ openssl s_client -connect localhost:31790
CONNECTED(00000003)
>cluFn7wTiGryunymYOu4RcffSxQluehd
Correct!
#### This provides the RSA private key for next level

## Level 17-18
#### Save the Key to file on your system as extension `.private`. Change the permissions. Log in again using this to next server
#### we can directly apply `diff` command
>bandit17@bandit:~$ ls
passwords.new  passwords.old
bandit17@bandit:~$ diff passwords.new passwords.old 
42c42
< kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
>w0Yfolrc5bwjS4qw5mq1nnQi6mF03bii
### New Password - kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
### Current Password - w0Yfolrc5bwjS4qw5mq1nnQi6mF03bii

## Level 18-19
#### Actually difficult one.
#### You have to skip the bashrc file. You have to get the access before it executes. Instead run `/bin/bash`
>bandit17@bandit:~$ ssh bandit18@localhost /bin/bash

>bandit18@localhost's password: 
ls
readme
cat readme
IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x
#### Password - IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x

## Level 19-20
#### `setup id` is for files with extra privileges. Simply use the id and run it on the bandit20 file
>bandit19@bandit:~$ ls
bandit20-do
>bandit19@bandit:~$ ls -l bandit20-do 
-rwsr-x--- 1 bandit20 bandit19 7296 May  7 20:14 bandit20-do

>bandit19@bandit:~$ file bandit20-do 
bandit20-do: setuid ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=8e941f24b8c5cd0af67b22b724c57e1ab92a92a1, not stripped

>bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
GbKksEFF4yrVs6il55v6gwY5aVje5f0j
### Password - GbKksEFF4yrVs6il55v6gwY5aVje5f0j

## Level 20 - 21
#### Connection has to be made for any random port `10000`. Different tabs are needed for listening and sending data. suconnect connects to a specified port and does the work. netcat is used for localhost connection and receives the data. 
`Tab 1`
>bandit20@bandit:~$ ls
suconnect

>bandit20@bandit:~$ ./suconnect 
Usage: ./suconnect <portnumber>
This program will connect to the given port on localhost using TCP. If it receives the correct password from the other side, the next password is transmitted back.

>bandit20@bandit:~$ nc -l localhost -p 10000 < /etc/bandit_pass/bandit20
gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr

`Tab 2`
>bandit20@bandit:~$ ./suconnect 10000
Read: GbKksEFF4yrVs6il55v6gwY5aVje5f0j
Password matches, sending next password



