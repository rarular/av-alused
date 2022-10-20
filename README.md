# av-alused

#link
https://github.com/Tallinna-Polutehnikum/KTA-22E-networks/blob/main/README.md

https://www.markdownguide.org/basic-syntax

Networking for web developers

From Ping to HTTP

Kasutan testkeskkonda https://cloud.google.com/shell

SSH - Secure Shell Protocol (SSH). a cryptographic network protocol for operating network services securely over an unsecured network. Its most notable applications are remote login and command-line execution
HTTP - Hypertext Transfer Protocol. Application layer protocol fot transmitting hypermedia documents (HTML)


Käsud:

sudo apt-get update - bring up to date

sudo apt-get install netcat-openbsd tcpdump traceroute mtr - network utility programs

Katsetamiseks:

ip addr show eth0
ip route show
ping -c3 8.8.8.8
host -t mx udacity.com
printf 'HEAD / HTTP/1.1\r\nHost: www.udacity.com\r\n\r\n' | nc www.udacity.com 80

ping -c3 8.8.8.8 - testing wether your computer can send and receive network traffic without that address; 8.8.8.8 is the address of a google service, -c3 means to send 3 test messages 

Ping vs HTTP

ping suhtleb op.süsteemiga (no server) HTTP kasutab suhtelmiseks veebiserverit
Ping - echo request

HTTP

printf 'HEAD / HTTP/1.1\r\nHost: en.wikipedia.org\r\n\r\n' | nc en.wikipedia.org 80

printf - command for printing formatted string
nc - net cat - manually talking to internet services
pipe | võtab ühe programi outputi ja edastab teisele programmile inputina

![image](https://user-images.githubusercontent.com/115222040/196377775-c02dfc2a-bb49-4733-98d7-ae22e8e48858.png)

printf 'HEAD / HTTP/1.1\r\nHost: wwww.google.com\r\n\r\n' | nc www.google.com 80 - server gws

![image](https://user-images.githubusercontent.com/115222040/196381013-a582295f-0393-4183-9df6-b050923816c4.png)
![image](https://user-images.githubusercontent.com/115222040/196381512-565640e5-2e60-4ddf-89b4-133bb5731f50.png)

TCP - Transmission Control Protocol. a set of rules that governs the delivery of data over the Internet or other network that uses the Internet Protocol, and sets up a connection between the sending and receiving computers. TCP provides reliable, ordered, and error-checked delivery of a stream of octets (bytes) between applications running on hosts communicating via an IP network
UDP- User Datagram Protocol. Transport Layer protocol. UDP is a part of the Internet Protocol suite, referred to as UDP/IP suite. Unlike TCP, it is an unreliable and connectionless protocol. So, there is no need to establish a connection prior to data transfer. 


man nc -BSD General Command Manual

"Client/server"

How would you get nc to listen on port 3456?

Mul puudub manualis klient/server osa



