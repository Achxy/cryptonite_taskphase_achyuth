# File Globbing

### Matching with *
We use `/ch*` to match the directory `/challenge` and then run the `run` executable.
```bash
achu@air cryptonite_taskphase_achyuth % ssh -i ~/key hacker@dojo.pwn.college 
Connected!                                                                        
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ ./run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{EY84JwYQQkAHQ4aWWUdvw2DfaUT.dFjM4QDLxUjN0czW}
hacker@globbing~matching-with-:/challenge$ 
```