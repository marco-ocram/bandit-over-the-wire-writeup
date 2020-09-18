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
