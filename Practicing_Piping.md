# Practicing Piping
  Input output redirection
  - Standard input channel: Takes input (stdin)
  - Standard output channel: Gives normal data output (stdout)
  - Standard error channel: Gives error output (stderr)

## Challenge 1: Redirecting output
   Redirect output to some file

### My solve
**Flag:** `pwn.college{0abR9hjzy993JbQzyA4qSi2NkPL.QX0YTN0wCM3gjNzEzW}`

redirecting the word *PWN* to file *COLLEGE*

```bash
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your 
flag:
pwn.college{0abR9hjzy993JbQzyA4qSi2NkPL.QX0YTN0wCM3gjNzEzW}
```

### What I learned
- *>* character is used to redirect output
- The redirected output can be read by implementing *cat* command
- File names and commands are case-sensitive, so care must be taken to type them correctly.


## Challenge 2: Redirecting more output
   Practice on redirecting output
### My solve
**Flag:** `pwn.college{EC7TwUUYvyIpdvs83PIMN2SckAR.QX1YTN0wCM3gjNzEzW}`

Redirecting the program output of */challenge/run* to file *myflag*

```bash
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{EC7TwUUYvyIpdvs83PIMN2SckAR.QX1YTN0wCM3gjNzEzW}
```

### What I learned
- *>* character can be used to redirect the outputs of any files or commands desired.

### References 
no references

## Challenge 3: Appending output
  To join the outputs redirected
### My solve
**Flag:** `pwn.college{4up5X-p-Q1ct-JjpLX6-JDAAXjm.QX3ATO0wCM3gjNzEzW}`

Used *>>* to join the two halves of the flag when redirecting output

```bash
hacker@piping~appending-output:~$ /challenge/run >> ~/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do 
the first write directly to the file, and the second write, I'll do to stdout 
(if it's pointing at the file). If you redirect the output in append mode, the 
second write will append to (rather than overwrite) the first write, and you'll 
get the whole flag!
hacker@piping~appending-output:~$ cat ~/the-flag
 | 
\|/ This is the first half:
 v 
pwn.college{4up5X-p-Q1ct-JjpLX6-JDAAXjm.QX3ATO0wCM3gjNzEzW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>) 
rather than *append* mode (>>), and so the write of the second half to stdout 
overwrote the initial write of the first half directly to the file. Try append 
mode!
```

### What I learned
- *>* character creates a new output file every time it is used, deleting all old data in the file
- In order to append to the output file, we need to use *>>*

## Challenge 4: redirecting errors
  Redirecting errors using file descriptor numbers
### My solve
**Flag:** `pwn.college{kueu4CuW5EY5O0-C1K2vuNuPkJO.QX3YTN0wCM3gjNzEzW}`

Used *>* for redirecting output and *2>* for redirecting error. The flag will be seen in the file in which error is stored (*instructions*)
```bash
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat instructions
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will check that error output is redirected to a specific file path : instructions
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!

[TEST] You should have redirected my stderr to instructions. Checking...

[PASS] The file at the other end of my stderr looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{kueu4CuW5EY5O0-C1K2vuNuPkJO.QX3YTN0wCM3gjNzEzW}
```

### What I learned
- File descriptor numbers tell where the channel communicates to: 
  - 0: Standard input
  - 1: standard Output
  - 2: Standard error
- Implicitly, *>* without a number defaults to Standard output. And *<* can also be used for standard input
- To redirect standard error, *2>* needs to be specified. It will redirect it to error.log 


 ## Challenge 5: Redirecting input
### My solve
**Flag:** `pwn.college{wABWqf7LjFMGjjyyk5hXwBdjL8r.QXwcTN0wCM3gjNzEzW}`

First, redirect output to *PWN* file. Then perform input redirection.

```bash
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read 
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{wABWqf7LjFMGjjyyk5hXwBdjL8r.QXwcTN0wCM3gjNzEzW}
```

### What I learned
- *<* is used to redirect input. 
- This means, we are telling the command to receive input from another source (maybe some file), and not the keyboard (or user).



## Challenge 6: Grepping stored results
 Sreach for flag in redirected output

### My solve
**Flag:** `pwn.college{Mmr9Mep2ad9A9Bl4dpr7XfrT-B5.QX4EDO0wCM3gjNzEzW}`
stroing output of */challenge/run* in */tmp/data.txt*, and then grepping for the flag in */tmp/data.txt*

```bash
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep pwn.college /tmp/data.txt
pwn.college{Mmr9Mep2ad9A9Bl4dpr7XfrT-B5.QX4EDO0wCM3gjNzEzW}
``` 

### What I learned
- We are simply combining the output redirection and grepping (finding flag) processes.

## Challenge 7: Grepping live output
   Using pipe operator
### My solve
**Flag:** `pwn.college{AGNfP4o_dg1oup5GM7bGqpodOOK.QX5EDO0wCM3gjNzEzW}`


```bash
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{AGNfP4o_dg1oup5GM7bGqpodOOK.QX5EDO0wCM3gjNzEzW}
```

### What I learned
- We can use the pipe operator *(|)* to give the standard output of command on left to the standard input to command on right
- This is simply a way of cutting out the middleman, or removing the need for storing the results. 


## Challenge 8: Grepping errors
   Directly grep through errors
### My solve
**Flag:** `pwn.college{Mn2ZbqmC9g1Cssrq1Go-TRLF1Ua.QX1ATO0wCM3gjNzEzW}`


```bash
hacker@piping~grepping-errors:~$ /challenge/run 2>& 1 | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{Mn2ZbqmC9g1Cssrq1Go-TRLF1Ua.QX1ATO0wCM3gjNzEzW}
```

### What I learned
- There is no way to use *2|* (*|* only pipes output). If we want to specifically grep through errors, we need to use *>&* operator
- *>&* operator redirects file descriptor into another file descriptor. This allows us to condense our program even more.
- The error gotten from */challenge/run* is given to standard output log, which is piped into the grep command input.


## Challenge 9: Filtering with grep -v
   How to find files which are *not matching* 
### My solve
**Flag:** `pwn.college{czOfI-BlLOq-PYeO3_Gxz2kqdry.0FOxEzNxwCM3gjNzEzW}`

```bash
hacker@piping~filtering-with-grep-v:~$ /challenge/run > flag
bash: flag: Permission denied
hacker@piping~filtering-with-grep-v:~$ ls
COLLEGE  Desktop  PWN  f  flag  instructions  myflag  not-the-flag  the-flag
hacker@piping~filtering-with-grep-v:~$ /challenge/run > myflag
hacker@piping~filtering-with-grep-v:~$ cat myflag | grep -v DECOY
pwn.college{czOfI-BlLOq-PYeO3_Gxz2kqdry.0FOxEzNxwCM3gjNzEzW}
```

### What I learned
- *-v* grep argument allows us to invert te function of grep command, by allowing us to find files which do NOT match the descriptions
- this is a method of filtering OUT the data that we do not want


## Challenge 10: Duplicating piped data with tee
   duplicate data to any number of files
### My solve
**Flag:** `pwn.college{QChlhJf8HePy5HahxuMFQX6EtpV.QXxITO0wCM3gjNzEzW}`

On trying to pipe */challenge/pwn*, it told us to intercept the output, and use a secret code. So I *cat* the output file and read the secret argument, along with its required code.

```bash
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | /challenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code 
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the 
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee output | /challenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code 
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the 
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat output
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "QChlhJf8"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret QChlhJf8 | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{QChlhJf8HePy5HahxuMFQX6EtpV.QXxITO0wCM3gjNzEzW}
```

### What I learned
- On using *tee*(for two files), we create three copies of the data. One is to stdout, one is to the first file, and the third is to the other file.
- This helps us see the flow of data, and debug it more easily.

## Challenge 11: Process substitution for input
   compare output of two commands
### My solve
**Flag:** `pwn.college{AUTVAQhL4W09UdyujQbv2fTsI9F.0lNwMDOxwCM3gjNzEzW}`

Used *diff* to compare output of commands */challenge/print_decoys* and */challenge/print_decoys_and_flag*

```bash
hacker@piping~process-substitution-for-input:~$ diff <(/challenge/print_decoys) <( /challenge/print_decoys_and_flag)
93a94
> pwn.college{AUTVAQhL4W09UdyujQbv2fTsI9F.0lNwMDOxwCM3gjNzEzW}
```

### What I learned
- In linux, everything is a file. So even commands are given file-like provisions.
- We can use "Process substitution* to to hook input and output of programs to command arguments
- *<(command)* is used to read a command. 
- The output is put to a temporary file (say abc). (abc) is not an actual file, it is a "named pipe"

## Challenge 12: Writing to multiple programs
   process substitution for writing TO commands

### My solve
**Flag:** `pwn.college{Ecv3NnTjinHFsV2sXwCpE-rHD5e.QXwgDN1wCM3gjNzEzW`


```bash
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) >(/challenge/planet)
This secret data must directly and simultaneously make it to /challenge/the and 
/challenge/planet. Don't try to copy-paste it; it changes too fast.
182972383184323957
Congratulations, you have duplicated data into the input of two programs! Here 
is your flag:
pwn.college{Ecv3NnTjinHFsV2sXwCpE-rHD5e.QXwgDN1wCM3gjNzEzW
```

### What I learned
- Similar to what we did in the previous challenge, we will now use *>(command)* to write to a command
- *tee* is again used to duplicate data in *the* and *planet* 
- The need for direct duplication arises since the secret data changes too fast to intercept it.


## Challenge 13: Split piping stderr and stdout
   Combine previous knowledge and explore redirectiong techniques
### My solve
**Flag:** `pwn.college{o7n4PB2dKHUPsydT6OAs1FSI6jw.QXxQDM2wCM3gjNzEzW}`
The main problem is the need for keeping stdout and stderr unmixed. This can be done using *>>* (allows apending, prevents overwriting)

```bash
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack > >(/challenge/planet) 2> >(/challenge/the)
Congratulations, you have learned a redirection technique that even experts 
struggle with! Here is your flag:
pwn.college{o7n4PB2dKHUPsydT6OAs1FSI6jw.QXxQDM2wCM3gjNzEzW}
```

### What I learned
- Using *>>*, we can redirect */challenge/planet* to stdout and */challenge/the* to stderr, without mixing.


## Challenge 14: Named pipes
  Introduction to *FIFO*
- During piping, the process substitution creates temporary files. We can create permanent files using FIFO
- FIFO = "First In First Out"
### My solve
**Flag:** `pwn.college{M9Z2STQLUiuDp4OTOFc3GA2-inG.01MzMDOxwCM3gjNzEzW}`

make a fifo and redirect the output of */challenge/run* to the fifo

```bash
hacker@piping~named-pipes:~$ mkfifo /tmp/flag_fifo
hacker@piping~named-pipes:~$ /challenge/run > /tmp/flag_fifo
You're successfully redirecting /challenge/run to a FIFO at /tmp/flag_fifo! 
Bash will now try to open the FIFO for writing, to pass it as the stdout of 
/challenge/run. Recall that operations on FIFOs will *block* until both the 
read side and the write side is open, so /challenge/run will not actually be 
launched until you start reading from the FIFO!
hacker@piping~named-pipes:~$ cat /tmp/flag_fifo
You've correctly redirected /challenge/run's stdout to a FIFO at 
/tmp/flag_fifo! Here is your flag:
pwn.college{M9Z2STQLUiuDp4OTOFc3GA2-inG.01MzMDOxwCM3gjNzEzW}
```

### What I learned
- we can create fifo using *mkfifo* command
- When we list the files in a fifo, we can see *-p* in front of the pipe
- fifos block operations until both sides of the pipe are open (i.e., there a command inputting or opening the fifo, AND a command outputting the fifo)
