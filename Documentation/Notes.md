Network Architecture Overview

The topology follows a classic three-tier enterprise model consisting of Core,
Distribution, and Access layers. The design goals are predictable routing
behavior, controlled Layer-2 domains, fast convergence, and a clean separation
between user access and backbone forwarding.

Two geographically separated offices connect through the core. Each site maintains
its own VLANs, HSRP pairs, and local services while sharing a unified OSPF domain.

Layer-2 Design

VLAN Strategy
Each site uses the following VLANs:

Management
User PC
Voice (IP Phones)
Wi-Fi or Server (site-dependent)

This segmentation supports scalability, straightforward QoS mapping, and clear
security boundaries.

VTP Approach
VTPv2 is deployed with one switch per site acting as the VTP server. This avoids
VLAN drift while preventing the risk of cross-site VTP updates causing unintended
changes.

EtherChannel

Site A: PAgP (mode active)
Site B: LACP (mode active)

Using different aggregation protocols demonstrates protocol knowledge and
awareness of vendor interoperability. EtherChannel increases aggregate bandwidth
and reduces spanning-tree complexity by bundling links logically.

Trunking and Edge Hardening

DTP disabled on all trunk links
Allowed VLAN lists restricted per site
Native VLAN set to 1000
Edge ports configured with PortFast and BPDU Guard

These measures reduce attack surface and promote predictable STP behavior.

Layer-3 Design

Routing Model
All Layer-3 devices participate in OSPF Area 0. A single-area design simplifies
operations and ensures fast convergence within Packet Tracer’s limitations.
Loopback interfaces provide stable router IDs, and passive interfaces suppress
unnecessary neighbor formation.

First-Hop Redundancy
HSRPv2 runs on all user VLANs in both sites. The Core switch at each location is
the HSRP active device, aligning with STP root placement for optimal traffic
flow and deterministic failover.

Recursive Default Routes
The edge router uses two default static routes pointing to separate next-hop
objects. Each route resolves recursively toward upstream addresses, preserving
failover while allowing OSPF redistribution back into the LAN.

Spanning Tree Design

Rapid PVST+ is used to ensure quick convergence across VLANs.

Primary Core switch is STP root
Secondary Core is root-secondary
Access switches rely on the Core layer to avoid STP domain fragmentation

This mirrors real enterprise designs where the Core anchors spanning-tree behavior.

Network Services

DHCP
Centralized on the edge router with appropriate excluded addresses. Each scope
provides gateway, DNS, domain name, and enterprise-appropriate lease timers.

NAT and DNS
NAT overload is configured on the edge router for outbound Internet access.
Internal DNS is handled by the server to support hostname resolution between
offices.

Logging, Monitoring, and Time
NTP, Syslog, SNMP, FTP, SSH, and banner protections are configured to reflect
standard operational baseline hardening.

Security Hardening
Password encryption
Local user authentication
Secure console and vty settings
Shutdown of unused switchports
Disabled negotiation on trunks
Management VLAN isolation

These measures follow common enterprise security guidelines.

Limitations

Packet Tracer does not support applying extended ACLs directly to SVIs on certain
switch models, which prevented finalizing one policy. All other intended features
are fully implemented.
