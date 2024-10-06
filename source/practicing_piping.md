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

### Appending output
We use `>>` to append to the redirecting destination instead of `>` which overwrites it.
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
hacker@piping~appending-output:~$ cat the-flag
 | 
\|/ This is the first half:
 v 
pwn.college{MOlr7uMGxAOlLooRetYOYMBQuIz.ddDM5QDLxUjN0czW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>) 
rather than *append* mode (>>), and so the write of the second half to stdout 
overwrote the initial write of the first half directly to the file. Try append 
mode!
hacker@piping~appending-output:~$ 
```

### Redirecting errors
We use file descriptor code `1` for `stdout`, and `2` for `stderr`, and we redirect according to the challenge instructions and get the flag.
```bash
hacker@piping~redirecting-errors:~$ /challenge/run 1> myflag 2> instructions
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
[FLAG] pwn.college{sp_ZXJhfK9lXcSRIUCUM4jzVaMg.ddjN1QDLxUjN0czW}

hacker@piping~redirecting-errors:~$ 
```

### Redirecting input
We write `COLLEGE` to `PWN` just like we did in a previous challenge, next we redirect input `PWN` to `/challenge/run` using `<`.
```bash
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read 
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{Q0feoSNOsoFwI3nYv6eibT6d83f.dBzN1QDLxUjN0czW}
hacker@piping~redirecting-input:~$ 
```