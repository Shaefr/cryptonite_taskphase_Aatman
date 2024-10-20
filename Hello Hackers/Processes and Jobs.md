# Challenge 1 | LISTING PROCESSES
In this challenge, we are introduced to the "ps" command, which stands for "process snapshot" or "process status".
On its own, its not a very useful command and it by default just lists out the processes running on our terminal.
Therefore, to make the old ps a little more useful, there are 2 syntaxes we learn here that give us a better idea of seeing every process in full format. This is using "-ef".
A similar but not the exact same command, known as "aux" helps to list processes for all users, list processes that arent running in a terminal, in a user legible manner. This is using "aux".
"ps -ef" outputs the Parent Process ID (PPID), which is the PID of the process that launched the one in question (and this is not done by aux), while ps aux outputs the percentage of total system CPU and Memory that the process is utilizing (which is not done by ps -ef).
Note- both -ef and aux take part in truncation of the command listing.
For this challenge, the file was not available using ls, but we were told it was up and running, which hinted we could find it using listing out the processes.
PIDs are process identifiers which help in killing a process we dont want.
```bash
hacker@processes~listing-processes:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.1  0.0   1056   640 ?        Ss   13:58   0:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bin/dojo-init /
root           7  0.0  0.0   5052  2560 ?        S    13:58   0:00 /run/dojo/bin/sleep 6h
root          68  0.0  0.0   4132  2560 ?        S    13:58   0:00 /challenge/28089-run-19248
root          72  0.0  0.0   2744  1600 ?        S    13:58   0:00 sleep 6h
hacker        73  0.1  0.0   5240  4160 pts/0    Ss   13:58   0:00 /run/dojo/bin/ssh-entrypoint
hacker        90  0.0  0.0   7868  3520 pts/0    R+   13:59   0:00 ps aux
hacker@processes~listing-processes:~$ /challenge/28089-run-19248
Yahaha, you found me! Here is your flag:
pwn.college{czcXYzJAr8UsjCzoHO19RI1aTiX.dhzM4QDLyczN1czW}
```
# Challenge 2 | Killing Processes
To end an unwanted running process, we can use the "kill command".
PIDs are process identifiers which help in killing a process we dont want.
"kill" will terminate a process in a way that gives it a chance to get its affairs in order before ceasing to exist.
For this challenge, i searched for running processes, found the PID of the unwanted program dont_run, killed it, checked for its existence, then ran /challenge/run.
```bash
hacker@processes~killing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 14:12 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bin/dojo-init /run/dojo/bin/sl
root           7       1  0 14:12 ?        00:00:00 /run/dojo/bin/sleep 6h
root          71       1  0 14:12 ?        00:00:00 su -c /challenge/.launcher hacker
hacker        73      71  0 14:12 ?        00:00:00 /challenge/dont_run
hacker        74      73  0 14:12 ?        00:00:00 sleep 6h
hacker        75       0  0 14:12 pts/0    00:00:00 /run/dojo/bin/ssh-entrypoint
hacker        92      75  0 14:12 pts/0    00:00:00 ps -ef
hacker@processes~killing-processes:~$ kill 73
hacker@processes~killing-processes:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.0   1056   640 ?        Ss   14:12   0:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bin/dojo-init /
root           7  0.0  0.0   5052  2240 ?        S    14:12   0:00 /run/dojo/bin/sleep 6h
hacker        74  0.0  0.0   5052  2240 ?        S    14:12   0:00 sleep 6h
hacker        75  0.0  0.0   5372  4160 pts/0    Ss   14:12   0:00 /run/dojo/bin/ssh-entrypoint
hacker        93  0.0  0.0   7868  3520 pts/0    R+   14:13   0:00 ps aux
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{8lriCVGrLr0uNnB0R-xPyKr7bhW.dJDN4QDLyczN1czW}
```
# Challenge 3 | Interrupting Processes
An interupting hotkey for processes that clog up the terminal is CTRL-C.
This allows the application to cleanly exit.
```bash
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{Y8qd35DlY-YyQOfeH29KLvCBVNx.dNDN4QDLyczN1czW}
```
# Challenge 4 | Suspending Processes
A less drastic measure to get our terminal back is "CTRL-Z" used to suspend processes.
For the challenge, i was told to invoke the run program, suspend it, then start another one.
Since the process is still showing, it means that it hasnt been killed, just temporarily halted but still "run-able".
```bash
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          84      67  0 14:34 pts/0    00:00:00 bash /challenge/run
root          86      84  0 14:34 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can
background me with Ctrl-Z or, if you're not ready to do that for whatever
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          84      67  0 14:34 pts/0    00:00:00 bash /challenge/run
root          91      67  0 14:34 pts/0    00:00:00 bash /challenge/run
root          93      91  0 14:34 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{AJolzSS96tSUeJUODXbYFbGbapr.dVDN4QDLyczN1czW}
```
# Challenge 5 | Resuming Processes
As mentioned earlier, suspendable processes can be resumed again. The fg builtin allows us to do so. fg sends it to the "foreground" again.
```bash
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{w5WxjcoZET6GotmO0-8LT81uOdR.dZDN4QDLyczN1czW}
Don't forget to press Enter to quit me!

Goodbye!
```
# Challenge 6 | Bakcgrounding Processes
There exists a bg command builtin, which allows the process to work in the backgroud and returns us the shell to invoke more commands.
It doesnt allow a process to keep staying suspended, and allows it to run behind the scenes.
T- means suspended.
R+ means actively running in the foreground.
Ss means sleeping until used.
For this challenge, i ran the run program, suspended it, then ran it in the bg and invoked another one to get the flag.
```bash
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          84 S+   bash /challenge/run
root          86 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the
background, and then launch a new version of me! You can background me with
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &
Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out.

hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!
UID          PID STAT CMD
root          84 S    bash /challenge/run
root          94 S    sleep 6h
root          95 S+   bash /challenge/run
root          97 R+   ps -o user=UID,pid,stat,cmd
Yay, I found another version of me running in the background! Here is the flag:
pwn.college{AwQrd_11gKtnEzlApzDoEQrtQmK.ddDN4QDLyczN1czW}
```
# Challenge 7 | Foregrounding Background Processes
We can foreground a background running process using fg.
Here, i ran /challenge/run, suspended it, ran it in the bg, then brought it to fg.
```bash
hacker@processes~foregrounding-processes:~$ fg
ssh-entrypoint: fg: current: no such job
hacker@processes~foregrounding-processes:~$ bg
ssh-entrypoint: bg: current: no such job
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the
background, and *then* foreground it without re-suspending it! You can
background me with Ctrl-Z (and resume me in the background with 'bg') or, if
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &

Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out. After that, resume me into the foreground with 'fg';
I'll wait.
hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{k7JXVGLKhdP-GMsRHnW9evt8OHI.dhDN4QDLyczN1czW}
```
# Challenge 8 | Starting BG Processes
As i noticed, hamesha suspending a process to then move it to the bg seemed a little inefficient.
Thankfully our super handsome seniors from cryptonite also noticed it and taught us a shortcut.
This is done by appending a "&" to the end of the command line.
This challenge made me run /challenge/run backgrounded, which i did in one line itself and got the flag.
This sent the process to the bg right of the bat instead of having to manually move it there.
```bash
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 82
Yay, you started me in the background! Because of that, this text will probably
overlap weirdly with the shell prompt, but you're used to that by now...
hacker@processes~starting-backgrounded-processes:~$
Anyways! Here is your flag!
pwn.college{4Y2DZbdrJe1xQSzReL3MoFIjcSE.dlDN4QDLyczN1czW}
```
# Challenge 9 | 
