# Challenge 1 - Changing File Ownership
```bash
hacker@permissions~changing-file-ownership:~$ ls -l
total 28
-rw-r--r-- 1 hacker hacker   4 Oct  9 16:41 COLLEGE
-rw-r--r-- 1 hacker hacker   8 Oct  9 17:18 PWN
-rw-r--r-- 1 hacker hacker  58 Oct  8 17:06 a
-rw-r--r-- 1 hacker hacker 829 Oct  9 17:12 instructions
-rw-r--r-- 1 hacker hacker  77 Oct  9 18:07 intercept
-rw-r--r-- 1 hacker hacker  93 Oct  9 17:12 myflag
lrwxrwxrwx 1 hacker hacker   5 Oct  9 18:30 not-the-flag -> /flag
lrwxrwxrwx 1 hacker hacker   5 Oct  9 11:49 ourfile -> /flag
-rw-r--r-- 1 hacker hacker 435 Oct  9 17:04 the-flag
hacker@permissions~changing-file-ownership:~$ cat not-the-flag
cat: not-the-flag: Permission denied
hacker@permissions~changing-file-ownership:~$ chown hacker not-the-flag
hacker@permissions~changing-file-ownership:~$ cat not-the-flag
pwn.college{wRHlK0Lb0n9t4HuG0S1zuKr1zcn.dFTM2QDLyczN1czW}
```
# Challenge 2 - 
```bash
hacker@permissions~groups-and-files:~$ id
uid=1000(hacker) gid=1000(hacker) groups=1000(hacker)
hacker@permissions~groups-and-files:~$ ls -i
62 COLLEGE  66 PWN  15 a  65 instructions  67 intercept  63 myflag  68 not-the-flag  50 ourfile  64 the-flag
hacker@permissions~groups-and-files:~$ ls -l
total 28
-rw-r--r-- 1 hacker hacker   4 Oct  9 16:41 COLLEGE
-rw-r--r-- 1 hacker hacker   8 Oct  9 17:18 PWN
-rw-r--r-- 1 hacker hacker  58 Oct  8 17:06 a
-rw-r--r-- 1 hacker hacker 829 Oct  9 17:12 instructions
-rw-r--r-- 1 hacker hacker  77 Oct  9 18:07 intercept
-rw-r--r-- 1 hacker hacker  93 Oct  9 17:12 myflag
lrwxrwxrwx 1 hacker hacker   5 Oct  9 18:30 not-the-flag -> /flag
lrwxrwxrwx 1 hacker hacker   5 Oct  9 11:49 ourfile -> /flag
-rw-r--r-- 1 hacker hacker 435 Oct  9 17:04 the-flag
hacker@permissions~groups-and-files:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{gFzbESLxYh0fu3Mxxk8CfF3UkBT.ddjN1QDLyczN1czW}

hacker@permissions~groups-and-files:~$ cat not-the-flag
cat: not-the-flag: Permission denied
hacker@permissions~groups-and-files:~$ cat ourfile
cat: ourfile: Permission denied
hacker@permissions~groups-and-files:~$ chrgp hacker ourfile
ssh-entrypoint: chrgp: command not found
hacker@permissions~groups-and-files:~$ chgrp hacker ourfile
hacker@permissions~groups-and-files:~$ cat ourfile
pwn.college{8ZkSjRlMM7cx0BLWEq2lGuJjErV.dFzNyUDLyczN1czW}
```
Challege 3 - 
```bash
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp30914) groups=1000(grp30914)
hacker@permissions~fun-with-groups-names:~$ ls -l
total 28
-rw-r--r-- 1 hacker grp30914   4 Oct  9 16:41 COLLEGE
-rw-r--r-- 1 hacker grp30914   8 Oct  9 17:18 PWN
-rw-r--r-- 1 hacker grp30914  58 Oct  8 17:06 a
-rw-r--r-- 1 hacker grp30914 829 Oct  9 17:12 instructions
-rw-r--r-- 1 hacker grp30914  77 Oct  9 18:07 intercept
-rw-r--r-- 1 hacker grp30914  93 Oct  9 17:12 myflag
lrwxrwxrwx 1 hacker grp30914   5 Oct  9 18:30 not-the-flag -> /flag
lrwxrwxrwx 1 hacker grp30914   5 Oct  9 11:49 ourfile -> /flag
-rw-r--r-- 1 hacker grp30914 435 Oct  9 17:04 the-flag
hacker@permissions~fun-with-groups-names:~$ chgrp grp30914 ourfile
hacker@permissions~fun-with-groups-names:~$ cat ourfile
pwn.college{YLuYKln0BQ-ZEFBy22ygFk7Wez1.dJzNyUDLyczN1czW}
```
