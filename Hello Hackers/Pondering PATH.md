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
