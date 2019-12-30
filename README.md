# Studymap for Networking

## Vajalik tarkvara

To run a Linux virtual machine (VM) on top of the regular operating system I installed:
- VirtualBox: is open-source software for virtualizing the x86 computing architecture. It created a VM to run another OS.
- Vagrant: is a tool for building and managing VM environments in a single workflow.

If you log out of the Linux instance or close the terminal, the next time you want to use it you need to run:
- cd networking
- vagrant up
- vagrant ssh

## Mõisted

- Ethernet - a system for connecting a number of computer systems to form a local area network, with protocols to control the passing of information and to avoid simultaneous transmission by two or more systems
- ISP - Internet Service Provider
- Host - a machine on the internet that might host services
- Endpoints - two machines or programs communicating over the connection
- DNS (Domain Name System) - the Internet's system for converting alphabetic names into numeric IP addresses
- Resolver - the DNS client code built into your OS
- ttl - time to live in cache server
- C-NAME - used to specify that a domain name is an alias for another domain
- Search Domain - a setting in the resolver configuration that makes the resolver look up names inside a domain
- IP Network Block (IP range) - continuous segment of Internet Protocol addresses assigned to an organization or country
- Router - a networking device that forwards data packets between computer networks and perform the traffic directing functions on the Internet
- Network address translation (NAT) - is a method of remapping one IP address space into another by modifying network address information in the IP header of packets while they are in transit across a traffic routing device
- Default gateway - the node in a computer network using the internet protocol suite that serves as the forwarding host (router) to other networks when no other route specification matches the destination IP address of a packet
Tcpdump - packet analyzer that allows the user to display TCP/IP and other packets being transmitted or received over a network to which the computer is attached

## Käsud Linuxis

- `ping -c 3 host_name` - sends a signal to host and recieves it (-c 3 means that 3 pings will be sent)
- `printf` - prints a request (for input using |)
- `netcat` - (nc) is a computer networking utility for reading from and writing to network connections
- `nc -l port_nr` - nc listens to port referred to
- `nc localhost port_nr` - receives the port referred to
- `^D` - nc disconnects from port
- `^C` - stops the request
- `> example.txt` - saves the results to the file example.txt
- `host host_name` - gets hosts alias and IP-adresses
- `dig host_name` - gets hosts alias, CNAME, IP-adresses, which server and when answered and more
- `ip addr show` - shows what interfaces (ethernet: eth0, wifi: wlan0, loopback: lo) your machine has
- `ip route show default` - finds default gateway
- `sudo tcpdump -n host host_name` - allows the user to catch the traffic (coming from, going to, length) between a network to which the computer is attached, to exit ctr+C

## Pordid

The port range that a normal (non-root) user can listen on is 1024 through 65535 (16 bits)
But using root access (including sudo) then you can listen on ports 1023 down to 1
Can't listen to the same port, which is already in use

## DNS

[DNS record types](https://en.wikipedia.org/wiki/List_of_DNS_record_types)
To register a new domain in the DNS with [Google](domains.google.com)

www.delfi.ee.
From right to left:
- . - referres to root nameserver
ee. - asks from one root nameserver: tell me .ee domain nameservers: `nslookup -q=ns .ee IP_adress`

## IP aadressid

IP adress types:
- IPv4: 
    - separated by dots .
    - written in decimal
    - 32-bits, network part (ex 22-bit for 1021 hosts or 24-bit for 253 hosts) and host part (10 or 8-bit)
    - 4 octets
    - used with NAT
- IPv6:
    - separated by colon :
    - written in hex
    - 128-bits, doesn't need separated network part and host part, because size is enough to get private address
    - 16 octets

## Protocol stack

1. HTTP (HyperText Transfer Protocol) - underlying protocol used by the World Wide Web which defines how messages are formatted and transmitted, and what actions Web servers and browsers should take in response to various commands
    - web applications send requests about resources and get responses
2. TCP session - lets two programs send streams of bites back and forward over the network
3. IP (Internet Protocol) - method or protocol by which data is sent from one computer to another on the Internet. Each computer (known as a host) on the Internet has at least one IP address that uniquely identifies it from all other computers on the Internet
4. Hardware

| Protocol | Concepts | Where the code is | Failures |
| --- | ---| --- | --- |
| HTTP | resources, URLs, verbs, cookies | Flask, Apache, browsers | error codes, slow responses |
| TCP | ports, sessions, stream sockets | OS kernel, system libraries | broken connections, timeouts |
| IP | IP addresses, packets | OS kernel, routers | various |
| Wifi | access points, WPA passwords | device drivers | network unavailable |

### TCP

| What TCP Does | How TCP Does It |
| --- | --- |
| communicate between two hosts | IP Layer (addresses + routing) |
| multiple applications per host | port numbers |
| in-order delivery | sequence numbers |
| lossless delivery | acknowledgment + retransmission |
| keeping connections distinct | random initial sequence numbers |

- TCP flag - is a Boolean value (true or false) that is stored in memory as a single bit. If a flag bit is 1, we say the flag is set. If the flag bit is 0, the flag is cleared (or unset). Usually, flags come in groups, each of which can be set or cleared.
The original TCP packet format has six flags. Two more optional flags have since been standardized, but they are much less important to the basic functioning of TCP. For each packet, `tcpdump` will show you which flags are set on that packet.
    - SYN (synchronize) [S] — This packet is opening a new TCP session and contains a new initial sequence number.
    - FIN (finish) [F] — This packet is used to close a TCP session normally. The sender is saying that they are finished sending, but they can still receive data from the other endpoint.
    - PSH (push) [P] — This packet is the end of a chunk of application data, such as an HTTP request.
    - RST (reset) [R] — This packet is a TCP error message; the sender has a problem and wants to reset (abandon) the session.
    - ACK (acknowledge) [.] — This packet acknowledges that its sender has received data from the other endpoint. Almost every packet except the first SYN will have the ACK flag set.
    - URG (urgent) [U] — This packet contains data that needs to be delivered to the application out-of-order. Not used in HTTP or most other current applications.

