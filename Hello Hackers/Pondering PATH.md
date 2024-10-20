# Challenge 1-
The PATH is a special shell variable that holds a list of directory paths where the shell looks for programs related to the commands you enter.
Hence, like other variables which we can blank out, if we blank path out, many basic programs wont run, due to the missing directories and files.
For this challenge, by blanking out path, i removed the rm command consequently, so the flag couldnt be deleted.
```
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ export PATH
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{4tkJHp-J4y0jGjIbfKPXI0AHWWR.dZzNwUDLyczN1czW}
```
# Challenge 2-
As useful uses of PATH, we canadd a new directory of programs to our command repertoire.
PATH stores a list of directories to find commands in. For commands in nonstandard places, we must typically execute them via their path.
Like here, win is in a non standared place, i.e. challenge/more_commands.
If we want to use win, like in this challenge, by calling it by its name only, we can store the directory to win inside PATH.
This exposes the win program when its invoked, and the flag is obtained.
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
In this challenge, win did not pre-exist.
therefore, we had to create a shell script for win, then add it to PATH.
So, first i created a file named win, then inputted the cat flag command into it.
Then, i appended this directory at the end of the PATH variable.
After changing permissions, i ran /challenge/run, which traversed the contents of PATH and found the win command.
```
hacker@path~adding-commands:~$ touch win
hacker@path~adding-commands:~$ echo "cat /flag" > /home/hacker/win
hacker@path~adding-commands:~$ PATH=$PATH:/home/hacker
hacker@path~adding-commands:~$ chmod a+x /home/hacker/win
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{Uf3JJkXb-Y6HK_SqTsTTTLhLpaw.dZzNyUDLyczN1czW}
```
# Challenge 4-
This challenge, worked almost the same as the previous one, but i had to trick Linux into running into the created rm first, instead of the removing rm program.
This worked by adding my new rm file at the beginning of PATH instead of appending it at the end.
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
