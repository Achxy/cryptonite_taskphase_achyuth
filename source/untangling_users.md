# Untangling Users

### Becoming root with su
Execute the `su` command and enter the root password `hack-the-planet` when prompted to switch to the root user. Once I have root privileges, run `cat /flag` to display the flag (which was restricted without elevated privileges).
```bash
hacker@users~becoming-root-with-su:~$ su
Password: 
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{MTftU5d7jDaQM13Hlgp9VxmHdtZ.dVTN0UDLxUjN0czW}
root@users~becoming-root-with-su:/home/hacker# 
```

### Other users with su
Use the `su zardus` command and enter the password `dont-hack-me` when prompted to switch to the zardus user, then execute `/challenge/run` as `zardus` to get the flag.
```bash
hacker@users~other-users-with-su:~$ su zardus
Password: 
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{AD_GZf5FHLdXHr4hESIOAm2lICa.dZTN0UDLxUjN0czW}
zardus@users~other-users-with-su:/home/hacker$ 
```
