# # RAID levels

+   - RAID levels have different characteristics
+     – RAID-5 is not "better" than RAID-1

+   - Use RAID level according to needs

| RAID level | Min # disks | Read performance | Write performance | Redundancy | Data capacity with 3x1GB disk | Other remarks |
|------------|-------------|------------------|-------------------|------------|-------------------------------|---------------|
| Linear     | 2           | Equal            | Equal             | No         | 3 GB                          | Can be used if disks are not equal |
| 0          | 2           | Fast             | Fast              | No         | 3 GB                          |               |
| 1          | 2           | Fast             | Somewhat slower   | Yes        | 1 GB                          | Can sustain N-1 disk crash(s) |
| 4          | 3           | Somewhat faster  | Slow              | Yes        | 2 GB                          | Can sustain one disk crash Parity disk is bottleneck |
| 5          | 3           | Somewhat faster  | Somewhat faster   | Yes        | 2 GB                          | Can sustain one disk crash CPU intensive |

(*) Performance compared to a single disk, for data transfers greater than block size