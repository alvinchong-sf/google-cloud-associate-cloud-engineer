# Cloud VPN
-  Connects your peer network to your VPC network through an IPsec VPN connection
-  IPsec tunnel over the public internet
-  Encrypted by one VPN gateway, and then decrypted by the other VPN gateway
-  Regional Service
-  Site to site VPN only (no site to client)
-  Allows Private Google Access for on-premises hosts
-  Supports up to 3Gbps per tunnel
-  Dynamic and static routing
-  Supports IKEv1 and IKEv2 using Shared Secret

## Types of Cloud VPN
| Classic VPN                                  | HA VPN                                           |
| -------------------------------------------- | ------------------------------------------------ |
| 99.9% SLA                                    | 99.99% SLA                                       |
| Static and dynamic routing                   | Dynamic routing only                             |
| 1 external IP address for a single interface | 2 external Ips to be configured for 2 interfaces |
| Deprecating functionality in 2021            | New default VPN                                  |


### When to use Cloud VPN
-  Public internet access is needed
-  Peering location is not available
-  Budget constraints
-  High speeds/low latency not needed
-  Outgoing traffic (egress) from GCP