# Week 02 — IP Addressing (FLSM & VLSM) and VLAN Configuration

**Internship:** Network Administration Internship Program
**Organization:** IT-Simplera Institute
**Supervisor:** Jawad Qayum (Senior Network Administrator)
**Intern:** Muhammad Usman
**Week:** 02
**Submission Deadline:** 10 July 2026

---

## 📌 Overview

This week focused on two core Network Administration skills:

1. **IP Addressing** — subnetting a network using both **Fixed Length Subnet Masking (FLSM)** and **Variable Length Subnet Masking (VLSM)** to design efficient IP allocation schemes.
2. **VLAN Configuration** — implementing Virtual LANs on Cisco switches to logically segment a network by department, configuring access ports and trunk links, and verifying connectivity.

The task was implemented and verified in both **Cisco Packet Tracer** and **GNS3**.

---

## 🎯 Objectives

- Understand and calculate FLSM and VLSM subnetting scenarios (network address, subnet mask, broadcast address, usable host range).
- Understand the purpose and benefits of VLANs in enterprise networks.
- Configure VLANs, access ports, and trunk links using Cisco IOS commands.
- Verify configuration and connectivity using `show vlan brief`, `show interfaces trunk`, and ping tests.

---

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| Cisco Packet Tracer | Building and configuring the VLAN topology (.pkt file) |
| GNS3 | Recreating the topology with a more realistic network emulation |
| PuTTY | Console/Telnet access to GNS3 device consoles |

---

## 📂 Repository Structure

```
Week2/
├── README.md
├── Report.pdf                     # Full IP Addressing + VLAN report (FLSM/VLSM worksheets, configs, verification)
├── Report.docx                    # Editable version of the report
├── Cisco_Packet_Tracer.pkt        # Packet Tracer topology file
├── GNS3_Project/                  # GNS3 project folder
└── Screenshots/
    ├── topology.png
    ├── switch0_vlan_trunk.png
    ├── switch1_vlan_trunk.png
    ├── ping_vlan10.png
    └── ping_vlan20.png
```

---

## 🧮 IP Addressing Summary

### FLSM
Solved 10 FLSM subnetting problems — equal-size subnet allocation across networks ranging from `/24` to `/8`, covering subnet counts from 2 to 32. Full calculations (subnet mask, network address, broadcast address, usable range) are documented in `Report.pdf`.

### VLSM
Designed 5 VLSM scenarios — allocating variable-size subnets based on actual host requirements, from a single-office LAN to a multi-branch WAN. Example (used for the VLAN lab below):

| Segment | Hosts Needed | Block/Mask | Network Address | Usable Range |
|---|---|---|---|---|
| VLAN10 – Sales | 60 | /26 (62 usable) | 192.168.10.0/26 | 192.168.10.1–.62 |
| VLAN20 – HR | 30 | /27 (30 usable) | 192.168.10.64/27 | 192.168.10.65–.94 |

---

## 🔀 VLAN Topology

```
      Switch1                              Switch2
   (VLAN10, VLAN20)  ── Trunk (Gig0/1) ──  (VLAN10, VLAN20)
      /        \                              /        \
   PC0(V10)   PC1(V20)                    PC2(V10)   PC3(V20)
```

| Device | VLAN | IP Address | Subnet Mask | Gateway |
|---|---|---|---|---|
| PC0 | 10 (Sales) | 192.168.10.2 | 255.255.255.192 | 192.168.10.1 |
| PC2 | 10 (Sales) | 192.168.10.3 | 255.255.255.192 | 192.168.10.1 |
| PC1 | 20 (HR) | 192.168.10.66 | 255.255.255.224 | 192.168.10.65 |
| PC3 | 20 (HR) | 192.168.10.67 | 255.255.255.224 | 192.168.10.65 |

### Switch Configuration (Cisco IOS)

```
enable
configure terminal
vlan 10
 name Sales
vlan 20
 name HR
exit
interface fastEthernet 0/1
 switchport mode access
 switchport access vlan 10
interface fastEthernet 0/2
 switchport mode access
 switchport access vlan 20
interface gigabitEthernet 0/1
 switchport mode trunk
 switchport trunk allowed vlan 10,20
exit
end
write memory
```

---

## ✅ Verification

- **`show vlan brief`** — confirms VLAN10 (Sales) and VLAN20 (HR) exist with correct port assignments.
- **`show interfaces trunk`** — confirms Gig0/1 is trunking with VLANs 10 and 20 allowed and active.
- **Ping tests:**
  - PC0 ↔ PC2 (same VLAN10, across trunk) → ✅ Success, 0% packet loss
  - PC1 ↔ PC3 (same VLAN20, across trunk) → ✅ Success, 0% packet loss
  - PC0 ↔ PC1 (cross-VLAN) → ❌ Fails as expected — confirms VLAN isolation is working correctly

Screenshots of all the above are in the `Screenshots/` folder and in `Report.pdf`.

---

## 📚 Key Learning Outcomes

- Difference between FLSM (simple, equal allocation) and VLSM (efficient, need-based allocation).
- How VLANs improve network security, performance, and manageability by segmenting broadcast domains.
- How trunk links use 802.1Q tagging to carry multiple VLANs between switches.
- How to verify Layer 2 configurations using Cisco IOS `show` commands and connectivity tests.

---

## 🔗 Links

- **LinkedIn Post:** [add your post link here]
- **Google Form Submission:** [add link if applicable]

---

*Part of the Network Administration Internship Program at IT-Simplera Institute.*
