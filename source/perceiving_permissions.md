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
