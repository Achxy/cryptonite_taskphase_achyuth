# Pondering Paths

### The Root
There's a program called `pwn` being contained at root (`/`), we need to invoke it in order to complete the challenge. The path in this case is absolute instead of relative because terminal is positoned at root.
```bash
hacker@paths~the-root:~$ /pwn
BOOM!!!

Here is your flag:
pwn.college{UDvq9_COrj8SOleEXa-TaidrQfS.dhzN5QDLxUjN@czW}
hacker@paths~the-root:~$ 
```

### Program and Absolute Path
Similar to the previous challenge, we'll invoke the `run` that is being nested inside `challenge`.
```bash
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{4rICRRg_zExY6_7eD6jL9fjzOl1I.dVDN1QDLxUjN@czW}
```

### Position thy self
---