# Compute Engine

## Virtualization Fundamentals
-  Process of running multiple operating system on a server simultaneously
-  Hardware - CPU, memory, network card, usb devices, server runs on top of the hardware. Kernel manages hardware distribution and all processes running on the computer.
-  Nested virtualization

## Compute Engine Overview
-  Virtual machine = Instance (IaaS)
-  Multiple instance sizes and types
-  Per second billing
-  Launched in a VPC network
-  Host is available in a Zone
-  Multi-tenant host or Sole-tenant node

## Machine Configuration
1.  Cores(vCPU) and Memory
    1.  Many machine types - General, compute, memory
    2.  Intel or AMD
    3.  vCPU = single hardware hyper-thread on CPU
    4.  Network throughput = 2Gbps per vCPU

2.  Operating System
    1.  Public Image - Linux or Windows
    2.  Custom Image - Private Images (Snapshots/existing disk)
    3.  Marketplace - OS + software

3.  Storage
    1.  Standard - Spinning Hard Drive
    2.  Balanced - Solid State Drive (alternative to SSD)
    3.  SSD - Solid State Drive
    4.  Local SSD - Physically attached (swap disk)

4.  Networking
    1.  Auto, default, custom networks
    2.  Many available regions and zones
    3.  Ingress/egress firewall rules (IP ranges, tags, instances)
    4.  Network load balancing
    5.  Regional/global load balancing


## Compute Engine Machine Types
> Series/generation-type-vCPU
> e2-standard-32

1.  General-purpose
    1.  E2
        1.  e2-micro
        2.  e2-small
        3.  e2-medium
        4.  shared-core
        5.  f1-micro
        6.  g1-small
    2.  N1 (GPU option)
        1.  Standard
        2.  High-memory
        3.  High-CPU
    3.  N2
    4.  N2D
2.  Compute-optimised
    1.  C2 (Standard)
3.  Memory-optimised
    1.  M1
        1.  Mega memory
        2.  Ultra Memory
    2.  M2
        1.  Mega memory
        2.  Ultra Memory

### GPU list
1.  NVIDIA Tesla k80
2.  NVIDIA Tesla P4
3.  NVIDIA Tesla T4
4.  NVIDIA Tesla V100
5.  NVIDIA Tesla P100

## Managing Instances
-  Provisioning State
   -  vCPU + memory 
   -  Root disk and Persistent disk
   -  Additional Disks
   -  No cost
-  Staging
   -  Internal IP
   -  External IP
   -  System Image
   -  Boot
   -  No cost
-  Running
   -  Startup script
   -  SSH | RDP
   -  Modify / Repair
   -  Live Migrate
   -  cost to instance, static IP's, disks

-  Stopping / Suspending
   -  Shutdown script
   -  cost to static IPs, disk


## SSH into linux instance using OS login

```bash
# run in your terminal
gcloud init

# follow the prompt

# run in your terminal, to generate a public and private key pair
ssh-keygen

# enter directory and passphrase

# Go to your instance vm and add custom metadata
key: enable-oslogin
val: TRUE

# in your terminal, login to your instance by running
gcloud compute os-login ssh-keys add --key-file .ssh/id_rsa.pub

# grab your username from the result above, and run
ssh -i .ssh/id_rsa <USERNAME>@<EXTERNAL_IP_ADDRESS>
```


## Query Metadata

```bash
# Query
curl -H "Metadata-Flavor: Google" http://metadata.google.internal/computeMetadata/v1/instance/

curl -H "Metadata-Flavor: Google" http://metadata.google.internal/computeMetadata/v1/project/

# Add custom meta data
gcloud compute instances add-metadata alvin-webserver --metadata env=dev --zone us-east1-b
```

## Compute Engine Billing
-  Each individial vCPU and each GB of memory is billed seperately
-  All VCPUs, GPUs, and each GB of memory are charged by the second with a minimum of 1 minute.
-  Instance uptime - number of seconds between when you start an instanfce and when you stop an instance (terminated)

### Reservations
-  Ensuring resources are available for when you need it
   -  Future increases in demand
   -  Planned or unplanned spikes
   -  Backup and disaster recovery
   -  Buffer

> Include sustanined use and committed use discounts
> Apply only to COmpute Engine, Dataproc and GKE VMs

### Discount types
-  Sustained use discounts
-  Committed use discounts
-  Preemptible VM's

### Sustained use discounts
-  Automatic discounts applied to vCPU, GPU and memory

### Committed use discounts
-  Purchased 1 year or 3 year contracts in return for deeply discounted prices
-  Predictable/steady-state resources
-  57% discount for most resources
-  70% for memory-optimized machine types
-  Apply at the project level, as well as share discounts across multiple projects

### Preemptible VMs
-  80% cheaper, fixed pricing
-  Compute engine stops them within 24 hours.
-  no charge if < 10min

> Cannot live migrate / Auto restart
> Fault-tolerant applications

## Storage Fundamentals
### Block Storage
-  High performance
-  Evenly sized blocks
-  Uniquely identifiable
-  Mountable
-  Bootable
-  Spinning hard drives or Solid State drives

### File Storage
-  Network File System (NFS)
-  Directory tree structure
-  Mountable
-  Not bootable

### Object Storage
-  Unstructured data
-  Data (movies, song, image)
-  Metadata
-  Globally unique identifier
-  Mounted in google cloud storage
-  Not mountable
-  Not bootable
-  Infinitely scalable

### Storage Performance Terms
1.  I/O - measures in 4kb, 256kb, 4mb
2.  I/O - queue depths
3.  IOPS(Input Output operations per second) - I/O operations per second
4.  Throughput - MB/s
5.  Latency - Measurement of delay between the time data is requested when the data starts being returned, measure in milliseconds
6.  Sequential Access - Large single file
7.  Random Access - Loading an application or operating system

## Persistent Disks and Local SSDs
-  Persistent disk can persists after vm instance is terminated
-  Detached and move to another instance.
-  Disk resize feature
-  Encrypted by default (option to use your own custom keys)
-  Up to 64TB in size


> Standard < Balanced < SSD < Local SSD
__*Zonal*__ is Faster but __*Regional*__ is use for more durability eg. backup data