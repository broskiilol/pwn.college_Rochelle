# File Globbing
  We can reference files, without typing them all out, by globbing
## Challenge 1: Matching with *
   First glob is *. It is a wildcard and it replaces the argument with any file which suits that pattern

### My solve
**Flag:** `pwn.college{MihZOdDFJzWBqwvebblJhH3WQiZ.QXxIDO0wCM3gjNzEzW}`


```bash
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ ./run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{MihZOdDFJzWBqwvebblJhH3WQiZ.QXxIDO0wCM3gjNzEzW}
```

### What I learned
- Glob * is used to list out files which suit the pattern of argument (like file_ pattern in the above case)
- In case of multiple arguments matching, it lists them all out
- in case of no argument matching, it outputs as it is.
- It cannot match "/" or leading "."


## Challenge 2: Matching with ?
   Single character wildcard
### My solve
**Flag:** `pwn.college{o7up3NnUFt8OGhetdVNicSwOttB.QXyIDO0wCM3gjNzEzW}`

```bash
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ ./run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{o7up3NnUFt8OGhetdVNicSwOttB.QXyIDO0wCM3gjNzEzW}
```

### What I learned
- It works like *, but only single characterwise
- Each *?* represents each character

### References 
no references

## Challenge 3: Matching with []
  Matching subsets of potential characters
### My solve
**Flag:** `pwn.college{gnDis32WaIMY8eCJpYQ4DlNXQDt.QXzIDO0wCM3gjNzEzW}`
Files differ by single character *a,b,s,h*. Thus, we can put it as a subset in []

```bash
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[absh]
You got it! Here is your flag!
pwn.college{gnDis32WaIMY8eCJpYQ4DlNXQDt.QXzIDO0wCM3gjNzEzW}
```

### What I learned
- All characters inside [] are matched individually to the shell

## Challenge 4: Matching paths with []
  Globbing done with respect to paths
### My solve
**Flag:** `pwn.college{ogVi314LA2DpJ2KEi1vEIT1Kdz4.QX0IDO0wCM3gjNzEzW}`

*We need to use a single line to find the flag*
```bash
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[absh]
You got it! Here is your flag!
pwn.college{ogVi314LA2DpJ2KEi1vEIT1Kdz4.QX0IDO0wCM3gjNzEzW}
```

### What I learned
- Full paths can be expanded using the arguments which are globbed
- Thus, our multiple line prompt can be condensed in a single line
*** My Mistake ***
- I was not putting a space (' ') after */run*. Spaces are used as separators between the command and the argument. By not putting the space, it was getting read as a single file path, thus giving errors


 ## Challenge 5: Multiple globs
  Usage of multiple globs
### My solve
**Flag:** `pwn.college{gUkHK5Lw9_70UK7YdJmCDD1Cz92.0lM3kjNxwCM3gjNzEzW}`

After entering */challenge/files*, I ran the program */challenge/run* using p as argument. "p" is used since *pwn* contains a p.

```bash
hacker@globbing~multiple-globs:~$ cd /challenge/files
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{gUkHK5Lw9_70UK7YdJmCDD1Cz92.0lM3kjNxwCM3gjNzEzW}
```

### What I learned
- /*abc will search for a file in / directory beginning with something (including nothing) and containing abc in its name
- using two * in it means we are using multiple globs.



## Challenge 6: Mixing globs
 Implementing all we have learnt so far

### My solve
**Flag:** `pwn.college{Es94-Y3s-yzgx7hqEyWJ41wCCsz.QX1IDO0wCM3gjNzEzW}`

We will search for the required files by matching the first character of each of them i.e., *cep*

```bash
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{Es94-Y3s-yzgx7hqEyWJ41wCCsz.QX1IDO0wCM3gjNzEzW}
``` 

### What I learned
- *** MY MISTAKE** I was not using the * wildcard, thus, not allowing it to expand to the required files

## Challenge 7: Exclusionary globbing
   Excluding certain files during matching
### My solve
**Flag:** `pwn.college{gtePRPlHZJrUGWQVV2WD9lcXeS8.QX2IDO0wCM3gjNzEzW}`

We need to find files not containing *p,w,n*

```bash
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{gtePRPlHZJrUGWQVV2WD9lcXeS8.QX2IDO0wCM3gjNzEzW}
```

### What I learned
- We use ! or ^ to show exclusion. These invert the glob, making it match files that are not listed.
- We need to be careful when to use ! and when to use ^ (^ is not on older shells)
*** MY MISTAKE** 
- I was not using the * wildcard, thus, not allowing it to expand to the required files


## Challenge 8: Tab completion
   Using *TAB* key to complete commandlines
### My solve
**Flag:** `pwn.college{wRPzCEHJvyn-S9lMxwyzg6fL53U.0FN0EzNxwCM3gjNzEzW}`

```bash
hacker@globbing~tab-completion:~$ cat /challenge/pwncollege​ 
pwn.college{wRPzCEHJvyn-S9lMxwyzg6fL53U.0FN0EzNxwCM3gjNzEzW}
```

### What I learned
- Using tab keys for filling in commands is much safer than using *
- Autocompletion makes it much easier for us to type in commands.

## Challenge 9: Multiple options for tab completion
   What if there are multiple options with same start in tab
### My solve
**Flag:** `pwn.college{4Cecwy25O2jRRGxdcthcAbfKTNJ.0lN0EzNxwCM3gjNzEzW}`

Using tab key, completed the file till pwncollege-
Then I listed the files starting the same way, and used *cat* to read them will I came to the flag file

```bash
hacker@globbing~multiple-options-for-tab-completion:~$ /challenge/files/pwn
pwn                    pwn-the-planet         pwncollege-flamingo    pwncollege-hacking     
pwn-college            pwncollege-family      pwncollege-flyswatter  
hacker@globbing~multiple-options-for-tab-completion:~$ /challenge/files/pwncollege-
pwncollege-family      pwncollege-flamingo    pwncollege-flyswatter  pwncollege-hacking     
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-family
No flag in this file!
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-fla
pwncollege-flag      pwncollege-flamingo  
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-flag
pwn.college{4Cecwy25O2jRRGxdcthcAbfKTNJ.0lN0EzNxwCM3gjNzEzW}
```

### What I learned
- TAB key can be used to list files having same starting. This is done by clicking TAB key twice.
- After we arrive at the file we want, we can simply cat it to read out the file.

## Challenge 10: Tab completion on commands
   Tab can also be used on commands
### My solve
**Flag:** `pwn.college{437qgeJIli5iRsHo9IkgjQOunYs.0VN0EzNxwCM3gjNzEzW}`

Given *pwncollege* is a command. We need to give the command using TAB key.

```bash
hacker@globbing~tab-completion-on-commands:~$ pwncollege-24964 
Correct! Here is your flag:
pwn.college{437qgeJIli5iRsHo9IkgjQOunYs.0VN0EzNxwCM3gjNzEzW}
```

### What I learned
- TAB key can be used to autocomplete commands too, not just files.