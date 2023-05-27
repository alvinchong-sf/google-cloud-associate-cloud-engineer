# Kubernetes

## Containers
-  consistent
-  efficient
-  standardized

## Virtual Machines vs Containers

#### Virtual Machine
-  VM has seperate OS per VM
-  Large overhead in CPU, memory and disk

```bash
    VM              VM           VM
----------     -----------   -----------
|   App   |    |   App   |   |   App   |
| Runtime |    | Runtime |   | Runtime |
| GuestOS |    | GuestOS |   | GuestOS |
----------     -----------   ----------- 
 _______________________________________
|                                       |
|               Hypervisor              |
|______________________________________ |

 _______________________________________
|                                       |
|            Infrastructure             |
|______________________________________ |

```

#### Containers
-  Abstracted OS
-  Lightweight, Portable, Efficient

```bash
----------     -----------   -----------
|   App   |    |   App   |   |   App   |
| Runtime |    | Runtime |   | Runtime |
----------     -----------   ----------- 
 _______________________________________
|                                       |
|           Container Engine            |
|______________________________________ |

 _______________________________________
|                                       |
|         Host Operating System         |
|______________________________________ |

 _______________________________________
|                                       |
|            Infrastructure             |
|______________________________________ |

```

> Dockerfile --> Container Image --> Container Registry --> Docker Hosts

## GKE and Kubernetes Concepts

#### Kubernetes
-  Orchestration platform for containers
-  Automate, schedule and run containers on clusters of physical or virtual machines

#### GKE
-  GKE environment consists of compute engine instances grouped together to form a cluster
-  Cloud Load Balancing
-  Node Pools
-  Automatic scaling
-  Automatic upgrades
-  Node auto repair
-  Logging and Monitoring

#### Cluster Architecture
-  One or more Control Planes
-  One or more Nodes
-  Control Plane responsible for schedling and management
-  Nodes run containerized apps
-  Nodes responsible for Docker runtime
-  Control Plane
   -  API serverthe point of interaction with the cluster (API calls or kubectl)
   -  Kube Scheduler: Discovers and assigns newly created pods
   -  Kube controller manager: Runs all controller processes
   -  Cloud controller manager: Runs controller specific to the cloud provider
   -  etcd: Key-value store that stores the state of the cluster
-  Node
   -  Kubelet: Agent for communication with Control Plane
   -  Kube-proxy: Network connectivity
   -  runtime: Runs container like Docker


`gcloud container clusters get-credentials`

## GKE Cluster and Node Management

### Node Pools
-  __*Group*__ of nodes within a cluster with the __*same configuration*__
-  One or multiple nodes
-  Custom node pools - Useful for pods that require more resources
-  Manually or automatically upgraded

### Cluster Types
-  Zonal Clusters
   -  Single-zone
      -  1 control plane
   -  Multi-Zonal
      -  1 control plane that controls nodes in other zone
-  Regional
   -  Each zone has its own control plane and nodes

-  Private Cluster
   -  Connected with VPC peering
   -  Disable to public internet

### Cluster Version
1.  Release Channel
    -  Rapid
    -  Regular
    -  Stable

### Cluster upgrades
-  Control plane and nodes do not always run the same version at all times
-  A control plane is always upgraded before its nodes
   -  Zonal: Cannot launch or edit workloads during upgrade
   -  Regional: Each control plane is upgraded one by one
-  Auto-upgrade enabled by default - best practice
-  Manual upgrade: cannot upgrade control plane more than one minor version at a time
   -  Maintenance window and exclusions available


### Node and Node pool upgrades
-  Auto-upgrade enabled by default - best practice
-  Manual upgrade available
   -  Maintenance window and exlusions available
-  Pods scheduled to run on another node during upgrade
-  Upgrade is complete only when
   -  All nodes have been recreated
   -  Cluster is in the desired state

### Surge Upgrades
-  Control the number of nodes GKE can upgrade at a time
-  Use surge upgrade parameters
   -  max-surge-upgrade
      -  Num of additional nodes added to the node pool during an upgrade
      -  Higher number = More parallel upgrades $$
   -  max-unavailable-upgrade
      -  Num of nodes that can be simultaneously unavailable during an upgrade
      -  Higher number = More disruptive

## Pods and Object Management

