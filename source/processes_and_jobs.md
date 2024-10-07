# Processes and Jobs

### Lising processes
We run `ps` command with flags `e` for "every" and `f` for "full format", and we find a process named `/challenge/27389-run-7215` 
whose execution yields our flag.
```bash
hacker@processes~listing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 14:49 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 14:49 ?        00:00:00 /run/dojo/bin/sleep 6h
root          68       1  0 14:49 ?        00:00:00 /challenge/27389-run-7215
root          72      68  0 14:49 ?        00:00:00 sleep 6h
hacker        73       0  0 14:49 pts/1    00:00:00 /run/dojo/bin/ssh-entrypoint
hacker        79       0  0 14:49 pts/0    00:00:00 /run/dojo/bin/ssh-entrypoint
hacker       107       0  0 14:49 pts/2    00:00:00 /run/dojo/bin/ssh-entrypoint
hacker       126     107  0 14:50 pts/2    00:00:00 ps -ef
hacker@processes~listing-processes:~$ /challenge/27389-run-7215
Yahaha, you found me! Here is your flag:
pwn.college{0WI4dfksOHHIlTFPx8cweNHfvSm.dhzM4QDLxUjN0czW}
Now I will sleep for a while (so that you could find me with 'ps').
```

### Killing processes
We find every process with `ps -ef`, pipe it to `grep`, find the pattern `dont_run`, get `PID` of `/challenge/dont_run` and `kill` it.
```bash
hacker@processes~killing-processes:~$ ps -ef | grep dont_run
hacker        73      71  0 14:57 ?        00:00:00 /challenge/dont_run
hacker       127      75  0 15:00 pts/2    00:00:00 grep --color=auto dont_run
hacker@processes~killing-processes:~$ kill 73
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{0_Va5UVLgjkG0OyJT0mf-xKHI7k.dJDN4QDLxUjN0czW}
hacker@processes~killing-processes:~$ 
```

# Interrupting processes
We give `^C` (`Control` + `C`) control code to the process to interrupt it.
```bash
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember, 
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{kMn_2xVj6bKPdosT-88pjacl-EU.dNDN4QDLxUjN0czW}
hacker@processes~interrupting-processes:~$ 
```