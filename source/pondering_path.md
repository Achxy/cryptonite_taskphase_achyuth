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

### Setting PATH
Set (overwrite and export) `PATH` variable to `/challenge/more_commands/`, by doing so `/challenge/run` can invoke it with it's bare name (which is just `win`).
```bash
hacker@path~setting-path:~$ export PATH=/challenge/more_commands/
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{Ez76TnxJqFhPGs9YoMDBUZXZTDx.dVzNyUDLxUjN0czW}
hacker@path~setting-path:~$ 
```

### Adding commands
We make the directory `scripts`, make a script there called `win` which reads off `/flag` file and has a sneaky message for cryptonite team, change the permission using `chmod` such that user `hacker` can execute `win`, export the and append the new path to `PATH` variable, then finally execute `/challenge/run` to complete the challenge.
```bash
hacker@path~adding-commands:~$ mkdir scripts
hacker@path~adding-commands:~$ printf "Hello cryptonite people, I got the flag :D\ncat /flag" > scripts/win
hacker@path~adding-commands:~$ chmod u+x scripts/win
hacker@path~adding-commands:~$ export PATH=$PATH:~/scripts/
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
Hello cryptonite people, I got the flag :D
pwn.college{Y7xl-Eg55R7B5snhHbaoRFt0B0L.dZzNyUDLxUjN0czW}
hacker@path~adding-commands:~$ 
```
