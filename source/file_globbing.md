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

### Matching with ?
We use `/?ha??enge` to match the directory `/challenge` as the `?` matches any single character, and then run the `run` executable.
```bash
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ ./run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{08xArZ215whR4fC1uPdLo2iYYok.dJjM4QDLxUjN0czW}
hacker@globbing~matching-with-:/challenge$ 
```

### Matching with []
We use `/challenge/files/file_[absh]` to match the files `file_a`, `file_b`, `file_s`, and `file_h`.
```bash
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[absh]
You got it! Here is your flag!
pwn.college{U4SSbBMcKZx_ucQ8T-3sdVzaVui.dNjM4QDLxUjN0czW}
hacker@globbing~matching-with-:/challenge/files$
```

### Matching paths with []
We use `/challenge/files/file_[absh]` to get the absolute path of the files `file_a`, `file_b`, `file_s`, and `file_h` like `/challenge/files/file_a`, `/challenge/files/file_b`, `/challenge/files/file_s`, and `/challenge/files/file_h`.
```bash
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[absh]
You got it! Here is your flag!
pwn.college{06uro4ewkH6aLnp8HHaPhOhZaM2.dRjM4QDLxUjN0czW}
hacker@globbing~matching-paths-with-:~$ 
```

### Mixing globs
We use `/challenge/files/[cep]*` to match the files `challenging`, `educational`, and `pwning` because no other files in the `files` directory starts with the letter `c`, `e`, or `p`.
```bash
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ ls
amazing    challenging  educational  great  incredible  kind      magical  optimistic  queenly  splendid   uplifting   wonderful  youthful
beautiful  delightful   fantastic    happy  jovial      laughing  nice     pwning      radiant  thrilling  victorious  xenial     zesty
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{gGMXJazVmJSnpzrPGpyirF3l6J0.dVjM4QDLxUjN0czW}
hacker@globbing~mixing-globs:/challenge/files$
```
