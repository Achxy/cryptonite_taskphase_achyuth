# Perceiving Permissions

### Changing file ownership
Use the `chown` command to change the ownership of `/flag` to the hacker user. Once you own the file, you can successfully read it with `cat /flag` to retrieve the flag.
```bash
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{043tpBW10z_wbaiOjtyAjmHWw4y.dFTM2QDLxUjN0czW}
hacker@permissions~changing-file-ownership:~$ 
```
