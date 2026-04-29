R1#show ntp associations 

address         ref clock       st   when     poll    reach  delay          offset            disp
 ~216.239.35.0  .INIT.          16   -        64      0      0.00           0.00              0.48
 ~127.127.1.1   .LOCL.          4    8        64      377    0.00           0.00              0.48
 ~203.0.113.1   127.127.1.1     1    24       64      377    0.00           -34291999.00      0.48
 * sys.peer, # selected, + candidate, - outlyer, x falseticker, ~ configured
R1#show ntp status 
Clock is unsynchronized, stratum 16, no reference clock
nominal freq is 250.0000 Hz, actual freq is 249.9990 Hz, precision is 2**24
reference time is 00000000.00000000 (00:00:00.000 UTC Mon Jan 1 1990)
clock offset is 0.00 msec, root delay is 0.00  msec
root dispersion is 0.00 msec, peer dispersion is 0.00 msec.
loopfilter state is 'FSET' (Drift set from file), drift is - 0.000001193 s/s system poll interval is 6, never updated.
