# Enterprise Networking Labs

Hands-on networking projects focused on CCNA and CCNP Enterprise concepts, routing and switching, network security, automation, and troubleshooting.

## About This Project

This repository documents my practical learning journey in enterprise networking using Cisco Packet Tracer and other networking tools. Each lab includes network topology, IP addressing, device configurations, verification commands, and troubleshooting notes.

## Lab Roadmap & Progress

| Lab | Project | Status |
|---|---|---|
| 01 | [OSPF Routing Across Multiple Routers](labs/01-ospf-routing/) | ✅ Completed & Tested |
| 02 | Network Security: VLANs, ACLs & Port Security | ⬜ Planned |
| 03 | Enterprise Network Design from Scratch | ⬜ Planned |
| 04 | Network Outage Troubleshooting | ⬜ Planned |

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
- OSPF and IPv4 routing
- VLANs, trunking, ACLs, and DHCP
- Python and JSON
- Git and GitHub
- EVE-NG for advanced labs where supported

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
│   ├── 03-network-automation/
│   ├── 04-enterprise-network/
│   └── 05-network-troubleshooting/
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
