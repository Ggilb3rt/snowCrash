# Solve Level08
pass : fiumuikeil55xe9cu4dood66h

## Description
- home
    - -rwsr-s---+ 1 flag08  level08 8617 Mar  5  2016 level08*
    - -rw-------  1 flag08  flag08    26 Mar  5  2016 token

### level08
The binary take a file as arg and print 1024 first char. If the file name contain 'token' return an error.
- if no arg ==> "./level08 [file to read]"
- if the file path has "token" ==> "You may not access '(xxx/)token'" (find strstr() with decompiler)
  - we can create an alias of the file with a different name, ```man ln``` ==> works
- if other name ==> print 1024 first bytes
- if no perm ==> error 'Unable to open %s'

## Solution
```bash
ln -s ./token /tmp/pouet
./level08 /tmp/pouet
#quif5eloekouj29ke0vouxean ==> be carefull it's the pass of flag08 not level09
```
flag08 : quif5eloekouj29ke0vouxean
level09 : 25749xKZ8L7DkSCwJkT9dyv6f

## Resolve problem
- do not validate the authenticity of a file with its name


