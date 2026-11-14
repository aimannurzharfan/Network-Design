# Campus Network Design: Block N28B, Faculty of Computing, UTM

The network design and Cisco Packet Tracer simulation for a new two-floor building at the Faculty of Computing, Universiti Teknologi Malaysia. It covers general-purpose labs, a Cisco networking lab, an embedded systems lab, a hybrid classroom and a video conference room, with room for 15% growth in users and devices over five years.

[Watch the walkthrough on YouTube](https://youtu.be/ewS-gqa3L7c)

## What's in this repo

| File | Contents |
| --- | --- |
| `Network Design Report.pdf` | Course deliverable: requirements, floor plans, device placement, structured cabling (TIA/EIA), cost and procurement |
| `Personal Project.pdf` | My extension beyond the course: OSPF, VLANs, extended ACLs and NAT/PAT on the same building |
| `Design.pkt` | The Packet Tracer simulation |
| `demo.mp4` | Local copy of the walkthrough video |

## What I added beyond the course

The course asked for the physical design. I took it further and built the logical network as it would run in production:

- **OSPF** for dynamic routing between the floor and lab routers
- **VLANs** to separate students, staff and lab traffic into their own broadcast domains
- **Extended ACLs** that restrict access to sensitive segments such as the video conference room
- **NAT/PAT** on the edge router so private subnets can reach the internet

## Spaces covered

**Floor 1:** two general-purpose labs (30 workstations each), a student lounge with high-density Wi-Fi, and a public waiting area on an isolated guest network.

**Floor 2:** a Cisco networking lab (30 workstations plus training racks), an embedded systems lab (30 workstations), a hybrid classroom with tracking cameras and smart boards, and a low-latency video conference room.

## Topology

A hierarchical star. The core connects to the UTM backbone, and each floor and lab has its own routing and switching for VLAN routing and fault isolation.

| Role | Device | Why |
| --- | --- | --- |
| Main router | Cisco ISR 4431 | Up to 1 Gbps routing and NAT |
| Lab router | Cisco ISR 4331 | Hands-on equipment for the Cisco lab |
| Access switches | Ubiquiti UniFi Enterprise 48 PoE | Layer 3, 2.5GbE PoE+ for dense areas |
| Lab switches | Cisco Catalyst 3750G | Stackable switches for the training racks |
| Wireless | LigoWave NFT 2ac | Dual-band 802.11ac for lounges and labs |
| Cabling | CAT6A shielded | 10 Gbps up to 100 m, less crosstalk |

## IP addressing (VLSM)

Allocated from 172.18.0.0/20:

| Location | Subnet | Usable hosts |
| --- | --- | --- |
| General Lab 1 | 172.18.0.0/24 | 172.18.0.1 to 172.18.0.254 |
| General Lab 2 | 172.18.1.0/24 | 172.18.1.1 to 172.18.1.254 |
| Student Lounge | 172.18.2.0/24 | 172.18.2.1 to 172.18.2.254 |
| Embedded Lab | 172.18.3.0/24 | 172.18.3.1 to 172.18.3.254 |
| Cisco Network Lab | 172.18.4.0/24 | 172.18.4.1 to 172.18.4.254 |
| Hybrid Classroom | 172.18.5.0/24 | 172.18.5.1 to 172.18.5.254 |
| Video Conference Room | 172.18.6.0/24 | 172.18.6.1 to 172.18.6.254 |

Router-to-router links use /30 subnets (for example 172.18.7.0/30).

## Open the simulation

1. Install Cisco Packet Tracer (latest version).
2. Clone the repo:
   ```bash
   git clone https://github.com/aimannurzharfan/Network-Design.git
   ```
3. Open `Design.pkt`.
