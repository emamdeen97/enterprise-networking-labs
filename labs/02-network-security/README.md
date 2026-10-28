# Lab 02 — Network Security: VLANs, ACLs & Port Security

**Status:** In Progress  
**Platform:** Cisco Packet Tracer  
**Devices:** 2 Cisco 2960 switches and 6 PCs

## 1. Objective

Build a small enterprise LAN with separate departmental VLANs, configure trunking between switches, and apply switch port security to the PC-facing access ports.

The lab demonstrates Layer 2 network segmentation, VLAN trunking, MAC address security, and connectivity verification. ACL configuration and additional security tests are planned next.

## 2. Network Topology

The topology contains two interconnected switches. Each switch connects three PCs, representing the Administration, Staff, and Guest departments.

- SW1 connects PC0, PC1, and PC2.
- SW2 connects PC3, PC4, and PC5.
- Fa0/24 connects SW1 to SW2 as an 802.1Q trunk.
- Fa0/1, Fa0/2, and Fa0/3 are access ports for the three departments.

## 3. VLAN and IP Addressing Plan

| Department | VLAN ID | Subnet | Devices |
|---|---:|---|---|
| ADMIN | 10 | 192.168.10.0/24 | PC0, PC3 |
| STAFF | 20 | 192.168.20.0/24 | PC1, PC4 |
| GUEST | 30 | 192.168.30.0/24 | PC2, PC5 |

| PC | Switch Port | IP Address | Subnet Mask |
|---|---|---|---|
| PC0 | SW1 Fa0/1 | 192.168.10.11 | 255.255.255.0 |
| PC1 | SW1 Fa0/2 | 192.168.20.11 | 255.255.255.0 |
| PC2 | SW1 Fa0/3 | 192.168.30.11 | 255.255.255.0 |
| PC3 | SW2 Fa0/1 | 192.168.10.12 | 255.255.255.0 |
| PC4 | SW2 Fa0/2 | 192.168.20.12 | 255.255.255.0 |
| PC5 | SW2 Fa0/3 | 192.168.30.12 | 255.255.255.0 |

Default gateways are not configured in the current Layer 2-only topology.

## 4. VLAN Configuration

Created the following VLANs on both switches:

- VLAN 10 — ADMIN
- VLAN 20 — STAFF
- VLAN 30 — GUEST

Assigned the PC-facing access ports to their corresponding VLANs.

## 5. Trunk Configuration

Configured Fa0/24 on both switches as an 802.1Q trunk.

VLANs 10, 20, and 30 are allowed across the trunk to provide connectivity between devices in the same VLAN on different switches.

## 6. Switch Port Security

Enabled port security on Fa0/1 through Fa0/3 on both switches.

Security settings:

- Maximum secure MAC addresses per port: 1
- Sticky MAC address learning: enabled
- Violation action: shutdown

This configuration limits each PC-facing port to one secure MAC address. An unauthorized MAC address can trigger a security violation and cause the port to enter an error-disabled state.

## 7. Verification Commands

Run these commands on each switch as appropriate:

```text
show vlan brief
show interfaces trunk
show port-security
show port-security address
show port-security interface fastEthernet0/1
show running-config
```

Save
