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

### Cracking passwords
Run `john /challenge/shadow-leak` to crack the password hash and retrieve Zardus's password. Once the password is obtained, execute `su zardus` and enter the cracked password to switch to the zardus user then execute `/challenge/run` to get the flag.
```bash
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Created directory: /home/hacker/.john
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04821g/s 280.7p/s 280.7c/s 280.7C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ su zardus
Password: 
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{IQHGSeYgXlVrLTDL12GlPojiZWa.ddTN0UDLxUjN0czW}
zardus@users~cracking-passwords:/home/hacker$ 
```
