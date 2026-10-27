# Lab 01: OSPF Routing Across Three Routers

**Status:** Completed and tested in Cisco Packet Tracer  
**Protocol:** OSPFv2  
**Area:** Area 0  
**Platform:** Cisco Packet Tracer — Cisco 2911 routers and Cisco 2960 switches

## 1. Project Overview

This lab demonstrates dynamic routing between three LANs using Open Shortest Path First (OSPF). Three routers exchange routing information, allowing hosts on separate IP networks to communicate without manually configuring static routes.

The lab covers interface configuration, OSPF neighbor formation, route learning, connectivity testing, and network verification.

## 2. Objectives

- Configure IPv4 addresses on router interfaces.
- Establish OSPF adjacencies in Area 0.
- Advertise LAN and transit networks through OSPF.
- Verify dynamically learned routes.
- Configure PCs with correct IP addresses and default gateways.
- Test connectivity between local and remote LANs.
- Document configuration and verification evidence.

## 3. Network Topology

The network consists of three routers connected in a line. Each router connects to a LAN containing a switch and a PC.

```text
PC0 --- SW1 --- R1 -------- R2 -------- R3 --- SW3 --- PC2
                  |           |           |
                LAN 1       LAN 2       LAN 3
                            |
                           SW2
                            |
                           PC1
```

**Router transit links**

- R1 Gi0/1 ↔ R2 Gi0/1
- R2 Gi0/2 ↔ R3 Gi0/1

**LAN interfaces**

- R1 Gi0/0 → SW1
- R2 Gi0/0 → SW2
- R3 Gi0/0 → SW3

## 4. IP Addressing Plan

### Router interfaces

| Device | Interface | IP address | Subnet mask |
|---|---|---|---|
| R1 | Gi0/0 | 192.168.10.1 | 255.255.255.0 |
| R1 | Gi0/1 | 10.0.12.1 | 255.255.255.252 |
| R2 | Gi0/0 | 192.168.20.1 | 255.255.255.0 |
| R2 | Gi0/1 | 10.0.12.2 | 255.255.255.252 |
| R2 | Gi0/2 | 10.0.23.1 | 255.255.255.252 |
| R3 | Gi0/0 | 192.168.30.1 | 255.255.255.0 |
| R3 | Gi0/1 | 10.0.23.2 | 255.255.255.252 |

### End devices

| Device | IP address | Default gateway |
|---|---|---|
| PC0 | 192.168.10.10/24 | 192.168.10.1 |
| PC1 | 192.168.20.10/24 | 192.168.20.1 |
| PC2 | 192.168.30.10/24 | 192.168.30.1 |

All PCs use subnet mask `255.255.255.0`.

## 5. OSPF Configuration

OSPF process ID: `1`  
OSPF area: `0`

| Router | Router ID | Advertised networks |
|---|---|---|
| R1 | 1.1.1.1 | 192.168.10.0/24, 10.0.12.0/30 |
| R2 | 2.2.2.2 | 192.168.20.0/24, 10.0.12.0/30, 10.0.23.0/30 |
| R3 | 3.3.3.3 | 192.168.30.0/24, 10.0.23.0/30 |

Router configuration files are available in the `configs/` directory.

## 6. Verification Commands

The following commands were used to inspect interface status, OSPF neighbors, and learned routes.

```cisco
show ip interface brief
show ip ospf neighbor
show ip route
show ip route ospf
show ip protocols
```

### OSPF neighbor verification

The middle router, R2, should form adjacencies with:

- R1 — Router ID `1.1.1.1`
- R3 — Router ID `3.3.3.3`

The expected neighbor state is `FULL`.

### Connectivity verification

From PC0, test the local gateway and remote LANs:

```text
ping 192.168.10.1
ping 192.168.20.10
ping 192.168.30.10
```

**Observed result:** Successful pings were reported for the configured network.

## 7. Troubleshooting Methodology

When troubleshooting this lab:

1. Verify interface IP addresses and operational status.
2. Check physical connections and interface states.
3. Confirm OSPF network statements, router IDs, and area assignments.
4. Check neighbor adjacency using `show ip ospf neighbor`.
5. Inspect learned routes using `show ip route ospf`.
6. Verify PC IP addresses, subnet masks, and default gateways.
7. Test connectivity from the local gateway toward remote LANs.

## 8. Evidence

Screenshots documenting the completed lab are stored in `screenshots/`.

- `topology.png` — Complete Packet Tracer topology.
- `ospf-neighbors.png` — OSPF neighbor output from R2.
- `connectivity-test.png` — Successful connectivity tests from PC0.

## 9. Repository Contents

```text
01-ospf-routing/
├── README.md
├── enterprise-ospf-lab.pkt
├── configs/
│   ├── R1.txt
│   ├── R2.txt
│   └── R3.txt
└── screenshots/
    ├── topology.png
    ├── ospf-neighbors.png
    └── connectivity-test.png
```

## 10. Key Learnings

- OSPF dynamically discovers neighbors and exchanges routing information.
- Wildcard masks determine which interfaces participate in OSPF.
- Remote LAN routes can be learned without static routes.
- Default gateways are required for hosts to reach remote IP networks.
- Successful routing requires correct interface addressing, operational links, routing information, and host configuration.

## Disclaimer

This is an educational simulation created in Cisco Packet Tracer. The configurations are intended for lab use and should be validated before any deployment in a production environment.
