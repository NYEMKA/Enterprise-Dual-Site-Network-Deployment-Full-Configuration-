R1#show dhcp lease 
Temp IP addr: 203.0.113.2 for peer on Interface: GigabitEthernet0/0/0
Temp sub net mask: 255.255.255.252
   DHCP Lease server: 203.0.113.1 , state: Bound
   DHCP Transaction id: 64BEB6E4
   Lease: 86400 secs,  Renewal: 43200 secs,  Rebind: 75600 secs
Temp default-gateway addr: 0.0.0.0
   Next timer fires after: 11:48:12
   Retry count: 0  Client-ID:cisco-00E0.A395.4D4E-Gig0/0/0
   Client-ID hex dump: 636973636F2D303045302E413339352E
                       44434452D476967302F302F30
   Hostname: R1
Temp IP addr: 203.0.113.6 for peer on Interface: GigabitEthernet0/1/0
Temp sub net mask: 255.255.255.252
   DHCP Lease server: 203.0.113.5 , state: Bound
   DHCP Transaction id: CCA14A51
   Lease: 86400 secs,  Renewal: 43200 secs,  Rebind: 75600 secs
Temp default-gateway addr: 0.0.0.0
   Next timer fires after: 11:48:12
   Retry count: 0  Client-ID:cisco-00E0.F768.6426-Gig0/1/0
   Client-ID hex dump: 636973636F2D303045302E463736382E
                       63432362D476967302F312F30
   Hostname: R1
R1#show ip dh
R1#show ip dhcp ?
  binding   DHCP address bindings
  conflict  DHCP address conflicts
  pool      DHCP pools information
  relay     Miscellaneous DHCP relay information
R1#show ip dhcp bi
R1#show ip dhcp binding ?
  <cr>
R1#show ip dhcp binding 
IP address       Client-ID/              Lease expiration        Type
                 Hardware address
10.1.0.11        0001.4290.A4D1           --                     Automatic
10.0.0.28        00E0.F9EA.1401           --                     Automatic
10.3.0.11        0060.3E12.301C           --                     Automatic
R1#show ip dhcp ?
  binding   DHCP address bindings
  conflict  DHCP address conflicts
  pool      DHCP pools information
  relay     Miscellaneous DHCP relay information
R1#show ip dhcp p
R1#show ip dhcp pool 

Pool A-Mgmt :
 Utilization mark (high/low)    : 100 / 0
 Subnet size (first/next)       : 0 / 0 
 Total addresses                : 14
 Leased addresses               : 0
 Excluded addresses             : 7
 Pending event                  : none

 1 subnet is currently in the pool
 Current index        IP address range                    Leased/Excluded/Total
 10.0.0.1             10.0.0.1         - 10.0.0.14         0    / 7     / 14

Pool A-PC :
 Utilization mark (high/low)    : 100 / 0
 Subnet size (first/next)       : 0 / 0 
 Total addresses                : 254
 Leased addresses               : 1
 Excluded addresses             : 7
 Pending event                  : none

 1 subnet is currently in the pool
 Current index        IP address range                    Leased/Excluded/Total
 10.1.0.1             10.1.0.1         - 10.1.0.254        1    / 7     / 254

Pool A-Phone :
 Utilization mark (high/low)    : 100 / 0
 Subnet size (first/next)       : 0 / 0 
 Total addresses                : 254
 Leased addresses               : 0
 Excluded addresses             : 7
 Pending event                  : none

 1 subnet is currently in the pool
 Current index        IP address range                    Leased/Excluded/Total
 10.2.0.1             10.2.0.1         - 10.2.0.254        0    / 7     / 254

Pool B-Mgmt :
 Utilization mark (high/low)    : 100 / 0
 Subnet size (first/next)       : 0 / 0 
 Total addresses                : 14
 Leased addresses               : 1
 Excluded addresses             : 7
 Pending event                  : none

 1 subnet is currently in the pool
 Current index        IP address range                    Leased/Excluded/Total
 10.0.0.17            10.0.0.17        - 10.0.0.30         1    / 7     / 14

Pool B-PC :
 Utilization mark (high/low)    : 100 / 0
 Subnet size (first/next)       : 0 / 0 
 Total addresses                : 254
 Leased addresses               : 1
 Excluded addresses             : 7
 Pending event                  : none

 1 subnet is currently in the pool
 Current index        IP address range                    Leased/Excluded/Total
 10.3.0.1             10.3.0.1         - 10.3.0.254        1    / 7     / 254

Pool B-Phone :
 Utilization mark (high/low)    : 100 / 0
 Subnet size (first/next)       : 0 / 0 
 Total addresses                : 254
 Leased addresses               : 0
 Excluded addresses             : 7
 Pending event                  : none

 1 subnet is currently in the pool
 Current index        IP address range                    Leased/Excluded/Total
 10.4.0.1             10.4.0.1         - 10.4.0.254        0    / 7     / 254

Pool Wi-Fi :
 Utilization mark (high/low)    : 100 / 0
 Subnet size (first/next)       : 0 / 0 
 Total addresses                : 254
 Leased addresses               : 0
 Excluded addresses             : 7
 Pending event                  : none

 1 subnet is currently in the pool
 Current index        IP address range                    Leased/Excluded/Total
 10.6.0.1             10.6.0.1         - 10.6.0.254        0    / 7     / 254
