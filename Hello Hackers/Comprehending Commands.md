Challenge 1-
Captured the flag using cat command.
```bash
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{QIl0Zqv2cuOQzOTFz9t2vI7cyNR.dFzN1QDLyczN1czW}
hacker@commands~cat-not-the-pet-but-the-command:~$ cat ~/flag
pwn.college{QIl0Zqv2cuOQzOTFz9t2vI7cyNR.dFzN1QDLyczN1czW}
```

Challenge 2-
Captured using absolute path.
```bash
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{cBJYq8RlQ3gxQK5i8RM_EPVcJ1L.dlTM5QDLyczN1czW}
```

Challenge 3-
Captured flag using absolute path and not cd command.
```bash
You cannot use the 'cd' command in this level, and must retrieve the flag by
absolute path. Plus, I hid the flag in a different directory! You can find it
in the file /lib/x86_64-linux-gnu/gtk-3.0/flag. Go cat it out **without** cding
into that directory!
hacker@commands~more-catting-practice:~$ cat /lib/x86_64-linux-gnu/gtk-3.0/flag
pwn.college{EwT0lyM379S3s7yxIQZNfYN_4rU.dBjM5QDLyczN1czW}
```

Challenge 4-
Learnt to use grep command, searched for pwn.college as its the beginning of every flag.
This approach worked in obtaining the flag.
```bash
Connected!
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{E3Nc3WbXHcaDnXsmr-RwF4DDXM9.ddTM4QDLyczN1czW}
```
Challenge 5-
Played around with ls command, realized that a path must be mentioned to get a specific file.
I used ls for challenge then captured the flag with the new name for the "run" file.
```bash
hacker@commands~listing-files:~$ ls /challenge
19320-renamed-run-19424  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/19320-renamed-run-19424
Yahaha, you found me! Here is your flag:
pwn.college{kN__V9VFnSz_mZzSYM53PhDhpu9.dhjM4QDLyczN1czW}
```

Challenge 6-
Created 2 files, pwn and college using touch command in tmp directory. Then obtained the flag in tmp.
checked for any differences if I convoked it from the home directory, there were none.
```bash
hacker@commands~touching-files:~$ cd /tmp
hacker@commands~touching-files:/tmp$ ls
bin  hsperfdata_root  tmp.MiOQGWw5Zc
hacker@commands~touching-files:/tmp$ touch pwn
hacker@commands~touching-files:/tmp$ touch college
hacker@commands~touching-files:/tmp$ /challenge/run
Success! Here is your flag:
pwn.college{YlU5Gbhxjfs5Dixo1a1g1vsYf_R.dBzM4QDLyczN1czW}
hacker@commands~touching-files:/tmp$ cd
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{YlU5Gbhxjfs5Dixo1a1g1vsYf_R.dBzM4QDLyczN1czW}
```

Challenge 7-
Learnt how to delete a file using rm command.
```bash
hacker@commands~removing-files:~$ /challenge/check
It looks like /home/hacker/delete_me still exists! rm it.
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ ls
a
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{sHRhUTIm6RIfS2-THgbBFczRr5I.dZTOwUDLyczN1czW}
```
