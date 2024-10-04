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
We find the intended dir using `cd` and then run `/challenge/run` from there.
```bash
hacker@paths~position-thy-self:~$ cd /
hacker@paths~position-thy-self:/$ ls -l
total 80
lrwxrwxrwx    1 root root    7 May 30 02:03 bin -> usr/bin
drwxr-xr-x    1 root root 4096 Apr 15  2020 boot
drwxr-xr-x    1 root root 4096 Oct  4 13:55 challenge
drwxr-xr-x    6 root root  380 Oct  4 13:55 dev
drwxr-xr-x    1 root root 4096 Oct  4 13:55 etc
-r--------    1 root root   58 Oct  4 13:55 flag
drwxr-xr-x    1 root root 4096 Sep 16 07:20 home
lrwxrwxrwx    1 root root    7 May 30 02:03 lib -> usr/lib
lrwxrwxrwx    1 root root    9 May 30 02:03 lib32 -> usr/lib32
lrwxrwxrwx    1 root root    9 May 30 02:03 lib64 -> usr/lib64
lrwxrwxrwx    1 root root   10 May 30 02:03 libx32 -> usr/libx32
drwxr-xr-x    1 root root 4096 May 30 02:03 media
drwxr-xr-x    1 root root 4096 May 30 02:03 mnt
drwxr-xr-x    4 root root 4096 Sep  6 16:54 nix
drwxr-xr-x    1 root root 4096 Sep  6 16:43 opt
dr-xr-xr-x 1884 root root    0 Oct  4 13:55 proc
drwx------    1 root root 4096 Sep  6 16:44 root
drwxr-xr-x    1 root root 4096 Oct  4 13:55 run
lrwxrwxrwx    1 root root    8 May 30 02:03 sbin -> usr/sbin
drwxr-xr-x    1 root root 4096 May 30 02:03 srv
dr-xr-xr-x   13 root root    0 Sep 16 00:15 sys
drwxrwxrwt    1 root root 4096 Oct  4 13:55 tmp
drwxr-xr-x    1 root root 4096 Sep  6 16:19 usr
drwxr-xr-x    1 root root 4096 May 30 02:07 var
hacker@paths~position-thy-self:/$ cd challenge
hacker@paths~position-thy-self:/challenge$ ./run
Incorrect...
You are not currently in the /etc/apt/sources.list.d directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:/challenge$ cd /etc/apt/sources.list.d
hacker@paths~position-thy-self:/etc/apt/sources.list.d$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{ozN9bStIfPxl1n0M4IPSKAH9Yu0.dZDN1QDLxUjN0czW}
hacker@paths~position-thy-self:/etc/apt/sources.list.d$ cd /
```

### Position elsewhere
Exactly the same as the previous challenge.
```bash
hacker@paths~position-elsewhere:~$ cd /
hacker@paths~position-elsewhere:/$ challenge/run
Incorrect...
You are not currently in the /usr/share/doc/fontconfig directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:/$ cd /usr/share/doc/fontconfig
hacker@paths~position-elsewhere:/usr/share/doc/fontconfig$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{U7walSaRDY5a-qleLKJHee4fh36.ddDN1QDLxUjN0czW}
hacker@paths~position-elsewhere:/usr/share/doc/fontconfig$
```

### Position yet elsewhere
Yet again, EXACTLY the same as the previous challenge.
```bash
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /etc/apt/sources.list.d directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /etc/apt/sources.list.d
hacker@paths~position-yet-elsewhere:/etc/apt/sources.list.d$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{gA2BOSg5ICp7PJI-qa-NWYagU79.dhDN1QDLxUjN0czW}
hacker@paths~position-yet-elsewhere:/etc/apt/sources.list.d$ 
```

### Implicit relative paths, from `/`
Since the terminal is positioned `/` we can use the relative path `challenge/run` insted of the absolute path `/challenge/run`
```bash
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{wHY7WRPWu-MRCTCoKGy5hDxgucD.dlDN1QDLxUjN0czW}
hacker@paths~implicit-relative-paths-from-:/$ 
```

### Explicit relative paths, from `/`
We use the period symbol `.` to make the path explicit (`/challenge/run` is implicit while `./challenge/run` is explicit).
```bash
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{I5k3QEGdGX6FsJecDQhwm86XxvC.dBTN1QDLxUjN0czW}
hacker@paths~explicit-relative-paths-from-:/$ 
```

### Implicit relative path
We'll move on over to `challenge`, and use `.` to explicitly mention the `run` file is in the current working directory and execute it.
```bash
hacker@paths~implicit-relative-path:~$ cd /
hacker@paths~implicit-relative-path:/$ cd challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{0tHR_k0nvLWS9VFcK-AcLyHNN7x.dFTN1QDLxUjN0czW}
hacker@paths~implicit-relative-path:/challenge$ 
```