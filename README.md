# Enterprise Networking Labs

Hands-on networking projects focused on CCNA and CCNP Enterprise concepts, routing and switching, network security, automation, and troubleshooting.

## About This Project

This repository documents my practical learning journey in enterprise networking using Cisco Packet Tracer and other networking tools. Each lab includes network topology, IP addressing, device configurations, verification commands, and troubleshooting notes.

## Lab Roadmap & Progress

| Lab | Project | Status |
|---|---|---|
| 01 | [OSPF Routing Across Multiple Routers](labs/01-ospf-routing/) | ✅ Completed & Tested |
| 02 | Network Security: VLANs, ACLs & Port Security | 🟡 In Progress |
| 03 | Enterprise Network Design from Scratch | ⬜ Planned |
| 04 | Network Outage Troubleshooting | ⬜ Planned |
| 05 | VLANs and Trunking | ⬜ Planned |
| 06 | Inter-VLAN Routing | ⬜ Planned |
| 07 | DHCP and NAT/PAT | ⬜ Planned |
| 08 | STP and EtherChannel | ⬜ Planned |
| 09 | Pv4 Subnetting Lab | ⬜ Planned |

## Mini Project

| Lab | Project | Status |
|---|---|---|
| 01 | IP Address Management Plan | ✅ Completed & Tested |
| 02 | Network Troubleshooting Casebook | ⬜ Planned |

## Completed Labs

### Lab 01 — OSPF Routing Across Three Routers

**Status:** Completed and tested in Cisco Packet Tracer

Built a three-router network using Cisco 2911 routers, Cisco 2960 switches, and three PCs.

**Key implementations:**
- Configured IPv4 addressing on router interfaces.
- Established OSPFv2 neighbor adjacencies in Area 0.
- Advertised LAN and transit networks using OSPF.
- Verified dynamically learned routes.
- Configured PC addressing and default gateways.
- Tested connectivity between different LANs.

**Technologies:** Cisco IOS CLI, OSPFv2, IPv4, Cisco Packet Tracer.

[View Lab 01 documentation and configurations](labs/01-ospf-routing/)

## Tools & Technologies

- Cisco Packet Tracer
- Cisco IOS-style CLI
- IPv4 addressing and subnetting
- OSPF routing
- VLANs, trunking, ACLs, and DHCP
- Git and GitHub
- EVE-NG for advanced labs where supported
- DHCP and NAT/PAT
- STP and EtherChannel
- Network troubleshooting commands

## Repository Structure

```text
enterprise-networking-labs/
├── README.md
├── LICENSE
├── labs/
│   ├── 01-ospf-routing/
│   │   ├── README.md
│   │   ├── configs/
│   │   └── screenshots/
│   ├── 02-network-security/
│   ├── 03-enterprise-network/
│   ├── 04-network-troubleshooting/
|   ├── 05-VLANs and Trunking
|   ├── 06-Inter-VLAN Routin
|   ├── 07-DHCP and NAT/PAT
|   ├── 08-STP and EtherChannel
│   └── 09-Pv4 Subnetting Lab
|
├── Mini Project
|    ├── 01-IP Address Management Plan
|    └── 02-Network Troubleshooting Casebook
└── docs/
```

## Learning Objectives

- Configure and verify dynamic routing protocols.
- Implement network segmentation and access controls.
- Automate repeatable network tasks using Python.
- Design enterprise network topologies.
- Troubleshoot connectivity using a structured methodology.
- Document technical work clearly and professionally.

## Project Progress

Labs are marked completed only after the relevant configurations and verification tests have been performed. Additional labs will be documented as they are built and tested.

## Disclaimer

This repository is an independent educational project. Configurations are intended for simulation and learning. Always validate configurations before applying them to production networks.
