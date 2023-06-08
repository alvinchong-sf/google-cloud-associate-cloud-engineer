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


### Control Plane
   -  API servers, the point of interaction with the cluster (API calls or kubectl)
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
      -  Single replica of the control plane, running in a single zone and has nodes running in multiple zones.
      -  1 control plane that controls nodes in other zone
-  Regional
   -  Multiple replicas of the control plane running in multiple zone.
   -  Each zone has its own control plane and nodes

-  Private Cluster
   -  Connected with VPC peering
   -  Disable to public internet

### Cluster Version
1.  Release Channel (Auto upgrade enabled)
    -  Rapid
       -  Several weeks after upstream open source GA
    -  Regular (Default)
       -  2 to 3 months after releasing in Rapid
    -  Stable
       -  2 to 3 months after releasing in Regular
    -  Speicifc Version
       -  Use a specific supported version of Kubernetes for a given workload.

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

### Kubernetes Objects
-  Represents the state of the cluster
-  Object Spec
   -  Desired state described by you
-  Object Status
   -  Current state described by Kubernetes

### Manifest File
-  apiVersion: Version of the Kubernetes API
-  kind: The kind of object you want to create
-  metadata: Identifies the object(name, UID, namespace)
-  spec: The desired state for this object

### Pod concepts
-  Smallest most basic, deployable object in Kubernetes.
-  Represents single instance of a running process in your cluster
-  Pod contains one or more containers
-  Generally, 1 pod 1 container
-  Remains on the node until:
   -  The pod's process is complete
   -  The pod is deleted
   -  The pod is evicted from the node due to lack of resources
   -  The node fails
```bash
 __________________________
|                          |
|           Node           |
|   ____________________   |
|  |        Pod         |  |
|  |     _________      |  |
|  |    |container|     |  |
|  |     ---------      |  |
|  |  shared storage    |  |
|  |  shared networking |  |
|  |____________________|  |
|                          |
|__________________________|

```

#### Namespaces
-  When creating an object without a namespace, a default namespace is applied
   -  Kube-system
   -  Kube-public
   -  kube-node-lease

#### Pod lifecycle
-  Pod lifecycle are ephemeral
   1.  Pending: Initial pod phase for container(s) to start
   2.  Running: At least one container in the pod is running
   3.  Succeeded/failed: All containers in the pod have terminated successfully or unsuccessfully
-  Unknown: state of the pod could not be obtained.

#### Creating pods
-  The kind of object you want to create
-  Specifies how many instances of a pod will run
-  Specification for a pod

#### Workloads
-  Deployments: runs multiple replicas of your app and automatically replaces any instances that fail or become unresponsive
-  StatefulSets: used for apps that requires persistent storage
-  DaemonSets: Ensures that every node in the cluster runs a copy of a pod
-  Jobs: Used to run a finite task until completion
-  CronJobs: Similar to jobs but runs until completion on a schedule
-  ConfigMaps - Configuration info for any workload to reference


## Kubernetes Services

### Service
-  Persistent single IP
-  Internal and external
-  Load Balancing
-  Scaling

### Service components
-  services.yaml
   -  kind: Service
   -  metadata.name: DNS name of the service
   -  spec.selector.mapp: Forward requests to pods with this label
   -  spec.type: The type of service it is
   -  spec.ports: internal and external ports
-  deployment.yaml


### Service Types
1.  ClusterIP
    1.  creates a stable ip address and port
    2.  Pod must be listening to the same target port from the services
2.  NodePort
    1.  Static port pre-configured range: 30,000 - 32,767
    2.  Node can be accessed by node ip and node port
    3.  An extended version of cluster ip
3.  LoadBalancer
    1.  Exposed as a load balancer
    2.  An extension of the NodePort service type. So it has a cluster ip
4.  Multi-port Services
    1.  Lets you expose more than one port.
5.  ExternalName
    1.  Mapping from an external DNS name to an internal DNS name
6.  Headless
    1.  No load balancing or cluster ip needed
7.  Ingress

#### Ingress for GKE
-  Creates a HTTPS load balancer
-  Creates a stable IP address that you can associate with the domain name
-  Ingress controller, most useful and cost effective. Exposes multiple services under the same Ip address, you only pay 1 load balancer. Use native GCP integration
-  ingress.yaml
   -  backend.serviceName
   -  paths.path
   -  servicePort

> Network Endpoint Group (NEG)

#### Health Checks
-  Default and inferred parameters are used if there are no specified health check parameters
-  Should be explicitly defined by using a Backend Config custom resource definition (CRD)
   -  Anthos Ingress controller
   -  >1 Container
   -  Specific port for LB health check
   -  Backend service's health check
   -  healthCheck parameter of a BackendConfig CRD referenced by service

#### SSL Certificates
-  Google-manged certificates
   -  Completely managed by Google
   -  Do not support wildcard domains
-  Self-managed
   -  Managed and shared with Google Cloud
   -  Provision your own certificates
   -  List the certificate in annotation for use
-  Self-managed as Secrets
   -  Provision your own certificates
   -  Create a secret to hold the certificate
   -  Refer to the secret for use

### GKE Storage Options
1.  Cloud SQL
2.  Cloud Spanner
3.  Datastore
4.  Filestore
5.  Cloud Storage
6.  Persistent Disk


