# Network Design for Faculty of Computing (Block N28B)

## Project Overview

This project involves the design and implementation of a comprehensive network infrastructure for the new two-story building (Block N28B) at the **Faculty of Computing, Universiti Teknologi Malaysia (UTM)**.

The design focuses on scalability, security, and performance to support a projected 15% growth in students and staff. It incorporates modern networking standards to support general-purpose computing, specialized embedded systems work, and Cisco networking training.

* **Course:** SECR1213: Network Communications
* **Semester:** 2024/2025
* **Author:** Aiman Nurzharfan Bin Mohd Ali Yusni (A24CS0039)
* **Group:** FYBER

## Infrastructure Scope

The network design covers two floors containing specialized facilities:

### **Ground Floor (Floor 1)**

* **2x General Purpose Labs:** 30 workstations each for programming and general study.
* **Student Lounge:** Casual study area with WiFi connectivity.
* **Waiting Area:** Public access zone.

### **Second Floor (Floor 2)**

* **Cisco Network Lab:** 30 workstations + rack-mounted equipment for networking certification training.
* **Embedded Lab:** 30 workstations equipped for IoT and electronics engineering.
* **Hybrid Classroom:** Equipped with auto-tracking cameras and smart boards for remote/hybrid learning.
* **Video Conference Room:** Dedicated space for high-quality remote meetings.

## 🛠️ Network Design & Topology

### **Topology**

The network utilizes a **Star Topology** to ensure ease of management, fault isolation, and scalability.

* **Core:** Connected to the UTM Backbone.
* **Distribution/Access:** Dedicated routers and switches for each lab and floor segment to reduce collision domains and improve performance.

### **Hardware Specifications**

The design incorporates enterprise-grade hardware to ensure reliability:

| Device Type | Model | Purpose |
| :--- | :--- | :--- |
| **Main Router** | Cisco ISR 4431 | High-throughput routing for building-wide traffic (up to 1Gbps). |
| **Lab Router** | Cisco ISR 4331 | Hands-on training equipment in the Cisco Lab. |
| **Switches** | Ubiquiti UniFi Enterprise 48 PoE | Layer 3 switching with 2.5GbE PoE+ support for high-density areas. |
| **Lab Switches** | Cisco Catalyst 3750G | Stackable switches for the Cisco Lab training racks. |
| **Wireless AP** | LigoWave NFT 2ac | Dual-band 802.11ac WiFi for coverage in lounges and labs. |
| **Cabling** | CAT 6A Shielded | Supports 10Gbps speeds up to 100m; minimizes crosstalk. |

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

*Inter-router links use /30 subnets (e.g., 172.18.7.0/30) to conserve addresses.*

## Repository Contents

* `Network Design Report.pdf`: Full documentation covering feasibility studies, floor plans, cable management, and cost analysis.
* `Design.pkt`: **Cisco Packet Tracer** simulation file demonstrating the logical topology and routing configurations.
* `README.md`: Project documentation.

## 🚀 How to Run the Simulation

1. Download and install [Cisco Packet Tracer](https://www.netacad.com/courses/packet-tracer).
2. Clone this repository:
   ```bash
   git clone [https://github.com/your-username/network-design-block-n28b.git](https://github.com/your-username/network-design-block-n28b.git)
