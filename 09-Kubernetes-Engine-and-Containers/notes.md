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
-  Abstract the infrastructure
-  

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