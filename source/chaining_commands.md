# Chaining Commands

### Chaining with semicolons
Execute `/challenge/pwn; /challenge/college` to run both commands sequentially. The semicolon (`;`) chains the commands.
```bash
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{csjgABMaMkaMV3OOaxxEaNHzVBn.dVTN4QDLxUjN0czW}
hacker@chaining~chaining-with-semicolons:~$ 
```

### Your first shell script
I used `printf` instead of the usual `echo` because I didn't want the `\n` to be interpretted literally, we use redirection to get the output of that to `x.sh` and then execute it with `bash x.sh`.
```bash
hacker@chaining~your-first-shell-script:~$ printf "/challenge/pwn\n/challenge/college" > x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{oXpm7HolZMDwoK4eFwogbMoL_pM.dFzN4QDLxUjN0czW}
hacker@chaining~your-first-shell-script:~$ 
```

### Redirecting script output
We use the same `x.sh` we created in the last challenge, provide it to `bash` as argument and pipe it to `/challenge/solve`.
```bash
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{0ac9nP_z0U-uB7mgShHw5szyV_G.dhTM5QDLxUjN0czW}
hacker@chaining~redirecting-script-output:~$ 
```

### Executable shell scripts
Make file `y.sh` with content `/challenge/solve`, add permision for execution of `y.sh` to user `hacker` with `u+s` using `chmod`, then execute the file with `./y.sh`.
```bash
hacker@chaining~executable-shell-scripts:~$ echo /challenge/solve > y.sh
hacker@chaining~executable-shell-scripts:~$ chmod u+x y.sh
hacker@chaining~executable-shell-scripts:~$ ./y.sh
Congratulations on your shell script execution! Your flag:
pwn.college{4HPzPm4lyZFbJ20VQ3Kv74ulINo.dRzNyUDLxUjN0czW}
hacker@chaining~executable-shell-scripts:~$ 
```
