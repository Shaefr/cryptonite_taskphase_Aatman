1-
```bash
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{42mnp9IHOXJzhKoWqyAfro8NIDn.dVTN4QDLyczN1czW}
```
2-
```bash
hacker@chaining~your-first-shell-script:~$ ls 
COLLEGE  PWN  a  instructions  intercept  myflag  not-the-flag  ourfile  the-flag  x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{gawBEYFzOwLii8WDmqyQY12fyRI.dFzN4QDLyczN1czW}
```
![image](https://github.com/user-attachments/assets/bc228d8e-d8ae-4448-ab54-a926e2af3db8)

3-
```
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{4iRBlkgJHy13wVhMBdcDJQFxp92.dhTM5QDLyczN1czW}
```
4-
```
hacker@chaining~executable-shell-scripts:~$ ./z.sh
bash: ./z.sh: Permission denied
hacker@chaining~executable-shell-scripts:~$ /home/hacker/z.sh
bash: /home/hacker/z.sh: Permission denied
hacker@chaining~executable-shell-scripts:~$ ls
COLLEGE  PWN  a  instructions  intercept  myflag  not-the-flag  ourfile  the-flag  x.sh  z.sh
hacker@chaining~executable-shell-scripts:~$ ls l
ls: cannot access 'l': No such file or directory
hacker@chaining~executable-shell-scripts:~$ ls -l
total 36
-rw-r--r-- 1 hacker hacker  33 Oct 19 13:44 x.sh
-rw-r--r-- 1 hacker hacker  16 Oct 19 14:03 z.sh
hacker@chaining~executable-shell-scripts:~$ chmod u+x z.sh
hacker@chaining~executable-shell-scripts:~$ ./z.sh
Congratulations on your shell script execution! Your flag:
pwn.college{0Flb5URfbUlbzDnH60qnYP8Omi_.dRzNyUDLyczN1czW}
```
