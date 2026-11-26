# Cabling (all copper straight-through)

| Device A | Port | Device B | Port | Note |
|---|---|---|---|---|
| PCs (5 per VLAN) | Fa0 | ACC switch | Fa0/1-5 | access |
| ACC-F1-ADMIN | Gi0/1 / Gi0/2 | DIST-A / DIST-B | Fa0/3 | trunk 10,191 |
| ACC-F1-HR | Gi0/1 / Gi0/2 | DIST-A / DIST-B | Fa0/4 | trunk 20,191 |
| ACC-F2-IT | Gi0/1 / Gi0/2 | DIST-A / DIST-B | Fa0/5 | trunk 30,192 |
| ACC-F2-SALES | Gi0/1 / Gi0/2 | DIST-A / DIST-B | Fa0/6 | trunk 40,192 |
| ACC-F3-FIN | Gi0/1 / Gi0/2 | DIST-A / DIST-B | Fa0/7 | trunk 50,193 |
| ACC-F3-MKT | Gi0/1 / Gi0/2 | DIST-A / DIST-B | Fa0/8 | trunk 60,193 |
| DIST-A | Fa0/9 | DIST-B | Fa0/9 | trunk interlink |
| DIST-A | Fa0/1 / Fa0/2 | CORE1 / CORE2 | Fa0/1 | routed |
| DIST-B | Fa0/1 / Fa0/2 | CORE1 / CORE2 | Fa0/2 | routed |
| CORE1 | Fa0/3 | CORE2 | Fa0/3 | routed |
| CORE1 | Fa0/4 | EDGE | Gi0/0 | routed |
| CORE2 | Fa0/4 | EDGE | Gi0/1 | routed |
| CORE1 / CORE2 | Fa0/5 | SRV-SW | Gi0/1 / Gi0/2 | VLAN 150 |
| SRV-SW | Fa0/1 / Fa0/2 | SRV-DHCP / SRV-DNS-WEB | Fa0 | VLAN 150 |
| EDGE | Gi0/2 | ISP | Gi0/0 | WAN |
| ISP | Gi0/1 | BRANCH | Gi0/0 | WAN |
| ISP | Gi0/2 | SRV-EXTERNAL | Fa0 | 8.8.8.0/24 |
| BRANCH | Gi0/1 | BRANCH-PC01 | Fa0 | 192.168.50.0/24 |
