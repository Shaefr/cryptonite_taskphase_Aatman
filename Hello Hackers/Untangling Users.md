Challenge 1 - 
```bash
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# cat /clag
cat: /clag: No such file or directory
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{EYLD1bA1tROE8Og2UtrP3AAVc0U.dVTN0UDLyczN1czW}
```
Challenge 2-
```bash
hacker@users~other-users-with-su:~$ su zardus
Password:
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{Axdhk3io80CCtSyiuDf8vYhKAOC.dZTN0UDLyczN1czW}
```
challenge 3-
```bash
hacker@users~cracking-passwords:~$ cat /challenge/shadow-leak
root:*:19873:0:99999:7:::
daemon:*:19873:0:99999:7:::
bin:*:19873:0:99999:7:::
sys:*:19873:0:99999:7:::
sync:*:19873:0:99999:7:::
games:*:19873:0:99999:7:::
man:*:19873:0:99999:7:::
lp:*:19873:0:99999:7:::
mail:*:19873:0:99999:7:::
news:*:19873:0:99999:7:::
uucp:*:19873:0:99999:7:::
proxy:*:19873:0:99999:7:::
www-data:*:19873:0:99999:7:::
backup:*:19873:0:99999:7:::
list:*:19873:0:99999:7:::
irc:*:19873:0:99999:7:::
gnats:*:19873:0:99999:7:::
nobody:*:19873:0:99999:7:::
_apt:*:19873:0:99999:7:::
hacker::20000:0:99999:7:::
zardus:$6$CODGI0/Xf7GuhRiB$yiAiLx15RgHNbFvhGhwjOLCSmw6e6HDtSETOEPDl7OQ.NJsqzf2CigrlWuesjEb/g5ltuuhk4MQaNgDGDtlCL0:20014:0:99999:7:::
hacker@users~cracking-passwords:~$ su zardus
Password:
su: Authentication failure
hacker@users~cracking-passwords:~$ su zardus
Password:
su: Authentication failure
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04943g/s 287.8p/s 287.8c/s 287.8C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$
hacker@users~cracking-passwords:~$ su zardus
Password:
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{QBa47TPF0pGdKWWerRzhmecVb1m.ddTN0UDLyczN1czW}
```
challenge 4-
```bash
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{kSORjTXO28uInl2pySxeZcuKi_X.dhTN0UDLyczN1czW}
```
