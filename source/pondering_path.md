# Pondering PATH

### The PATH variable
We set `PATH` to `""` (empty), and use `export` it to make sure children processes have the values overwritten as well causing `rm` to not be found by `/challenge/run`.
```bash
hacker@path~the-path-variable:~$ export PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{8EDmyhUGn_5SjwHGGfu5YgmV4P0.dZzNwUDLxUjN0czW}
hacker@path~the-path-variable:~$ 
```
