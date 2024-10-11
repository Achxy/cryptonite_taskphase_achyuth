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
