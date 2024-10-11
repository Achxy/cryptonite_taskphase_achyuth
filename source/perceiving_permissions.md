# Perceiving Permissions

### Changing file ownership
Use the `chown` command to change the ownership of `/flag` to the hacker user. Once you own the file, you can successfully read it with `cat /flag` to retrieve the flag.
```bash
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{043tpBW10z_wbaiOjtyAjmHWw4y.dFTM2QDLxUjN0czW}
hacker@permissions~changing-file-ownership:~$ 
```

### Groups and files
Use the `chgrp hacker /flag` command to change the group ownership of the `/flag` file to the hacker group. This grants the hacker user the necessary group permissions to read the file. Then, execute `cat /flag` to display the flag.
```bash
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{0cw8vOx10Ja9rh0blqOoB_S5PTO.dFzNyUDLxUjN0czW}
hacker@permissions~groups-and-files:~$ 
```

### Fun with group names
Run the `id` command to determine your current group name. Use `chgrp [your_group] /flag` (in this case `grp16875`) to change the group ownership of the `/flag` file to your group. This modification grants your user the permissions needed to access the file. Finally, execute `cat /flag` to read and obtain the flag.
```bash
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp16875) groups=1000(grp16875)
hacker@permissions~fun-with-groups-names:~$ chgrp grp16875 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{Q5mO0Vn2jY6BoYR2Kk77TxmQONo.dJzNyUDLxUjN0czW}
hacker@permissions~fun-with-groups-names:~$ 
```

### Changing permissions
Use `chmod a+r /flag` to add read permissions for all users on the `/flag` file. This allows the `hacker` user to access and read the file despite not owning it or being part of the owning group. Then, execute `cat /flag` to display the flag.
```bash
hacker@permissions~changing-permissions:~$ chmod a+r /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{kzQDu1XTQcAngBwupUGbR99czWC.dNzNyUDLxUjN0czW}
hacker@permissions~changing-permissions:~$ 
```

### Executable files
Add execute permissions for the user by running `chmod u+x /challenge/run`. This grants the `hacker` user the ability to execute the `/challenge/run` program. After modifying the permissions, execute the program with `/challenge/run` to receive the flag.
```bash
hacker@permissions~executable-files:~$ chmod u+x /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{Qxk2Qv4ZFSatihegc_xfIoNhAI0.dJTM2QDLxUjN0czW}
hacker@permissions~executable-files:~$ 
```
