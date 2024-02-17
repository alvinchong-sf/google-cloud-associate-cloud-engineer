# Load Balancer
-  Distributes user traffic across multiple instances
-  Single point of entry with multiple backends
-  Fully distributed and software defined
-  Global and Regional
-  Serve content as close as possible to users
-  Autoscaling with health checks

## Load Balancing Types
1.  Global vs Regional
    1.  Global
        1.  External HTTP(s)
        2.  SSL Proxy Load
        3.  TCP Proxy Load

    2.  Regional
        1.  Internal HTTP(s)
        2.  Internal TCP/UDP
        3.  TCP/UDP network

2.  External vs Internal
    1.  External
        1.  External HTTP(S)
        2.  SSL Proxy Load
        3.  TCP Proxy Load
        4.  TCP/UDP Network
    2.  Internal
        1.  Internal HTTP(S)
        2.  Internal TCP/UDP

3.  Traffic Type
    1.  HTTP(S)
    2.  TCP
    3.  UDP

### Load Balancer Types
1.  HTTP(s)
2.  SSL Proxy
3.  TCP Proxy
4.  Network
5.  Internal

### Backend Services
-  Defines how Cloud Load Balancing distributes traffic
-  Health Checks
-  Session Affinity
-  Service Timeout
-  Traffic Distribution
-  Backends

### HTTP(s) traffic management
-  Cross-region load balancing
-  Content-based load balancing
-  Global, proxy-based Layer 7 load balancer behind a single external IP address
-  Google Front Ends (GFE)
-  Global, external, internal
-  HTTPS and SSL for excryption in transit
-  IPv4/IPv6 traffic
-  IPv6 traffic terminates at LV and is served as IPv4 to backend
-  Distribute traffic by location or by content
-  Forwarding rules in place to distribute defined targets to target pools
-  URL maps direct requests based on rules
-  SSL certificates must be used for HTTPS (Google managed or self managed)
-  Ports 
   -  80 (HTTP - Hyper Text Transfer Protocol)
   -  443 (HTTPS - HTTP with TLS(Transport Layer Security) and SSL(Secure Sockets Layer))
   -  22 (SSH - Secure Shell)
   -  25 (SMTP - Simple Mail Transfer Protocol)
   -  21 (FTP - File Transfer Protocol)
   -  8080 (Use for development purposes, popular in Java)

### SSL Proxy
-  Reverse proxy load balancer that distributes SSL traffic coming from the internet to VMs
-  Client SSL sessions terminated at the load balancer
-  Distribute traffic by locaiton only
-  Single Unicast IP address
-  Layer 4 load Balancer
-  Support for TCP with SSL offload
-  IPv4/IPv6 traffic
-  IPv6 traffic termiantes at LV and is served as IPv4 to backend
-  Forwarding rules in place to distribute defined targets to target pools
-  Used for other protocols that use SSL; Websockets and IMAP over SSL

### TCP Proxy
-  Reverse proxy load balancer that distributes TCP traffic coming from the internet to VMs
-  Client TCP sessions terminated at the load balancer
-  Forward traffic as SSL or TCP
-  Intelligent routing: Route to locations that have capacity
-  Single Unicast IP address
-  Layer 4 Load Balancer
-  Global and external
-  Distribute traffic by location only
-  Intended for non HTTP traffic
-  IPv4/IPv6 traffic
-  IPv6 traffic terminates at LBl and is served as IPv4 to backend
-  Supports many well-known TCP ports

### Network Load Balancer
-  Pass-thorugh load balancer that distributes TCP and UDP traffic to VMs
-  Not a proxy
-  Responses from backend go directly to client
-  Regional and external
-  Supports either TCP or UDP; not both
-  Support traffic on ports that are not supported by TCP proxy and SSL proxy
-  SSL decrypted by backends not by load balancer
-  Traffic distributed by protocol, scheme and scope
-  No TLS offloading or proxying
-  Multiple forwarding rules reference one target pool
-  Other protocols use target instances
-  Self managed SSL certificates

### Internal Load Balancer
-  Pass-through load balancer that distributes TCP and UDP traffic to VMs
-  Layer 4 Load Balancer
-  Regional and internal
-  Supports either TCP or UDP; not both
-  Balancers internal traffic between instances
-  Cannot be used to balance internet traffic
-  Traffic sent to backend directly; does not terminate client connections
-  When using forwarding rules
   -  You must specify at least one and up to 5 ports by number
   -  You must specify ALL to forward traffic to all ports


## Instance Groups and Instance Templates
-  A collection of VM instances that you can manage as a single entity
-  Managed Instance Groups
-  Unmanaged Instance Groups

### Managed Instance Groups (MIGs)
-  Stateless serving workloads: website frontend, web servers, web apps
-  Stateless batch: high-performance or high throughput compute workloads
-  Stateful workloads: use stateful managed instance groups

1.  High Availability
    1.  Autohealing
        1.  Keeps VMs in RUNNING state
        2.  Recreate VMs not in RUNNING state
        3.  Application-based autohealing
        4.  Recreate VMs when app is fronzen or has crashed
    2.  Regional (multi-zone)
        1.  Zonal or Regional
        2.  Regional provides higher availability
        3.  Zonal MIGs are in one zone only
        4.  Google recommends regional MIGs
2.  Scalability
    1.  Load Balancing
        1.  Load Balancing can use stnace groups to serve traffic
        2.  Work together to know how much traffic can be handled
        3.  LB health checks do not send traffic to unhealthy instances
    2.  Autoscaling
        1.  Dynamically add or remove instances from the MIG
        2.  Scale up to meet load demands
        3.  Shrink as the load decreases to reduce costs.
3.  Updates
    1.  Auto-updating
        1.  Deploy new versions of software to instances
        2.  Update deployment happens automatically
        3.  Perform rolling updates (rolling lets you restart or update without down time)
        4.  Partial roolouts for canary testing


### UnManaged Instance Groups
-  Does not support Auto-healing, Auto-scaling or Auto-updating.
-  Not highly available or highly scalable

### Instance Templates
-  Resource used to create VM instances and MIGs
-  Mancine type, boot disk image, container image, labels
-  Use to create MIG or VM
-  If you want to create a group of identical instances, you must use an instance template to create a MIG
-  Existing instance template cannot be updated or changed
-  Save the configuration of an existing VM and create a new one `gcloud instance-templates create`
-  To make changes, you can create another one with similar properties using the console
-  Use custom or public images

