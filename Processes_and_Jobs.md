# Processes and Jobs
 Software has two categories : 
 - Operating system kernels
 - Processes
This module is about the processes of software.
## Challenge 1: Listing Processes
   We can list running processes using *ps* command (process status or snapshot)

### My solve
**Flag:** `pwn.college{st8zgmsl-t4T51JGeIJXuLoD-Pj.QX4MDO0wCM3gjNzEzW}`
The flag is hidden with a different name and it cannot be listed using *ls*. But it has been launched (the process is running), so we can find it using *ps*

```bash
hacker@processes~listing-processes:~$ cd /challenge
hacker@processes~listing-processes:/challenge$ ls
ls: cannot open directory '.': Permission denied
hacker@processes~listing-processes:/challenge$ ps
    PID TTY          TIME CMD
    150 pts/0    00:00:00 bash
    163 pts/0    00:00:00 ps
hacker@processes~listing-processes:/challenge$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 08:45 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           8       1  0 08:45 ?        00:00:00 /run/dojo/bin/sleep 6h
root         132       1  0 08:45 ?        00:00:00 /challenge/18639-run-9279
root         135     132  0 08:45 ?        00:00:00 sleep 6h
hacker       146       1  0 08:45 ?        00:00:00 /nix/store/g0q8n7xfjp7znj41hcgrq893a9m0i474-ttyd-1.7.7/bin/ttyd --port 7681 --interface 0.0.0.
hacker       150     146  0 08:45 pts/0    00:00:00 /run/dojo/bin/bash --login
hacker       164     150  0 08:47 pts/0    00:00:00 ps -ef
hacker@processes~listing-processes:/challenge$ /challenge/18639-run-9279
Yahaha, you found me! Here is your flag:
pwn.college{st8zgmsl-t4T51JGeIJXuLoD-Pj.QX4MDO0wCM3gjNzEzW}
Now I will sleep for a while (so that you could find me with 'ps').
```

### What I learned
 - *ps* can take it various arguments to make it more useful
  - 
  - 


## Challenge 2: Killing processes
   Terminating processes
### My solve
**Flag:** `pwn.college{gUEQ_RPkcpcOKEhMRej4AO4KUZE.QXyQDO0wCM3gjNzEzW}`

Used *ps -e* to get the PID value to kill the sleep process. Used the PID value as argument for kill command.
```bash
hacker@processes~killing-processes:~$ ps -e
    PID TTY          TIME CMD
      1 ?        00:00:00 docker-init
      7 ?        00:00:00 /run/dojo/bin/s
    135 ?        00:00:00 su
    136 ?        00:00:00 bash
    137 ?        00:00:00 sleep
    148 ?        00:00:00 ttyd
    152 pts/0    00:00:00 bash
    164 pts/0    00:00:00 ps
hacker@processes~killing-processes:~$ ps -e | grep sleep
    137 ?        00:00:00 sleep
hacker@processes~killing-processes:~$ kill 137
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{gUEQ_RPkcpcOKEhMRej4AO4KUZE.QXyQDO0wCM3gjNzEzW}
```

### What I learned
- We can terminate a command by *kill*ing it. The PID of the process to be killed needs to be used as argument to the *kill* command
- We can get the PID using *ps -e* as seen from previous challenge.

### References 
no references

## Challenge 3: Interrupting processes
  How to unclog the process in the terminal
### My solve
**Flag:** `pwn.college{E4jB1vMTduaYnllMMr0HZNqin1x.QXzQDO0wCM3gjNzEzW}`


```bash
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember, 
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{E4jB1vMTduaYnllMMr0HZNqin1x.QXzQDO0wCM3gjNzEzW} 
```

### What I learned
- If some process is clogging up the terminal, we can use CTRL+C to interrupt it (instead of killing it)

## Challenge 4: Killing misbehaving processes
  
### My solve
**Flag:** ``



```bash

```

### What I learned
- 

 ## Challenge 5: Suspending processes

### My solve
**Flag:** `pwn.college{M7SPBlOV5uz_3DxIqLD6krs9s7W.QX1QDO0wCM3gjNzEzW`

The challenge requires two copies of *run* challenge to run at the same time.

```bash
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         146     136  0 17:57 pts/0    00:00:00 bash /challenge/run
root         148     146  0 17:57 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can 
background me with Ctrl-Z or, if you're not ready to do that for whatever 
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         146     136  0 17:57 pts/0    00:00:00 bash /challenge/run
root         153     136  0 17:58 pts/0    00:00:00 bash /challenge/run
root         155     153  0 17:58 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{M7SPBlOV5uz_3DxIqLD6krs9s7W.QX1QDO0wCM3gjNzEzW}
```

### What I learned
- ctrl+Z is used to SUSPEND a process
- suspending basically means keeping the process in the background (not stopping it completely)



## Challenge 6: Resuming processes
### My solve
**Flag:** `pwn.college{sRKSV20Opd_Sk5qtn7YZNukYXgy.QX2QDO0wCM3gjNzEzW}`
Suspend *run* like before, then bring it back

```bash
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with 
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{sRKSV20Opd_Sk5qtn7YZNukYXgy.QX2QDO0wCM3gjNzEzW}
Don't forget to press Enter to quit me!

Goodbye!

``` 

### What I learned
- We can bring the suspended process using *fg* builtin
- It takes the process from the *background* and gets it to the *foreground*

## Challenge 7: Backgrounding processes
 Resuming the suspended process in the background so that we can keep the terminal open to do anything else we need to do

### My solve
**Flag:** `pwn.college{sbjX8DUuAEipt9WNxr3s3x1SVcS.QX3QDO0wCM3gjNzEzW}`

 suspended the *run* process (ctrl+Z). Then ran it in the background using *bg* and ran its copy on the foreground to get the flag
```bash
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         146 S+   bash /challenge/run
root         148 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the 
background, and then launch a new version of me! You can background me with 
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to 
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~backgrounding-processes:~$ 


Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out.

hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         146 S    bash /challenge/run
root         156 S    sleep 6h
root         157 S+   bash /challenge/run
root         159 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{sbjX8DUuAEipt9WNxr3s3x1SVcS.QX3QDO0wCM3gjNzEzW}

``` 

### What I learned
- We can run the suspended process in the background using *bg* command (we just cannot see it on the terminal) (*fg* in the previous challenge refers to the foreground)
- We can see the status of our processes using "ps -o"
   - *T* means suspended
   - *S* means sleeping
   - *R* means active
   - *+* means foreground

 ## Challenge 8: Foregrounding processes
 Getting background process to foreground

### My solve
**Flag:** `pwn.college{U259Oq9fiLbBFSE4fJDfSK_wh0-.QX4QDO0wCM3gjNzEzW}`
Suspend *run*, then resume it in the background, bring it to the foreground, and get the flag
```bash
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the 
background, and *then* foreground it without re-suspending it! You can 
background me with Ctrl-Z (and resume me in the background with 'bg') or, if 
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~foregrounding-processes:~$ 


Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out. After that, resume me into the foreground with 'fg'; 
I'll wait.

hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{U259Oq9fiLbBFSE4fJDfSK_wh0-.QX4QDO0wCM3gjNzEzW}

``` 

### What I learned
- We can get our background running processes to the foreground by simply using *fg* again


## Challenge 9: Starting Backgrounded processes
 Running processes in background, without suspending them first

### My solve
**Flag:** `pwn.college{Uzi1ojT-llGwdOat9y0qV9pgwy8.QX5QDO0wCM3gjNzEzW}`

```bash
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 149
hacker@processes~starting-backgrounded-processes:~$ 


Yay, you started me in the background! Because of that, this text will probably 
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{Uzi1ojT-llGwdOat9y0qV9pgwy8.QX5QDO0wCM3gjNzEzW}

[1]+  Done                    /challenge/run
``` 

### What I learned
- We can directly run a process in the background (without first suspending it) by using *&* appended to the command

## Challenge 10: Process Exit Codes
 All commands and processes exit with an exit code. This might be 0 (for success), 1 (for failure) or any other non-zero number for error.

### My solve
**Flag:** `pwn.college{wBOEkmF5SxCUw6CV_kuohKbTiT7.QX5YDO1wCM3gjNzEzW}`

*get-code* gave an error (read by using *echo $?*). The error code is then passed as an argument into *submit-code*

```bash
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
175
hacker@processes~process-exit-codes:~$ /challenge/submit-code 175
CORRECT! Here is your flag:
pwn.college{wBOEkmF5SxCUw6CV_kuohKbTiT7.QX5YDO1wCM3gjNzEzW}
``` 

### What I learned
- We can read the exit code of the most recent command using *$?* (the $ is to read the value)
- We can thus determine the functionality of a process by reading its error codes.