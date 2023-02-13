# Solve Level01
pass : x24ti5gi3x0ol2eh4esiuxias

- Try to find infos in /etc/passwd
    - find a password set clear for flag01 : 42hDRfypTqqnw ==> failure
    - password probably hash, need to find the algo of hash
    - man 5 passwd then man 3 crypt
    - no vulnerability found for crypt(), it's a one way encryption
    - john the ripper can help

- Put /etc/passwd of flag01 to file
```bash
    grep flag01 /etc/passwd > cryptPass
    #flag01:42hDRfypTqqnw:3001:3001::/home/flag/flag01:/bin/bash
```
- Put it to my local machine with scp
- Use [John the ripper][df2] (can by combine with wordlist /usr/share/wordlist) [source][df3]
```bash
    john cryptPass
    #Using default input encoding: UTF-8
    #Loaded 1 password hash (descrypt, traditional crypt(3) [DES 128/128 AVX])
    #No password hashes left to crack (see FAQ)
    john --show
    #flag01:abcdefg:3001:3001::/home/flag/flag01:/bin/bash
```

## Solution
flag01 : abcdefg
level02 : f2av5il02puano7naaf6adaaf

## Resolve problem
- don't put any password on /etc/passwd file, let the system put it to /etc/shadow
- use harder pass

[df3]: https://www.cyberciti.biz/faq/unix-linux-password-cracking-john-the-ripper/