# Data Manipulation
## Challenge 1: Translating characters
   Changing characters to print something else

### My solve
**Flag:** `pwn.college{0wmPP2tE_uANoITMCdB3OwnVnC-.01MxEzNxwCM3gjNzEzW}`


```bash
hacker@data~translating-characters:~$  /challenge/run | tr '[a-z][A-Z]' '[A-Z][a-z]'
yOUR CASE-SWAPPED FLAG:
pwn.college{0wmPP2tE_uANoITMCdB3OwnVnC-.01MxEzNxwCM3gjNzEzW}
```

### What I learned
- *tr* command is used to change the characters of the arguments given
- Multiple characters can be changed at once too. 
- We use pipe (|) cause we want to put the output of flag file as an input in *tr* 


## Challenge 2: Deleting characters
   Removing certain characters
### My solve
**Flag:** `pwn.college{YS0ma6_dr-QSSymta29VAXLSQxU.0FNxEzNxwCM3gjNzEzW}`

The flag file showed the flag with *^%* as unwanted and extra characters, so we removed them
```bash
hacker@data~deleting-characters:~$ /challenge/run
Your character-stuffed flag:
pw^%n^.c^%o%l%l^e^%g%e^{^Y%S0%m%a6^%_^%d^%r^%-Q%S^%S^y^%m^%t^a%2^9^V^%A^X%LS^%Q^%x^%U^%.%0F^%N%x%E%z^N^%x^w%C^M^%3^%gj%N^%z%E^zW}^%^%
hacker@data~deleting-characters:~$ /challenge/run | tr -d ^%
Your character-stuffed flag:
pwn.college{YS0ma6_dr-QSSymta29VAXLSQxU.0FNxEzNxwCM3gjNzEzW}
```

### What I learned
- Adding *-d* command to the *tr* command helps "translate" the character to nothing (essentially deleting it)
- Whatever argument is given to the command, is deleted. Multiple characters can also be given as an argument to delete them.

### References 
no references

## Challenge 3: Deleting newlines
  Convert a sentence having many lines, to a single line
### My solve
**Flag:** `pwn.college{8QaBXfkrP9_1C6SlUneMwGULfUr.0VNxEzNxwCM3gjNzEzW}`


```bash
hacker@data~deleting-newlines:~$ /challenge/run | tr -d "\n"
Your line-split flag: pwn.college{8QaBXfkrP9_1C6SlUneMwGULfUr.0VNxEzNxwCM3gjNzEzW}hacker@data~deleting-newlines:~$ 
```

### What I learned
- Similar to how we delete characters, we can also delete newlines by passing *"\n"* as the argument. 
- \n signifies a newline character (anything follwed by \ is for the computer to understand that the character is normally difficult to input)
- \n needs to be in quotes so that the computer passes it to tr, and does not try to interpret it.

## Challenge 4: Extracting the first lines with head
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

 ## Challenge 5: Extracting specific sections of text
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



## Challenge 6: Storing data
 Sorting given text files in order

### My solve
**Flag:** `pwn.college{kH7eCNZqEV5WxKvQ2YyB3ml4Wu3.0FM0MDOxwCM3gjNzEzW}`

```bash
hacker@data~sorting-data:~$ sort /challenge/flags.txt
pwn.colldge{kH7eCNYqDU5WxKvP2YyB3ml4Wu3.0EM0MDOxvCM3gjNzEyW}
pwn.colldge{kH7eCNZqEU4WxKvQ2XyB2ml3Wu3.0FM0MDOxwCL2fiNzDzW}
pwn.colldge{kH7eCNZqEU5WwKvP2XxB3ml4Wu3.0FM0MDOxwCM3giNzEzV}
pwn.collefe{jH6eBNZqEV5WxKvQ2XyA3ml4Vu2.0EM0LCNwwCM3gjMzEzW}
pwn.collefe{kH7dCNZqDV5WxKvQ2YyB3ml4Wu2.0FL0MDOxwCL3gjNzEyW}
pwn.collefe{kH7eCMZpEV4WxKvQ2YyB3ml4Wu3.0FM0MDOxwCM3gjNzEzV}
pwn.college{jH7eBNZpEV5WxKvQ1XxB3ll3Vu3.0EM0MDOwwCM2gjNyEyW}
pwn.college{jH7eCNYqEV5WxKvQ1YyA3ml4Wu2.0FM0LDOxwCM3giMzEzW}
pwn.college{jH7eCNZqEV4WxJuP2YxB3mk4Vu3.0FL0LCNxvBM2fjNzEzW}
pwn.college{kH6dCNZpEV4WwKuQ1YxA3lk4Vu3.0EL0LCNxwCM3giMzEyV}
pwn.college{kH7dCNZqDV5WxKvQ2YyB3ml4Wu3.0FM0MCOxvCM3gjNzEzW}
pwn.college{kH7eCMYpEV5WxKvQ2YyB3ll3Wu3.0FM0LDNxwBM3fiNzEyV}
pwn.college{kH7eCMZqEV4WxKuQ2YyB3ml4Vu2.0EM0MDOxwBM2giNzEzV}
pwn.college{kH7eCMZqEV5WwKvQ2YxB3ll4Wu3.0FL0MDNxwCM2gjNzEzW}
pwn.college{kH7eCNYqDV5WxKvQ2XyB3ml4Wt3.0EL0MDOxwCM2fjMzEzW}
pwn.college{kH7eCNYqEV5WxKvQ2YyB3ml4Wu3.0FM0LDOxwCM3gjNzEzW}
pwn.college{kH7eCNZqDU5WxKvP1YyB3ml4Wu3.0FM0MDNxwCM3gjNzDzW}
pwn.college{kH7eCNZqEU4WxKvQ2YyB3ml4Wu3.0FM0MDOwwCL3fiNzEzW}
pwn.college{kH7eCNZqEV5WxKvQ2YyB3ml4Wu3.0EM0MDOxvCM3gjNzEzW}
pwn.college{kH7eCNZqEV5WxKvQ2YyB3ml4Wu3.0FM0MDNxwCM3gjNzEzW}
pwn.college{kH7eCNZqEV5WxKvQ2YyB3ml4Wu3.0FM0MDOxwCM3gjNzEzW}
``` 

### What I learned
- *sort* command is used to sort the data in a file
- By default, it sorts the data alphebetically
- Arguements can alter the way it is sorted
   - *-r* for reverse alphabetical order
   - *-n* for numeric order
   - *-u* removes the duplicate lines of data
   - *-R* sorts in a random order
