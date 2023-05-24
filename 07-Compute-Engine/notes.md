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