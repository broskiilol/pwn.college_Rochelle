# Perceiving Permissions
 
## Challenge 1: Changing file ownership

### My solve
**Flag:** `pwn.college{kX_TmNgPWsCwcZP3svNw5hdb-Xv.QXxEjN0wCM3gjNzEzW}`
```bash
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{kX_TmNgPWsCwcZP3svNw5hdb-Xv.QXxEjN0wCM3gjNzEzW}
```

### What I learned
- Every file in Linux is owned by a user on the system. The two important user accounts are:
   - Your user account (On pwn.college, the hacker user)
   - root which is the administrative account.
- We can change the ownership of files via the chown (change owner) command.


## Challenge 2: Groups and files
### My solve
**Flag:** `pwn.college{o2n71g72V8Go0gboSZOKO4r4nnz.QXxcjM1wCM3gjNzEzW}`

In this challenge, I invoked the chgrp command to change ownership and read out the flag using cat command.
```bash
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{o2n71g72V8Go0gboSZOKO4r4nnz.QXxcjM1wCM3gjNzEzW}
```

### What I learned
- files have an owner user and a group. A group can have multiple users in it and a user can be a member of multiple groups. 
- The group ownership can be changed with *chgrp* ( change group command)


### References 
no references

## Challenge 3: Fun with group names

### My solve
**Flag:** `pwn.college{MBGvwTyewb-4fzw1QtzQQnI4oWA.QXycjM1wCM3gjNzEzW}`


```bash
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp16531) groups=1000(grp16531)
hacker@permissions~fun-with-groups-names:~$ chgrp grp16531 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{MBGvwTyewb-4fzw1QtzQQnI4oWA.QXycjM1wCM3gjNzEzW} 
```

### What I learned
- *id* command helps us list the names of the groups

## Challenge 4: Changing permissions

### My solve
**Flag:** `pwn.college{QemDw8AfO1_pLYy4Tv6NoUaNFHI.QXzcjM1wCM3gjNzEzW}`


```bash
hacker@permissions~changing-permissions:~$ ls -l /flag
-r-------- 1 root root 60 Oct 10 17:08 /flag
hacker@permissions~changing-permissions:~$ chmod a+r /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{QemDw8AfO1_pLYy4Tv6NoUaNFHI.QXzcjM1wCM3gjNzEzW}
```

### What I learned
- The first character is the file type. The next nine characters are the actual access permissions of the file or directory, split into 3 characters denoting permissions for the owning user, 3 characters denoting the permissions for the owning group, and 3 characters denoting the permissions that all other access.
- - r - user/group/other can read the file (or list the directory)
  - w - user/group/other can modify the files (or create/delete files in the directory)
  - x - user/group/other can execute the file as a program (or can enter the directory, e.g., using `cd`)
   - nothing


 ## Challenge 5: Executable files
### My solve
**Flag:** `pwn.college{0ooqVI37fNDtLa3srQgkD7yvjLF.QXyEjN0wCM3gjNzEzW}`

In this challenge, I made the chmod command and made it executable to print the flag.

```bash
hacker@permissions~executable-files:~$ ls -l /challenge/run
-r--r--r-- 1 hacker hacker 32 Jan 14  2025 /challenge/run
hacker@permissions~executable-files:~$ chmod a+x /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{0ooqVI37fNDtLa3srQgkD7yvjLF.QXyEjN0wCM3gjNzEzW}
```

### What I learned
- Linux only executes the program if there is an execute-access to the program file. 
- If the permissions are removed, the execution fails.




## Challenge 6: Permission tweaking practice
 
### My solve
**Flag:** `pwn.college{kH7eCNZqEV5WxKvQ2YyB3ml4Wu3.0FM0MDOxwCM3gjNzEzW}`

```bash
hacker@data~sorting-data:~$ sort /challenge/flags.txt
pwn.colldge{kH7eCNYqDU5WxKvP2YyB3ml4Wu3.0EM0MDOxvCM3gjNzEyW}


``` 

### What I learned
- *sort* command is used to sort the data in a file
- By default, it sorts the data alphebetically
- Arguements can alter the way it is sorted
   - *-r* for reverse alphabetical order
   - *-n* for numeric order
   - *-u* removes the duplicate lines of data
   - *-R* sorts in a random order

## Challenge 7: Permission setting practice
 
### My solve
**Flag:** `pwn.college{kH7eCNZqEV5WxKvQ2YyB3ml4Wu3.0FM0MDOxwCM3gjNzEzW}`

```bash
hacker@data~sorting-data:~$ sort /challenge/flags.txt
pwn.colldge{kH7eCNYqDU5WxKvP2YyB3ml4Wu3.0EM0MDOxvCM3gjNzEyW}

``` 

### What I learned
- chmod command can also overwrite the old permissions using an = symbol instead of a + or - symbol.
   - u=rw sets read and write permissions for the user, and wipes the execute permission
   - o=x sets only executable permissions, wiping read and write
   - a=rwx sets read, write, and executable permissions for the user and group.

## Challenge 8: The SUID Bit

### My solve
**Flag:** `pwn.college{MPLOpEfLplGQ4NHJsrS86ahVKuH.QXzEjN0wCM3gjNzEzW}`

```bash
hacker@permissions~the-suid-bit:~$ chmod u+s /challenge/getroot
hacker@permissions~the-suid-bit:~$ /challenge/getroot
SUCCESS! You have set the suid bit on this program, and it is running as root! 
Here is your shell...
root@permissions~the-suid-bit:~# cat /flag
pwn.college{MPLOpEfLplGQ4NHJsrS86ahVKuH.QXzEjN0wCM3gjNzEzW}
``` 

### What I learned
- The "Set User ID" (SUID) permissions bit allows the user to run a program as the owner of that program's file 
- The s signifies that the program is executable with SUID. 
- The program will execute as the owner user regardless of what user runs the program

