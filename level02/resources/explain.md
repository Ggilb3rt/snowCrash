# Solve Level02
pass : f2av5il02puano7naaf6adaaf

- We got a file .pcap on our home, it's a packet capture file use to get the netwoks logs  [source][df1]. From a first look the file seems to be corrupted, maybe just need to find the good program.
- Check TCP protocol describtion on RFC-793
- [tcpdump and libpcap][df2] look good to help, ```man tcpdump``` cf section 'TCP Packets' line 695
    - usefull option (?) :
        - use -r with file.pcap
        - use -n don't convert addresses to names
- Use wireshark would be maby easyer
    - following packets I find : 'ft_wandr   NDRel L0L' ==> seems to easy, doesn't works
    - right click on first packet -> Follow -> TCP stream can help. Show data has Hex dump
    - some char space have 00 (\0) as Hex, others have 7f (DEL) or 0d (\r), let's go ```man ascii```
        - ft_wandr then 3 DEL
        - ft_waNDRel then 1 DEL
        - ft_waNDReL0L

## Solution
- flag02 : ft_waNDReL0L
- level03 : kooda2puivaav1idi4f57q8iq

## Resolve problem
- use encryption on network

[df1]: https://fr.wikipedia.org/wiki/Pcap
[df2]: https://www.tcpdump.org/index.html#documentation