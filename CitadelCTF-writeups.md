# Citadel CTF writeups
## Challenge 1: Zahard's Welcome

### Description
The base of Citadel rises before you, its great doors sealed with fractured steel and dead circuitry. Faded corporate protocols still hum in the lock, relics of the world that fell.

Those who came before tried to climb but all failed. Their echoes linger as fragments of voices, reminders of broken attempts to free humanity. Now you have chosen to take their place. You will be the one to scale the Citadel and finish what they could not.

The voices of the fallen whisper through the static: “The path begins in the gathering place. There, candidates are chosen.”

Here is your invitation - https://discord.gg/FfBw8VzfRR. Step into the gathering place where all climbers are briefed before the ascent.

### Solve
 Clicked the link to the discord server (joined the server) and got the flag
 Flag: ```citadel{7h3_c174d3l_b3ck0n5}```


## Challenge 2: The social network
   
### Description
OSINT pt1: The ascent begins. The first floor is not metal or binaries but of memory. Among the echoes, one voice lingers, of an early climber. He was among the earliest to challenge the Citadel, and though he failed, his traces remain scattered across the ruins of the old world.

It is said that the key to the next floor can be found by tracing the socials of this legendary climber. Start by checking out citadweller on Instagram.

### Solve
Visited *citadweller* instagram account. Their story highlight had the 1st half of the flag
The *citadweller* twitter account had the 2nd account
Flag: ```citadel{17_1s_jus7_7h3_b3g1nn1ng}```

## Challenge 3: Omniscient Flag's Metadata
   
### Description
As you step into the second chamber, a figure manifests before you. Before you stands a forgotten deity, a dead god spoken of only in whispers. Known by countless names: “Apostle of Epilogue and Eternity,” “Lone Messiah” and many more lost to time.

They leave nothing but a single image, a relic carrying his final secret. Hidden within its layers lies the key to ascend to the next chamber.
![alt text](<challenge (1).jpg>)

### Solve
We get hint that key is *hidden within layers*. We manipulate the image by uploading in exiftool. Thus we get another image which contains the flag
![alt text](flag.png)
Flag: ```citadel{17_1s_jus7_7h3_b3g1nn1ng}```

## Challenge 4: Track8
   
### Description
Bypassing the second chamber leads to an empty floor except for a single artifact in the center: an old MP3 player, scratched and worn. On its surface, a cipher is etched, a message left behind for anyone who can decode it:

twj eys zpr ukm 'viamnwqw' bx lzgo: esmqqui{yyr_oshwwcm_bwupa}
When you power it on, the sound fills the chamber. The tracks play like whispers from a lost world, and you recognize it as a song from Panchiko’s latest studio album, particularly track no. 8. Its title feels familiar, hinting at a famous cipher. Decrypt it by using the album name as your key and continue your ascent

### Solve
*twj eys zpr ukm 'viamnwqw' bx lzgo: esmqqui{yyr_oshwwcm_bwupa}* is a vingere cipher
The key is *Panchiko's latest studio album* i.e., ginkgo
- This decodes to *now use the key 'panchiko' on flag: rigckmv{osd_ikumqog_tjkjm}*
- Using vingere again with gingko key we get flag as *citadel{add_vinegar_twice}*
Flag: ```citadel{17_1s_jus7_7h3_b3g1nn1ng}```


## Challenge 5: Test of Sweetness
   
### Description
This floor feels like a digital world. The space is an illusion, all pink and sweet, stretching around you in impossible patterns. Here, you are no longer a climber but just another user.

Ahead, a door glows faintly. It is the only path forward and requires a level of authority you do not yet have. Fragments of session memory flicker, hinting at what it might take to gain higher access.

Challenge: https://testofsweetness.citadel.cryptonitemit.in

### Solve
The link takes us to a website which asks us to become an admin in order to enter it
![alt text](image-1.png)
- *how does the website remember you* This refers to the website cookies
- On opening the cookies, we  see that we are saved as *user*, so we change it to *admin*, thus allowing us to get the flag
Flag: ```citadel{fru1tc4k3_4nd_c00k13s}```


## Challenge 6: Rotten Apple
   
### Description
Among the debris of this floor, you find a relic of sound: An album which turns out to be D>E>A>T>H>M>E>T>A>L by Panchiko, a long lost album. But the music is warped, as though it has undergone disc rot.

The path forward is hidden in the distortion. Similar to how the album was warped, the password to the next floor has been warped first by a factor of 47, then by a factor of 13. Untangle these changes to reveal the code and continue your ascent.

4:R256=Y3oRRoP0#~%Ro?A

### Solve
- *rot* hint tells us that we use rot cipher
- *47* and *13* hints at the rot numbers
- no sensible flag forms with 13, so we used 47 to get flag
Flag: ```citadel{b3tt3r_ROTt3n}```


## Challenge 7: Randomly Accessed Memories
   
### Description
On your ascent to this floor, you hear these fragments being played back —

clone it, pull it, reset it, stage it, 
commit, push it, fork, rebase it. 
merge it, branch it, tag it, log it, 
add it, stash it, diff, untrack it … 

You look around and discover a chamber containing a vast archive of Daft Punk’s music, intertwined with cryptic commits left behind by other musicians. They seem ordinary at first glance, but not everything in the history is what it seems. The archive: https://github.com/evilcryptonite/daft-punk-archive

### Solve
- In the github changes.txt file, changes 56, 122, 279 are missing
- Looking through the past commits, we see the commits 56, 122, 279 replaced with secret chunks 1, 2, 3
- concatenate the chunks and get a text which is encoded
- Thus, we decode using b64 to get flag '\n'
Flag: ```citadel{w3_4r3_up_4ll_n1t3_t0_g1t_lucky}```


## Challenge 8: Selected Ambient Work
   
### Description
The symphonic adventure does not end here. On the next floor, a single song keeps echoing through the floor, repeating in a haunting loop. Amid the sound, you find a note left by a past candidate. It hints that the song holds a secret message, hidden in plain sight, much like how Aphex Twin concealed his face within his music with the help of spectrograms.

To move forward, you must find the message hidden in this sound.

Note: Separate the words in the flag with _ and make it UPPERCASE. Example: citadel{S3L3CT3D_AMB13NT_W0RK}

### Solve
- used https://databorder.com/transfer/morse-sound-receiver/ to play the morse code
- The morse does not display message at first (there is background music messing with the code) we need to increase the frequency to like 750 for the letters to come
- There a long message decoded (which is not the answer)
- on the spectogram, *citadel{* appears. We use the part of text encoded within {} brackets
Flag: ```citadel{1_L0V3_1DM}```


## Challenge 9: The Robot's Trail
   
### Description
You enter a virtual maze, a labyrinth of shifting corridors and endless paths. A guardian robot patrols the floor, leaving a trail behind as it moves. Follow the path it carves, trace its movements carefully, and uncover the key it leads you to. Only by following the robot’s trail can you reach the door to the next floor.
Challenge: https://therobotstrail.citadel.cryptonitemit.in

### Solve
- the website opens to 5 decoy buttons, out of which none are correct. We use *inspect* to find the hidden hint
  ![alt text](image-4.png)
- On *hidden* class, we get hint to search */robots.txt*
  ![alt text](image-5.png)
- From here, we get hint as such 
   ![alt text](image-6.png)
- file */etc/passwd* tells us to *Check the web server config at /var/www/html/config.php:/home/webadmin:/bin/bash\n*
- We are asked to *Check the access logs for unusual activity*
   and log has location */var/log/apache2/access.log*
- message *Interesting environment variables might be found at /proc/self/environ* is next hint
- *SECRET_LOCATION=/home/ctf/.secret* is our next hint
- Finally we get the flag at */home/ctf/.secret/flag.txt*

Flag: ```citadel{p4th_tr4v3rs4l_m4st3ry_4ch13v3d}```


## Challenge 10: Rotting in the Deep
   
### Description
The floor is quiet, almost unnervingly so – like the Citadel has paused to take your measure. A soft ring of presence settles around the chamber, the kind that marks a true landing: from here, it will ask for more and, in return, grant more. Etched into its surface is a sequence of numbers, worn and faint, as if time itself is eating them away. A whisper from the echoes guides you:

The message lies beneath the surface. Push it three steps forward in the cycle of life, and only then will the words emerge from the void.

### Solve
- The python file gives us a fake file (don't fall for that)
- A text file is also given with numbers 
  *6895840967002953721051398351211751734500850509315790892845302801984496338433523326225010635779036738800318*
- The python code gives us the code as 3. We shift the numbers by 3 and convert it to string to get the flag

Flag: ```citadel{br0_r34lly_unr0tt3d_m3_b4ck_t0_l1f3}```


## Challenge 11: Coco Conjecture
   
### Description
The door to the next floor is guarded by a figure who calls herself "The Dragon CEO". She does not speak of mercy or choice, only of order and efficiency.

To enter the next chamber, you must complete the task presented by her. Complete it exactly as instructed, achieving operational efficiency by her standards, and the path forward will open.

Connection: nc chall_citadel.cryptonitemit.in 61234

### Solve
- We need to solve the problem statement in given pdf
  file:///C:/Users/Rochelle/Downloads/Coco_Conjecture.pdf
  We are given a network challenge where the server sends us random positive integers (`1 ≤ n ≤ 10^18`).  
  Our task is to compute how many steps it takes to reduce `n` to `1` using the following rules:

  - If `n` is **even**, replace `n` with `n / 2`.
  - If `n` is **odd**, replace `n` with `3n + 1`
  *collatz conjecture*
- In the netcat, the server sends numbers line-by-line (each followed by a newline).
 For each number n we apply the Collatz transformation until it becomes 1 and count the number of steps.
  when all numbers are answered correctly, the flag is revealed.
- we use python code to automate this 
 ```python
 from pwn import *

# Connect to the challenge
conn = remote('chall_citadel.cryptonitemit.in', 61234)

def steps(n):
    count = 0
    while n != 1:
        if n % 2 == 0:
            n //= 2
        else:
            n = 3 * n + 1
        count += 1
    return count

while True:
    data = conn.recvline().decode().strip()
    if not data:
        break
    if data.startswith("citadel"):
        print(data)
        break
    n = int(data)
    ans = steps(n)
    conn.sendline(str(ans))
  ```
Flag: ```citadel{k1ryu_c0c0_h4s_4_g0_4t_4n_uns0lv3d_m4th3m4t1cs_pr0bl3m}```


## Challenge 12: schlagenheim
   
### Description
Your quest continues, but you feel something odd about this room. The only artifact on this floor is a corrupted file held in the hands of a jet-black statue, frozen in the pose of a band mid-performance. The passcode to the next floor is hidden within this piece of music, but it can’t be played, as if the wrong extension has scrambled it.

You must take the corrupted file and repair it to reveal the true code that will unlock the door forward.

### Solve
- we get a .wav file which is cannot play as it is corrupted (the extension is wrong, it should be a midi file as hinted by description *mid*)
- Using hex editor, we change the file extention to midi file (change header to MThd)
- opening the changed midi file in a music editor, we can see the keys played in it. The key pattern on screen shows us the flag.
![alt text](image.png)
Flag: ```citadel{8lackM1D1wa5c00l}```


## Challenge 13: XOR Slide
   
### Description
You realise that a previous climber has set up a puzzle in what was otherwise an empty room, blocking the entrance to the next floor on the ceiling. You must slide the blocks forming the pyramid to create a path above.

### Solve
- Text file given has hexadecimal form text as
*b31113bd631c7207ec9587b32e686c8b6df255d66f4a987adacf6c283875ded5d1633b5f8823fa0b9bbbfab3195f1a51506afd54e03392ae338d872445c9025d88c8d4425a00a9b4478f86acadbd781df6a4194e376c09145a6f9afcbe02d36b5709f74d910edf94552dc4680041d6717fea824718c21385bdfd6176f722100548336d10ead87f01a95c5497dcb6c2*
- The hint / solution notes say this is a **ciphertext encrypted with a sliding XOR**: each ciphertext position is XORed with a known wrapper (plaintext fragments that appear before and after the flag) and with previously recovered keystream bytes. Using the wrappers and the sliding property we can recover the keystream and then decrypt the ciphertext to reveal the hidden message (and the flag).
- From the python code given , we can run the program and get output `bro i have a cRAzy story to tell you i went to ant4rctica and BOOM i saw a random citadel{pyr4m1d+x0r} it was crazy like how did it get there??`


Flag: ```citadel{pyr4m1d+x0r}```


## Challenge 14: The Sound of Music
   
### Description
OSINT pt2: citadweller had a newfound interest in tracking the music they last listened to and posting ratings of new albums on various online platforms.

The flag is hidden in these digital footprints across music platforms and split into three segments. You will need to find all three to uncover the complete code and move on to the next floor.

### Solve
- We need to find the flag in different online music streaming sites using *citadweller* username
- Spotify : On their profile, there is one playlist, the playlist description has the 3rd part of flag
- from description we see hint as *last* (last.fm) where the first part of flag is in the shoutbox
- rateyourmusic has the 2nd part of the flag

Flag: ```citadel{c0mputers_st0pped_exchang1ng_1nf0rmat10n_n_started_shar1ng_st0r1es_n_then_they_were_n0where_t0_be_f0und}```


## Challenge 15: Echoes and Pings
   
### Description
You come across the remnants of a fallen corporation and the final network communication ever sent by them.

Allegedly, the message contained an image that predicted the rise of the Citadel. Your task is to uncover what was sent and decode the communication to extract the passcode that will unlock the next floor.

### Solve
We are given a .pcap file (thus we can see the network traffic)
- We can see the ICMP (error detecting) has 2 packets. We searched for image file in it (Since description hinted at *image*) (could not find image file in TCP) and we found one jpg header in the 1st and 2nd ICMP packet
- We extracted the image bytes using CLI `tshark -r challenge.pcap -Y "icmp" -w icmp_packets.pcap` and visualised it in a Hex editor.

Flag: ```citadel{1_r34lly_w4nt_t0_st4y_4t_y0ur_h0us3}```


## Challenge 16: The Ripper
   
### Description
The guardian of this floor steps from the shadows. Known only as Jack the Ripper, he watches you carefully. He proclaims himself merciful and hands you a word list to help. He asks you to find the passcode hidden in the file. The word list is your only aid. Only by combining the two correctly, can you uncover the key and move on to the next floor

### Solve
- We have a file and given a wordlist. We need to combine two of them to form the actual flag
- the file with *$2a$04$RNoyoWAcW0StwSri4YN1Eeb2j1gBNKutDOMxsLzfyfSvB/ghMHToa* to be decoded
- We decrypted the code in a hash identifier to come to *bcrypt $2*$, Blowfish (Unix)* as algorithm
- To get password from wordlist.txt, we use *john* command (learnt in pwn.college). This gets us the password as `fake_flag_4_fake_pl4y3rs` 

Flag: ```citadel{fake_flag_4_fake_pl4y3rs}```


## Challenge 17: AetherCorp NetprobeX
   
### Description
You step into a simulation of the past, entering the ruins of AetherCorp, the most ambitious corporation in history, and their creation, NetProbeX, once the most advanced networking tool the world had ever seen. The floor reconstructs the events that led to humanity’s downfall.

Your task is to find the hidden backdoor in NetProbeX, the flaw that triggered the collapse. By uncovering it, you can reverse the damage and retrieve the passcode to advance to the next floor.

Engineers left faint traces in the logs — small, odd markers where separators once sat. Read these traces as if they divide commands.

Challenge: http://chall_citadel.cryptonitemit.in:32772/

### Solve
- in the website link, we have an inputting area asking for pings.
    ![alt text](image-3.png)
- After trying various pings, we realise that many separators (like . , ; {} etc) are *malicious*
- %0A is being accepted, so we use it to enter commands
- *ls* command helps list out all files, out of which one is *mission_briefing.txt*
- we use *less* (since cat is not allowed) to read the file
  *Agent, your objective is to recover the Blacksite Key.  Our intel confirms it’s hidden deep within the AetherCorp network*
- We find the aerthercorp directory and list its files (using *ls* AND *ls -a* to find secret files)
- We get *.secrets* directory and get *blacksite_key.dat* file, reading which we get the flag
Flag: ```citadel{17_1s_jus7_7h3_b3g1nn1ng}```



## Challenge 18: Feels Like We Only Go Backwards
   
### Description
After finding the backdoor and making your way to the next floor, you step into a chamber awash with shifting colors and swirling echoes, a concert frozen in time. Kevin Parker stands at the center, his riffs bending reality around him. To ascend, you’ll need to join the session on his terms: push your voice further than comfort, align yourself with the number he hides in the haze, and piece together the melody concealed within layers of reverb. Only then will the music open the way upward.

### Solve
We get a code which we can use by reverse engineering it. We open it into ghidra (reverse engineering software)
thus we can see that
- `FUN_00101240` is the main function (has constants)
- `1340` and `14c0` are for level 2 and level 1 (redundant), thus main is `1240`
- flag is formed using the code, giving us the citadel{} answer
Flag: ```citadel{17_1s_jus7_7h3_b3g1nn1ng}```


## Challenge 19: Database Incursion
   
### Description
After your legendary battle with the artist, the virtual world has returned, stretching around you in endless grids and flickering data, you find a rogue data terminal and on careful inspection, you find you’re able to inject rogue structured queries. Using this critical vulnerability, find a way to extract the hidden passcode.

Challenge: https://databaseincursion.citadel.cryptonitemit.in

### Solve
The link given opens to a website asking for username and password (both of which we do not know yet)
![alt text](database_incursion.JPG)
We use SQLi. We input something in the working payload which is always true (in this case, we inputted 1=1 which is always true)
- From here, we come to a page where we have employee details (we need to enter admin password) Hint: *someone from management has the admin password.*
- We see the management people `department='Management'--` and we see that *KIWI* has the password
- We search for kiwi from management `(department='Management' and name='Kiwi')--`
Thus we get the flag from the employee
Flag: ```citadel{wh3n_w1ll_y0u_f1nd_0u7_1f_175_5ql_0r_53qu3l?}```


## Challenge 20: BRATCHA
   
### Description
A clear chime rolls through the chamber and a new crest ignites on your badge – a quiet promotion. The outer ring is behind you. From here, the Citadel opens its inner systems, and the locks grow heavier because the keys are worth more. Your answers now carry more weight – and earn more in return. The citadel welcomes you to the inner climb.

Near the gate to the next floor you come across a CAPTCHA verification test, but it has been covered by scratches on the decaying wall and misleading letters stopping you from finding the correct key, all to prove you’re human.

### Solve
The image had a URL having overwriting.
![alt text](BRATCHA.jpg)
- the characters were `c/s g/q x/y h/n x/v B/D h/n S/Z`
- This meant 256 possible outcomes. Listed down these 256 outcomes and pasted into https://httpstatus.io/ 
- This showed the only url which was working, *https://pastebin.com/sqxnxBhZ* where we got the flag
Flag: ```citadel{1m_3v3rywh3r3_1m_s0_jul1a}```


## Challenge 21: A Memory's a Heavy Burden
   
### Description
You now find yourself in the place where many climbers have been laid to rest. A cold wind moves through the temple grounds, carrying whispers of the departed. Stone lanterns and marble graves reflect Buddhist traditions, their shadows stretching across the frost-covered earth.

The temple rests in the shadow of a very iconic mountain, quiet and imposing. Every detail in the image, the arrangement of the graves, the lanterns, and the lingering scent of incense, holds clues to its true location. You need to uncover the exact coordinates of where you are to move on from here.

Note: round off coordinates to 3 decimal places.

Flag format: citadel{XX.XXX_XXX.XXX}

### Solve
A picture is given. We can see mount Fuji in the distance, meaning its in Japan. The compass direction showed the place was North of Mt.Fuji
![alt text](location.png)
The description hints at a temple or a cemetary (also confirmed by the picture)

- On Google Earth, approximate coordinates were coming as 35.XXX and 138.XXX

- From description, it is a *buddhist* *cemetary*. Searching for all buddhist cemetaries north of mt.fuji, and checking them on street view, we land on the correct one (*Tsugenji Temple*), noting down its coordinates, and getting the flag (round the number to 3 decimal places)

Flag: ```citadel{35.486_138.699}```


## Challenge 22: Case Sensitivity
   
### Description
You step into a constricted floor where every movement and operation is limited. Commands are few, space is tight, and options are restricted.

A guardian looms over the floor, its body shifting like liquid metal, enforcing these constraints. It watches your every move, daring you to make do with what you have and uncover the passcode to the next floor despite the restrictions.

Connection: nc chall_citadel.cryptonitemit.in 32770

### Solve
- We need to do the challenge in the given netcat
  ```bash
  Ha, I bet you can't find what "FLAG" is in this shitty python interpreter.
   What could you possibly even do here?

  >>>
  ```
- Giving any word or command gives us error `ValueError: NUH UH, cat is not allowed!`
- When we give certain words like `print` or `environ`, it shows `ValueError: NUH UH, environ is not allowed! (although environ is very close)`. This can be made right using captial letters as PRINT and ENVIRON (since challenge name is *case sensitivity*) which changes the error to `NameError: name 'ENVIRON' is not defined`
Giving command `exec` is allowed. 
- Using the whitelist words, we can find out the correct command to be `exec("PRINT(ENVIRON".lower() + "['FLAG'])")` which gives the flag

Flag: ```citadel{d34th_d035_n07_fr33_y0u_fr0m_7h3_gu17ar15t}```


## Challenge 23: Viral Bionic Anomaly
   
### Description
This floor is haunted by a phantom of the past. You encounter a presentation created by the last employee of a forgotten corporation, made just minutes before the Citadel awoke.

Rumor has it that the corporation predicted the rise of the Citadel. Within the slides, a "starter pack" holds the clues you need. Use it to confront the "final boss," a threat trapped inside a macro hidden deep within the presentation, and claim the key to the next floor

### Solve
We are given a .pptm file instructing us to use macro. So we enable the developer tab and view the VBA (Visual Basic) code
There are three parts to the code. The first part is Base32 encoded, second is base64 and third is base32. Each part is further divided into many strings. Concatenating all of the string parts and decoding them gets us the bytes of a JPG file (image, as seen by the header `FF D8 FF E0`)
Each part of the code is a part of the image forming
![alt text](image-2.png)
(we did not decode the entire code, we decoded the major part of it and we could make out the flag from that itself)
Flag: ```citadel{gr4b_y0ur_l4bubus_m4tch4s_4nd_dub41_ch0c0l4t3s_y0u_4r3_1n_f0r_4_r1d3}```
