# Solve Level03
pass : kooda2puivaav1idi4f57q8iq

- basics rigth on file : read, write and execute. But there is more : special right SUID, (set user id) and SGID (set group id), file can be executed without sudo...
```bash
    man chmod
    chmod u+s file
    chmod g+s file
```

- we have a binary file with SUID sets, printing 'Exploit me'
    - find an article about privilege escalation with SUID binary [here][df1]
    - try to decompile and understand the binary file (install hex editor on vscode)
        - ```strings level03``` gives us all strings with more than 5 ascii char
        - use radare2[df2]/ghidra to decompile the program
            - find functions setgid, getgid, setuid, getuid ==> can be exploited with special rights
            - system() can execute bash cmd
            - echo is use
- change PATH to make him execute something else[df3]

## Solution
- cf script.sh
- flag empty because we execute getflag as flag03
level04 : qi0maab88jeaj46qoumi7maus

## Resolve problem
- never trust users, always sanitize your data
- don't give special right to files using system functions
- use write or printf to write on stdout

[df1]: https://www.hackingarticles.in/linux-privilege-escalation-using-suid-binaries/
[df2]: https://www.youtube.com/watch?v=vXWHmucgZW0
[df3]: https://www.hackingarticles.in/linux-privilege-escalation-using-path-variable/