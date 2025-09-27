# Disgesting Documentation
  How to ask for help 
## Challenge 1: Learning from documentation
 Understanding documentation

### My solve
**Flag:** `pwn.college{gSWDpctRso9vd7seY73BRxuXcZv.QX0ITO0wCM3gjNzEzW}`


```bash
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{gSWDpctRso9vd7seY73BRxuXcZv.QX0ITO0wCM3gjNzEzW}
```

### What I learned
- Command functions can be enhanced by giving it the correct arguments
- like in *ls* command, we give *-a* in order to see hidden files as well.
- giving different arguments will help perform different functions using the same commands.


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

## Challenge 3: Reading manuals
  Using *man* command to read how to use specific commands
### My solve
**Flag:** `pwn.college{sUUcXVGXvL5r3EHENgvUiGWkZcS.QX0EDO0wCM3gjNzEzW}`

I first read the manual for how to call the flag in */challenge/challenge*. This showed me that I must use argument *--scvrgv NUM* whose NUM argument must be 530 to display the flag.

```bash
hacker@man~reading-manuals:~$ man challenge
hacker@man~reading-manuals:~$ /challenge/challenge --scvrgv 530
Correct usage! Your flag: pwn.college{sUUcXVGXvL5r3EHENgvUiGWkZcS.QX0EDO0wCM3gjNzEzW}
```

### What I learned
- *man* lets us access a manpage (a central database)
- We can use *man* to open a manual to the various arguments and funtions that can be passed in a file
- **NOTE** Arguments to man are not file paths, they are names (putting file paths will give error)

## Challenge 4: Searching manuals
  Searching the manual 
### My solve
**Flag:** `pwn.college{MOLHQzBO4TwsSvO3N_XLxpenV_m.QX1EDO0wCM3gjNzEzW}`

On reading the manual for *challenge* I found that flag is found by using argument *--veqk*

```bash
hacker@man~searching-manuals:~$ man challenge
gzip: stdout: Broken pipe

hacker@man~searching-manuals:~$ /challenge/challenge --veqk
Initializing...
Correct usage! Your flag: pwn.college{MOLHQzBO4TwsSvO3N_XLxpenV_m.QX1EDO0wCM3gjNzEzW}
```

### What I learned
- Manpages have a lot of information about the file. We can skip to the important part by searching for what we need.
- This can be done by using /(info) where (info) is what we want to search about
- we can use *?* to search backwards, *n* to go to next result, and *N* to go to previous result


 ## Challenge 5: Searching for manuals
  Manual to use the manpage
### My solve
**Flag:** `pwn.college{gw7bQwkboVhTkulH8WulIVC9e71.QX2EDO0wCM3gjNzEzW}`

We use *man man* to understand how to use the manpage. 

```bash
hacker@man~searching-for-manuals:$ man man
hacker@man~searching-for-manuals:~$ man -k challenge
gwbwkbohku (1)       - print the flag!
hacker@man~searching-for-manuals:~$ man gwbwkbohku
hacker@man~searching-for-manuals:~$ /challenge/challenge --gwbwkb 789
Correct usage! Your flag: pwn.college{gw7bQwkboVhTkulH8WulIVC9e71.QX2EDO0wCM3gjNzEzW}
```

### What I learned
- all manpages are kept in a searchable database
- Thus, we can search the database to find out how to use *man*, thus making it print the required flag.



## Challenge 6: Helpful programs
 Learn to ask help

### My solve
**Flag:** `pwn.college{EjO90ewskS7oiHr3WptFcnKBEiY.QX3IDO0wCM3gjNzEzW}`

By using *--help*, asked for possible arguments in */challenge/challenge*. Thus, found that we need to use *-g* with a unique number as arguments. 
So, first found the unique number using *-p* as specified in *--help*

```bash
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge --print-value
The secret value is: 907
hacker@man~helpful-programs:~$ /challenge/challenge -g 907
Correct usage! Your flag: pwn.college{EjO90ewskS7oiHr3WptFcnKBEiY.QX3IDO0wCM3gjNzEzW}
``` 

### What I learned
- *--help* argument is used like a manpage
- It tells us which argument does what in the directory

## Challenge 7: Help for builtins
   understanding working and meaning of shell builtins and builtins
### My solve
**Flag:** `pwn.college{wvU4_lxZlWu8tkjG6nE42XED3jT.QX0ETO0wCM3gjNzEzW}`

- since *challenge* is a shell builtin command, we ise *help* to understand how to operate it
- this informs us that *--secret* argument will print the flag (provided the correct argument is given to it) 

```bash
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!
    
    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "wvU4_lxZ".
hacker@man~help-for-builtins:~$ challenge --secret wvU4_lxZ
Correct! Here is your flag!
pwn.college{wvU4_lxZlWu8tkjG6nE42XED3jT.QX0ETO0wCM3gjNzEzW}
```

### What I learned
- builtins are commands built into the shell itself. the shell handles them internally
- *help* builtin displays the list of shell builtins
