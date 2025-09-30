# Shell Variables
## Challenge 1: Printing variables
   To print out Variables

### My solve
**Flag:** `pwn.college{gM1aRKwUn2zXxSpjRhCkqkurPRM.QX3UTN0wCM3gjNzEzW}`

Used *echo* to print out variable *FLAG*
```bash
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{gM1aRKwUn2zXxSpjRhCkqkurPRM.QX3UTN0wCM3gjNzEzW}
```

### What I learned
- The flag has been put into *FLAG* variable, meaning we just need to print it out from there
- we use *$* before the variable name in order to specify and tell the computer that it is a variable. This also tells the computer to take the value of *FLAG*. It is basically used to access variables


## Challenge 2: Setting Variables
   Storin values in variables
### My solve
**Flag:** `pwn.college{g0tBgDpP4nXLBiEM8OHICaRENSD.QX5UTN0wCM3gjNzEzW}`

Setting variable *PWN* to *COLLEGE* using = operator
```bash
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{g0tBgDpP4nXLBiEM8OHICaRENSD.QX5UTN0wCM3gjNzEzW}
```

### What I learned
- The symbol *=* is used to allot values to variables
- IT IS CRITICAL TO *NOT* PUT SPACES DURING THE ASSIGNMENT OF VARIABLES. If spaces are put, the computer will think that the variable name is a command.
- *$* is not used here, since we do not want to trigger variable expansion. 
- Names and values of variables are case-sensitive, so care needs to be taken.

### References 
no references

## Challenge 3: Multi-word variables
  How to include spaces in variable assignments
### My solve
**Flag:** `pwn.college{4TFGj1GW4MWnpU5H9OhFB18I6kV.QXwYTN0wCM3gjNzEzW}`


```bash
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{4TFGj1GW4MWnpU5H9OhFB18I6kV.QXwYTN0wCM3gjNzEzW}
```

### What I learned
- During variable assignment, spaces cannot be simply used, since the computer will treat the spaced word as a command.
- If we wish to assign something with a space to a variable, we need to enclose it within double quote ("")

## Challenge 4: Exporting Variables
  How to export variables into other shells
### My solve
**Flag:** `pwn.college{AkgPVpvvY-AxpHexyypbrpbgz-u.QXyYTN0wCM3gjNzEzW}`

*PWN* variable is exported, while *COLLEGE* variable is local.

```bash
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great 
job! Here is your flag:
pwn.college{AkgPVpvvY-AxpHexyypbrpbgz-u.QXyYTN0wCM3gjNzEzW}
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
```

### What I learned
- Variables set in a shell session are local, they are not inherited by other shell sessions.
- If we want it to be used in other shell sessions as well, we need to export it.
- This is done using *export* command


 ## Challenge 5: Printing Exported variables
  
### My solve
**Flag:** `pwn.college{IP3biy4m_YnszbHzSV2uPEN9mBE.QX4UTN0wCM3gjNzEzW}`

Using *env* command, a list of exported variables are found. FLAG variable will give us the needed flag.

```bash
hacker@variables~printing-exported-variables:~$ env
SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
MANPATH=/run/dojo/share/man:
DOJO_AUTH_TOKEN=6dcd52af3afb82dc96c0adcc28ae2f35ed0d39da2c15e35d1063bd506248df89
HOME=/home/hacker
LANG=C.UTF-8
FLAG=pwn.college{IP3biy4m_YnszbHzSV2uPEN9mBE.QX4UTN0wCM3gjNzEzW}
TERMINFO=/run/dojo/share/terminfo
TERM=xterm-256color
SHLVL=2
LC_CTYPE=C.UTF-8
SSL_CERT_FILE=/run/dojo/etc/ssl/certs/ca-bundle.crt
PATH=/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
DEBIAN_FRONTEND=noninteractive
_=/run/dojo/bin/env
```

### What I learned
- Exported variables can be printed using the *env* command



## Challenge 6: Storing command output
 Implementing command substitution

### My solve
**Flag:** `pwn.college{koRtooPebWT30cumR7cDMKdvUQs.QX1cDN1wCM3gjNzEzW}`

Stored output of */challenge/run* in *PWN*, The variable is then printed using *echo* 

```bash
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out 
and submit it!
hacker@variables~storing-command-output:~$ echo $PWN
pwn.college{koRtooPebWT30cumR7cDMKdvUQs.QX1cDN1wCM3gjNzEzW}
``` 

### What I learned
- Variables can store command outputs directly. This is called COMMAND SUBSTITUTION.

## Challenge 7: Reading input
   Getting input from user.
### My solve
**Flag:** `pwn.college{kUCR4qgYz_swT7W1Ph0Adn7NKWe.QX4cTN0wCM3gjNzEzW}`

Using *read* command to take inputs (in this case the input to be given is COLLEGE)

```bash
hacker@variables~reading-input:~$ read PWN
COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{kUCR4qgYz_swT7W1Ph0Adn7NKWe.QX4cTN0wCM3gjNzEzW}
```

### What I learned
- Command *read* is used to read data from standard input and store it in the variable
- *-p* argument can be used to give prompts to the user (to tell user what should be inputted)


## Challenge 8: Reading files
   Directly read from files
### My solve
**Flag:** `pwn.college{kTz8Bjw_T0J6Km12NEAXj48QAve.QXwIDO0wCM3gjNzEzW}`
Redirect file */challenge/read_me* into standard input of *read* which read from variable *PWN* 
This is done in one command since the file keeps changing.
```bash
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{kTz8Bjw_T0J6Km12NEAXj48QAve.QXwIDO0wCM3gjNzEzW}
```

### What I learned
-  Using *<*, we can read files with the shell
- This compresses the command lines needed, preventing *USELESS USE OF CAT*