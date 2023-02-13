# Solve Level09
pass : 25749xKZ8L7DkSCwJkT9dyv6f

## Description
- home
    - -rwsr-sr-x 1 flag09  level09 7640 Mar  5  2016 level09*
    - ----r--r-- 1 flag09  level09   26 Mar  5  2016 token

### level09
The binary must take one arg.
- ```r2 level09``` ==> many content with many jumps, maybe obfuscation, find a string "You should not reverse this"
- Try some random arg
    - abc ==> ace
    - abcdef ==> acegik
    - try a prediction : ba\`_^]\\[ZYX should print bbbbbbbbbb ==> works
- Easy pattern to see ==> c[i] = c[i] + i
    - the binary can decode the content of token

### token
- ```cat token``` return some unprintable char

## Solution
```bash
cd /tmp
vi pouet.c #copy paste the content of ./reverser.c
gcc pouet.c -o pouet
cd 
/tmp/pouet `cat token`
```

- flag09 : f3iji1ju5yuevaus41q1afiuq
- level10 : s5cAJpM8ev6XHw998pRWG728z


## Resolve problem
- please don't do that
