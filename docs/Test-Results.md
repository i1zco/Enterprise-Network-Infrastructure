# Test Results

Fill in the result column and add screenshots to `../screenshots/`.

| # | Test | Command / Method | Expected | Result | Screenshot |
|---|---|---|---|---|---|
| 1 | DHCP on all 30 PCs | Desktop > IP Configuration > DHCP | Address 10.1.V.11+ | [ ] | |
| 2 | Ping gateway | ping 10.1.V.1 | Success | [ ] | |
| 3 | Reach servers | ping 10.1.150.11 | Success from all VLANs | [ ] | |
| 4 | Allowed paths | ADMIN<->SALES, SALES<->MKT, IT->all | Success | [ ] | |
| 5 | Blocked paths | ADMIN->HR, SALES->FIN, MKT->HR | Destination unreachable | [ ] | |
| 6 | DNS | Browser: http://www.company.local | Page opens | [ ] | |
| 7 | HTTP/HTTPS | http:// and https:// to 10.1.150.11 | Opens | [ ] | |
| 8 | OSPF neighbors | show ip ospf neighbor (CORE1) | 4 neighbors FULL | [ ] | |
| 9 | Routes | show ip route ospf (CORE, DIST-A) | All networks, 2 paths on DIST, O*E2 default | [ ] | |
| 10 | NAT | ping 8.8.8.8, then show ip nat translations (EDGE) | Success + entries | [ ] | |
| 11 | VPN | ping 192.168.50.10; show crypto isakmp sa / ipsec sa | QM_IDLE, encaps increasing | [ ] | |
| 12 | Port security | show port-security interface fa0/1 | Enabled + sticky MAC | [ ] | |
| 13 | ACL | show access-lists (DIST) | Match counters increase | [ ] | |
| 14 | Traceroute | tracert 8.8.8.8 | PC > DIST > CORE > EDGE > ISP > SRV | [ ] | |
| 15 | HSRP | show standby brief (both DIST) | One Active, one Standby per VLAN | [ ] | |
| 16 | STP | show spanning-tree (access) | One uplink forwarding, one blocking | [ ] | |
| 17 | Failover DIST | ping -t 10.1.150.11, shut DIST-A | Brief loss, recovers via DIST-B | [ ] | |
| 18 | Failover CORE | ping 8.8.8.8, shut CORE1 | Recovers via CORE2 | [ ] | |
| 19 | Failover access | shut ACC Gi0/1 | Recovers via Gi0/2 | [ ] | |
| 20 | Restore | no shutdown | Preempt returns roles | [ ] | |
