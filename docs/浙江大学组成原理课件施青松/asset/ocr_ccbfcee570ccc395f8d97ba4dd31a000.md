# RAID 3: Bit-Interleaved Parity Disk

10010011
11001101
10010011
…

logical record

![](bbox=[0.397, 0.179, 0.932, 0.361])

Striped physical
records

| Disk 1 | Disk 2 | Disk 3 | P |
|---:|---:|---:|---:|
| 1 | 1 | 1 | 1 |
| 0 | 1 | 0 | 1 |
| 1 | 0 | 1 | 0 |
| 0 | 0 | 0 | 0 |
| 0 | 0 | 0 | 1 |
| 0 | 1 | 0 | 1 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 1 | 1 |

P contains sum of
other disks per stripe
mod 2 (“parity”)
If disk fails, subtract
P from sum of other
disks to find missing information