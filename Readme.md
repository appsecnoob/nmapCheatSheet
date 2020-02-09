Welcome to the nmapCheatSheet wiki!

NMap

nmap -sP 10.0.0.0/24 ping scan (CIDR notation will scan all hosts in last 8 bits i.e 256 hosts  /0 will scan the whole internet and /32 will scan only the host 				mentioned, /16 will scan last 16 bits ie 256*256 hosts)
nmap -sP 10.0.0.1, 10.0.0.2

nmap - sP 10.0.0.1-100

Nmap -sS -A 10.0.0.105 syn stealth scan , OS fingerprinting


nmap [Scan Types(s)] [options] {Target specification}

Target Specification ( can pass hostnames, Ip Addresses, Networks etc.)

-iL <input filename>: input from a list of hosts/networks

-iR <num hosts>: choose random targets
	
--exclude <hosts1, host2

Host Discovery
-sL : List Scan - simply lists targets to scan without any info about how many of them are up

-sP : ping sweep  (to find online alive hosts) it is replaced by -sn

-sn : disable port scan or no port scan also callled ping scan, This is by default one step more intrusive than the list scan. it gives info about how many hosts are up.

-Pn : no ping (if no results in ping sweep try this one) treat all hosts as online - skip host discovery

-SP : TCP SYN ping

-SA : TCP ACK Ping

-SU : UDP ping

Scan Techniques
-sS TCP SYN (stealth scan)  syn/ack -open , reset - close, no response - filter

-sT TCP Connect Scan

-sU udp scan

-sX X-Mas Scan  (psh, urg, fin flags)- more stealthier then syn scan can passthrough stateful and packet firewall         
		no response - open/filtered(if ICMP unreachable error type 0,1, 2, 3), reset - close 
		
-sN null scan

-sF Fin Scan

-b FTP bounce (used to probe systems behind firewall)

-sA TCP ACK scan( list out filered or unfiltered ports never returns an open port, in this scan only ack bit is set,  it uses RST packet to determine that the port is unfiltered, else filtered when it recives ICMP error msgs (type 3, code 0,1,2,3,9,10,13) 

-sW windows scan - same as -sA except that it sometimes find out open or close ports based on the window size of RST packet for positive window size it gives port as open and for 0 window size of RST packet it gives the port to be closed.


port specification

-p1-65535

--exclude-ports 

--top-ports

-r 

Service version detection
-sV

OS detection
-O

OS and Version detection
-A

verbose 
-v
Extra Information
-VV

default scripts
-SC

grep-able output
-oG 

output all formats
-oA
 
Timing and Performance

-T<0-5> : higher is faster
