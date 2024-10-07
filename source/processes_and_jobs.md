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