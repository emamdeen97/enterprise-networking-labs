# Mini Project 01 --- IP Address Management Plan

**Status:** In Progress\
**Starting network:** `192.168.10.0/24`\
**Method:** Variable Length Subnet Masking (VLSM)

## 1. Scenario

Create an IPv4 addressing plan for four company departments:

  Department         Required devices
  ---------------- ------------------
  Guest Wi-Fi                      60
  IT                               50
  Administration                   25
  HR                               12

This plan uses the private IPv4 block `192.168.10.0/24`. The suggested
default gateway for each subnet is the first usable IP address. This is
a planning assumption and can be changed to match the actual router or
Layer 3 switch design.

## 2. Final VLSM allocation

  -------------------------------------------------------------------------------------------------------------------------------------------------
  Department         Devices CIDR   Subnet mask       Network address  First usable     Last usable      Suggested        Broadcast          Usable
                      needed                                                                             gateway                              hosts
  ---------------- --------- ------ ----------------- ---------------- ---------------- ---------------- ---------------- ---------------- --------
  Guest Wi-Fi             60 /26    255.255.255.192   192.168.10.0     192.168.10.1     192.168.10.62    192.168.10.1     192.168.10.63          62

  IT                      50 /26    255.255.255.192   192.168.10.64    192.168.10.65    192.168.10.126   192.168.10.65    192.168.10.127         62

  Administration          25 /27    255.255.255.224   192.168.10.128   192.168.10.129   192.168.10.158   192.168.10.129   192.168.10.159         30

  HR                      12 /28    255.255.255.240   192.168.10.160   192.168.10.161   192.168.10.174   192.168.10.161   192.168.10.175         14
  -------------------------------------------------------------------------------------------------------------------------------------------------

**Address space remaining:** `192.168.10.176–192.168.10.255` (80
addresses, currently unallocated).

## 3. VLSM calculations, step by step

### Step 1 --- Sort by largest host requirement

VLSM works most efficiently when you allocate the largest subnet first:

1.  Guest Wi-Fi --- 60 devices
2.  IT --- 50 devices
3.  Administration --- 25 devices
4.  HR --- 12 devices

### Step 2 --- Add two reserved addresses

For a typical IPv4 subnet, two addresses cannot be assigned to ordinary
hosts: - Network address identifies the subnet. - Broadcast address
sends traffic to all hosts in that subnet.

So calculate `required hosts + 2`, then choose the next power of two.

  ------------------------------------------------------------------------------
  Department       Hosts needed    Hosts + 2      Minimum Usable hosts Prefix
                                               block size              
  ---------------- ------------ ------------ ------------ ------------ ---------
  Guest Wi-Fi                60           62 64 addresses           62 /26

  IT                         50           52 64 addresses           62 /26

  Administration             25           27 32 addresses           30 /27

  HR                         12           14 16 addresses           14 /28
  ------------------------------------------------------------------------------

IPv4 subnet size is `2^(32 − prefix length)`. For example, a `/26` has
`2^(32−26) = 64` total addresses and 62 usable host addresses.

### Step 3 --- Determine subnet masks

-   `/26` = `255.255.255.192` (64 addresses per subnet)
-   `/27` = `255.255.255.224` (32 addresses per subnet)
-   `/28` = `255.255.255.240` (16 addresses per subnet)

### Step 4 --- Allocate blocks in order

Starting from `192.168.10.0`:

-   Guest Wi-Fi takes 64 addresses: `.0` through `.63`.
-   IT takes the next 64 addresses: `.64` through `.127`.
-   Administration takes the next 32 addresses: `.128` through `.159`.
-   HR takes the next 16 addresses: `.160` through `.175`.

The next available address is `.176`, which is outside all four
allocated subnets.

### Step 5 --- Find usable range and broadcast

For each subnet: - The first address is the **network address** and is
not assigned to a host. - The last address is the **broadcast address**
and is not assigned to a host. - The usable range is the addresses
between them. - This plan suggests the first usable address as the
default gateway.

Example for Guest Wi-Fi (`192.168.10.0/26`): - Network: `192.168.10.0` -
First usable / gateway: `192.168.10.1` - Last usable: `192.168.10.62` -
Broadcast: `192.168.10.63`

## 4. Validation

-   All four subnets fit inside `192.168.10.0/24`.
-   No allocated subnets overlap.
-   Each subnet supports the required device count.
-   Total allocated block size is `64 + 64 + 32 + 16 = 176` addresses.
-   The remaining 80 addresses are available for future growth, subject
    to subnet-boundary planning.

## 5. Suggested GitHub files

``` text
mini-projects/
└── 01-ip-address-management/
    ├── README.md
    └── IP_Address_Management_Plan.xlsx
```

## 6. Learning outcomes

This project demonstrates IPv4 addressing, CIDR notation, subnet masks,
VLSM allocation, usable host range calculations, and basic IP address
documentation.

> This is a planning exercise. Mark the project **Completed** only after
> you have reviewed the allocation and committed the documentation to
> your repository.
