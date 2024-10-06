# Practicing Piping

### Redirecting output
We redirect stdout (of what should be `PWN`) to the file `COLLEGE` using `>`.
```bash
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your 
flag:
pwn.college{siLSywg1p0rQF-Nh8FqKiqYwPMC.dRjN1QDLxUjN0czW}
hacker@piping~redirecting-output:~$ 
```

### Redirecting more output
We redirect stdout of `/challenge/run` to `myflag`, the text displayed in the terminal by `/challenge/run` is actually `stderr`.
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
[FLAG] pwn.college{wzdYppfWUfO8A2Ssrc5lmaTzkMU.dVjN1QDLxUjN0czW}

hacker@piping~redirecting-more-output:~$ 
```
