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
Challenge 6-
Normally redirected content of /challenge/run to the given file.
Then i recalled the function of grep file and how it helps us to search through files via our mentioned keywords.
Initially i tried flag, and it failed to give me any scope, hence i tried pwn.college and it gave me my flag.
```bash
hacker@piping~grepping-stored-results:~$ /challenge/run>/tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep flag /tmp/data.txt
[FLAG] Here is your flag:
flagellating
flagrantly
flags
flagships
flagellation's
conflagration
camouflage's
flagstone
flagstaff
flagship
flag's
flagon
flagellates
flagons
flagon's
camouflaged
flagstone's
conflagrations
flagellated
flagging
camouflaging
flagellums
flagpoles
flagellate
flagstaff's
flagellum
persiflage
flagella
unflagging
conflagration's
flagstones
flagpole
flag
flagellum's
flagellation
flagship's
flagstaffs
flagrant
camouflage
flagged
flagpole's
camouflages
persiflage's
hacker@piping~grepping-stored-results:~$ grep pwn.college /tmp/data.txt
pwn.college{sGWEly9QLitBA5Wd2GG4dC1sAYc.dhTM4QDLyczN1czW}
```
Challenge 7-
Here i was introduced to | (pipe) operator and how it helps us to skip storing unwanted results in a file.
I searched for flag, it displayed many outputs, so i searched for pwn.college.
```bash
hacker@piping~grepping-live-output:~$ /challenge/run | grep flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
[FLAG] Here is your flag:
flagons
flag's
camouflage's
flagship's
flagon
flagellation
camouflage
flagged
persiflage's
camouflages
flagstone's
flagship
flagon's
flagellated
flagstaff
flagellate
flagellums
flagstaff's
flagellating
flagella
conflagration's
flagstones
flagging
flagellates
unflagging
flag
flagellum's
flagrant
flagpoles
flagstone
flagellation's
conflagration
flags
camouflaging
flagrantly
conflagrations
flagpole's
flagpole
flagstaffs
flagships
camouflaged
persiflage
flagellum
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{gLCd4qcm-pInDJxc5OS3sWIehWF.dlTM4QDLyczN1czW}
```
Challenge 8-
Learnt and recalled that 2> can help us to redirect to standard error and | only helps us to redirect standard output.
I used 2>&1 to redirect standadrd errors to standard output, then proceeded to pipe using |.
I searched for pwn.college after using my brainy brain.
NOTE- this level took me a little more time, as i used a permutation of commands which led me to this one working.
I got my desired flag.
```bash
hacker@piping~grepping-errors:~$ /challenge/run 2>&1 | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{UNBgWZCUNY1iUNu369ubdTdrQ4A.dVDM5QDLyczN1czW}
```
Challenge 9-
I learnt about tee command here and how it helps us to see our data being passed in a live manner.
This will help us in knowing whats missing by breaking the flow in a piece by piece manner, and hence we can correct it if needed.
I realized that we need to copy the work of tee into an intermediate file. I named it intercept.
I then found out the missing piece, --secret, along with its argument.
i replaced intercept with --secret [ARG] and then proceeded with the commands.
This worked and gave me my desired flag.
```bash
hacker@piping~duplicating-piped-data-with-tee:~$  /challenge/pwn | tee /challenge/college
Processing...
You are trying to use 'tee' *instead* of /challenge/college. Use it *between*
/challenge/pwn and /challenge/college!
You must pipe the output of /challenge/pwn into /challenge/college (or 'tee'
for debugging).
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee challenge/college
Processing...
You are trying to use 'tee' *instead* of /challenge/college. Use it *between*
/challenge/pwn and /challenge/college!
You must pipe the output of /challenge/pwn into /challenge/college (or 'tee'
for debugging).
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee intercept | /challenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat intercept
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "YFbUdtE0"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret YFbUdtE0 | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{YFbUdtE0MsectnvDpHUeSWOLqGL.dFjM5QDLyczN1czW}
```
Challenge 10-
Here, i was told to use process substitution to copy data into two commands side by side using with "tee".
I took out the output of /challenge/hack using piping, and sent it to /challenge/the and /challenge/planet.
This helped me then get my desired flag.
This level took some trial and error, and 20+ minutes to crack
```bash
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) >(/challenge/planet)
This secret data must directly and simultaneously make it to /challenge/the and
/challenge/planet. Don't try to copy-paste it; it changes too fast.
2919916440202987898
Congratulations, you have duplicated data into the input of two programs! Here
is your flag:
pwn.college{gBsYQTfTuj7DXBk_xK4_H9cLtwO.dBDO0UDLyczN1czW}
```
Challenge 11-
Here, using everything I had learnt so far about process substitutions and redirection.
I had to redirect stdout from the /challenge/hack command to the /challenge/planet program. 
Then I redirected stderr to /challenge/the program.
This gave me my desired flag.
Took me many tries, and i had gotten the spacing wrong initially too
```bash
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack>>(/challenge/planet)2>>(/challenge/the)
ssh-entrypoint: syntax error near unexpected token `('
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack > >( /challenge/planet) 2> >( /challenge/the)
Congratulations, you have learned a redirection technique that even experts
struggle with! Here is your flag:
pwn.college{g8-lmKt3kKqDE_0-c2ENsO-buiJ.dFDNwYDLyczN1czW}
```


