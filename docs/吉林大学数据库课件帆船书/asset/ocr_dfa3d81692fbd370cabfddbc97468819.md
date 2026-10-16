# RAID Levels (Cont.)

+   RAID Level 5: Block-Interleaved Distributed Parity; partitions data and parity among all N + 1 disks, rather than storing data in N disks and parity in 1 disk.

+   E.g., with 5 disks, parity block for nth set of blocks is stored on disk (n mod 5) + 1. with the data blocks stored on the other 4 disks.

![](bbox=[0.35, 0.42, 0.68, 0.53])

(f) RAID 5: block-interleaved distributed parity

| P0 | 0 | 1 | 2 | 3 |
| 4 | P1 | 5 | 6 | 7 |
| 8 | 9 | P2 | 10 | 11 |
| 12 | 13 | 14 | P3 | 15 |
| 16 | 17 | 18 | 19 | P4 |