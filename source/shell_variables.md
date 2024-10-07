# Shell variables

### Printing variables
There's a variable named `FLAG`, we'll prepend it with `$` forming `$FLAG` and pass it to `echo` to have it displayed.
```bash
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{Yz881o8y6bSKn6_k9BCiqeMG404.ddTN1QDLxUjN0czW}
hacker@variables~printing-variables:~$ 
```

### Setting variables
We set the value of `PWN` to `COLLEGE` using `=`, spaces must not be used, and `$` is for variable expansion but we
don't need that in this context.
```bash
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{IHaWy-lTCGQTPko73DnzUaHRaF5.dlTN1QDLxUjN0czW}
hacker@variables~setting-variables:~$ 
```

### Multi-word variables
We use quotes `"` here because `COLLEGE YEAH` contains a space and we don't want the shell to terminate the variable
assignment context.
```bash
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{IbwxAXGIPWKuHRrYD02Lizt0as6.dBjN1QDLxUjN0czW}
hacker@variables~multi-word-variables:~$ 
```

### Exporting variables
We set `COLLEGE=PWN` without using `export`. However, we do use `export` for `PWN`, which is assigned the value `COLLEGE`.
This makes `PWN` accessible to child processes, unlike `COLLEGE`.
```bash
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great 
job! Here is your flag:
pwn.college{stTFyph2SpHCXSjfsVPWR_2RPfp.dJjN1QDLxUjN0czW}
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ 
```

### Printing Exported Variables
We use `env` to get all the environment variables and pipe it to `grep` to search for the `pwn.college` pattern.
```bash
hacker@variables~printing-exported-variables:~$ env | grep pwn.college
FLAG=pwn.college{4GQ44ufapoF6FZn3ntb_jFL9KkA.dhTN1QDLxUjN0czW}
hacker@variables~printing-exported-variables:~$
```
