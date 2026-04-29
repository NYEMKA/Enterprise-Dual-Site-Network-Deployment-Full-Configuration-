R1#show ip nat statistics 

Total translations: 1 (1 static, 0 dynamic, 0 extended)
Outside Interfaces: GigabitEthernet0/0/0 , GigabitEthernet0/1/0
Inside Interfaces: GigabitEthernet0/0 , GigabitEthernet0/1
Hits: 0  Misses: 147
Expired translations: 0
Dynamic mappings:
-- Inside Source
access-list 2 pool POOL1 refCount 0
 pool POOL1: netmask 255.255.255.248
       start 203.0.113.200 end 203.0.113.207
       type generic, total addresses 8 , allocated 0 (0%), misses 0

________________
R1#show running-config | section ip nat

ip nat pool POOL1 203.0.113.200 203.0.113.207 netmask 255.255.255.248
ip nat inside source list 2 pool POOL1 overload
ip nat inside source static 10.5.0.4 203.0.113.113 
