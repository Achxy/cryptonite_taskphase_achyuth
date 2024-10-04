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

### Searching for manuals
We can provide `-k` flag followed by the argument `flag` to search for the man pages, we find `cueityvivd`, read it's man page which informs us of it's usage and we proceed with `/challenge/challenge --cueity 407` which gets us the flag.
```bash
hacker@man~searching-for-manuals:~$ man -k flag
cueityvivd (1)       - print the flag!
dpkg-buildflags (1)  - returns build flags to use during package build
Dpkg::BuildFlags (3perl) - query build flags
fegetexceptflag (3)  - floating-point rounding and exception handling
fesetexceptflag (3)  - floating-point rounding and exception handling
i386 (8)             - change reported architecture in new program environment and/or set personality flags
ioctl_iflags (2)     - ioctl() operations for inode flags
linux32 (1)          - change reported architecture in new program environment and/or set personality flags
linux64 (1)          - change reported architecture in new program environment and/or set personality flags
pcap-config (1)      - write libpcap compiler and linker flags to standard output
security_compute_av_flags (3) - query the SELinux policy database in the kernel
security_compute_av_flags_raw (3) - query the SELinux policy database in the kernel
set_matchpathcon_flags (3) - set flags controlling the operation of matchpathcon or matchpathcon_index and configure the behaviour of validity checking and...
set_matchpathcon_invalidcon (3) - set flags controlling the operation of matchpathcon or matchpathcon_index and configure the behaviour of validity checkin...
set_matchpathcon_printf (3) - set flags controlling the operation of matchpathcon or matchpathcon_index and configure the behaviour of validity checking an...
setarch (1)          - change reported architecture in new program environment and/or set personality flags
setarch (8)          - change reported architecture in new program environment and/or set personality flags
x86_64 (8)           - change reported architecture in new program environment and/or set personality flags
hacker@man~searching-for-manuals:~$ man cueityvivd

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

       --cueity NUM
              print the flag if NUM is 407

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)

pwn.college                                                              May 2024                                                             CHALLENGE(1)
hacker@man~searching-for-manuals:~$ /challenge/challenge --cueity 407
Correct usage! Your flag: pwn.college{4cDuX0-eVB_Z7PMXHityvi0v3GS.dZTM4QDLxUjN0czW}
hacker@man~searching-for-manuals:~$ 
```

### Helpful programs
We get the help text of `/challenge/challenge` with `--help` flag, we use `-p` to get the secret value and enter it as an argument to `-g` to get the flag.
```bash
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 73
hacker@man~helpful-programs:~$ /challenge/challenge -g 73
Correct usage! Your flag: pwn.college{Ux0PF73wHxqhBQM4UOXDm3TQZgh.ddjM4QDLxUjN0czW}
hacker@man~helpful-programs:~$ 
```