# Digesting Documentation

### Learning from the documentation
We execute `/challenge/challenge` with the flag `--giveflag`
```bash
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{gP1tYh6Kp_cEtgGpoVqe0t8NF24.dRjM5QDLxUjN0czW}
hacker@man~learning-from-documentation:~$ 
```

### Learning complex usage
Same as the previous challenge.
If they say it's not the flag, then it's definitely the flag :^)
```bash
hacker@man~learning-complex-usage:~$ ls
Desktop  college  not-the-flag  x
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile not-the-flag
Correct argument! Here is the not-the-flag file:
pwn.college{cw6okzp3rE70Xq8mXv-FGz-_YLu.dVjM5QDLxUjN0czW}
hacker@man~learning-complex-usage:~$ 
```

### Reading manuals
We get the manual of `challenge` using `man challenge` which clearly mentions `--wymzbt NUM` -> `print the flag if NUM is 852`
```bash
hacker@man~reading-manuals:~$ man challenge

CHALLENGE(1)                                                        Challenge Commands                                                        CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --wymzbt NUM
              print the flag if NUM is 852

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)

pwn.college                                                              May 2024                                                             CHALLENGE(1)
hacker@man~reading-manuals:~$ /challenge/challenge --wymzbt 852
Correct usage! Your flag: pwn.college{wKDF85ym2JFAzMDbODtpWY0j68-.dRTM4QDLxUjN0czW}
```

### Searching manuals
We use `/` to search in the man pages, and `n` & `N` to traverse over the positive matches.
```bash
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ /challenge/challenge --nuybjx
Initializing...
Correct usage! Your flag: pwn.college{AART6m7FIdjRWwMTIPRhdn2HQm_.dVTM4QDLxUjN0czW}
hacker@man~searching-manuals:~$ 
```