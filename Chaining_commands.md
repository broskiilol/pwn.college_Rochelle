# Chaining commands
 
## Challenge 1: chaining with semicolons
   ### My solve
**Flag:** `pwn.college{Qv1ALgI_qzHa49-YLdq1hvPmDVn.QX1UDO0wCM3gjNzEzW}`

```bash
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{Qv1ALgI_qzHa49-YLdq1hvPmDVn.QX1UDO0wCM3gjNzEzW}
```

### What I learned
 - a semicolon (;) is same as a new line command (similar to how we type *enter* key)


## Challenge 2: Building on success
   
### My solve
**Flag:** `pwn.college{I23ODpiegpSbjixk6mVIbxJxCNP.0lM0MDOxwCM3gjNzEzW}`

```bash
hacker@chaining~building-on-success:~$ /challenge/first-success
hacker@chaining~building-on-success:~$ /challenge/second
Error: /challenge/first-success must be successfully chained with 
/challenge/second using &&
hacker@chaining~building-on-success:~$ /challenge/first-success && /challenge/second
Nice chaining! Flag: pwn.college{I23ODpiegpSbjixk6mVIbxJxCNP.0lM0MDOxwCM3gjNzEzW}
```

### What I learned
- We use the *&&* operator as AND. 
- the 2nd command will work only if the first command is successful (and returns 0) i.e., both commands must work for the output to come


## Challenge 3: Handling Failure
### My solve
**Flag:** `pwn.college{8IXZAPy61Y2NWhnezMkHicrFOfz.01M0MDOxwCM3gjNzEzW}`


```bash
hacker@chaining~handling-failure:~$ /challenge/first-failure || /challenge/second
Nice chaining! Flag: pwn.college{8IXZAPy61Y2NWhnezMkHicrFOfz.01M0MDOxwCM3gjNzEzW}
```

### What I learned
- || is used to run the second command only if the first command FAILS.
- this is similar to the OR operator
- this is useful for error handling

## Challenge 4: Your first shell script
  Understanding shell script
### My solve
**Flag:** `pwn.college{YHVyDYXAz3jJaEGJ3UpUB2rMOOM.QXxcDO0wCM3gjNzEzW`

We can create a shell script in a text editor and store our script in it
then we call is in bash

```bash
hacker@chaining~your-first-shell-script:~$ touch x.sh
hacker@chaining~your-first-shell-script:~$ nano x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{YHVyDYXAz3jJaEGJ3UpUB2rMOOM.QXxcDO0wCM3gjNzEzW}
```

### What I learned
- *nano* used to create the shell script *x.sh*
- We can use such scripts to combine prompts quickly
- The command is run from the file, not the user.

## Challenge 5: Redirecting script output
### My solve
**Flag:** `pwn.college{sFRMVr2B474iqAo7Ll6dOc0u40c.QX4ETO0wCM3gjNzEzW}`

```bash
hacker@chaining~redirecting-script-output:~$ touch x.sh
hacker@chaining~redirecting-script-output:~$ nano x.sh
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{sFRMVr2B474iqAo7Ll6dOc0u40c.QX4ETO0wCM3gjNzEzW}
```

### What I learned
- We can pipe the outputs of multiple programs to a command using a script. To a pipe, scripts are just a command. Thus we can redirect the script output to another command
- Even redirection and appending methods work


## Challenge 6: Executable shell scripts

### My solve
**Flag:** `pwn.college{Yu7a94bZyx9_CAqh2UJ0ot0wVXz.QX0cjM1wCM3gjNzEzW}`

created shell script *shell.sh*. allowed executing powers to the user using *+x* and ran the script
```bash
hacker@chaining~executable-shell-scripts:~$ touch shell.sh
hacker@chaining~executable-shell-scripts:~$ nano shell.sh
hacker@chaining~executable-shell-scripts:~$ chmod +x shell.sh
hacker@chaining~executable-shell-scripts:~$ ./shell.sh
Congratulations on your shell script execution! Your flag:
pwn.college{Yu7a94bZyx9_CAqh2UJ0ot0wVXz.QX0cjM1wCM3gjNzEzW}
``` 

### What I learned
- we can invoke the shell script without using *bash* by making the script executable

## Challenge 7: Understanding shebangs

### My solve
**Flag:** `pwn.college{c2GgX22Ow3Myw8V_xqxQ2Y88T2m.0VOzMDOxwCM3gjNzEzW}`

```bash
hacker@chaining~understanding-shebangs:~$ touch solve.sh
hacker@chaining~understanding-shebangs:~$ nano solve.sh
hacker@chaining~understanding-shebangs:~$ chmod +x solve.sh
hacker@chaining~understanding-shebangs:~$ /challenge/run
Testing your script...
Perfect! Your flag:
Flag: pwn.college{c2GgX22Ow3Myw8V_xqxQ2Y88T2m.0VOzMDOxwCM3gjNzEzW}
``` 

### What I learned
- a program is called in interpretted program is it starts with the characters "#!" (called a shebang). The rest of the line is the pathway of the shell
  - #!/bin/bash for bash scripts
  - #!/usr/bin/python3 for Python scripts
- This is helpful so that if the code is in python or any other programming language we can still launch the shell script

## Challenge 8: Scripting with arguments
 
### My solve
**Flag:** `pwn.college{obw2HvLnI7XcfXJc8kZehsBYnAv.0VNzMDOxwCM3gjNzEzW}`

we can reverse the argument by simply *echo*ing the $2 argument before $1 argument.

```bash
hacker@chaining~scripting-with-arguments:~$ nano solve.sh
hacker@chaining~scripting-with-arguments:~$ bash /home/hacker/solve.sh pwn college
college
pwn
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Not quite right!
Expected: college_PuFDFq4GhA pwn_JM39rGcMeFg
Got: college_PuFDFq4GhA
pwn_JM39rGcMeFg
hacker@chaining~scripting-with-arguments:~$ nano solve.sh
hacker@chaining~scripting-with-arguments:~$ bash /home/hacker/solve.sh pwn college
college pwn
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Correct! Your script properly reversed the arguments.
Here's your flag:
pwn.college{obw2HvLnI7XcfXJc8kZehsBYnAv.0VNzMDOxwCM3gjNzEzW}
``` 

### What I learned
- We can use arguments in shell variables 
- $1 is for first argument, $2 for second argument, etc.

 
## Challenge 9: Scripting with conditionals
   Making conditional statements in shell scripts

### My solve
**Flag:** `pwn.college{gB-yHXhsKtgcnNQkU1t_D4WO4yA.0lNzMDOxwCM3gjNzEzW}`

```bash
#!/bin/bash
if [ "$1" == "pwn" ]
then
   echo "college"
fi
```
```bash
hacker@chaining~scripting-with-conditionals:~$ nano solve.sh
hacker@chaining~scripting-with-conditionals:~$ bash /home/hacker/solve.sh pwn 
college
hacker@chaining~scripting-with-conditionals:~$ /challenge/run
Correct! Your script properly handles all the conditions.
Here's your flag:
pwn.college{gB-yHXhsKtgcnNQkU1t_D4WO4yA.0lNzMDOxwCM3gjNzEzW}
```

### What I learned
 - We can create conditional statements in shell scripts, choosing which arguments (and how many) to take in.
 - *we need to take precaution to keep spaces between if and [, ], and have then, fi on different lines


## Challenge 10: scripting with default cases
   Using else case
### My solve
**Flag:** `pwn.college{EsPAOxUGSw9YraVwLT7Wp9g6K9C.01NzMDOxwCM3gjNzEzW}`

```bash
hacker@chaining~scripting-with-default-cases:~$ nano solve.sh
hacker@chaining~scripting-with-default-cases:~$ bash /home/hacker/solve.sh pwn 
college
hacker@chaining~scripting-with-default-cases:~$ bash /home/hacker/solve.sh hack
nope
hacker@chaining~scripting-with-default-cases:~$ /challenge/run
Correct! Your script properly handles the if/else conditions.
Here's your flag:
pwn.college{EsPAOxUGSw9YraVwLT7Wp9g6K9C.01NzMDOxwCM3gjNzEzW}
```

### What I learned
- We can also use *else* to create a default case if the *if* case is not true


## Challenge 11: Scripting with multiple conditions
 Using multiple conditional statements
### My solve
**Flag:** `pwn.college{U-5qJR9FfFnOOMqqApef_xyz1Q0.0FOzMDOxwCM3gjNzEzW} `

```bash
#!/bin/bash
if [ "$1" == "hack" ]
then
   echo "the planet"
elif [ "$1" == "pwn" ]
then
   echo "college"
elif [ "$1" == "learn" ]
then
   echo "linux"
else
   echo "unknown"
fi
```
```bash
hacker@chaining~scripting-with-multiple-conditions:~$ nano solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ /challenge/run
Correct! Your script properly handles all the conditions with elif.
Here's your flag:
pwn.college{U-5qJR9FfFnOOMqqApef_xyz1Q0.0FOzMDOxwCM3gjNzEzW} 
```

### What I learned
- We can use many if-else statements

## Challenge 12: Reading shell scripts
  
### My solve
**Flag:** ` `



```bash

```

### What I learned
- 
