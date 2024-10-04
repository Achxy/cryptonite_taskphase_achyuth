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