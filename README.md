# Enterprise Campus Network — Redundant Three-Floor Design

## Overview
Full design and configuration of a redundant enterprise campus network simulating a three-floor office environment. Built entirely in Cisco Packet Tracer.

The topology covers 6 departments across 3 floors, with complete Layer 2 and Layer 3 redundancy at every level.

## Technologies Implemented
- **VLANs + VTP** — 7 VLANs (6 departments + management), propagated via VTP
- **Inter-VLAN routing** — Layer 3 switching via SVIs on dual multilayer switches
- **HSRP** — First-hop redundancy, gateway failover transparent to hosts
- **Rapid PVST+** — Loop prevention with split root bridge per VLAN plane
- **LACP EtherChannel** — 3-link Port-Channel between core switches
- **DHCP relay** — Centralized DHCP server in VLAN 60 serving all floors
- **Static routing** — Dual edge routers with floating backup routes to ISP

## Network Summary
| Layer | Devices | Role |
|---|---|---|
| Access | SW2 – SW7 | One switch per department, dual-homed |
| Core | MLS-1, MLS-2 | Inter-VLAN routing, HSRP, EtherChannel |
| Edge | R-1, R-2 | Dual uplinks to simulated ISP |
| ISP | ISP-R | Simulated external reachability |

## IP Addressing
| VLAN | Name | Subnet | HSRP Gateway |
|---|---|---|---|
| 10 | Sales | 172.16.10.0/25 | 172.16.10.3 |
| 20 | HR | 172.16.20.0/25 | 172.16.20.3 |
| 30 | Finance | 172.16.30.0/25 | 172.16.30.3 |
| 40 | Admins | 172.16.40.0/25 | 172.16.40.3 |
| 50 | ICT | 172.16.50.0/25 | 172.16.50.3 |
| 60 | Servers | 172.16.60.0/28 | 172.16.60.3 |
| 100 | Management | 172.16.99.0/26 | 172.16.99.3 |

## Documentation
Full technical documentation (PDF) is available in this repository.
It includes topology diagram, IP addressing plan, all verification outputs,
and end-to-end DHCP proof.

## Status
Fully configured and verified. Next phase: firewall policies (pfSense + FortiGate),
IDS deployment (Snort), and site-to-site VPN.

## Author
BINGhost007 a.k.a D.Yahya
