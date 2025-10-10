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
  Output only the first 10 lines
### My solve
**Flag:** `pwn.college{c3ixgnj3lM4taBq4NGjbOEsgTdD.0lNxEzNxwCM3gjNzEzW}`

The output of */challenge/pwn* is piped to *head* command. The output of this is given to */challenge/college* which will check and accordingly give the flag

```bash
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{c3ixgnj3lM4taBq4NGjbOEsgTdD.0lNxEzNxwCM3gjNzEzW}
```

### What I learned
- *head* command displays the first 10 lines of the output
- If we need it to specifically display a certain number of lines, we can use *-n* follwed by the number of lines we want it to show

 ## Challenge 5: Hijacking commands
  Extracting specified columns from the text.
### My solve
**Flag:** `pwn.college{guuhcmqE0xXW90HtXkdQHfTeU66.01NxEzNxwCM3gjNzEzW}`

We output the contents of */challenge/run* into *cut* command. This gives us the 2nd column data. This is used as input to *tr* command to get it all in one line.

```bash
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d " " -f 2 | tr -d "\n"
pwn.college{guuhcmqE0xXW90HtXkdQHfTeU66.01NxEzNxwCM3gjNzEzW}
```

### What I learned
- *cut* command is used to extract columns from data
- *-d* argument followed by a character (say 'a') means that the columns are separated by that character ('a')
- *-f* argument is used to tell the command which column number needs to be extracted.
