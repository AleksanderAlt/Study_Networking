# Study_Networking

## Vajalik tarkvara

To run a Linux virtual machine (VM) on top of the regular operating system I installed:
- VirtualBox: is open-source software for virtualizing the x86 computing architecture. It created a VM to run another OS.
- Vagrant: is a tool for building and managing VM environments in a single workflow.

If you log out of the Linux instance or close the terminal, the next time you want to use it you need to run:
- cd networking
- vagrant ssh

## Mõisted

- Ethernet - a system for connecting a number of computer systems to form a local area network, with protocols to control the passing of information and to avoid simultaneous transmission by two or more systems
- Host - a machine on the internet that might host services
- Endpoints - two machines or programs communicating over the connection
- DNS (Domain Name System) - the Internet's system for converting alphabetic names into numeric IP addresses
- Resolver - the DNS client code built into your OS

## Käsud

- ping -c 3 host_name - sends a signal to host and recieves it (-c 3 means that 3 pings will be sent)
- printf - prints a request (for input using |)
- netcat - (nc) is a computer networking utility for reading from and writing to network connections
- nc -l port_nr - nc listens to port referred to
- nc localhost port_nr - receives the port referred to
- ^D - nc disconnects from port
- ^C - stops the request
- '> example.txt - saves the results to the file example.txt
- host host_name - gets hosts alias and IP-adresses
- dig host_name - gets hosts alias, CNAME, IP-adresses, which server and when answered and more

## Pordid

The port range that a normal (non-root) user can listen on is 1024 through 65535
But using root access (including sudo) then you can listen on ports 1023 down to 1
Can't listen to the same port, which is already in use

## DNS

[DNS record types](https://en.wikipedia.org/wiki/List_of_DNS_record_types)
