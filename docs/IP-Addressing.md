# IP Addressing, VLAN and DHCP

## VLANs (HSRP virtual gateway = .1, DIST-A = .2, DIST-B = .3)
| VLAN | Name | Access switch | Subnet | HSRP active |
|---|---|---|---|---|
| 10 | Administration | ACC-F1-ADMIN | 10.1.10.0/24 | DIST-A |
| 20 | Human Resources | ACC-F1-HR | 10.1.20.0/24 | DIST-B |
| 30 | IT | ACC-F2-IT | 10.1.30.0/24 | DIST-A |
| 40 | Sales | ACC-F2-SALES | 10.1.40.0/24 | DIST-B |
| 50 | Finance | ACC-F3-FIN | 10.1.50.0/24 | DIST-A |
| 60 | Marketing | ACC-F3-MKT | 10.1.60.0/24 | DIST-B |
| 150 | Servers | SRV-SW | 10.1.150.0/24 (CORE1 .2 / CORE2 .3, VIP .1) | CORE1 |
| 191-193 | MGMT F1-F3 | - | 10.1.191-193.0/24 | DIST-A |

## Transit links
| Link | Subnet | Side A | Side B |
|---|---|---|---|
| CORE1-DIST-A | 10.0.0.0/30 | .1 | .2 |
| CORE2-DIST-A | 10.0.0.4/30 | .5 | .6 |
| CORE1-DIST-B | 10.0.0.8/30 | .9 | .10 |
| CORE2-DIST-B | 10.0.0.12/30 | .13 | .14 |
| CORE1-CORE2 | 10.0.0.16/30 | .17 | .18 |
| CORE1-EDGE | 10.0.0.20/30 | .21 | .22 |
| CORE2-EDGE | 10.0.0.24/30 | .25 | .26 |
| EDGE-ISP | 200.0.0.0/30 | .1 | .2 |
| ISP-BRANCH | 200.0.1.0/30 | .1 | .2 |
| ISP-External | 8.8.8.0/24 | .1 | 8.8.8.8 |
| Branch LAN | 192.168.50.0/24 | .1 | PC .10 |

Router IDs: CORE1 1.1.1.1, CORE2 1.1.1.2, DIST-A 2.2.2.1, DIST-B 2.2.2.2, EDGE 3.3.3.3

## Management IPs
| Device | IP | Gateway |
|---|---|---|
| ACC-F1-ADMIN / HR | 10.1.191.11 / .12 | 10.1.191.1 |
| ACC-F2-IT / SALES | 10.1.192.11 / .12 | 10.1.192.1 |
| ACC-F3-FIN / MKT | 10.1.193.11 / .12 | 10.1.193.1 |
| SRV-SW | 10.1.150.5 | 10.1.150.1 |

## Servers (mask 255.255.255.0, GW 10.1.150.1)
| Server | IP | Services |
|---|---|---|
| SRV-DHCP | 10.1.150.10 | DHCP, DNS = 10.1.150.11 |
| SRV-DNS-WEB | 10.1.150.11 | DNS (`www.company.local`), HTTP, HTTPS |
| SRV-EXTERNAL | 8.8.8.8 (GW 8.8.8.1) | HTTP |

## DHCP pools (on SRV-DHCP; delete default `serverPool`)
| Pool | Gateway | DNS | Start IP | Mask | Max users |
|---|---|---|---|---|---|
| VLAN10_ADMIN | 10.1.10.1 | 10.1.150.11 | 10.1.10.11 | 255.255.255.0 | 200 |
| VLAN20_HR | 10.1.20.1 | 10.1.150.11 | 10.1.20.11 | 255.255.255.0 | 200 |
| VLAN30_IT | 10.1.30.1 | 10.1.150.11 | 10.1.30.11 | 255.255.255.0 | 200 |
| VLAN40_SALES | 10.1.40.1 | 10.1.150.11 | 10.1.40.11 | 255.255.255.0 | 200 |
| VLAN50_FIN | 10.1.50.1 | 10.1.150.11 | 10.1.50.11 | 255.255.255.0 | 200 |
| VLAN60_MKT | 10.1.60.1 | 10.1.150.11 | 10.1.60.11 | 255.255.255.0 | 200 |

Addresses .1-.10 are reserved for network devices.
