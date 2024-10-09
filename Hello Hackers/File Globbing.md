Challenge 1-
Learnt about the start of globbing, and how * is basically a wildcard treated character, that reciprocates the argument with any file that matches the corresponding patterns.
I was asked to cd to challenge using * so i used only 2 characters from the limit of 4.
I then ran /challenge/run to get my flag.
Initially i didnt use star to see the output message.
```bash
This challenge resets your working directory to /home/hacker unless you change
directory properly...
hacker@globbing~matching-with-:~$ cd /challenge
You specified the path to 'cd' to in more than 4 characters. Disallowed!
This challenge resets your working directory to /home/hacker unless you change
directory properly...
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{E2jFEsE4e3qsi2hiq4lzprCtcII.dFjM4QDLyczN1czW}
```
Challenge 2-
Learnt about "?" after "*". ? essentially reciprocates just 1 character and hence gives us matching files which can be brought by only single character replacement.
```bash
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{owTjpMkonVtubAjdH8xrsiAsqnV.dJjM4QDLyczN1czW}
hacker@globbing~matching-with-:/challenge$
```
Challenge 3-
Here, i learnt about [].These square brackets can be used by passing a number of characters, and they give us the files that are matching with those characters, but each of them singly, like the ? character.
I unordered the bash term into hasb to learn that they can be passed in any sequence (kind of obvious but still).
Then i ran the command to get my flag.
```bash
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[hasb]
You got it! Here is your flag!
pwn.college{Ur1YrOE-mnLr5Lvqdmj_B4oDZqc.dNjM4QDLyczN1czW}
```
Challenge 4-
Here i learnt how globbing can work on a path basis.
I initially wasted time becuase i didnt know a space was supposed to be mentioned after /challenge/run before writing /challenge/files.
For the first time, i asked chat gpt to help me out because i had tried everything else. It helped me point out my flaw in the command.
I proceeded to run the code with the " ", which functioned perfectly and gave my my flag.
external referenced source- https://chatgpt.com/.
NOTE- i cleared out some messy trials before entering it in the codelblock here.
```bash
hacker@globbing~matching-paths-with-:~$ /challenge/run/challenge/files/file_[bash]
ssh-entrypoint: /challenge/run/challenge/files/file_[bash]: Not a directory
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{kjddJmgjDEKPmK5AhPrQqh65fnC.dRjM4QDLyczN1czW}
```
Challenge 5-
Here i combined all previous knowledges of globbing. 
cep was taken before in the brackets (the leading letter of the files).
Then i used wildcard "*" to finish of the file names, and it gave my desired flag.
```bash
hacker@globbing~mixing-globs:/challenge/files$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{AW-bX7ZskAQYZac3uixMC9zvn49.dVjM4QDLyczN1czW}
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run *
Error: you did not use a square bracket glob...
```
Challenge 6-
Here i learnt about ! and ^ characters working like NOT operators in programming languages.
I used them to ensure p,w,n werent a part of the files i was looking for.
I added * in the end as i initially hadnt read the part where it was mentioned that p,w,n were the STARTING letters of the files!
I proceeded to get my desired flag.
```bash
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]
Your expansion did not expand to the requested files (amazing beautiful
challenging delightful educational fantastic great happy incredible jovial kind
laughing magical optimistic queenly radiant splendid thrilling uplifting
victorious xenial youthful zesty).
Instead, it expanded to:
[!pwn]
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{8F-SJ0-sL_iosh4o74u1gx7oPNA.dZjM4QDLyczN1czW}
```

