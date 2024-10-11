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
