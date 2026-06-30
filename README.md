# Week 1 — Networking Fundamentals & Network Simulation Tools
**IT-Simplera Institute | Network Administration Internship**

**Intern:** Muhammad Usman
**Supervisor:** Jawad Qayum (Senior Network Administrator)

## Overview
This repository contains the Week 1 deliverables for the Network Administration
Internship at IT-Simplera Institute. The task focused on building a simple LAN
topology and verifying connectivity using two industry-standard network
simulation tools: **Cisco Packet Tracer** and **GNS3**.

## Objectives
- Understand core networking concepts (LAN, IP addressing, subnetting, switching)
- Install and explore Cisco Packet Tracer and GNS3
- Design and implement a LAN topology in both platforms
- Configure static IP addressing and verify connectivity using `ping`

## Topology
- 1 Switch + 4 PCs, all on the **192.168.1.0/24** subnet
- IP assignments:
  - PC1 — `192.168.1.10`
  - PC2 — `192.168.1.11`
  - PC3 — `192.168.1.12`
  - PC4 — `192.168.1.13`

## Repository Structure
```
Week1/
├── Report.pdf
├── Cisco_Packet_Tracer.pkt
├── GNS3_Project/
├── Screenshots/
│   ├── gns3_topology.png
│   ├── gns3_ping_results.png
│   ├── packet_tracer_topology.png
│   └── packet_tracer_ping_results.png
└── README.md
```

## Tools Used
- Cisco Packet Tracer 8.2.1
- GNS3 2.2.40.1
- PuTTY

## Results
Both platforms confirmed full connectivity between all four hosts with
**0% packet loss** on all ping tests.

## Key Learnings
- Switches operate at Layer 2 and forward traffic based on MAC addresses
- Static IP addressing requires all hosts to share the same subnet to communicate directly
- GNS3 emulates closer-to-real device behavior, while Packet Tracer simulates networking concepts for learning

## Author
Muhammad Usman — BS Computer Engineering, International Islamic University Islamabad (IIUI)
