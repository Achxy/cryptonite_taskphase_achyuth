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

### Grepping stored results
Identical to previous challenges, we redirect `/challenge/run` to `/tmp/data.txt`, and we grep the stored file for `pwn.college` pattern.
```bash
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep pwn.college /tmp/data.txt
pwn.college{cpA44fj6_efFXeUDnXaWXWpAy7C.dhTM4QDLxUjN0czW}
hacker@piping~grepping-stored-results:~$ 
```

### Grepping live output
We'll use `|` to pipe the stdout of `/challenge/run` to the standard input of `grep` with the search pattern `pwn.college`.
```bash
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{4XBYWKDUf2i2nAAzYrLTfj7oup6.dlTM4QDLxUjN0czW}
hacker@piping~grepping-live-output:~$ 
```

### Grepping errors
We're redirecting stderr as evident by `2>` to stdout by using `&1` then piping it using `|` to `grep` which proceeds to find the pattern.
```bash
hacker@piping~grepping-errors:~$ /challenge/run 2>&1 | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{UCCVR2V9r51PRmICTikAKDjYkzH.dVDM5QDLxUjN0czW}
hacker@piping~grepping-errors:~$ 
```

### Duplicating piped data with tee
We pipe the stdout of `/challenge/pwn` to `tee` which pipes it to `~/intercept` and `/challenge/college`,
we understand the "secret" usage of `/challenge/pwn` by reading contents of `~/intercept`.
```bash
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee ~/intercept | /challenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code 
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the 
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat intercept
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "wPuE-FSt"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret wPuE-FSt | tee ~/intercept | /challenge/college
Processing...
WARNING: you are overwriting file /home/hacker/intercept with tee's output...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{wPuE-FStCMm5URRh7Jcd_iRmVXs.dFjM5QDLxUjN0czW}
hacker@piping~duplicating-piped-data-with-tee:~$ 
```

### Writing to multiple programs
We pipe the output of `/challenge/hack`, we pipe it too `tee`, then we use process substitution on `/challenge/the` by writing it as
`>(/challenge/the)`, there by temporarily creating a file in `/dev/fd/...` asssociated with it which we will be used for piping, then
the out of `tee` is piped to `/challenge/planet`
```bash
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) | /challenge/planet
Congratulations, you have duplicated data into the input of two programs! Here 
is your flag:
pwn.college{k2QlzBDVSLLUyQ3mzlMROfXCZ00.dBDO0UDLxUjN0czW}
hacker@piping~writing-to-multiple-programs:~$ 
```

### Split-piping stderr and stdout
Exactly the same as the previous challenges, this time we redirect `hack` to `/challenge/planet` using `>` (which is implicitly `1>`, ie,
stdout), and to `/challenge/the` using `2>` which is standard error. Process substitution is used.
```bash
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack > >(/challenge/planet) 2> >(/challenge/the)
Congratulations, you have learned a redirection technique that even experts 
struggle with! Here is your flag:
pwn.college{QnvXsZS5GwWALiWLKsSicF_4Zq2.dFDNwYDLxUjN0czW}
hacker@piping~split-piping-stderr-and-stdout:~$ 
```
