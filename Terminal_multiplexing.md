# Terminal multiplexing
## Challenge 1: Launching screen
  
### My solve
**Flag:** `pwn.college{YWoZNKD0GmPO_cHkYbAhPQgE8Qd.0VN4IDOxwCM3gjNzEzW}`

```bash
Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{YWoZNKD0GmPO_cHkYbAhPQgE8Qd.0VN4IDOxwCM3gjNzEzW}
```

### What I learned
 - *screen* command helps use open a screen session


## Challenge 2: Detaching and attaching
### My solve
**Flag:** `pwn.college{4o9_pY72VXNGF7ZfFL6EQaoWpTK.0lN4IDOxwCM3gjNzEzW}`
Opened a screen, detached from it and ran *run*, the reattached.
```bash
hacker@terminal-multiplexing~detaching-and-attaching:~$ /challenge/run
Your screen session is still attached!

You need to detach from your screen session first.
Press Ctrl-A then d to detach.
hacker@terminal-multiplexing~detaching-and-attaching:~$
hacker@terminal-multiplexing~detaching-and-attaching:~$ echo Yes! Flag is: pwn.college{4o9_pY72VXNGF7ZfFL6EQaoWpTK.0lN4IDOxwCM3gjNzEzW}
Yes! Flag is: pwn.college{4o9_pY72VXNGF7ZfFL6EQaoWpTK.0lN4IDOxwCM3gjNzEzW}
```

### What I learned
- *ctrl+A* and *d* helps detached from screen
- *screen -r* used to reattach 

### References 
no references

## Challenge 3: Finding sessions
  Find the session needed when lots of session are there
### My solve
**Flag:** `pwn.college{kQ6QjqWWAqn36CdnHggI74TEGgV.01N4IDOxwCM3gjNzEzW}`
```bash
hacker@terminal-multiplexing~finding-sessions:~$ screen -ls
There are screens on:
        156.pts-0.terminal-multiplexing~launching-screen        (Remote or dead)
        159.pts-0.terminal-multiplexing~launching-screen        (Remote or dead)
        147.pts-0.terminal-multiplexing~detaching-and-attaching (Remote or dead)
        158.pts-0.terminal-multiplexing~launching-screen        (Remote or dead)
        144.session_eab5d663908c7dc7    (Detached)
        147.session_be6b7931e549c669    (Detached)
        150.session_c14ff1b7f9c2b20a    (Detached)
7 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~finding-sessions:~$ screen -r session_eab5d663908c7dc7
[detached from 144.session_eab5d663908c7dc7]
```

```bash
hacker@terminal-multiplexing~finding-sessions:~$  echo 'Congratulations! You found the right session!'
Congratulations! You found the right session!
hacker@terminal-multiplexing~finding-sessions:~$  echo pwn.college{kQ6QjqWWAqn36CdnHggI74TEGgV.01N4IDOxwCM3gjNzEzW}
pwn.college{kQ6QjqWWAqn36CdnHggI74TEGgV.01N4IDOxwCM3gjNzEzW}
```

### What I learned
- *screen -ls* is used to list all sessions. Is also shows if the session is attached or not
- We can thus accordingly reattach to the screen we want

## Challenge 4: Switching windows
  switching between windows (tabs) on a screen
### My solve
**Flag:** `pwn.college{8JcMsmktr_XxSC1YF3NPT1QE-dv.0FO4IDOxwCM3gjNzEzW}`

started a screen. was first in windows 1, but the flag is in windows 0, so switched using *ctrl+A and 0*

```bash
hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{8JcMsmktr_XxSC1YF3NPT1QE-dv.0FO4IDOxwCM3gjNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{8JcMsmktr_XxSC1YF3NPT1QE-dv.0FO4IDOxwCM3gjNzEzW}
```

### What I learned
- In a screen, we can have multiple windows (like tabs)
- Shortcuts we can use in the windows are
   - Ctrl-A c - Create a new window
   - Ctrl-A n - Next window
   - Ctrl-A p - Previous window
   - Ctrl-A (0-9) - Jump directly to window 0-9
   - Ctrl-A '' - bring up a selection menu of all of the windows

## Challenge 5: Detaching and attaching (tmux)
 tmux = terminal multiplexer
### My solve
**Flag:** `pwn.college{IDDsGl1wDM_AhAL7r0_rg8WPOFp.0VO4IDOxwCM3gjNzEzW}`

```bash
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...

Flag sent! Now reattach to your tmux session with:
  tmux attach

You'll find the flag waiting for you there!
```
```bash
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$  echo Congratulations, here is your flag: pwn.college{IDDsGl1wDM_AhAL7r0_rg8WPOFp.0VO4IDOxwCM3gjNzEzW}
Congratulations, here is your flag: pwn.college{IDDsGl1wDM_AhAL7r0_rg8WPOFp.0VO4IDOxwCM3gjNzEzW}
```

### What I learned
- Difference in commands (mostly ctrl+a is replaced with ctrl+b)
  - tmux ls - List sessions
  - tmux attach or tmux a - Reattach to session
  - Ctrl-B and d - detach from tmux

## Challenge 6: Switching windows (tmux)
### My solve
**Flag:** `pwn.college{IIleKlm_b7uIHyESe-O-OdU0zEg.0FM5IDOxwCM3gjNzEzW`
entered tmux (entered at window 0), switched to window 1 to view the flag

```bash
hacker@terminal-multiplexing~switching-windows-tmux:~$ Here is your flag: pwn.college{IIleKlm_b7uIHyESe-O-OdU0zEg.0FM5IDOxwCM3gjNzEzW}
```

### What I learned
- tmux also has windows
- it shows the window at bottom of status bar `[0] 0:bash* 1:bash` where * shows current window
- Different key combos
  - Ctrl-B c - Create a new window
  - Ctrl-B n - Next window
  - Ctrl-B p - Previous window
  - Ctrl-B (0 -9) - Jump to window (0-9)
  - Ctrl-B w - See window picker
