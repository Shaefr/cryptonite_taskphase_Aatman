Learnt about stdin, stdout, stderr for input output and error.
Challenge 1-
Learnt the use of input redirection characted ">".
```bash
hacker@piping~redirecting-output:~$ PWN>COLLEGE
ssh-entrypoint: PWN: command not found
You have created the COLLEGE file, but you didn't write the correct value to
it. Make sure to write PWN to the COLLEGE file.
hacker@piping~redirecting-output:~$ echo PWN>COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your
flag:
pwn.college{kDUkGRQZMCJ8hBIeD_60P9gxiFD.dRjN1QDLyczN1czW}
```
Challenge 2-
Learnt that we can input the output of one command into the other which DOES NOT always have to be echo.
Rest all was the same logic used in challenge 1.
Then, i displayed the newly inputted content of myflag using cat command.
```bash
hacker@piping~redirecting-more-output:~$ /challenge/run>myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{cT4Y6jMUOyv8cLEKyXvsc3gMCiC.dVjN1QDLyczN1czW}
```
Challenge 3-
Learnt how to append using >>. 
Initially saw what would happen if i only used >.
Mistook stdout to give a direct output which i thought would append into the desired file, but it gave an error.
I finally appended it correctly to get both parts of the flag.
```bash
Connected!
hacker@piping~appending-output:~$ /challenge/run>/home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do
the first write directly to the file, and the second write, I'll do to stdout
(if it's pointing at the file). If you redirect the output in append mode, the
second write will append to (rather than overwrite) the first write, and you'll
get the whole flag!
hacker@piping~appending-output:~$ stdout>>/home/hacker/the-flag
ssh-entrypoint: stdout: command not found
hacker@piping~appending-output:~$ cat /home/hacker/the-flag
l-t2jSbp1Gwzv8Pfe7yDSaa.ddDM5QDLyczN1czW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>)
rather than *append* mode (>>), and so the write of the second half to stdout
overwrote the initial write of the first half directly to the file. Try append
mode!
hacker@piping~appending-output:~$ /challenge/run>>/home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do
the first write directly to the file, and the second write, I'll do to stdout
(if it's pointing at the file). If you redirect the output in append mode, the
second write will append to (rather than overwrite) the first write, and you'll
get the whole flag!
hacker@piping~appending-output:~$ cat /home/hacker/the-flag
 |
\|/ This is the first half:
 v
pwn.college{4HrSl-t2jSbp1Gwzv8Pfe7yDSaa.ddDM5QDLyczN1czW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>)
rather than *append* mode (>>), and so the write of the second half to stdout
overwrote the initial write of the first half directly to the file. Try append
mode!
```
Challenge 4-
In this challenge i learnt about file descriptors and their numbers.
This essentially helps us to redirect errors into their respective files, and also other segregrations (error was just an example).
Hence i redirected the flag to myflag and feedback in instructions.
I then displayed everything.
```bash
hacker@piping~redirecting-errors:~$ /challenge/run>myflag 2>instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{gFzbESLxYh0fu3Mxxk8CfF3UkBT.ddjN1QDLyczN1czW}

hacker@piping~redirecting-errors:~$ cat instructions
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will check that error output is redirected to a specific file path : instructions
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!

[TEST] You should have redirected my stderr to instructions. Checking...

[PASS] The file at the other end of my stderr looks okay!
[PASS] Success! You have satisfied all execution requirements.
```
Challenge 5-
Interestingly, here i learnt that we can also send back redirected inputs to the programs.
This is done using <.
I passed the word COLLEGE into PWN file using echo command. I then redirected content of PWN file to /challenge/run as the task asked me to.
I got my desired flag.
Minor braindead errors were made where i forgot that linux is case sensitive and forgetting /.
```bash
hacker@piping~redirecting-input:~$ echo COLLEGE>PWN
hacker@piping~redirecting-input:~$ cat college
cat: college: No such file or directory
hacker@piping~redirecting-input:~$ cat pwn
cat: pwn: No such file or directory
hacker@piping~redirecting-input:~$ cat PWN
COLLEGE
hacker@piping~redirecting-input:~$ challenge/run<PWN
ssh-entrypoint: challenge/run: No such file or directory
hacker@piping~redirecting-input:~$ /challenge/run<PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{YVBCdoEg0htzb7JYdpfsbzSYOg3.dBzN1QDLyczN1czW}
```
