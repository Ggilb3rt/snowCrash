# Solve Level00

- Find users list with ```cat /etc/passwd```
  - Notice flag00 is present
- Find all files that belongs to flag00 with ```(find / -user flag00 2>/dev/null) | grep -v proc```
- ```cat /usr/sbin/john  # cdiiddwpgswtgt ```

- Maybe it is encoded, we can use tool like [www.dcode.fr] to help us
Test with cesar decode

## Solution
flag00 = nottoohardhere
level01 = x24ti5gi3x0ol2eh4esiuxias

## Resolve problem
Don't put your passoword in a file with readable access

Nice :-)