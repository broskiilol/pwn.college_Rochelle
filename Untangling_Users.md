# Untangling Users
There are many users on a system. list of users can be accessed from */etc/passwd*
## Challenge 1: Becoming with su
   Change the user (*hacker*) to root 

### My solve
**Flag:** `pwn.college{s6ao2ypLHSDiS-SDs2iY6CTa-vM.QX1UDN1wCM3gjNzEzW}`
Using *su* we can become a root.
This then asks us for the password, which is "hack-the-planet" and we are given root access
```bash
hacker@users~becoming-root-with-su:~$ su
Password: 
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{s6ao2ypLHSDiS-SDs2iY6CTa-vM.QX1UDN1wCM3gjNzEzW}
```

### What I learned
- the flag file can only be accessed by the root 
- Thus, to become the root, (*change users*) we use *su*. After becoming the root, we can carry out whatever processes which a root can.


## Challenge 2: Other users with su
   We need to become *zardus* user to run the challenge.
### My solve
**Flag:** `pwn.college{wVj60EUc-es0hmNQEOsuZLhms9O.QX2UDN1wCM3gjNzEzW}`

```bash
hacker@users~other-users-with-su:~$ su zardus
Password: 
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{wVj60EUc-es0hmNQEOsuZLhms9O.QX2UDN1wCM3gjNzEzW}
```

### What I learned
- We can become any user on the system using *su*

## Challenge 3: Cracking Passwords
  Getting passwords to the users from the leaks
### My solve
**Flag:** `pwn.college{85II0il_VcAdp8lf9BZEEwI5jVq.QX3UDN1wCM3gjNzEzW}`

Using *john* gives us the password, with which we can access Zardus.

```bash
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Created directory: /home/hacker/.john
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
0g 0:00:00:12 0% 2/3 0g/s 281.0p/s 281.0c/s 281.0C/s brenda..keith
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04821g/s 280.7p/s 280.7c/s 280.7C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ su zardus
Password: 
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{85II0il_VcAdp8lf9BZEEwI5jVq.QX3UDN1wCM3gjNzEzW}
```

### What I learned
- Passwords are stored in */etc/shadow* file
- All the password storing files have different fields in them, separated by ":"
   - The first ":" separates the username and the password
   - In the password field, 
      - :: Implies no password 
      - :!: or :*: implies password login is disabled
      - :(long string): is the one-way-encryption of the password (also called hashing)
- ***WORKING OF PASSWORDS:** On entering password, it is hashed (or one-way-encrypted) and compared to the stored password. Access is granted accordingly.
- We can crack passwords by using *john*, which essentially decrypts the password. Thus, we can access the user.

## Challenge 4: Using sudo
  Using *sudo* command
### My solve
**Flag:** `pwn.college{Ugu5BD-6svkrZ29w8EEkhziGz3N.QX4UDN1wCM3gjNzEzW}`

```bash
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{Ugu5BD-6svkrZ29w8EEkhziGz3N.QX4UDN1wCM3gjNzEzW}
```

### What I learned
- *su* requires passwords which is tough to maintain and can leak, thus we use sudo
- sudo defaults to running a command as root, instead of giving access to root.
- *sudo* checks policies to see if the user has access to run commands as root (*/etc/sudoers* have the policies)
