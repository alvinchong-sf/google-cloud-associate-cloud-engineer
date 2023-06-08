# Georgraphy and Regions

### Zone
A zone is a __*deployment area*__ for Google Cloud resources __*within a region*__. The smallest entity of Google's global infrastructure.

### Region
Regions are independent geographic areas that are __*sub-divided into zones.*__

### Multi-Region
Multi-Regions are large geographic areas, that contains __*two-or more regions.*__


# Compute Service Options
1.  IaaS - Compute Engine (Virtual Machines)
2.  CaaS - Google Kubernetes Engine (GKE)
    1.  Cluster is a group of nodes or Compute Engine instances.
3.  PaaS - App Engine -  
    1.  Can be deployed using Standard of Flexible environment of your choice of language eg. (Go, Java, .NET, NodeJs, PHP, Python or Ruby)
4.  FaaS - Cloud Functions - 
    1.  Serverless execution environment for building and connecting cloud services.
    2.  Simple, single-purpose functions that are attached to events.
    3.  Triggered when an event being watched is fired.
    4.  Your code executes in a fully managed environment
    5.  No need to provision any infrastructure.
    6.  Cloud Functions can be written using Javascript, Python3, Go, or Java
    7.  ETL operations, webhooks to HTTP triggers
5.  FaaS - Cloud Run
    1.  Fully managed compute platform for deploying and scaling containerized applications quickly and securely.
    2.  Can be written in any language.


# Storage & Databases
## Storage
1.  Cloud Storage
    1.  Consistent, scalable, large-capacity, highly durable object storage(documents or pictures, videos). Not to be confused with blob storage.
    2.  11 9's Durability (99.999999999%)
    3.  Unlimited Storage with no minimum object size
    4.  Cloud Storage for content delivery, data lakes
    5.  Storage Classes
        1.  Standard - Maximum availability no limitation
        2.  Nearline - Low-cost archival storage, Accessed < 1/month
        3.  Coldline - Even lower-cost achrival storage, Accessed < 1/quarter>
        4.  Archive - Lowest-cost archival storage, Accessed < 1/year

2.  Filestore
    1.  Fully managed NFS file server
    2.  NFSv3 compilant
    3.  Store data from running applications

3.  Persistent Disks (blob storage)
    1.  Durable block storage for instances
    2.  Standard (HDD) or Solid State (SSD)(lower latency)

## Databases
### SQL
1.  Cloud SQL (PostgreSQL, MySQL, SQL Server)
2.  Cloud Spanner
    1.  Scalable relational database service
    2.  Support transactions, strong consistency and synchornous replication
    3.  High availability across regions and globally

### No-Sql
1.  Bigtable
2.  Datastore
3.  Firestore
    1.  Realtime database
4.  Memorystore
    1. Memory service for redis

# Networking Services
## Virtual Private Cloud(VPC)
1.  Virtualized network within Google Cloud
2.  Core networking service
3.  Global resource
4.  Each VPC contains default network
5.  Networks cannot be shared between networks.

## Firewall Rules
1.  Govern traffic coming into stances on a network.
2.  Default network has a default set of firewall rules.
3.  Custome rules can be created.

## Routes
1.  Advanced networking functions for your instances.
2.  Specifies how packets leaving an instance should be directed.

## Load Balancing
1.  HTTP(s) Load Balancing
    1.  Distribute traffic across regions to ensure that requests are routed to the closest region or in the event of a failure or over-capacity, to a healthy isntance in the next closest region.
    2.  Distribute traffic based on content type.

2.  Network Load Balancing - Distribute traffic among server instance in the same region based on incoming IP protocol data, such as address, port and protocol.

## Google Cloud DNS
1.  Publish and maintain DNS records by using the same infrastructure that Google uses.
2.  Work with managed zones and DNS records through the CLI, API or SDK.

## Advanced Connectivity
1.  Cloud VPN
    1.  Connect your on-premise network to your VPC through IPsec connection
2.  Direct Interconnect
3.  Direct Peering
4.  Carrier Peering
