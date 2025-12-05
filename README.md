# Enterprise Network Infrastructure Design: Faculty of Computing Expansion (Block N28B)

## Executive Summary

This project encompasses the end-to-end design, simulation, and configuration of a robust network infrastructure for the new two-story expansion (Block N28B) at the Faculty of Computing, Universiti Teknologi Malaysia (UTM).

Designed to support high-density usage for general computing, embedded systems engineering, and specialized networking training, this infrastructure prioritizes scalability, fault tolerance, and security. The network is provisioned to handle a projected 15% growth in personnel and connected devices over the next five years.

**Author:** Aiman Nurzharfan Bin Mohd Ali Yusni (A24CS0039)
**Course:** SECR1213: Network Communications
**Group:** FYBER

---

## Project Phases and Documentation

This repository documents the project's evolution from initial feasibility planning to a fully functional, advanced network simulation.

### Phase 1: Planning and Physical Design (Academic Requirement)
**File:** `Network Design Report.pdf`

This document represents the foundational scope required for the university curriculum. It details:
* Feasibility studies and requirement analysis.
* Physical floor plans and device placement strategies.
* Structured cabling standards (Cable management and TIA/EIA compliance).
* Cost analysis and hardware procurement planning.

### Phase 2: Advanced Implementation & Security Hardening (Personal Project)
**File:** `Personal Project.pdf`

Beyond the academic requirements, I expanded the project scope to implement enterprise-level protocols, simulating a production environment. This phase focuses on logical topology optimization and security:
* **Dynamic Routing (OSPF):** Implemented Open Shortest Path First for efficient load balancing and rapid network convergence.
* **Network Segmentation (VLANs):** Configured Virtual LANs to isolate broadcast domains and separate user traffic (Student, Staff, Lab) for improved security and performance.
* **Access Control (ACLs):** Applied Extended ACLs to enforce granular traffic filtering, restricting unauthorized access to critical segments such as the Video Conference infrastructure.
* **Edge Connectivity (NAT/PAT):** Configured Network Address Translation on the edge router to facilitate secure internet connectivity for private internal subnets.

---

## Video Demonstration

A comprehensive walkthrough of the network simulation, including connectivity tests, packet flow analysis, and security verification, can be viewed here:

* **YouTube Demo:** [Insert YouTube Link Here]
* **Local File:** `demo.mp4` (Located in root directory)

---

## Infrastructure Scope

The network design covers two floors containing specialized facilities with distinct traffic requirements:

### Ground Floor (Floor 1)
* **General Purpose Labs (x2):** 30 workstations per lab for programming and general study.
* **Student Lounge:** High-density WiFi zone for casual access.
* **Waiting Area:** Public access zone requiring guest isolation.

### Second Floor (Floor 2)
* **Cisco Network Lab:** 30 workstations plus rack-mounted equipment for networking certification training.
* **Embedded Lab:** 30 workstations equipped for IoT and electronics engineering traffic.
* **Hybrid Classroom:** High-bandwidth requirement for auto-tracking cameras and smart boards.
* **Video Conference Room:** Dedicated low-latency segment for remote meetings.

---

## Technical Design & Topology

### Logical Topology
The network utilizes a **Hierarchical Star Topology** to ensure ease of management, fault isolation, and scalability.
* **Core Layer:** Connected to the UTM Backbone.
* **Distribution/Access Layers:** Dedicated routers and switches for each lab and floor segment to reduce collision domains and enable VLAN routing.

### Hardware Specifications

| Device Type | Model | Purpose |
| :--- | :--- | :--- |
| **Main Router** | Cisco ISR 4431 | High-throughput routing (up to 1Gbps) and NAT services. |
| **Lab Router** | Cisco ISR 4331 | Hands-on training equipment in the Cisco Lab. |
| **Switches** | Ubiquiti UniFi Enterprise 48 PoE | Layer 3 switching with 2.5GbE PoE+ support for high-density areas. |
| **Lab Switches** | Cisco Catalyst 3750G | Stackable switches for the Cisco Lab training racks. |
| **Wireless AP** | LigoWave NFT 2ac | Dual-band 802.11ac WiFi for coverage in lounges and labs. |
| **Cabling** | CAT 6A Shielded | Supports 10Gbps speeds up to 100m; minimizes crosstalk. |

---

## IP Addressing Scheme (VLSM)

The network uses **IPv4** with **Variable Length Subnet Masking (VLSM)** to efficiently allocate addresses from the assigned block: **172.18.0.0/20**.

| Location | Subnet ID | Usable Host Range |
| :--- | :--- | :--- |
| **General Lab 1** | 172.18.0.0/24 | 172.18.0.1 - 172.18.0.254 |
| **General Lab 2** | 172.18.1.0/24 | 172.18.1.1 - 172.18.1.254 |
| **Student Lounge** | 172.18.2.0/24 | 172.18.2.1 - 172.18.2.254 |
| **Embedded Lab** | 172.18.3.0/24 | 172.18.3.1 - 172.18.3.254 |
| **Cisco Network Lab** | 172.18.4.0/24 | 172.18.4.1 - 172.18.4.254 |
| **Hybrid Classroom** | 172.18.5.0/24 | 172.18.5.1 - 172.18.5.254 |
| **Video Conf. Room** | 172.18.6.0/24 | 172.18.6.1 - 172.18.6.254 |

*Note: Inter-router links utilize /30 subnets (e.g., 172.18.7.0/30) to conserve address space and enhance security.*

---

## Simulation Deployment

To examine the logical topology and routing configurations:

1.  Ensure **Cisco Packet Tracer** (Latest Version recommended) is installed.
2.  Clone this repository:
    ```bash
    git clone [https://github.com/your-username/network-design-block-n28b.git](https://github.com/your-username/network-design-block-n28b.git)
    ```
3.  Open `Design.pkt` in Packet Tracer.
