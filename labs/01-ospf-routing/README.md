# Lab 01: OSPF Routing Across Multiple Routers

## 1. Overview

This lab demonstrates how to configure Open Shortest Path First (OSPF) routing across three routers. The goal is to establish OSPF neighbor relationships, exchange routes dynamically, and verify end-to-end connectivity between three LANs.

**Difficulty:** Beginner to Intermediate  
**Protocol:** OSPFv2  
**OSPF area:** Area 0  
**Environment:** Cisco Packet Tracer

## 2. Objectives

- Configure IPv4 addresses on router interfaces.
- Enable OSPF on three routers.
- Establish OSPF neighbor adjacencies.
- Advertise LAN and transit networks.
- Verify dynamically learned routes.
- Test connectivity between remote LANs.
- Document troubleshooting procedures.

## 3. Network Topology

```text
 LAN 1                 LAN 2                 LAN 3
192.168.10.0/24      192.168.20.0/24      192.168.30.0/24
      |                     |                     |
     R1 ------------------- R2 ------------------- R3
 10.0.12.1             10.0.12.2
                       10.0.23.1             10.0.23.2

              OSPF Area 0 across all routers
```

The diagram is conceptual. Interface names depend on the router models used in the simulator.

## 4. IP Addressing Table

| Device | Interface role | IP address | Subnet mask |
|---|---|---|---|
| R1 | LAN | 192.168.10.1 | 255.255.255.0 |
| R1 | R1-R2 link | 10.0.12.1 | 255.255.255.252 |
| R2 | R1-R2 link | 10.0.12.2 | 255.255.255.252 |
| R2 | LAN | 192.168.20.1 | 255.255.255.0 |
| R2 | R2-R3 link | 10.0.23.1 | 255.255.255.252 |
| R3 | R2-R3 link | 10.0.23.2 | 255.255.255.252 |
| R3 | LAN | 192.168.30.1 | 255.255.255.0 |

## 5. OSPF Configuration

Configure interface IP addresses and enable the interfaces before configuring OSPF. Use the appropriate interface names for your selected devices.

### R1

```cisco
enable
configure terminal
router ospf 1
 router-id 1.1.1.1
 network 192.168.10.0 0.0.0.255 area 0
 network 10.0.12.0 0.0.0.3 area 0
end
write memory
```

### R2

```cisco
enable
configure terminal
router ospf 1
 router-id 2.2.2.2
 network 192.168.20.0 0.0.0.255 area 0
 network 10.0.12.0 0.0.0.3 area 0
 network 10.0.23.0 0.0.0.3 area 0
end
write memory
```

### R3

```cisco
enable
configure terminal
router ospf 1
 router-id 3.3.3.3
 network 192.168.30.0 0.0.0.255 area 0
 network 10.0.23.0 0.0.0.3 area 0
end
write memory
```

## 6. Verification Commands

Run these commands on the routers and record the results.

```cisco
show ip interface brief
show ip ospf neighbor
show ip route
show ip route ospf
show ip protocols
```

Test connectivity between hosts in different LANs:

```cisco
ping 192.168.30.10
traceroute 192.168.30.10
```

The remote host address assumes a PC is configured at `192.168.30.10` with the correct subnet mask and default gateway.

## 7. Expected Results

- Router interfaces have the correct IP addresses and are operational.
- R1 and R2 form an OSPF adjacency.
- R2 and R3 form an OSPF adjacency.
- Remote LAN routes appear as OSPF-learned routes.
- Hosts in different LANs can communicate when all configurations are correct.

These results must be verified in the simulator before marking the lab complete.

## 8. Troubleshooting Checklist

If OSPF neighbors or remote routes are missing:

1. Check interface status and IP addressing.
2. Verify the subnet masks on both ends of each transit link.
3. Check OSPF network statements and area assignments.
4. Confirm that OSPF neighbors reach the FULL state.
5. Inspect routing tables for missing remote networks.
6. Verify host IP addresses, subnet masks, and default gateways.
7. Repeat the ping test after correcting the issue.

## 9. Results and Evidence

After completing the lab, add:

- A screenshot of the final topology.
- OSPF neighbor output from each router.
- Routing table output showing remote OSPF routes.
- Successful end-to-end connectivity tests.
- A short explanation of any issue encountered and its resolution.

## 10. Learning Notes

Document what you learned about OSPF neighbor formation, route advertisement, wildcard masks, and dynamic routing.

## Status

**Status:** In Progress

Update this status only after the configuration and connectivity tests have been completed successfully.
