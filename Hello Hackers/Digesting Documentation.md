Challenge 1-
Learnt how to specify an argument to the command line to obtain the flag. Invoked /challenge/challenge program using --give flag argument.
```bash
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{gmgkrq6Euruc-3-UJZLVwew1gOF.dRjM5QDLyczN1czW}
```

Challenge 2-
Learnt about arguments taking arguments on linux. The printfile argument allowed me to print my arbitrary file (in this case "/flag") which led me to obtain the right flag.
I initially ran it without an argument to see what would linux give as a response.
```bash
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile
You must pass a file for --printfile to read!
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{YfLjib_dfbvLy-1MaCiNUh2CyuU.dVjM5QDLyczN1czW}
```

Challenge 3-
Learnt about the manual-displaying command "man".
Learnt that it exists interestingly in a centralized database named /usr/share/man.
Then i proceeded to invoke the manual of /challenge, which guided me to use an argument --sngjon which would return the flag when it in turn had an integer argument of 542 passed.
Had small braindead moments where i forgot to use /challenge/challenge and instead used "challenge" :')
```bash
hacker@man~reading-manuals:~$ man challenge

CHALLENGE(1)                                            Challenge Commands                                           CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --sngjon NUM
              print the flag if NUM is 542

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)

pwn.college                                                  May 2024                                                CHALLENGE(1)
hacker@man~reading-manuals:~$ challenge  --sngjon NUM 542
ssh-entrypoint: challenge: command not found
hacker@man~reading-manuals:~$ challenge  --sngjon 542
ssh-entrypoint: challenge: command not found
hacker@man~reading-manuals:~$  challenge --sngjon 542
ssh-entrypoint: challenge: command not found
hacker@man~reading-manuals:~$ challenge --sngjon 542
ssh-entrypoint: challenge: command not found
hacker@man~reading-manuals:~$ /challenge/challenge  --sngjon 542
Correct usage! Your flag: pwn.college{sX5JnY4Q2BVPgN05jonctNO-7Lh.dRTM4QDLyczN1czW}
```
Challenge 4- 
Learnt how to quickly navigate through a long long long manpage using / to search, n and N to go to next/ previous.
I searched for flag and got to --de command. Then i used q to quit the manual.
Used --de to get the flag.
```bash
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ /challenge/challenge --de
Initializing...
Correct usage! Your flag: pwn.college{gGcXAeN7iaufWipnegumTHVqhGU.dVTM4QDLyczN1czW}
```
Challenge 5-
Learnt the advanced usage of man. Scrolled down to see the following:
man -k printf -
"Search the short descriptions and manual page names for the keyword printf  as  regular  expression.   Print  out any matches.  Equivalent to apropos printf."
Then i proceeded with the hidden manpage and used it according to the knowledge of previous challenges.
```bash
hacker@man~searching-for-manuals:~$ man -k challenge
qpphnpphov (1)       - print the flag!
hacker@man~searching-for-manuals:~$ man qpphnpphov

CHALLENGE(1)                                            Challenge Commands                                           CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --qpphnp NUM
              print the flag if NUM is 108

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)

pwn.college                                                  May 2024                                                CHALLENGE(1)
hacker@man~searching-for-manuals:~$ /challenge/challenge --qpphnp 108
Correct usage! Your flag: pwn.college{U1qZpNN0pMhnPpp8YhFToDv8hGI.dZTM4QDLyczN1czW}
```
Challenge 6-
used --help command to get instructions for getting secret value which in turn would be passed as the argument for GIVE_THE_FLAG or -g. Then i executed the command and got the flag.
Learnt about helpful programs in this challenge.
eventually got trhough after some trial and error due to some misunderstandigns.
```bash
hacker@man~helpful-programs:~$ --help
ssh-entrypoint: --help: command not found
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge  -g GIVE_THE_FLAG
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]
a challenge to make you ask for help: error: argument -g/--give-the-flag: invalid int value: 'GIVE_THE_FLAG'
hacker@man~helpful-programs:~$ /challenge/challenge --print-value
The secret value is: 983
hacker@man~helpful-programs:~$ -g 983
ssh-entrypoint: -g: command not found
hacker@man~helpful-programs:~$ -g GIVE_THE_FLAG 983
ssh-entrypoint: -g: command not found
hacker@man~helpful-programs:~$ -g
ssh-entrypoint: -g: command not found
hacker@man~helpful-programs:~$  /challenge/challenge  -g GIVE_THE_FLAG 983
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]
a challenge to make you ask for help: error: argument -g/--give-the-flag: invalid int value: 'GIVE_THE_FLAG'
hacker@man~helpful-programs:~$  /challenge/challenge -g 983
Correct usage! Your flag: pwn.college{URfW9IDxjAG8LMDQ3VHobC2-Yuh.ddjM4QDLyczN1czW}
```
Challenge 7-
Learnt about builtins, their invoking and usage. They are engraved into the shells aready.
cd is a built in ive been using. help is the command used to see challenge here.
I obtained the --secret program and also its argument value after using help for challenge.
i then ran the final command to print the flag.
```bash
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!

    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "ElwpfHr4".
hacker@man~help-for-builtins:~$ help --secret
ssh-entrypoint: help: --: invalid option
help: usage: help [-dms] [pattern ...]
hacker@man~help-for-builtins:~$ challenge --secret ElwpfHr4
Correct! Here is your flag!
pwn.college{ElwpfHr4TTgfMC3flxgUGDeNxYs.dRTM5QDLyczN1czW}
```

 
