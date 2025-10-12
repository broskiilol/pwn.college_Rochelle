# Pondering PATH
 How does the shell know where the command processes are?
## Challenge 1: The PATH variable
   understanding Shell variable PATH 

### My solve
**Flag:** `pwn.college{IFQ78jnRcej6ffV-cKyeTZ3DXni.QX2cDM1wCM3gjNzEzW}`
We empty out the PATH variable first, thus removing the *rm* command. Now *run* file cannot be removed.

```bash
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ rm
bash: rm: No such file or directory
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{IFQ78jnRcej6ffV-cKyeTZ3DXni.QX2cDM1wCM3gjNzEzW}
```

### What I learned
 - PATH variable stores directory commands. Commands are gotten from it and blanking the variable will remove all the commands stored in it.
 - Thus *PATH=""* deletes all commands stored, we cannot use any command then.


## Challenge 2: Setting PATH
   Adding thing to PATH variable
### My solve
**Flag:** `pwn.college{UJPamwt6suU1rwVME8sYwBfT1I1.QX1cjM1wCM3gjNzEzW}`

*run* file needs to be run by using */challenge/more_commands/challenge/run*, but we dont want to type so much everytime, so we store the pathway */challenge/more_commands* in *PATH* variable. we can now *run* using just */challenge/run*

```bash
hacker@path~setting-path:~$ PATH=/challenge/more_commands
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{UJPamwt6suU1rwVME8sYwBfT1I1.QX1cjM1wCM3gjNzEzW}
```

### What I learned
- WE dont need to use the bare name everytime we want to use a file. We can store the path of the file in *PATH* and call the file using its name directly (as done above)


## Challenge 3: Finding commands
  Seeing the pathway of a command
### My solve
**Flag:** `pwn.college{4ujsqe24mxK25jlCdYtNc_W5dkD.01NzEzNxwCM3gjNzEzW}`
The flag is stored in the same directory as *win* command. So we need to find where *win* command is stored

```bash
hacker@path~finding-commands:~$ which win
/challenge/paths/8708/win
hacker@path~finding-commands:~$ cat /challenge/paths/8708/flag
pwn.college{4ujsqe24mxK25jlCdYtNc_W5dkD.01NzEzNxwCM3gjNzEzW}
```

### What I learned
- *which* command allows us to see the full path of the command we pass in it as argument

## Challenge 4: Adding commands

### My solve
**Flag:** `pwn.college{cZY_n6150qy-A8qPSErzJ9Qw1om.QX2cjM1wCM3gjNzEzW}`
I am trying to create a custom command *win*

```bash
hacker@path~adding-commands:~$ mkdir /tmp/pwn
hacker@path~adding-commands:~$ cd /tmp/pwn
hacker@path~adding-commands:/tmp/pwn$ echo /bin/cat /flag > win
hacker@path~adding-commands:/tmp/pwn$ chmod +x win
hacker@path~adding-commands:/tmp/pwn$ PATH="/tmp/pwn:$PATH" /challenge/run
Invoking 'win'....
pwn.college{cZY_n6150qy-A8qPSErzJ9Qw1om.QX2cjM1wCM3gjNzEzW}
```

### What I learned
- I use the absolute path of *cat* (*/bin/cat*) so that the real cat program is being run and changes in PATH will not affect it.
- I store a set of commands to be run when *win* is executed (*echo /bin/cat /flag* meaning displaying the reading of flag) and make *win* executable using chmod
- *PATH="/tmp/pwn:$PATH" /challenge/run* makes it so that when *run* program is run, *tmp/run* is the first place they will try to find it
   - When *win* command is invoked, PATH makes it so that each and every directory is searched to find executable file named       win. so we put the *win* file on top to find it first

 ## Challenge 5: Hijacking commands
  Changing the operation that a command carries out
### My solve
**Flag:** `pwn.college{o2htbfKGu0jaWb5FueDxs90wGUq.QX3cjM1wCM3gjNzEzW}`
according to the design of the challenge, When */challenge/run* is carried out, *rm* command is also carried out, thus deleting the flag. The main logic behind solving this, is creating OUR *rm* and putting it at the top of the PATH.

```bash
hacker@path~hijacking-commands:~$ mkdir /tmp/pwn
hacker@path~hijacking-commands:~$ cd /tmp/pwn
hacker@path~hijacking-commands:/tmp/pwn$ echo '#!/bin/bash' > /tmp/pwn/rm
hacker@path~hijacking-commands:/tmp/pwn$ chmod a+x /tmp/pwn/rm
hacker@path~hijacking-commands:/tmp/pwn$ echo 'cat -- "$@"' >> /tmp/pwn/rm
hacker@path~hijacking-commands:/tmp/pwn$ PATH="/tmp/pwn:$PATH" 
hacker@path~hijacking-commands:/tmp/pwn$ /challenge/run
Trying to remove /flag...
Found 'rm' command at /tmp/pwn/rm. Executing!
cat: -f: No such file or directory
pwn.college{o2htbfKGu0jaWb5FueDxs90wGUq.QX3cjM1wCM3gjNzEzW}
```

### What I learned
- */tmp/pwn* is a temporary place for storing OUR *rm*
- *$@* means that everything in the file needs to be passed exactly as they are given
- *PATH="/tmp/pwn:$PATH"* put our created *rm* at the start of the list, so that our rm (/tmp/pwn/rm) is executed, not (/bin/rm) which is the ACTUAL rm
