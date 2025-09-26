# Pondering Paths
  Challenges to learn about the working of file systems in linux. 
## Challenge 1: The root:
 The filesystems can be viewed as a tree. There are various branches i.e., directories, and it all starts from a root. The root of the filesystem is "/". The path taken from "/" is called the absolute path. 

### My solve
**Flag:** `pwn.college{cfMLp3ZT_5mgCqk5YeCWD9L-xZ7.QX4cTO0wCM3gjNzEzW}`


```bash
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{cfMLp3ZT_5mgCqk5YeCWD9L-xZ7.QX4cTO0wCM3gjNzEzW}
```

### What I learned
Since the path pwn starts from "/", it means that "/pwn" is an absolute path.


## Challenge 2: Program and absolute paths
   To access the "run" file in the "challenge" directory
### My solve
**Flag:** `pwn.college{8pNZBAoOe9sljHJIkt1wgxurXWI.QX1QTN0wCM3gjNzEzW}`


```bash
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{8pNZBAoOe9sljHJIkt1wgxurXWI.QX1QTN0wCM3gjNzEzW}
```

### What I learned
This challenge helps us access files in various directories. The "run" file is stored in the "challenge" directory. So, to access the file, we first will need to enter the pathway of the challenge directory, which is in turn in the root directory. Again, since the pathway starts from the "/" directory, or the root, it is an absolute path.

### References 
no references

## Challenge 3: Position thy self
  change the current working directory to run the "/challenge/run" program
### My solve
**Flag:** `pwn.college{wM9_OSLfpDhNdFQIiwtR1aXAaHb.QX2QTN0wCM3gjNzEzW}`

First, I tried to run the program by typing "challenge/run" like I normally would, but since I was not in the required directory, it gave an error and told me to enter the specific directory.

```bash
hacker@paths~position-thy-self:/$ challenge/run
Incorrect...
You are not currently in the /proc/138/fd directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:/$ cd /proc/138/fd
hacker@paths~position-thy-self:/proc/138/fd$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{wM9_OSLfpDhNdFQIiwtR1aXAaHb.QX2QTN0wCM3gjNzEzW}
```

### What I learned
the command "cd" helps us change our directory. 
Out of curiosity, I furthur went to search the purpose for "~" in the bash shell. "~" refers to the home directory (or default directory) of the user.

## Challenge 4: Position elsewhere
  change the current working directory to run the "/challenge/run" program
### My solve
**Flag:** `pwn.college{snwkwgFdVaawaN_NjS5YJXS6FAL.QX3QTN0wCM3gjNzEzW}`

This time, the specific directory is different from what is was in challenge 3. Thus, we need to first change our directory to the said directory, then run the program.

```bash
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/doc/fontconfig directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /usr/share/doc/fontconfig
hacker@paths~position-elsewhere:/usr/share/doc/fontconfig$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{snwkwgFdVaawaN_NjS5YJXS6FAL.QX3QTN0wCM3gjNzEzW}
```

### What I learned
we need to change our directories with respect to where the file or program is stored. In challenge 3, the program path was "/proc/138/fd", but in this challenge it has been changed to "/usr/share/doc/fontconfig". Thus, we need to accordingly change our directories. 
Like the previous challenge, this is also an absolute path (it is directly started from root "/")


 ## Challenge 5: Position yet elsewhere
  change the current working directory to run the "/challenge/run" program
### My solve
**Flag:** `pwn.college{gpfNsW9MGVm4Sodu3Doy01LXlHF.QX4QTN0wCM3gjNzEzW}`

This time, the specific directory is different from what is was in challenge 3. Thus, we need to first change our directory to the said directory, then run the program.

```bash
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/doc/fontconfig directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /usr/share/doc/fontconfig
hacker@paths~position-yet-elsewhere:/usr/share/doc/fontconfig$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{gpfNsW9MGVm4Sodu3Doy01LXlHF.QX4QTN0wCM3gjNzEzW}
```

### What I learned
This is same as challenge 4.


## Challenge 6: Implicit relative paths, from /:
 A path which is not beginning with root "/", is called a relative path. It is taken in relation to the "cwd" or  current working directory. According to which directory we are in, we need to change our relative path.

### My solve
**Flag:** `pwn.college{Q6RmXLdeqYwBV2nNAQRw34SOdGX.QX5QTN0wCM3gjNzEzW}`


```bash
hacker@paths~implicit-relative-paths-from-:~$ /challenge/run
Incorrect...
You are not currently in the / directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{Q6RmXLdeqYwBV2nNAQRw34SOdGX.QX5QTN0wCM3gjNzEzW}
```
When I tried to run the "/challenge/run" program, it showed an error saying that i was not in the "/" directory. Thus, I had to first go inside the root directory using "cd". 

### What I learned
In relative paths it is important to make sure I am in the correct directory. Since in the given challenge, we were inside "/" directory, the relative directory starts from "challenge".  


## Challenge 7: Explicit relative paths, from /
   Exploring explicit methods of using relative paths
### My solve
**Flag:** `pwn.college{gIZ_lIUkvLrN8EqieY_YlOAcL2o.QXwUTN0wCM3gjNzEzW}`


```bash
hacker@paths~explicit-relative-paths-from-:~$ /challenge/run
Incorrect...
You are not currently in the / directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ challenge/run
Incorrect...
This challenge must be called with a relative path that explicitly starts with a `.`!
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{gIZ_lIUkvLrN8EqieY_YlOAcL2o.QXwUTN0wCM3gjNzEzW}
```

### What I learned
In challenge 6, we were using naked relative paths i.e., we were stating which directory to enter and from where. In explicit relative paths, we will use "." and ".."
1. "." refers to the same directory we are currently in. In the above example, I first enter the root directory using "cd /". Then I use "./" to indicate that I am trying to run the challenge program from inside the root directory (which I have entered)
2. ".." refers to the parent directory of the directory we currently are in. For example, if cwd is "/user/challenge", then "../run" refers to "/user/run", while "/run" refers to "/user/challenge/run".

### References 
- https://pwn.college/linux-luminarium/paths/ [Module- Pondering Paths]

## Challenge 8: Implicit relative path
   Explore ways to explicitly run relative paths
### My solve
**Flag:** `pwn.college{oBJYp6YbQkKnvdPYqoFjOS1gVRQ.QXxUTN0wCM3gjNzEzW}`

When I tried to launch "run" from "challenge", it would not allow me to, since "run" is a directory. On typing "/run" directly, it would come out of "challenge" directory and go into "run" directory (which is not what we wanted). Thus, we had to use "./run" to launch the "run" file from inside "challenge" directory.

```bash
hacker@paths~implicit-relative-path:~$ cd /
hacker@paths~implicit-relative-path:/$ challenge/run
Incorrect...
You are not currently in the /challenge directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~implicit-relative-path:/$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ /run
bash: /run: Is a directory
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{oBJYp6YbQkKnvdPYqoFjOS1gVRQ.QXxUTN0wCM3gjNzEzW}
```

### What I learned
- Typing "cd /challenge" and then typing "run" is not equivalent to "/challenge/run". 
- When using a naked path, Linux does not look into the current working directory, rather it goes back to the home directory.
- This is a safety measure, so that we do not acidently launch some program in current directory which has the same name as the core system directory.
- Thus, to execute a program in another specific directory, we need to use "./" or "../" like in challenge 7.

### References 
- https://pwn.college/linux-luminarium/paths/ [Module- Pondering Paths]

## Challenge 9: Home sweet home
Workings of the home directory
### My solve
**Flag:** `pwn.college{UuAYQj3c4vUfHj0Cs0wKaQlA1MF.QXzMDO0wCM3gjNzEzW}`

```bash
  hacker@paths~home-sweet-home:~$ /challenge/run ~/f
Writing the file to /home/hacker/f!
... and reading it back to you:
pwn.college{UuAYQj3c4vUfHj0Cs0wKaQlA1MF.QXzMDO0wCM3gjNzEzW}
Explore ways to explicitly run relative paths

```

### What I learned
- *~* expands to */home/hacker* (this is in our case, since our home directory is /home/hacker)
- *cd* command by default directs us to the home directory

### References 
- https://pwn.college/linux-luminarium/paths/ [Module- Pondering Paths]
   