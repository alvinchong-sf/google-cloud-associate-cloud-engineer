## OSI(Open Systems Interconnection) Model
Communications between a computing system

7.  Application (HTTP/HTTPS - DHCP - DNS - SSH - Telnet)
6.  Presentation
5.  Session
4.  Transport (TCP - UDP)
3.  Network (IPv4 - IPv6)
2.  Data Link
1.  Physical

### Network
#### IPv4
Dotted decimal
192.168.255.255
ranging from 0 - 255

```bash
classful addressing

Single Class A
10.0.0.0 - 10.255.255.255
16,777,216 addresses

16 Class B
172.16.0.0 - 172.31.255.255
1,048,576 addresses

256 Class C
192.168.0.0 - 192.168.255.255
65,536 addresses
```
```bash
Classless Inter-Domain Routing(CIDR)

Network Address/Prefix
Prefix -> Size of the network (The bigger prefix is smaller network, the smaller prefix is bigger network)
Subnet breaks down 1st and 2nd octet in ip addresses

192.168.0.0/16
192.168.0.0 - 192.168.255.255
65,536 addresses
```

```bash
Helpful Reference
192.168.0.0/8 # 16+ million IP addresses
192.168.0.0/16 # 65,536 IP addresses
192.168.0.0/24 # 256 IP addresses

192.168.1.2/32 # 1 IP addresses
0.0.0.0/0 # All IP addresses
```

#### IPv6

```bash
Hexadecimal notation
1452:0db8:0000:0000:0000:fe02:0042:8452
each one is called an Hextet

2001:de3::/64 # Network address/prefix and 128 bits long

1452:0db8:0:0:0:fe02:0042:8452 # shortened version

2001:de3:0000:0000:0000:0000:0000:0000 # Start Address

2001:de3:0000:0000:ffff:ffff:ffff:ffff # End Address

::/0 # All Addresses
```

### Transport
TCP - Transmission Control Protocol
UDP - User Datagram Protocol

IP Packet contains:
1.  Source IP Address
2.  Destination
3.  Protocol/Port Number
4.  Data

### Application
1.  HTTP(S)
2.  UDP - Port 53
3.  Port 22