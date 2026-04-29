R1#show ip route 
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
       i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
       * - candidate default, U - per-user static route, o - ODR
       P - periodic downloaded static route

Gateway of last resort is 203.0.113.1 to network 0.0.0.0

     10.0.0.0/8 is variably subnetted, 28 subnets, 4 masks
O       10.0.0.0/28 [110/3] via 10.0.0.34, 00:00:48, GigabitEthernet0/0
                    [110/3] via 10.0.0.38, 00:00:48, GigabitEthernet0/1
O       10.0.0.16/28 [110/3] via 10.0.0.34, 00:00:48, GigabitEthernet0/0
                     [110/3] via 10.0.0.38, 00:00:48, GigabitEthernet0/1
C       10.0.0.32/30 is directly connected, GigabitEthernet0/0
L       10.0.0.33/32 is directly connected, GigabitEthernet0/0
C       10.0.0.36/30 is directly connected, GigabitEthernet0/1
L       10.0.0.37/32 is directly connected, GigabitEthernet0/1
O       10.0.0.40/30 [110/2] via 10.0.0.34, 00:00:48, GigabitEthernet0/0
                     [110/2] via 10.0.0.38, 00:00:48, GigabitEthernet0/1
O       10.0.0.44/30 [110/2] via 10.0.0.34, 00:01:21, GigabitEthernet0/0
O       10.0.0.48/30 [110/2] via 10.0.0.34, 00:01:21, GigabitEthernet0/0
O       10.0.0.52/30 [110/2] via 10.0.0.34, 00:01:21, GigabitEthernet0/0
O       10.0.0.56/30 [110/2] via 10.0.0.34, 00:01:21, GigabitEthernet0/0
O       10.0.0.60/30 [110/2] via 10.0.0.38, 00:01:21, GigabitEthernet0/1
O       10.0.0.64/30 [110/2] via 10.0.0.38, 00:01:21, GigabitEthernet0/1
O       10.0.0.68/30 [110/2] via 10.0.0.38, 00:01:21, GigabitEthernet0/1
O       10.0.0.72/30 [110/2] via 10.0.0.38, 00:01:21, GigabitEthernet0/1
C       10.0.0.76/32 is directly connected, Loopback0
O       10.0.0.77/32 [110/2] via 10.0.0.34, 00:01:21, GigabitEthernet0/0
O       10.0.0.78/32 [110/2] via 10.0.0.38, 00:01:21, GigabitEthernet0/1
O       10.0.0.79/32 [110/3] via 10.0.0.34, 00:01:11, GigabitEthernet0/0
                     [110/3] via 10.0.0.38, 00:01:11, GigabitEthernet0/1
O       10.0.0.80/32 [110/3] via 10.0.0.34, 00:01:11, GigabitEthernet0/0
                     [110/3] via 10.0.0.38, 00:01:11, GigabitEthernet0/1
O       10.0.0.81/32 [110/3] via 10.0.0.34, 00:01:11, GigabitEthernet0/0
                     [110/3] via 10.0.0.38, 00:01:11, GigabitEthernet0/1
O       10.0.0.82/32 [110/3] via 10.0.0.34, 00:01:11, GigabitEthernet0/0
                     [110/3] via 10.0.0.38, 00:01:11, GigabitEthernet0/1
O       10.1.0.0/24 [110/3] via 10.0.0.34, 00:01:11, GigabitEthernet0/0
                    [110/3] via 10.0.0.38, 00:01:11, GigabitEthernet0/1
O       10.2.0.0/24 [110/3] via 10.0.0.34, 00:01:11, GigabitEthernet0/0
                    [110/3] via 10.0.0.38, 00:01:11, GigabitEthernet0/1
O       10.3.0.0/24 [110/3] via 10.0.0.34, 00:01:11, GigabitEthernet0/0
                    [110/3] via 10.0.0.38, 00:01:11, GigabitEthernet0/1
O       10.4.0.0/24 [110/3] via 10.0.0.34, 00:01:11, GigabitEthernet0/0
                    [110/3] via 10.0.0.38, 00:01:11, GigabitEthernet0/1
O       10.5.0.0/24 [110/3] via 10.0.0.34, 00:01:11, GigabitEthernet0/0
                    [110/3] via 10.0.0.38, 00:01:11, GigabitEthernet0/1
O       10.6.0.0/24 [110/3] via 10.0.0.34, 00:01:11, GigabitEthernet0/0
                    [110/3] via 10.0.0.38, 00:01:11, GigabitEthernet0/1
     203.0.113.0/24 is variably subnetted, 4 subnets, 2 masks
C       203.0.113.0/30 is directly connected, GigabitEthernet0/0/0
L       203.0.113.2/32 is directly connected, GigabitEthernet0/0/0
C       203.0.113.4/30 is directly connected, GigabitEthernet0/1/0
L       203.0.113.6/32 is directly connected, GigabitEthernet0/1/0
S*   0.0.0.0/0 [1/0] via 203.0.113.1
