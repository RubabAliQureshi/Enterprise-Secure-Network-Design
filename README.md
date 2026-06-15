# CE313 — Secure Enterprise Campus Network

> **Course:** CE313 – Computer Communications and Networks  
> **Instructor:** Engr. Muhammad Ahmad Nawaz  
> **Semester:** Spring 2026 | GIK Institute of Engineering Sciences and Technology  

**Group Members**
| Name | Reg No. |
|------|----------|
| Rubab Ali | 2023614 |
| M. Afeef Bari | 2023356 |
| Yashfa Fatima | 2023762 |
| Mahad Aqeel | 2023286 |

---

## Overview

A fully functional secure campus network simulated in **Cisco Packet Tracer**, modeled on the real infrastructure of GIK Institute. A single **Cisco 2911 ISR** handles all Layer 3 duties — inter-VLAN routing, NAT/PAT, ACL enforcement, and IPsec VPN — connected to a **Catalyst 2960-24TT** core switch aggregating twelve departmental and residential access switches.

All seven core functions were verified end-to-end in simulation mode: DHCP, inter-VLAN routing, WAN connectivity, VPN, HTTP, FTP, and ACL filtering.

---

## Network Architecture

| Component | Detail |
|-----------|--------|
| Router | Cisco 2911 ISR (Campus_RTR) |
| Core Switch | Cisco 2960-24TT (Core_sw) |
| Access Switches | 12× Cisco 2960-24TT |
| Routing | Static — router-on-a-stick over 802.1Q trunk |
| NAT | PAT overload on WAN interface |
| DNS | `campus.giki.edu.pk` → `192.168.3.20` |
| Services | HTTP (GIKI Smart Campus page) + FTP |
| VPN | IPsec IKEv2 tunnel |
| Security | 3 extended ACLs |

## VLAN Segmentation

| VLAN | Name | Subnet |
|------|------|--------|
| 10 | FCSE | 192.168.10.0/24 |
| 20 | FBS | 192.168.20.0/24 |
| 30 | ME | 192.168.30.0/24 |
| 40 | MATERIALS | 192.168.40.0/24 |
| 50 | BARBERS | 192.168.50.0/24 |
| 60 | ACB | 192.168.60.0/24 |
| 70 | INCUBATION | 192.168.70.0/24 |
| 100 | BOYS_HOSTELS | 192.168.100.0/24 |
| 120 | GIRLS_HOSTELS | 192.168.120.0/24 |
| 130 | WIFI_GH | 192.168.130.0/24 |
| 200 | ADMIN | 192.168.200.0/24 |
| 300 | SERVICES | 192.168.3.0/24 |

---

## Security Policies

- **HOSTEL_RESTRICT** — Hostel VLANs (100/120/130): DNS and HTTP/HTTPS to server only; no raw access to other VLANs
- **INCUBATION_ISOLATE** — VLAN 70: isolated from all academic segments; server and Internet only
- **ADMIN ACL** — VLAN 200: blocked from academic lab VLANs; server and Internet permitted

---

---

## Test Results

| Test | Status |
|------|--------|
| DHCP (all 12 VLANs) | ✅ Pass |
| Inter-VLAN Routing | ✅ Pass |
| WAN Connectivity via PAT | ✅ Pass |
| VPN Tunnel | ✅ Pass |
| HTTP — campus.giki.edu.pk | ✅ Pass |
| FTP Login | ✅ Pass |
| ACL Filtering (all 3 policies) | ✅ Pass |

---

## Tools

- Cisco Packet Tracer 8.x
- IEEE LaTeX (IEEEtran class)
