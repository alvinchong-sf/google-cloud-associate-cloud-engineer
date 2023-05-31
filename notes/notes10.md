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

## Cloud Interconnect
-  Low Latency, highly available connection between your on-premises and Google Cloud VPC networks
-  Directly accessible internal IP addresses - Private Google Access
-  __*Does not traverse*__ the public internet
-  Dedicated connection
-  __*Not encrypted*__
-  Expensive

### Dedicated Interconnect
-  8 x 10 Gbps connections (80 Gbps total)
-  2 x 100 Gbps connections (200 Gbps total)

### Partner Interconnect
-  50 Mbps to 50 Gbps VLAN attachments (50Gpbs total)

### Direct Peering
-  Direct peering connection between your on-premises network and Google's edge network
-  100 locations in 33 countries
-  Direct egress pricing available
-  Direct Peering connection with Google is FREE

### CDN Internconnect
-  Enables select third-party CDN providers to establish direct peering links with Google's edge network
-  Direct traffic from VPC network to the provider's network
-  Reduced pricing on egress costs

### When to use Cloud Interconnect
-  Prevent traffic from traversing the public internet
-  Dedicated physical conneciton
-  Extension of your VPC network
-  High speed/low latency is needed - 200Gbps
-  Heavy outgoing traffic (egress) from GCP
-  Private Google Access