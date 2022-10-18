# av-alused

#link
https://github.com/Tallinna-Polutehnikum/KTA-22E-networks/blob/main/README.md

https://www.markdownguide.org/basic-syntax

Networking for web developers

From Ping to HTTP

Kasutan testkeskkonda https://cloud.google.com/shell

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
