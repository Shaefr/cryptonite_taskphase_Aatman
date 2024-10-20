# Preview
I learnt that in Linux, files have different file modes. Using ls -l, i could check out a permissions of a file or directory.
The first character of each line represented the file type. "d" indicates that it's a directory, and  "-" indicatess that it's a normal file.
The following 9 symbols tell us the respective abilities a user, group, and others have to that file (in that order).
r means readability permission, w means we can write in it, x means that person can execute it.

# Challenge 1 - Changing File Ownership
In this challenge, we learn the importance of being the root user, the one who owns the file completely.
He can change the entire accesibility of the file, when it comes to reading, writing and executing.
The root user can also transfer ownership to another user.
As a root user, this can be done using the chown command.
chown [username] [file] is the syntax.
This challenge had us start out as a root user, then chown to hacker and access the flag.
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
A group can have multiple users in it, and a user can be a member of multiple groups.
If a file is owned by a user and a root group too, gaining access to be the group will give one the permission to completely utilize the file.
This is where chgrp command comes in handy.
Here, i changed group ownership using syntax "chgrp grpname filename".
This allowed me access to the flag and print it.
It was kept in ourfile.
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

hacker@permissions~groups-and-files:~$ cat ourfile
pwn.college{8ZkSjRlMM7cx0BLWEq2lGuJjErV.dFzNyUDLyczN1czW}
```
# Challege 3 - 
Here, i simply had to chgrp into a different name to get access, instead of the classic hacker group name the earlier challenges had.
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
# Challege 4
Learnings of this challenge have been mentioned in preview.
The syntax i used was [name of domain who's permission i wanted to change]+[permission to be added] [file_name].
```bash
hacker@permissions~changing-permissions:~$ chmod go+rwx /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{8etkyiLcY6YpEiD7ET4gfeGQkzU.dNzNyUDLyczN1czW}
```
# Challenge 5
same as challenge 4
```bash
hacker@permissions~executable-files:~$ chmod ogu+rwx /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{YLs7-kptSojrFcigil9K-0kVIV5.dJTM2QDLyczN1czW}
```
challenge 6-
Learnings are the same as earlier challenges.
"a" is a short for ugo, and - sign allows us to remove permissions too.
Here i had to consecutively execute the right permission commands 8 times in a row to get the flag.
```bash
Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$  chmod a-rwx /challenge/pwn
You set the correct permissions!
Round 1 (of 8)!

Current permissions of "/challenge/pwn": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rwx------
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u+rwx /challenge/pwn
You set the correct permissions!
Round 2 (of 8)!

Current permissions of "/challenge/pwn": rwx------
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod a-rwx /challenge/pwn
You set the correct permissions!
Round 3 (of 8)!

Current permissions of "/challenge/pwn": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -----x---
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod g+x /challenge/pwn
You set the correct permissions!
Round 4 (of 8)!

Current permissions of "/challenge/pwn": -----x---
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw---x---
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u+rw /challenge/pwn
You set the correct permissions!
Round 5 (of 8)!

Current permissions of "/challenge/pwn": rw---x---
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -----x---
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u-rw /challenge/pwn
You set the correct permissions!
Round 6 (of 8)!

Current permissions of "/challenge/pwn": -----x---
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": ---r-x---
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod g+r /challenge/pwn
You set the correct permissions!
Round 7 (of 8)!

Current permissions of "/challenge/pwn": ---r-x---
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": ---r-xr-x
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod o+rx /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod ogu+rwx /flag
hacker@permissions~permission-tweaking-practice:~$ cat /flag
pwn.college{ckuvpewQ_AGEXsFJqpyDTklubr1.dBTM2QDLyczN1czW}
```
# Challenge 7
Learnings are the same as earlier challenges.
This time, "=" sign allows us to simply set permissions altogether, overwriting the old ones.
Here i had to consecutively execute the right permission commands 8 times in a row to get the flag.
```bash
Connected!
hacker@permissions~permissions-setting-practice:~$ /challenge/run
Round 0 (of 8)!

Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r-xr-xrw-
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rx,g=rx,o=rw /challenge/pwn
You set the correct permissions!
Round 1 (of 8)!

Current permissions of "/challenge/pwn": r-xr-xrw-
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": --xr-x---
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=x,g=rx,o=- /challenge/pwn
You set the correct permissions!
Round 2 (of 8)!

Current permissions of "/challenge/pwn": --xr-x---
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -w-r--rw-
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=w,g=r,o=rw /challenge/pwn
You set the correct permissions!
Round 3 (of 8)!

Current permissions of "/challenge/pwn": -w-r--rw-
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r-x------
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rx,g=-,o=- /challenge/pwn
You set the correct permissions!
Round 4 (of 8)!

Current permissions of "/challenge/pwn": r-x------
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rwx-w-r-x
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rwx,g=w,o=rx /challenge/pwn
You set the correct permissions!
Round 5 (of 8)!

Current permissions of "/challenge/pwn": rwx-w-r-x
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": -w-rwx--x
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=w,g=rwx,o=x /challenge/pwn
You set the correct permissions!
Round 6 (of 8)!

Current permissions of "/challenge/pwn": -w-rwx--x
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": -wx--xrwx
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=wx,g=x,o=rwx /challenge/pwn
You set the correct permissions!
Round 7 (of 8)!

Current permissions of "/challenge/pwn": -wx--xrwx
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": r-x-w--wx
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rx,g=w,o=wx /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod ogu=rwx /flag
hacker@permissions~permissions-setting-practice:~$ cat /flag
pwn.college{kF102mX19__dT3hZ2smFUr_L9mB.dNTM5QDLyczN1czW}
```
challenge 8-
```bash
/challenge/getroothacker@permissions~the-suid-bit:~$ chmod u+s /challenge/getroot
hacker@permissions~the-suid-bit:~$ /challenge/getroot
SUCCESS! You have set the suid bit on this program, and it is running as root!
Here is your shell...
root@permissions~the-suid-bit:~# cat /flag
pwn.college{QAQKAlVeSuUqWlv8Fp4gh-cSnHG.dNTM2QDLyczN1czW}
```
