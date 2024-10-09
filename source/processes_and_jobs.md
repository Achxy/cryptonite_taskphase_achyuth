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

### Suspending Processes
We send `^Z` code to an existing instance of `run`, then run a new instance of it to get the flag.
```bash
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          99      82  0 15:09 pts/1    00:00:00 bash /challenge/run
root         101      99  0 15:09 pts/1    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can 
background me with Ctrl-Z or, if you're not ready to do that for whatever 
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          99      82  0 15:09 pts/1    00:00:00 bash /challenge/run
root         106      82  0 15:09 pts/1    00:00:00 bash /challenge/run
root         108     106  0 15:09 pts/1    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{0x0lguIPcEdD3aVRnClrdy9WwfE.dVDN4QDLxUjN0czW}
hacker@processes~suspending-processes:~$ 
```

### Resuming processes
We run `run`, suspend it with `^Z`, then run use `fg` command to resume it and brings it forth to the foreground of the terminal.
```bash
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with 
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{U5J1wBLbV1UTEMKRKbSwqIMwL1K.dZDN4QDLxUjN0czW}
Don't forget to press Enter to quit me!

Goodbye!
hacker@processes~resuming-processes:~$ 
```

### Backgrounding processes
Suspend the first process using `^Z` and then resume it in the background with the `bg` command. This allows you to launch a second instance in the same terminal, ensuring another copy is running and not suspended to obtain the flag.
```bash
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          82 S+   bash /challenge/run
root          84 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the 
background, and then launch a new version of me! You can background me with 
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to 
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out.
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          82 S    bash /challenge/run
root          92 S    sleep 6h
root          93 S+   bash /challenge/run
root          95 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{cyqnd5jqG3gDXUoVeqgiCSMoH-k.ddDN4QDLxUjN0czW}
hacker@processes~backgrounding-processes:~$ 
```

### Foregrounding Processes
Suspend the running process with `^Z`, then move it to the background using the `bg` command. Next, bring the backgrounded process back to the foreground with `fg` without suspending it again.
```bash
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the 
background, and *then* foreground it without re-suspending it! You can 
background me with Ctrl-Z (and resume me in the background with 'bg') or, if 
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out. After that, resume me into the foreground with 'fg'; 
I'll wait.
hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{4GARBCxRslMc1117tcHN-81vXQ1.dhDN4QDLxUjN0czW}
hacker@processes~foregrounding-processes:~$ 
```

### Starting background processes
Launch the `/challenge/run` command with an `&` to start it directly in the background. This ensures the process runs actively without being suspended, allowing the terminal to remain available for other commands.
```bash
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 99


Yay, you started me in the background! Because of that, this text will probably 
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{oM5MUUcqrQT6jb9JEqsPVlN1O3d.dlDN4QDLxUjN0czW}
hacker@processes~starting-backgrounded-processes:~$

[1]+  Done                    /challenge/run
hacker@processes~starting-backgrounded-processes:~$ 
```
