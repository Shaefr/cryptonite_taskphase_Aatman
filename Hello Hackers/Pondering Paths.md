Challenge 1-
Learnt about how files work, their pathing, with a tree comparision. 
Invoked pwn program using its absolute path, and captured its flag.
```
bash
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{87ftlFg5aO7BdQHNTbKYYnYZzrj.dhzN5QDLyczN1czW}
```
Challenge 2-
Learnt how to access challenges through file paths. This challenge was available by executing /challenge/run command to obtain the flag.
Initially thought the root /pwn was still in consideration
```bash
hacker@paths~program-and-absolute-paths:~$ /pwn/challenge/run
ssh-entrypoint: /pwn/challenge/run: No such file or directory
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{Al4UKb2sT_YJhy0-1ecOEQHVKDT.dVDN1QDLyczN1czW}
```
Challenge 3-
Learnt how to use the change directory command. "cd".
Wasted a lot of time trying to find the right way, eventually noticed there is a space after cd.
Minor source- https://www.geeksforgeeks.org/cd-command-in-linux-with-examples/
```bash
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /proc/67/fd directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /proc/67/fd
hacker@paths~position-thy-self:/proc/67/fd$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{kWtJ3VyrVNquE6B01e7oDFW0ie9.dZDN1QDLyczN1czW}
hacker@paths~position-thy-self:/proc/67/fd$
```
Challenge 4-
Method of approach same as challenge 3.
```bash
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the / directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd //
hacker@paths~position-elsewhere://$ /challenge/run
Incorrect...
You are not currently in the / directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere://$ cd /
hacker@paths~position-elsewhere:/$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{M1fTofpdbnE21YFfJ31YA5R4e-t.ddDN1QDLyczN1czW}
```
Challenge 5-
Approach same as challenge 3
```bash
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/include directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /usr/include
hacker@paths~position-yet-elsewhere:/usr/include$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{QVmLET9pW2o7noc9ZTl_y_kQfMH.dhDN1QDLyczN1czW}
```
Challenge 6-
Used help from https://www.educba.com/linux-relative-path/ to figure out syntax.
```bash
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{Y3acL23MCrDkTcVZDQJdCq4HsUG.dlDN1QDLyczN1czW}
```
Challenge 7-
Learnt to use explicit directory, after initially misunderstanding the question.
```bash
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./
ssh-entrypoint: ./: Is a directory
hacker@paths~explicit-relative-paths-from-:/$ cd ./
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{QpdTmCRjZ1umzKneV2sLUhbT-wT.dBTN1QDLyczN1czW}
```
Challenge 8-
Learnt the use of explicit pathing where we tell linux what we want, so it does not accidentally execute a code under the same name.
```bash
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ .run
ssh-entrypoint: .run: command not found
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{QNoO8lVw5YDgi_OAaE9ytyO9cYG.dFTN1QDLyczN1czW}
```


