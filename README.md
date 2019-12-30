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
