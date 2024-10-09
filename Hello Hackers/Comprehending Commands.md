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
Challenge 8-
Found the hidden flag file by listing out hidden files too using ls -a.
Then I used cat command to display it.
```bash
hacker@commands~hidden-files:~$ cd /
hacker@commands~hidden-files:/$ ls -a
.   .dockerenv            bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-26067198225605  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:/$ cd /tmp
hacker@commands~hidden-files:/tmp$ /challenge/run
There's no flag here for you! I made the flag readable but hid it as a .-prepended file in the / directory. Go find it!
hacker@commands~hidden-files:/$ cat /.flag-26067198225605
pwn.college{0q00QEMDGfqSYFs6TwlSkrFYyfa.dBTN4QDLyczN1czW}
hacker@commands~hidden-files:/$
```
Challenge 9- 
THE MOST FUN I've had here so far, after trial and error of reading and searching through files using cat, ls, ls -a, cd, and parsing through the files for the clues, i found the flag.

```bash
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls
TIP  boot       dev  flag  lib    lib64   media  nix  proc  run   srv  tmp  var
bin  challenge  etc  home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~an-epic-filesystem-quest:/$ ls -a
.   .dockerenv  bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
..  TIP         boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@commands~an-epic-filesystem-quest:/$ cat /flag
cat: /flag: Permission denied
hacker@commands~an-epic-filesystem-quest:/$ cat /TIP
Great sleuthing!
The next clue is in: /opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/encoders/arm
hacker@commands~an-epic-filesystem-quest:/$ cat //opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/encoders/arm
cat: //opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/encoders/arm: Is a directory
hacker@commands~an-epic-filesystem-quest:/$ cat /opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/encoders/arm
cat: /opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/encoders/arm: Is a directory
hacker@commands~an-epic-filesystem-quest:/$ cat /opt
cat: /opt: Is a directory
hacker@commands~an-epic-filesystem-quest:/$ ls /opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/encoders/arm
INSIGHT  __init__.py  __pycache__  alphanumeric  xor.py
hacker@commands~an-epic-filesystem-quest:/$ ls /INSIGHT
ls: cannot access '/INSIGHT': No such file or directory
hacker@commands~an-epic-filesystem-quest:/$ cat /INSIGHT
cat: /INSIGHT: No such file or directory
hacker@commands~an-epic-filesystem-quest:/$ cat /opt/INSIGHT
cat: /opt/INSIGHT: No such file or directory
hacker@commands~an-epic-filesystem-quest:/$ cat /opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/encoders/arm/INSIGHT
Congratulations, you found the clue!
The next clue is in: /usr/lib/python3/dist-packages/matplotlib/sphinxext/__pycache__

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/$ cd /usr/lib/python3/dist-packages/matplotlib/sphinxext/__pycache__
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/matplotlib/sphinxext/__pycache__$ ls
CUE  __init__.cpython-38.pyc  mathmpl.cpython-38.pyc  plot_directive.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/matplotlib/sphinxext/__pycache__$ cat CUE
Congratulations, you found the clue!
The next clue is in: /usr/lib/ruby/2.7.0/reline

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/matplotlib/sphinxext/__pycache__$ ls /usr/lib/ruby/2.7.0/reline
MESSAGE-TRAPPED  config.rb      history.rb  key_actor.rb   kill_ring.rb    unicode     version.rb
ansi.rb          general_io.rb  key_actor   key_stroke.rb  line_editor.rb  unicode.rb  windows.rb
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/matplotlib/sphinxext/__pycache__$ cat /usr/lib/ruby/2.7.0/reline/MESSAGE-TRAPPED
Great sleuthing!
The next clue is in: /opt/pwndbg/.venv/lib/python3.8/site-packages/rpyc/cli/__pycache__

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/matplotlib/sphinxext/__pycache__$ ls /opt/pwndbg/.venv/lib/python3.8/site-packages/rpyc/cli/__pycache__
__init__.cpython-38.pyc  rpyc_classic.cpython-38.pyc  rpyc_registry.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/matplotlib/sphinxext/__pycache__$ ls opt/pwndbg/.venv/lib/pyt
hon3.8/site-packages/rpyc/cli/__pycache__
ls: cannot access 'opt/pwndbg/.venv/lib/python3.8/site-packages/rpyc/cli/__pycache__': No such file or directory
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/matplotlib/sphinxext/__pycache__$ ls -a
.  ..  CUE  __init__.cpython-38.pyc  mathmpl.cpython-38.pyc  plot_directive.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/matplotlib/sphinxext/__pycache__$ cd /opt/pwndbg/.venv/lib/python3.8/site-packages/rpyc/cli/__pycache__
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/rpyc/cli/__pycache__$ ls -a
.  ..  .HINT  __init__.cpython-38.pyc  rpyc_classic.cpython-38.pyc  rpyc_registry.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/rpyc/cli/__pycache__$ cat .HINT
Lucky listing!
The next clue is in: /opt/radare2/libr
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/rpyc/cli/__pycache__$ cd /opt/radare2/libr
hacker@commands~an-epic-filesystem-quest:/opt/radare2/libr$ ls
Makefile    bin            config.h.in     cons      depgraph.pl  fs         libr.pc.acr             meson.build  stripsyms.sh
REVELATION  bp             config.h.tail   core      do-ar-sh     include    libs.custom.mk.example  reg          symgraph.pl
anal        config         config.mk       count.sh  egg          io         libs.mk                 rules.mk     syscall
arch        config.h       config.mk.head  crypto    esil         lang       magic                   search       util
asm         config.h.head  config.mk.tail  debug     flag         ld.script  main                    socket
hacker@commands~an-epic-filesystem-quest:/opt/radare2/libr$ cat REVELATION
Congratulations, you found the clue!
The next clue is in: /usr/lib/x86_64-linux-gnu/perl-base/unicore/lib/PCM

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/opt/radare2/libr$ cd  /usr/lib/x86_64-linux-gnu/perl-base/unicore/lib/PCM
hacker@commands~an-epic-filesystem-quest:/usr/lib/x86_64-linux-gnu/perl-base/unicore/lib/PCM$ ls -a
.  ..  .README  Y.pl
hacker@commands~an-epic-filesystem-quest:/usr/lib/x86_64-linux-gnu/perl-base/unicore/lib/PCM$ cat .README
Congratulations, you found the clue!
The next clue is in: /opt/aflplusplus/qemu_mode/qemuafl/scripts/tracetool

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/usr/lib/x86_64-linux-gnu/perl-base/unicore/lib/PCM$ cd /opt/aflplusplus/qemu_mode/qemuafl/scripts/tracetool
hacker@commands~an-epic-filesystem-quest:/opt/aflplusplus/qemu_mode/qemuafl/scripts/tracetool$ ls
BLUEPRINT  __init__.py  backend  format  transform.py  vcpu.py
hacker@commands~an-epic-filesystem-quest:/opt/aflplusplus/qemu_mode/qemuafl/scripts/tracetool$ cat BLUEPRINT
Great sleuthing!
The next clue is in: /usr/share/javascript/mathjax/unpacked/jax/output/HTML-CSS/fonts/Latin-Modern/Size7

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/opt/aflplusplus/qemu_mode/qemuafl/scripts/tracetool$ cd  /usr/share/javascript/mathjax/unpacked/jax/output/HTML-CSS/fonts/Latin-Modern/Size7
ssh-entrypoint: CLUE-TRAPPED: Permission denied
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/mathjax/unpacked/jax/output/HTML-CSS/fonts/Latin-Modern/Size7$ ls
ssh-entrypoint: CLUE-TRAPPED: Permission denied
CLUE-TRAPPED  Regular
ssh-entrypoint: CLUE-TRAPPED: Permission denied
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/mathjax/unpacked/jax/output/HTML-CSS/fonts/Latin-Modern/Size7$ cat CLUE-TRAPPED
ssh-entrypoint: CLUE-TRAPPED: Permission denied
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{8bdYlXTg29CqpwdVzl1TphRAOIb.dljM4QDLyczN1czW}
```
Challenge 10-
learnt how to create a directory and then created a file in it then ran /challenge/run. 
Obtained the flag. I had initially checked for pwn inside of temp.
```bash
hacker@commands~making-directories:~$ cd /tmp
hacker@commands~making-directories:/tmp$ ls
bin  hsperfdata_root  tmp.MiOQGWw5Zc
hacker@commands~making-directories:/tmp$ mkdir pwn
hacker@commands~making-directories:/tmp$ ls
bin  hsperfdata_root  pwn  tmp.MiOQGWw5Zc
hacker@commands~making-directories:/tmp$ cd /tmp/pwn
hacker@commands~making-directories:/tmp/pwn$ touch college
hacker@commands~making-directories:/tmp/pwn$ /challenge/run
Success! Here is your flag:
pwn.college{g3FwaO9O36_8wyAoSVEiAvysYM4.dFzM4QDLyczN1czW}
```
Challenge 11-
Learnt how to use the find command, parsed through the directories named with "flag" used trial and error method and it worked for the fourth directory.
```bash
hacker@commands~finding-files:~$ find / -name flag
find: ‘/tmp/tmp.MiOQGWw5Zc’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
/usr/local/lib/python3.8/dist-packages/pwnlib/flag
/usr/local/share/radare2/5.9.5/flag
/usr/share/javascript/mathjax/unpacked/jax/output/SVG/fonts/TeX/AMS/flag
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/mysql-files’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/mysql’: Permission denied
find: ‘/var/lib/mysql-keyring’: Permission denied
find: ‘/var/lib/php/sessions’: Permission denied
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/apache2’: Permission denied
find: ‘/var/log/mysql’: Permission denied
find: ‘/run/mysqld’: Permission denied
find: ‘/run/sudo’: Permission denied
find: ‘/root’: Permission denied
/opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
/opt/radare2/libr/flag
find: ‘/proc/tty/driver’: Permission denied
find: ‘/proc/1/task/1/fd’: Permission denied
find: ‘/proc/1/task/1/fdinfo’: Permission denied
find: ‘/proc/1/task/1/ns’: Permission denied
find: ‘/proc/1/fd’: Permission denied
find: ‘/proc/1/map_files’: Permission denied
find: ‘/proc/1/fdinfo’: Permission denied
find: ‘/proc/1/ns’: Permission denied
find: ‘/proc/7/task/7/fd’: Permission denied
find: ‘/proc/7/task/7/fdinfo’: Permission denied
find: ‘/proc/7/task/7/ns’: Permission denied
find: ‘/proc/7/fd’: Permission denied
find: ‘/proc/7/map_files’: Permission denied
find: ‘/proc/7/fdinfo’: Permission denied
find: ‘/proc/7/ns’: Permission denied
/nix/store/1yagn5s8sf7kcs2hkccgf8d0wxlrv5sz-radare2-5.9.0/share/radare2/5.9.0/flag
/nix/store/pmvk2bk4p550w182rjfm529kfqddnvh3-python3.11-pwntools-4.12.0/lib/python3.11/site-packages/pwnlib/flag
hacker@commands~finding-files:~$ cat /usr/share/javascript/mathjax/unpacked/jax/output/SVG/fonts/TeX/AMS/flag
```
Challenge 12-
```bash
hacker@commands~linking-files:~$ ln -sf /flag /home/hacker/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{Uqfn7W-DDXiCQgwlKrbxYoWpoD4.dlTM1UDLyczN1czW}
```
