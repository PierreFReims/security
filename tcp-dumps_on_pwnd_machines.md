# TCP-Dumps on pwnd machines

If you are on a network with other machines that you still haven't owned, it might be useful to take a tcp-dump from the machine you have owned. So that you can inspect the traffic between that machine and the other machines on the network. This might be helpful when attacking the other machines.

So after we have exploited a machine we want to use that machine to learn as much about the network as possbible. To be able to map the entire network. We want to know about switches, firewalls, routers, other computers, server, etc. We want to know what ports are open, their operating systems.

1. First we need to figure out what interfaces the machine is using.
- Ifconfig. Then we can just start tapping in on that and start to record it.

### Commands and flags
Let's start with the basics.
tcpdump - this command will output all network traffic straight to the terminal. Might be hard to understand if there is a lot of traffic.

**-A** - stands for Ascii, and output it in ascii.
**-w file.pcap ** - the w-flag will save the output into the filename of your choice. The traffic is stored in pcap-format, which is the standard packet-analysis-format. 
**-i any ** - will record traffic for all interfaces.
**-D** - show list of all interfaces
**-q** - be less verbose. Be more **quiet**
**-s** - The default size that tcpdump captures is only 96 bytes. If you want it to capture more you have to define it yourself `-s0` gives you the whole packet.
**-c** - count. Set how many packets you want to intercept. And then stop.
**port 22** - only see traffic on a specific port.
**-vvv** - Verbose. Depending on how verbose you want the output. 

### Useful commands


`tcpdump -i wlan0 -vvv -A | grep "GET"`- This will grep all GET from the wlan0 interface.
This will not get any SSL-encrypted traffic.

sudo tcpdump -i wlan0 src port 80 or dst port 80 -w port-80-recording.pcap
sudo tcpdump -i eth0 src port 80 or dst port 80 -w port-80-recording.pcap


## References


http://www.thegeekstuff.com/2010/08/tcpdump-command-examples/
https://danielmiessler.com/study/tcpdump/
https://www.sans.org/reading-room/whitepapers/testing/post-exploitation-metasploit-pivot-port-33909

http://jvns.ca/blog/2016/03/16/tcpdump-is-amazing/