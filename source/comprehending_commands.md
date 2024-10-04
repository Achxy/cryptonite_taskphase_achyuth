# Comprehending Commands

### Cat
`cat` short for concatenate, is to merge multiple files (or single file) and then to stream it to standard outputs.
```bash
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{MI5072BCTFOq8FwP2sN7msOhUmg.dFzN1QDLxUjN@czW}
hacker@commands~cat-not-the-pet-but-the-command:~$ 
```

### Catting absolute paths
Similar to the previous challenge, this time we'll invoke the `cat` command with `/flag` (which is an absolute path) as it's argument.
```bash
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{YTK1lvgqmEIB8XcUkV1R8T8z73It.d1TM5QDLxUjN@czW}
hacker@commands~catting-absolute-paths:~$
```
  
### More catting practice
Exactly the same as previous challenge, except this time the absolute path is `/usr/share/binfmts/flag`
```bash
hacker@commands~more-catting-practice:~$ cat /usr/share/binfmts/flag
pwn.college{Ie@sZKke4B101B4gU_6RB1j0SjD.dBjM5QDLxUjN@czW}
hacker@commands~more-catting-practice:~$ 
```

### Grepping
Every pwn college flag begins with a `pwn.college{` boiler, we can use it as a base for our search and subsequently provide it as our first argument, the second argument is the absolute path to the file.
```bash
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{EoosSQJLRDsYUrHaecNKxhT--vx.ddTM4QDLxUjN@czW}
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ 
```

### Listing files
First we need to head on over to `/challenge`, which we will do using the `cd` command, then then we'll use `ls` to list all files and folders in the current directory and we'll find the the renamed run file and execute it to get the flag.
```bash
hacker@commands~listing-files:/$ cd challenge
hacker@commands~listing-files:/challenge$ ls -lha

total 20K
drwxr-xr-x 1 root root 4.0K Oct 3 09:42 .
drwxr-xr-x 1 root root 4.0K Oct 3 09:42 ..
-rwsr-xr-x 1 root root 70 May 14 07:38 
-rwsr-xr-x 1 root root 83 May 14 07:38 
-rwsr-xr-x 1 root root 790 May 14 07:38 
hacker@commands~listing-files:/challenge$ ./10184-renamed-run-31609
Yahaha, you found me! Here is your flag:
pwn.college{w13q5HsVzoIDX9cbh1rMkHm3j1D.dhjM4QDLxUjN@czW}
hacker@commands~listing-files:/challenge$ 
```

### Touching files
We are supposed to create two empty files `/tmp/pwn` and `/tmp/college`, so we provide them as arguments to `touch` and then run `/challenge/run` to complete the challenge.
```bash
hacker@commands~touching-files:~$ touch /tmp/pwn
hacker@commands~touching-files:~$ touch /tmp/college
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{0nGpcXEzrlZ3EbaE4hqhvDGpSsH.dBzM4QDLxUjN0czW}
hacker@commands~touching-files:~$ 
```

### Removing files
We provide the `delete_me` argument to `rm` command to remove the file `delete_me`
```bash
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{0RKG4mLY6RK5ng_uwDXq4x2zTS1.dZTOwUDLxUjN0czW}
hacker@commands~removing-files:~$ 
```

### Hidden files
We head on over to the root `/`, and then proceed to list all the files including the "hidden" ones (prepended with `.`). We find the flag file `.flag-18132218732151` as our point of interest and read it.
```bash
hacker@commands~hidden-files:~$ cd /
hacker@commands~hidden-files:/$ ls -a
.   .dockerenv            bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-18132218732151  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:/$ cat .flag-18132218732151 
pwn.college{kObpsNzgeom9FeLoW1FDMAbyJyG.dBTN4QDLxUjN0czW}
hacker@commands~hidden-files:/$ 
```

### An epic filesystem quests

### Making directories
We use `mkdir` to create directories, we use the `-p` flag to create the parent directory if it doesn't exist, then we provide the `/tmp/pwn/college` argument to `touch` command for it to create the empty file `college` essentially completing the challenge.
```bash
hacker@commands~making-directories:~$ mkdir -p /tmp/pwn
hacker@commands~making-directories:~$ touch /tmp/pwn/college
hacker@commands~making-directories:~$ /challenge/run
Success! Here is your flag:
pwn.college{gl1o5JobwjfBOrn26OVNx97n06u.dFzM4QDLxUjN0czW}
hacker@commands~making-directories:~$ 
```

### Finding files
We provide `/` argument to make `find` search the entire filesystem, we use the `name` flag to provide the name `flag`. Since the scope of the challenge is quite rudimentary we we'll use trial and error to find the correct file containing the flag among the positive result.
```bash
hacker@commands~finding-files:~$ find / -name flag
find: ‘/root’: Permission denied
find: ‘/proc/1/task/1/fd’: Permission denied
find: ‘/proc/1/task/1/fdinfo’: Permission denied
find: ‘/proc/1/task/1/ns’: Permission denied
find: ‘/proc/1/fd’: Permission denied
find: ‘/proc/1/map_files’: Permission denied
find: ‘/proc/1/fdinfo’: Permission denied
find: ‘/proc/1/ns’: Permission denied
find: ‘/proc/7/task/7/fd’: Permission denied
find: ‘/proc/7/task/7/fdinfo’: Permission denied
find: ‘/proc/7/task/7/ns’: Permission denied
find: ‘/proc/7/fd’: Permission denied
find: ‘/proc/7/map_files’: Permission denied
find: ‘/proc/7/fdinfo’: Permission denied
find: ‘/proc/7/ns’: Permission denied
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/apache2’: Permission denied
find: ‘/var/log/mysql’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/php/sessions’: Permission denied
find: ‘/var/lib/mysql-files’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/mysql-keyring’: Permission denied
find: ‘/var/lib/mysql’: Permission denied
find: ‘/tmp/tmp.XvrUsDZh8M’: Permission denied
find: ‘/run/mysqld’: Permission denied
find: ‘/run/sudo’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
/usr/local/lib/python3.8/dist-packages/pwnlib/flag
/usr/local/share/radare2/5.9.5/flag
/opt/rappel/.git/objects/4c/flag
/opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
/opt/radare2/libr/flag
/nix/store/pmvk2bk4p550w182rjfm529kfqddnvh3-python3.11-pwntools-4.12.0/lib/python3.11/site-packages/pwnlib/flag
/nix/store/1yagn5s8sf7kcs2hkccgf8d0wxlrv5sz-radare2-5.9.0/share/radare2/5.9.0/flag
hacker@commands~finding-files:~$ cat /usr/local/share/radare2/5.9.5/flag
cat: /usr/local/share/radare2/5.9.5/flag: Is a directory
hacker@commands~finding-files:~$ /opt/radare2/libr/flag
ssh-entrypoint: /opt/radare2/libr/flag: Is a directory
hacker@commands~finding-files:~$ cat /nix/store/1yagn5s8sf7kcs2hkccgf8d0wxlrv5sz-radare2-5.9.0/share/radare2/5.9.0/flag
cat: /nix/store/1yagn5s8sf7kcs2hkccgf8d0wxlrv5sz-radare2-5.9.0/share/radare2/5.9.0/flag: Is a directory
hacker@commands~finding-files:~$ cat /nix/store/pmvk2bk4p550w182rjfm529kfqddnvh3-python3.11-pwntools-4.12.0/lib/python3.11/site-packages/pwnlib/flag
cat: /nix/store/pmvk2bk4p550w182rjfm529kfqddnvh3-python3.11-pwntools-4.12.0/lib/python3.11/site-packages/pwnlib/flag: Is a directory
hacker@commands~finding-files:~$ cat /opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
cat: /opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag: Is a directory
hacker@commands~finding-files:~$ cat /opt/rappel/.git/objects/4c/flag
pwn.college{0E0QmYvCIr7v-zFjim5dY3TnDOG.dJzM4QDLxUjN0czW}
hacker@commands~finding-files:~$ 
```