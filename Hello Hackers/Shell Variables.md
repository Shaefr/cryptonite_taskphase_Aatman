# This module teaches about variables, (shell variables).
# Challenge 1-
The /challenge/run program wasnt allowed to give us the flag here. The flag was put in a variable named "FLAG".
We had to print the contents of the variable FLAG. 
This could be done using "echo" which is a basic printing command.
If we are printing variables using echo, the syntax asks us to use a $ sign infront of it, to notify to the computer that its a variable and not just a word to be echoed.
```bash
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{s6XdEjQfzVzbcnO2ahZDUsblAQI.ddTN1QDLyczN1czW}
```
No references used

# Challenge 2-
We can assign a value to the variable. This is done using the = operator. No spaces must be mentioned before or after the operator.
Else, the shell will recognize the variable as a command and try executing it which will lead to an unwanted output or error.
$ signs are also not needed here. If they are accidentally put, variable expansion is triggered.
For this challenge,  i simply had to set COLLEGE as the value of PWN.
```bash
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{8rTn7YUlGIIvie7HtU5TscDrRQn.dlTN1QDLyczN1czW}
```
# Challenge 3-
For giving a multi word value to a variable, simple spacing doesnt work. Here we take the use of "" quotations, which pass our value as a single token to the shell.
Here i applied this logic to assign COLLEGE YEAH to PWN.
```bash
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{MnwKObQyjtkgOMs3Gwr48tjr8Ta.dBjN1QDLyczN1czW}
```
# Challenge 4-
Here we learn that shell variables are local to only that shell process.
The next commands i run, wont inherit the true value of the certain variable in consideration.
This helps as it doesnt allow unwanted leakage of variable's content to the next program.
If we do want to pass it to the next program, we can explicitly cause it to.
This is done by "exporting" the variable, which causes it to be an environment variable and can be read by the next prompts.
Eg- "export VAR" will allow the child shell to receive the contents of VAR.
We can also directly use export command while assigning the value to the variable itself, to save time.
For this challenge I assigned PWN to COllEGE and COLLEGE to PWN. And then explicitly exported PWN. Then ran my command.
```bash
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ PWN=COLLEGE
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ export PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great
job! Here is your flag:
pwn.college{0-nHJjEJTcSF0M_zK9rC87JscVX.dJjN1QDLyczN1czW}
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
```
# Challenge 5-
env command is used to print every exported variable in the shell. echo is not the only command known to access and print variables.
```bash
hacker@variables~printing-exported-variables:~$ env
SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
DOJO_AUTH_TOKEN=cc3e71e4e0b79582f397bfef3f5796a972d885f38078a770e11254b15472bb7e
HOME=/home/hacker
LANG=C.UTF-8
LS_COLORS=LONG BLOCK OF TEXT MENTIONED THAT I CUT OUT
FLAG=pwn.college{QLs0Ffb8LpQ8oaruhQ7ZT9m7lUA.dhTN1QDLyczN1czW}
LESSCLOSE=/usr/bin/lesspipe %s %s
TERM=xterm
LESSOPEN=| /usr/bin/lesspipe %s
SHLVL=1
LC_CTYPE=C.UTF-8
PATH=/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
_=/run/workspace/bin/env
```
# Challenge 6-
We can store the output of some command in a variable. This is done using the syntax Var_NAME=$(YOUR_COMMAND).
In older versions, ` (backsticks) were used instead of brackets. The problem was, we couldnt nest command substitutions here, as each bakcstick would work like opening and closing brackets and there was no notability of them, unlike "(" being opening and ")" being closing.
For this challenge, i storued the output of /challenge/run in PWN, then printed out the content of PWN.
```bash
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out
and submit it!
hacker@variables~storing-command-output:~$ echo $PWN
pwn.college{8bi3Dn14tMYbxF5XN9_QL4SykqD.dVzN0UDLyczN1czW}
```
# Challenge 7-
"read" builtin allows the shell to accept an input from the user itself. 
Note- the "-p" argument allows us to pass a prompt of our choice too, which can be used to help the user understand the program's request/gesture.
Here, simply as the challenge asked me to, i allowed the shell to read my input of COLLEGE.
```bash
COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{YylDH9SLtNixorWy0TOLW3gsLV5.dhzN1QDLyczN1czW}
```
# Challenge 8-
Here we learn that an inefficient way of reading a file into an environment variable is by using the cat program.
This can be avoided and efficiency can be increased if we simply apply our 2 previously learnt concepts- use of read builtin and the skill of file redirection.
For this question, i allowed read to read into the content of /challenge/read_me whilst i presented its data into the standard input of read itself. It was stored in PWN. This was enough for the challenge.
```bash
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{8WupOWah72KAt5No7_eoCyXEpP5.dBjM4QDLyczN1czW}
```



