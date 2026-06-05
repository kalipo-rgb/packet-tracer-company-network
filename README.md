# Company Network — Cisco Packet Tracer

A simulated small company network built with Cisco Packet Tracer, featuring VLAN segmentation, inter-VLAN routing, DHCP, DNS, a web server, and access control policies.

---

## Topology Overview

- **Router:** Cisco 2911 — Router-on-a-Stick (802.1Q trunk)
- **Switch:** Layer 2 — VLAN access/trunk configuration
- **Servers:** DNS + Web server (VLAN 99 — management subnet)
- **End devices:** 2 PCs per VLAN, dynamically addressed via DHCP

---

## VLAN Design

| VLAN | Name  | Subnet           | Purpose              |
|------|-------|------------------|----------------------|
| 2    | HR    | 192.168.10.0/24  | Human Resources      |
| 3    | IT    | 192.168.20.0/24  | IT Department        |
| 4    | SALES | 192.168.30.0/24  | Sales Department     |
| 99   | MGMT  | 192.168.99.0/24  | Servers & Management |

---

## Services

- **DHCP:** Configured directly on the router. Each VLAN has its own pool with excluded addresses for gateway and servers.
- **DNS:** Single DNS server at `192.168.99.10`, assigned to all VLAN pools.
- **Web server:** Accessible from all VLANs (except where restricted by ACL).

---

## Access Control (ACLs)

A named extended ACL (`SALES_POLICY`) is applied inbound on the SALES subinterface (`GigabitEthernet0/0.4`):
**Effect:** SALES hosts cannot communicate with HR. All other inter-VLAN traffic is permitted.

---

## How to Open

1. Download and install [Cisco Packet Tracer](https://www.netacad.com/courses/packet-tracer)
2. Clone or download this repository
3. Open the `.pkt` file in Packet Tracer
