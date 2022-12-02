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

Tegin kaks akent, kus ühes käsklus nc -l 3456 (server) teises nc localhost 3456 (klient), iga järgnev text, mis teise aknasse sisestada on kuvatud esimeses aknas
Klient saab ühenduse katkestada cntr+d, (unix end of input)

https://www.ionos.com/digitalguide/server/tools/netcat/ - siin lehel on leitav hea juhend nc kasutamiseks 
Käsklus nc -h avab manuali

NC ja HTTP
https://en.wikipedia.org/wiki/List_of_HTTP_header_fields
Kui saata HTTP request, siis ilmub header pärast käsklust (HEAD; POST; GET; jt). Enamik käsklusi on HEAD käsklused, kus tagastatakse ainult soovitud ressursi päis.
printf "GET / HTTP/1.1\r\nHost: www.example.com\r\n\r\n" | nc www.example.com 80

printf "GET / HTTP/1.1\r\nHost: www.example.com\r\n\r\n" | nc www.example.com 80 > example.txt - see käsklus salvestab vastuse faili, mille nimi on example.txt

Kõrgeim pordi number, mida nc-ga kuulata saab on 65535
Madalaim pordi number, mida nc-ga kuulata saab on 1024
Madalamad on reserveeritud superuseri programmidele. Root või sudo kärklustega, saab ka madalamaid porte kuulata. Kui proovida nc ühenduset prodiga, mis on juba kasutuses annab nc veateate.

lsof käsklus kuulab avatud faile, sh võrguühendusi. 

selle käsklusega: printf 'HTTP/1.1 302 Moved\r\nLocation: https://www.eff.org/' | nc -l 2345 ja minnes browseris vastavale ip- aadressile, suunatakse eff.org veebilehele. Browseri request kuvatakse nc-s

2.Names and Addresses

Host - masin, mis hoiab endas mingeid teenuseid.
Endpoint - kaks masinat suhtlemas üle ühenduse

Ping a hostname
Ping yahoo.com annab vastuste hulgas ka hosti ip aadressi
Ping käsklus jookseb kuni ctrl+c käsuni või tuleb käsklusesse märkida, mitu pingi teha nt - ping -c 4 yahoo.com (4X)
Nt google.com'il ei ole ainult ühte hosti ja seega võib mitme pingimise vastused olla erinevad
Hosti nimi tõlgitakse ip aadressiks läbi DNSi (domain name system)
A-record - kasutatakse, et leida arvuti aadressi, tema nime järgi. Browserid vaatavad need recordid läbi, et leida õige aadress/teenus.
Veebilehe omanikud peavad registreerima oma domeeni mõne teenuse pakkuja juures, et lehe ip aadress oleks registreeritud/leitav läbi DNSi
DNS resolver - client code built into your operating system
HOST käsklus aitab leida üles utilitid läbi DNSi
nt:
![image](https://user-images.githubusercontent.com/115222040/204097599-43b82ae1-1713-4a6b-8353-e67bc5b1a1a5.png)

Host käskluse manuali saab avada käsklusega man host
Host käskluse alternatiiv:
dig
See näitab sama infot (ja natuke metadatat), kuid  loetavam scriptide jaoks ja sarnasem sellele, kuidas seda infot DNSis säilitatakse

DNS kirjeid on mitut tüüpi, näiteks:
AAAA - ipv6aadress
CNAME - canonical name (ametlik nimi), kasutatakse aliase loomiseks
NS - dns nimeserver

![image](https://user-images.githubusercontent.com/115222040/204098467-4fd8a2f8-4029-4c07-94ec-b06c40fb85c1.png)

CACHE - vahemälu/kohalik mälu (koduruuter), mis salvestab teatud ajaks ip aadressi, et klient ei peaks seda uuesti DNSist küsima.
TTL - time to live ehk aeg, kui kauaks info cache'itud on, et juhul, kui ip muutub, siis leitaks leht ikka üles
Headeris on hosti/domeeni nimi, sest neid võib ühel lehel olla mitu või samanimelistel lehtedel olla erinevad.
Kui veebirakendus paigaldab küpsise, siis see on seotud kindla domeeninimega ja järgmise requestiga saadetakse see küpsis tagasi. SSL krüpteering on välja antud kindlale domeenile, sellega takistatakse kolmandatel pooltel privaatset infot lugeda ja kindlustatakse, et klient avab oodatava lehe õigest serverist (mitte mõne pahalase lehe)

![image](https://user-images.githubusercontent.com/115222040/205300123-9637bc63-8852-41c5-97a3-92b7d1b4d29e.png)


Domeeni loomiseks peab seda tegema mõne teenusepakkuja juures (tasuline). Võimalik on osta juba olemasoleva domeeninimi või luua täiesti uus Seal resitreerid oma ipv aadressi A recorordisse, ehk suunad domeeni nime oma ipv4 aadressile.

IPv4 vs IPv6?
IPv4 on vanem.
IPv4 koosneb neljast punktidega eraldatud 1-bytisest (8biti) numbrist:







Loeng 20.10

ip aadressid
ssh võtmed ja nende kasutamine
webhosting 
github

##Avalik/salajane võti
- autentimine

- autoriseerimine

- krüpteerimine

Githubis, saab seda kasutada settingutes -> SSH
Git CMD
