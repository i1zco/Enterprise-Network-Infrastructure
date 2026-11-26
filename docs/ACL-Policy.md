# ACL Policy

One extended ACL per department, `ACL_VLAN<id>_IN`, applied **inbound on the VLAN SVI of both DIST-A and DIST-B**. ACLs are stateless, so return traffic must be permitted in the peer's ACL too.

## Rule order (same in every ACL)
1. Permit DHCP (`udp bootpc -> bootps`)
2. Permit ping to own gateway
3. Permit DNS (udp 53) to 10.1.150.11
4. Permit HTTP/HTTPS (tcp 80/443) to 10.1.150.11
5. Permit ICMP to the server network 10.1.150.0/24
6. Permit approved peer departments
7. Deny all other internal networks (`10.0.0.0/8`)
8. Permit everything else (Internet and VPN)

## Approved peers
| ACL | Allowed peers | Purpose |
|---|---|---|
| ACL_VLAN10_IN | IT, Sales | Admin talks to IT and Sales |
| ACL_VLAN20_IN | IT | HR isolated except IT support |
| ACL_VLAN30_IN | Admin, HR, Sales, Finance, Marketing, MGMT-F1/F2/F3 | IT reaches everything |
| ACL_VLAN40_IN | Admin, IT, Marketing | Sales |
| ACL_VLAN50_IN | IT | Finance isolated except IT support |
| ACL_VLAN60_IN | IT, Sales | Marketing |

Complete rules: `configs/DIST-A.txt`, `configs/DIST-B.txt`.
