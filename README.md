# Enterprise Dual-Site Network Deployment (Full Configuration)

## Overview
This project is a complete end-to-end implementation of a multi-site enterprise network built inside Cisco Packet Tracer. The design includes Core, Distribution, and Access layers across two offices, with full Layer-2 and Layer-3 redundancy, dynamic routing, network services, device hardening, secure management access, and wireless integration.

Scenario Source: Lab instructions and topology originate from Jeremy’s IT Lab.  
All configurations, implementation, verification, and troubleshooting were performed independently.

---

# Key Features Implemented

## Authentication & Device Hardening
- Unique hostnames on all routers and switches  
- `enable secret` configured using Type 9 (or Type 5 where unavailable)  
- Local user account (`cisco` / secret `ccna`) using secure hashing  
- Console lines protected with local login, 30-minute inactivity timeout, synchronous logging  
- VTY lines restricted to SSH only, authenticated locally  
- Unused interfaces manually disabled  
- CDP disabled globally; LLDP enabled (LLDP Tx disabled on Access ports)

---

## Layer-2 Architecture
- VLANs configured and managed via VTPv2 (server/client model)  
- Access, Voice, Management, Server, and Wi-Fi VLANs mapped per office  
- Layer-2 EtherChannels:  
  - Office A: PAgP (active)  
  - Office B: LACP (active)  
- Trunking across all uplinks with:  
  - DTP disabled  
  - Native VLAN 1000  
  - Site-specific allowed VLAN lists  
- Access ports configured for PCs, IP Phones, APs, and SRV1

---

## Layer-3 Architecture & Redundancy
- IPv4 routing enabled on multilayer switches  
- L3 EtherChannel between Core switches  
- Complete interface addressing across all routed links and SVIs  
- HSRPv2 configured on all user subnets for both sites:  
  - Management, PCs, Phones, Wi-Fi (Office A)  
  - Management, PCs, Phones, Servers (Office B)  
- Loopback interfaces used for Router IDs and management reachability

---

## Rapid PVST+
- Root Bridge alignment with the active HSRP switch for each VLAN  
- Standby switch priorities tuned for deterministic failover  
- PortFast + BPDU Guard enabled on all edge ports

---

## Routing: OSPF + Static Defaults
- OSPF Area 0 across all routers and multilayer switches (Process ID 1)  
- SVIs and loopbacks set passive where appropriate  
- Point-to-point network type on routed links for predictable DR/BDR elections  
- R1 configured as the ASBR:  
  - Two recursive static default routes (primary + higher AD secondary)  
- Default-information originate controlled manually due to Packet Tracer limitations

---

# Network Services

## DHCP (R1)  
DHCP pools created for all wired and wireless subnets with the first 10 usable addresses excluded.  
Each pool includes correct gateway, domain name, WLC relay (where applicable), and DNS settings.

**Pools Implemented**
- A-Mgmt (10.0.0.0/28)  
- A-PC (10.1.0.0/24)  
- A-Phone (10.2.0.0/24)  
- B-Mgmt (10.0.0.16/28)  
- B-PC (10.3.0.0/24)  
- B-Phone (10.4.0.0/24)  
- Wi-Fi (10.6.0.0/24)

Distribution switches configured with DHCP relay pointing to R1’s Loopback0.

---

## DNS (SRV1)
Static forward lookup entries:
- google.com → 172.253.62.100  
- youtube.com → 152.250.31.93  
- jeremysitlab.com → 66.235.200.145  
- www.jeremysitlab.com → jeremysitlab.com  

All routers and switches configured with domain name `jeremysitlab.com` and DNS server → SRV1.

---

## NTP  
- R1 configured as Stratum 5 and synchronized to 216.239.35.0  
- All switches and routers sync to R1 Loopback0  
- NTP authentication enabled (key 1, password `ccna`)

---

## SNMP  
- SNMP community string configured as **SNMPSTRING** (RO only)

---

## Syslog  
- All devices send logs of all severity levels to SRV1  
- Logging buffered (8192 bytes)

---

## FTP (R1)  
- Default FTP credentials (`cisco` / `cisco`) configured  
- IOS image `c2900-universalk9-mz.SPA.155-3.M4a.bin` downloaded from SRV1  
- R1 rebooted using the new IOS, old image removed

---

## SSH Access Control  
- RSA keys generated with maximum supported modulus  
- SSHv2 only  
- Standard ACL 1 limits SSH access exclusively to Office A PCs subnet  
- VTY lines accept **SSH only**, with synchronous logging

---

## NAT / PAT  
- Static NAT: SRV1 reachable publicly via 203.0.113.113  
- Dynamic PAT:  
  - ACL 2 defines inside local ranges (A-PC, A-Phone, B-PC, B-Phone, Wi-Fi)  
  - POOL1: 203.0.113.200–203.0.113.207 (/29)  
  - Mapped to ACL 2 with overload (PAT)  
- Internet failover tested by shutting R1 G0/0/0 and reapplying `default-information originate` manually

---

# Wireless

## WLC1 (10.0.0.7)
Configuration performed via HTTPS GUI using admin/adminPW12.

### Dynamic Interface: Wi-Fi
- VLAN 40  
- IP address: 10.6.0.4  
- Gateway: 10.6.0.1  
- DHCP server: 10.0.0.76  

### WLAN:
- Profile: Wi-Fi  
- SSID: Wi-Fi  
- ID: 1  
- Status: Enabled  
- Security: WPA2 + AES, PSK `cisco123`  

Both LWAPs successfully register with WLC1.  
Packet Tracer limitation: Wireless clients do not receive DHCP leases.

---

# Repository Contents
- `/configs/` — Complete device configurations  
- `/topology/` — Packet Tracer .pka file and network diagram  
- `/docs/` — Notes, addressing tables, protocol design references  
- `README.md`

---

# Notes
- The SVI ACL visibility issue is a known Packet Tracer quirk; the configuration is correct.  
- The network is fully functional, including redundancy, routing, services, management access, wireless, and NAT.
