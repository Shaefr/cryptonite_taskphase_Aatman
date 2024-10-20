# Challenge 1-
The ; is a symbol that we can use to execute more than one command in the same line. 
The order will be the same in which we have typed out the commands.
This is an appropriate use of chaining commands, as, it saves time, and gives a structured output when needed, without the intrustion of the command prompt line in between the outputs.
```bash
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{42mnp9IHOXJzhKoWqyAfro8NIDn.dVTN4QDLyczN1czW}
```
# Challenge 2-
As the number of commands increases, the length of the resulting prompt can become quite cumbersome. 
In such cases, we can save these commands in a file known as a shell script and run them by executing that file.
This saves time by allowing us to reuse the same shell scripts which we can create once and save.
Here i created my shell script named x.sh from VSCode. I then invoked it using bash command.
I got my flag thereafter.
```bash
hacker@chaining~your-first-shell-script:~$ ls 
COLLEGE  PWN  a  instructions  intercept  myflag  not-the-flag  ourfile  the-flag  x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{gawBEYFzOwLii8WDmqyQY12fyRI.dFzN4QDLyczN1czW}
```
![image](https://github.com/user-attachments/assets/bc228d8e-d8ae-4448-ab54-a926e2af3db8)

# Challenge 3-
In this level, i learned how to redirect shell scripts into other commands.
All the previous operators learnt in piping and redirection work here too.
For the challenge, i had to pipe the contents of the earlier created x.sh script into /challenge/solve program.
This was achieved using | obviously.
```
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{4iRBlkgJHy13wVhMBdcDJQFxp92.dhTM5QDLyczN1czW}
```
# Challenge 4-
Instead of always having to use bash commands to run and execute my shell script, here i learnt that i can give the absolute path instead too.
This works as long as the executable permission has been granted.
Here, i made a shell script named z.sh, and gave it the command /challenge/solve.
then, i copied its absolute path and invoked it using that.
i ran into the part where i forgot to change permissions, so i did that and it ran as i needed it to, and got the flag.
```
hacker@chaining~executable-shell-scripts:~$ /home/hacker/z.sh
bash: /home/hacker/z.sh: Permission denied
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
