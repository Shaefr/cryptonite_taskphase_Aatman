# Challenge 1 - 
Here i learnt that instead of having to run programs to get the root and then act as the root user, we can use su (switch user) which is basically a setuid binary.
It helps run as a root, and hence can start a root shell.
For authentication, it can ask a root password.
```bash
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# cat /clag
cat: /clag: No such file or directory
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{EYLD1bA1tROE8Og2UtrP3AAVc0U.dVTN0UDLyczN1czW}
```
# Challenge 2-
Instead of root user always, we can also act as other users, by mentioning the username after su.
Obviously, password is also needed.
```bash
hacker@users~other-users-with-su:~$ su zardus
Password:
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{Axdhk3io80CCtSyiuDf8vYhKAOC.dZTN0UDLyczN1czW}
```
# Challenge 3 -
su compares the entered password with the stored value. 
It one-way-encrypts (known as hashing) it.
Interestingly, if we know the hashed value of the password, we can crack it.
When a leaked /etc/shadow is encountered, the data can be used to cause havoc.
For this level, i got the hashed value of zardus, the su-ed to zardus and ran the program to crack it.
```bash
hacker@users~cracking-passwords:~$ cat /challenge/shadow-leak
WALL OF TEXT
zardus:$6$CODGI0/Xf7GuhRiB$yiAiLx15RgHNbFvhGhwjOLCSmw6e6HDtSETOEPDl7OQ.NJsqzf2CigrlWuesjEb/g5ltuuhk4MQaNgDGDtlCL0:20014:0:99999:7:::
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04943g/s 287.8p/s 287.8c/s 287.8C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ su zardus
Password:
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{QBa47TPF0pGdKWWerRzhmecVb1m.ddTN0UDLyczN1czW}
```
# Challenge 4-
As we saw above, managing root passwords can be challenging. 
They (or their hashes) are susceptible to leaks and are not well-suited for larger environments.
To tackle this issue, the approach has shifted over the past few decades from using su to using sudo (superuser do).
sudo relies on policies that it checks to determine the user's authorization run things as root, rather than authentication using pwds.
For this level, i just had to sudo and then cat flag.
```bash
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{kSORjTXO28uInl2pySxeZcuKi_X.dhTN0UDLyczN1czW}
```
