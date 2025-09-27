# Comprehending Commands
  This module will introduce various commands in linux OS. 
## Challenge 1: cat: not the pet, but the command
 learn about *cat* command

### My solve
**Flag:** `pwn.college{4ti6WTMOgUk7Nk9gHPu7Xx9o8lq.QXxcTN0wCM3gjNzEzW}`
The flag is stored in a "flag" file in the home directory (given), thus to capture the flag it, we simply need to read the "flag" file

```bash
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{4ti6WTMOgUk7Nk9gHPu7Xx9o8lq.QXxcTN0wCM3gjNzEzW}
```

### What I learned
"cat" is a command in linux which helps us read files. If multiple arguments are given (for example "cat a b"), it will concatenate the files (giving a and b files output together). 
**Note** By default (if no arguments are given in cat command), then the output will be read from the terminal input


## Challenge 2: Catting absolute paths
   cat (or read) files from absolute paths
### My solve
**Flag:** `pwn.college{A8wmh-H8h6KQ5tJzmjE9PH8TyXc.QX5ETO0wCM3gjNzEzW}`

The flag is not stored in the home directory. Thus, we need to use absolute paths to access it.

```bash
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{A8wmh-H8h6KQ5tJzmjE9PH8TyXc.QX5ETO0wCM3gjNzEzW}
```

### What I learned
Since the flag is stored in the absolute file "/flag", we need to change our cat command arguments. 
- One way to access the file is by changing the directory, but since we need to learn how to use "cat" command, we shall not use "cd"
- Thus, we can read the flag file by using the absolute path "/flag" as its argument.

### References 
no references

## Challenge 3: More catting practice
  exploring different paths as aruments for "cat" command
### My solve
**Flag:** `pwn.college{0jtWyebZLebC-HQH-azYATBMk8n.QXwITO0wCM3gjNzEzW}`

 The file in which the flag is stored is already given to us. Thus, I can read the file by using cat command, follwed by the absolute path.

```bash
You cannot use the 'cd' command in this level, and must retrieve the flag by 
absolute path. Plus, I hid the flag in a different directory! You can find it 
in the file /usr/share/application-registry/flag. Go cat it out **without** 
cding into that directory!
hacker@commands~more-catting-practice:~$ cat /usr/share/application-registry/flag
pwn.college{0jtWyebZLebC-HQH-azYATBMk8n.QXwITO0wCM3gjNzEzW}
```

### What I learned
By editing the arguments, we can read any directory that we want from the absolute paths.

## Challenge 4: grepping for a needle in a haystack
  learning about the "grep" command
### My solve
**Flag:** `pwn.college{sky-S65m0rxTRGlCZLO1SstEX8W.QX3EDO0wCM3gjNzEzW}`

We need to search for the flag in the thousands of lines of text stored in the data.txt file. 
- We know that all flags begin with "pwn.college", thus we can use the grep comman to search for our flag.

```bash
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{sky-S65m0rxTRGlCZLO1SstEX8W.QX3EDO0wCM3gjNzEzW}
```

### What I learned
When "cat" files are too big, it is very difficult to read through the entire thing to get to what we want. This is where the "grep" command come into place.
- "grep" helps us search for the contents we need.
- the syntax to use grep here is "~$ grep (string to search) /(path)"


 ## Challenge 5: comparing files
  to compare to files using "diff" command
### My solve
**Flag:** `pwn.college{o4VXDHCSweyN-R-kaWlS5FK2Jbk.01MwMDOxwCM3gjNzEzW}`

We are given that the first file has 100 fake flags and second file has 100 fake plus one real file. So finding the difference between the both of them, will help us find the real flag.

```bash
hacker@commands~comparing-files:~$ diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt
61a62
> pwn.college{o4VXDHCSweyN-R-kaWlS5FK2Jbk.01MwMDOxwCM3gjNzEzW}
```

### What I learned
- *diff* command helps differentiate between the contents of 2 files. It compares the files and shows us exactly what is different and where in the file it is located.
- In the above solve, 61a62 means that after the 61st line of file 1, the second file has an additional line (which is the 62nd line of file 2). *'a' means added*
- if it was something like 61c61, it would mean that the 62nd line of both files are not matching. *'c' means compared* 



## Challenge 6: listing files:
 command "ls" lists the files in the directory given as argument

### My solve
**Flag:** `pwn.college{IKIK2WeTrXlyTzqAtIpxyW06Sbs.QX4IDO0wCM3gjNzEzW}`

In this challenge, the flag is not in the *run* file like before. It has been hidden in some other file, which I need to find by listing the files in the *challenge* directory.

```bash
hacker@commands~listing-files:~$ ls /challenge
10705-renamed-run-733  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/10705-renamed-run-733
Yahaha, you found me! Here is your flag:
pwn.college{IKIK2WeTrXlyTzqAtIpxyW06Sbs.QX4IDO0wCM3gjNzEzW}
``` 

### What I learned
- I gave the "ls" command with "/challenge" as the argument. This means that i want to *list* the files in the *challenge* directory.  
- Using *ls* without an argument, will list all the files in the current directory.

## Challenge 7: touching files
   Creating files
### My solve
**Flag:** `pwn.college{EIshbIZijNPGnVD2w7ighWtpJuK.QXwMDO0wCM3gjNzEzW}`

- We need to create */pwn* and */college* files in */tmp* directory. Thus, we need to first go inside */tmp* by using *cd* command. Then, we can create the files using *touch* command.
- Only if both the files are created, will the */challenge/run* file run and flag be obtained. 

```bash
hacker@commands~touching-files:~$ cd /tmp
hacker@commands~touching-files:/tmp$ touch pwn
hacker@commands~touching-files:/tmp$ touch college
hacker@commands~touching-files:/tmp$ cd 
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{EIshbIZijNPGnVD2w7ighWtpJuK.QXwMDO0wCM3gjNzEzW}
```

### What I learned
- We use *touch* command to create files
- By default, the new file created is blank (does not have any content in it)

### References 
- https://pwn.college/linux-luminarium/commands/ [Module- Comprehending commands]

## Challenge 8: Removing files
   using *rm* command to delete (remove) files
### My solve
**Flag:** `pwn.college{wMpXFVKxzuZwcz_8chR838QxUGt.QX2kDM1wCM3gjNzEzW}`

removed *delete_me* file from the home directory, then ran the */challenge/check* program. This checked if the *delete_me* file is still present and accordingly gave me the flag.

```bash
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{wMpXFVKxzuZwcz_8chR838QxUGt.QX2kDM1wCM3gjNzEzW}
```

### What I learned
- *rm* command is used to delete files from the current directory.
- This is useful when there are a large number of files in a directory which no longer have a use.


## Challenge 9: moving files
  Moving files from one place to another
### My solve
**Flag:** `pwn.college{kwbEN42t9dqNUBj1CieOaP-mzfF.0VOxEzNxwCM3gjNzEzW}`

The flag is originally stored in */flag*. I moved it to the */tmp/hack-the-planet* file using *mv* command, then ran the */challenge/check* program, which checked if the file is moved correctly, and accrodingly gave me the flag.

```bash
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet
Correct! Performing 'mv /flag /tmp/hack-the-planet'.
hacker@commands~moving-files:~$ /challenge/check
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
pwn.college{kwbEN42t9dqNUBj1CieOaP-mzfF.0VOxEzNxwCM3gjNzEzW}
```

### What I learned
- Files can be moved from one place to another using the *mv* command.
- two arguments need to be given along with the command i.e., the place from which it needs to be moved, and the place where it needs to move to.
- Thus, syntax will be *mv (file from) (file to)*

## Challenge 10: hidden files
  access hidden files in directory
### My solve
**Flag:** `pwn.college{0dfDNW9xyjzC-Vsdt0GZQBewvEu.QXwUDO0wCM3gjNzEzW}`

Entered the */* directory and listed all files in it (including the hidden files). Read the *.flag* file to find the flag

```bash
hacker@commands~hidden-files:~$ cd /
hacker@commands~hidden-files:/$ ls -a
.   .dockerenv            bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-13684313621531  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:/$ cat .flag-13684313621531
pwn.college{0dfDNW9xyjzC-Vsdt0GZQBewvEu.QXwUDO0wCM3gjNzEzW}
```

### What I learned
- *ls* does not list all the files in the directory when invoked. It does not shows the "." files, making them hidden files.
- In order to list these hidden files, we need to use *list -a* command

## Challenge 11: An epic Filesystem Quest
  Find the hidden flag by following clues
### My solve
**Flag:** `pwn.college{QlcYWq6Mg_M4hy4EnVqhChlYLMp.QX5IDO0wCM3gjNzEzW}`



```bash
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls
MESSAGE  boot       dev  flag  lib    lib64   media  nix  proc  run   srv  tmp  var
bin      challenge  etc  home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~an-epic-filesystem-quest:/$ cat MESSAGE
Great sleuthing!
The next clue is in: /opt/linux/linux-5.4/Documentation/devicetree/bindings/iio/multiplexer

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/$ cd opt/linux/linux-5.4/Documentation/devicetree/bindings/iio/multiplexer
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/Documentation/devicetree/bindings/iio/multiplexer$ ls
LEAD  io-channel-mux.txt
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/Documentation/devicetree/bindings/iio/multiplexer$ cat LEAD
Great sleuthing!
The next clue is in: /opt/linux/linux-5.4/include/config/drm/fbdev

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/Documentation/devicetree/bindings/iio/multiplexer$ cd /opt/linux/linux-5.4/include/config/drm/fbdev
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/include/config/drm/fbdev$ ls -a
.  ..  .DISPATCH  emulation.h  overalloc.h
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/include/config/drm/fbdev$ cat .DISPATCH
Great sleuthing!
The next clue is in: /usr/local/etc/jupyter/nbconfig

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/include/config/drm/fbdev$ cd /usr/local/etc/jupyter/nbconfig
hacker@commands~an-epic-filesystem-quest:/usr/local/etc/jupyter/nbconfig$ ls -a
.  ..  .REVELATION  notebook.d
hacker@commands~an-epic-filesystem-quest:/usr/local/etc/jupyter/nbconfig$ cat .REVELATION
Congratulations, you found the clue!
The next clue is in: /opt/linux/linux-5.4/tools/perf/arch/x86/tests
hacker@commands~an-epic-filesystem-quest:/usr/local/etc/jupyter/nbconfig$ cd /opt/linux/linux-5.4/tools/perf/arch/x86/tests
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/tools/perf/arch/x86/tests$ ls
Build   arch-tests.c  dwarf-unwind.c        gen-insn-x86-dat.sh  insn-x86-dat-64.c   insn-x86.c   intel-pt-pkt-decoder-test.c  rdpmc.c
README  bp-modify.c   gen-insn-x86-dat.awk  insn-x86-dat-32.c    insn-x86-dat-src.c  intel-cqm.c  perf-time-to-tsc.c           regs_load.S
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/tools/perf/arch/x86/tests$ cat README
Great sleuthing!
The next clue is in: /usr/share/doc/libxcb1

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/tools/perf/arch/x86/tests$ cd /usr/share/doc/libxcb1
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/libxcb1$ ls -a
.  ..  .SECRET  changelog.Debian.gz  copyright
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/libxcb1$ cat .SECRET
Yahaha, you found me!
The next clue is in: /opt/linux/linux-5.4/drivers/firmware/google

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/libxcb1$ cat /opt/linux/linux-5.4/drivers/firmware/google
cat: /opt/linux/linux-5.4/drivers/firmware/google: Is a directory
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/libxcb1$ ls /opt/linux/linux-5.4/drivers/firmware/google
INFO-TRAPPED  Makefile          coreboot_table.h        gsmi.c                 memconsole-x86-legacy.c  memconsole.h  vpd_decode.c
Kconfig       coreboot_table.c  framebuffer-coreboot.c  memconsole-coreboot.c  memconsole.c             vpd.c         vpd_decode.h
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/libxcb1$ cat /opt/linux/linux-5.4/drivers/firmware/google/INFO-TRAPPED
Lucky listing!
The next clue is in: /usr/libexec
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/libxcb1$ cd /usr/libexec
hacker@commands~an-epic-filesystem-quest:/usr/libexec$ ls
SPOILER  dconf-service  glib-pacrunner  neovim  valgrind
hacker@commands~an-epic-filesystem-quest:/usr/libexec$ cat SPOILER
Lucky listing!
The next clue is in: /opt/linux/linux-5.4/tools/arch/powerpc/include/uapi

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/usr/libexec$ cd /opt/linux/linux-5.4/tools/arch/powerpc/include/uapi
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/tools/arch/powerpc/include/uapi$ ls
MEMO  asm
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/tools/arch/powerpc/include/uapi$ cat MEMO
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{QlcYWq6Mg_M4hy4EnVqhChlYLMp.QX5IDO0wCM3gjNzEzW}
```

### What I learned
- Revised all the commands learnt so far.

## Challenge 12: making directories
 create directories
### My solve
**Flag:** `pwn.college{gtVYPM8ZQVUyIWJgXH6PeXdt4oZ.QXxMDO0wCM3gjNzEzW}`

made a Directory */tmp/pwn*. Then entered the directory using *cd* command (since the file needs to be created inside he directory). Created a file using *touch* command and then ran the */challenge/run* file to get the flag.

```bash
hacker@commands~making-directories:~$ mkdir /tmp/pwn
hacker@commands~making-directories:~$ cd /tmp/pwn
hacker@commands~making-directories:/tmp/pwn$ touch college
hacker@commands~making-directories:/tmp/pwn$ cd 
hacker@commands~making-directories:~$ /challenge/run
Success! Here is your flag:
pwn.college{gtVYPM8ZQVUyIWJgXH6PeXdt4oZ.QXxMDO0wCM3gjNzEzW}
```

### What I learned
- The command to create new directories is *mkdir* follwed by the directory name as argument
- This command cannot be used to create files. Files need to be created using *touch* command.

## Challenge 13: finding files
  Search for a file using *find* command
### My solve
**Flag:** `pwn.college{cT5rKRMMJaxADWB8qIpPcH7pWdt.QXyMDO0wCM3gjNzEzW}`

I searched for the flag in */* directory by specifying the name of file *flag*.
This gave me various files, for many of which access was denied.
I entered the directories I was allowed to as a user, which gave me the flag

```bash
hacker@commands~finding-files:~$ cd /
hacker@commands~finding-files:/$ find -name flag
find: ‘./tmp/tmp.TpSOPGOVKK’: Permission denied
find: ‘./etc/ssl/private’: Permission denied
./usr/lib/python3/dist-packages/cryptography/hazmat/primitives/serialization/__pycache__/flag
./usr/local/lib/python3.8/dist-packages/pwnlib/flag
find: ‘./var/cache/apt/archives/partial’: Permission denied
find: ‘./var/cache/ldconfig’: Permission denied
find: ‘./var/cache/private’: Permission denied
find: ‘./var/lib/apt/lists/partial’: Permission denied
find: ‘./var/lib/mysql-files’: Permission denied
find: ‘./var/lib/private’: Permission denied
find: ‘./var/lib/mysql’: Permission denied
find: ‘./var/lib/mysql-keyring’: Permission denied
find: ‘./var/lib/php/sessions’: Permission denied
find: ‘./var/log/private’: Permission denied
find: ‘./var/log/apache2’: Permission denied
find: ‘./var/log/mysql’: Permission denied
find: ‘./run/mysqld’: Permission denied
find: ‘./run/sudo’: Permission denied
find: ‘./root’: Permission denied
./opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
find: ‘./proc/tty/driver’: Permission denied
find: ‘./proc/1/task/1/fd’: Permission denied
find: ‘./proc/1/task/1/fdinfo’: Permission denied
find: ‘./proc/1/task/1/ns’: Permission denied
ind: ‘./proc/7/map_files’: Permission denied
find: ‘./proc/7/fdinfo’: Permission denied
find: ‘./proc/7/ns’: Permission denied
./nix/store/ka6xbd6z6wj5d6frl7ym4nzfc6p2wkdx-radare2-5.9.8/share/radare2/5.9.8/flag
./nix/store/f31j0igg7ms3yrj5gm3cm76bjcmdl8w5-python3.12-pwntools-4.13.1/lib/python3.12/site-packages/pwnlib/flag
./nix/store/7ns27apnvn4qj4q5c82x0z1lzixrz47p-radare2-5.9.8/share/radare2/5.9.8/flag
./nix/store/5z3sjp9r463i3siif58hq5wj5jmy5m98-python3.12-pwntools-4.13.1/lib/python3.12/site-packages/pwnlib/flag
./nix/store/n6vb30rd7kkwjj595pgm0dmsmfaqi6i5-rizin-0.7.3/share/rizin/flag
./nix/store/5n5lp1m8gilgrsriv1f2z0jdjk50ypcn-rizin-0.7.3/share/rizin/flag
./nix/store/bnlabj2vsbljhp597ir29l51nrqhm89w-rizin-0.7.4/share/rizin/flag
./nix/store/s8b49lb0pqwvw0c6kgjbxdwxcv2bp0x4-radare2-5.9.8/share/radare2/5.9.8/flag
./nix/store/8qvj9mzdq2qxgjigw4ysqgbkcx1zi80y-python3.13-pwntools-4.14.1/lib/python3.13/site-packages/pwnlib/flag
./nix/store/1hyxipvwpdpcxw90l5pq1nvd6s6jdi5m-python3.12-pwntools-4.14.1/lib/python3.12/site-packages/pwnlib/flag
./nix/store/dz2qxywk6d8hc1gkarpwbhyxb50sh2ak-pwntools-4.14.0/lib/python3.13/site-packages/pwnlib/flag
hacker@commands~finding-files:/$ cd flag
bash: cd: flag: No such file or directory
hacker@commands~finding-files:/$ find ./usr -name flag
./usr/lib/python3/dist-packages/cryptography/hazmat/primitives/serialization/__pycache__/flag
./usr/local/lib/python3.8/dist-packages/pwnlib/flag
hacker@commands~finding-files:/$ cd ./usr/lib/python3/dist-packages/cryptography/hazmat/primitives/serialization/__pycache__/flag
bash: cd: ./usr/lib/python3/dist-packages/cryptography/hazmat/primitives/serialization/__pycache__/flag: Not a directory
hacker@commands~finding-files:/$ cd ./usr/lib/python3/dist-packages/cryptography/hazmat/primitives/serialization/__pycache__
hacker@commands~finding-files:/usr/lib/python3/dist-packages/cryptography/hazmat/primitives/serialization/__pycache__$ cat flag
pwn.college{cT5rKRMMJaxADWB8qIpPcH7pWdt.QXyMDO0wCM3gjNzEzW}
```

### What I learned
- using *find* command without any argument will search the entire filesystem
- we can specify the criteria of searching by using *-(criteria)*
- we can also search a particular location by specifying the location.

## Challenge 14: linking files
  How to link one file to another.
### My solve
**Flag:** `pwn.college{Y4Ltk8PPS4RcCmquBMnLJ4LFYj8.QX5ETN1wCM3gjNzEzW}`

Since, *~/not-the-flag* already existed, I first deleted it in order to create the symlink. Then I created a symlink to */flag* and ran */challenge/catflag*

```bash
hacker@commands~linking-files:~$ ln -s /flag not-the-flag
ln: failed to create symbolic link 'not-the-flag': File exists
hacker@commands~linking-files:~$ rm ~/not-the-flag
hacker@commands~linking-files:~$ ln -s /flag not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{Y4Ltk8PPS4RcCmquBMnLJ4LFYj8.QX5ETN1wCM3gjNzEzW}

```

### What I learned
1. links are used when we want to acces the same file from two different paths. 
2. there are two types of links: Hard and Soft links
  - Hard links: directly lead you to the file you want to go to
  - Soft links: simply reference the file you want (or gives you its name)
3. Soft links (symlinks/ symbolic links) are created using *ln -s*, while hard links are created using *ln* only.
4. syntax for sym links is *ln -s (original path)(linkpath)*

### references
https://www.youtube.com/watch?v=m55AtwjBXpE&list=PL-ymxv0nOtqqRAz1x90vxNbhmSkeYxHVC
   