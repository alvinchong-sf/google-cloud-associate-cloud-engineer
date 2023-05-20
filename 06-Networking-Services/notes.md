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


## VPC (Must know for exam)
-  Virtual Private Cloud(VPC)
-  VPC is a Global resource
-  Encapsulated within a Project
-  VPC's do not have any IP address ranges associated with them
-  Firewall rules control traffic flowing in and out of the VPC
-  Resources within a VPC can communicate with one another by using internal(private) IPv4 addersses
-  Support only for IPv4 addresses
-  Each VPC contains a default network with default subnet
-  2 Network types: Auto Mode or Custom Mode


## Subnets
-  A subnetwork of a VPC
-  Each VPC network consists of one or more subnets and each subnet is associated with a region
-  The name or region of a subnet cannot be changed after you have created it.
-  Primary and secondary ranges for subnets cannot overlap with any allocated range.

### Increasing subnet IP space
-  Must not overlap with other subnets in the same VPC network
-  Inside the RFC 1918 address-space
-  Network range must be larger than the original
-  Once subnet has been expanded you cannot undo it
-  /20 -> /16 (One way direction)

### Reserved IP Addresses
Network - First address
Default Gateway - Second address
Second-to-last address - Google Cloud future use
Broadcast - Last address

## Routing and Private Google Access
-  Routes define the network traffic path from one destination to the other
-  In a VPC routes consists of a single destination (CIDR) and a single next hop
-  All routes are stored in the routing table for the VPC of an applicable route based on a routing order

### Routing Types
1.  System-generated
    1.  Default Route
        1.  Path to the internet
        2.  Path for Private Google Access
        3.  Can be deleted only by replacing with custom route
        4.  Lowest priority
    2.  Subnet Route
        1.  Routes that define paths to each subnet in the VPC.
        2.  Each subnet has aat least one subnet route whose destination matches the primary IP range of the subnet
        3.  When a subnet is created, a corresponding subnet route is created for both primary and secondary IP range
        4.  Cannot delete a subnet route unless you modify or delete the subnet
2.  Custom Routes
    1.  Static Route
        1.  Can use next hop feature
        2.  Can be created manually
        3.  Static routes for the remote traffic selectors are created automatically when creating Cloud VPN tunnels
    2.  Dynamic Route
        1.  Managed by one or more Cloud Routers
        2.  Dynamically exchange routes between a VPC and on-premises networks
        3.  Destination IP ranges outside the VPC network
        4.  Used with dynamically routed VPNs and Interconnect

3.  Routing order
4.  Special return paths

## IP Addressing
```bash
                    IP Address
                    /            \
     Internal(Private)            External(Public)
     /               \                     /           \
     Auto           Custom              Ephemeral     Static
    /    \          /     \             
Ephemeral Static  Ephemeral Static
  v         ^      v         ^
  v --------^      v --------^
        Promote to Static

```

### Internal IP address reservation
1.  Reserve a specific address and then associate it with a speicifc resource
2.  Specify an ephemeral internal IP address for a resource and then promote the address

### External IP address reservation
1.  Reserve a new static external IP address and then assign it to a resource
2.  Specify an ephemeral external IP address for a resource and then promote the address

Regional IP address
Global IP address


## VPC Firewall rules
-  protocol
-  ports
-  sources
-  destinations
-  target

## Implied and pre-populated rules
-  TCP: PORT 25 (not allowed)
-  TCP, UDP, ICMP, GRE (block)
-  Metadata Server: 169.254.169.254
    -  DHCP
    -  DNS
    -  Instance Metadata
    -  NTP

### Implied Rules
-  allow egress
-  deny ingress

### Firewall rule characteristics
-  incoming or outgoing but not both
-  IPv4
-  Allow or Deny but not both
-  Must select VPC network
-  Stateful (Return traffic matching this connection is allowed)
-  Connection tracking table