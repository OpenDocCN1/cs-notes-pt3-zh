# # Direct-Mapped Cache Simulation

t=1 s=2 b=1

x xx x

M=16 bytes (4-bit addresses), B=2 bytes/block, S=4 sets, E=1 Blocks/set

Address trace (reads, one byte per read):
0 [0000₂], miss
1 [0001₂], hit
7 [0111₂], miss
8 [1000₂], miss
0 [0000₂] miss

| v | Tag | Block |
|---|-----|-------|
| Set 0 | 1 | 0 | M[0-1] |
| Set 1 | | | |
| Set 2 | | | |
| Set 3 | 1 | 0 | M[6-7] |

Bryant and O’Hallaron, Computer Systems: A Programmer’s Perspective, Third Edition