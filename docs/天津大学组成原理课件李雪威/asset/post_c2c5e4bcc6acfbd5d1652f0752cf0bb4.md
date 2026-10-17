
## Direct-Mapped Cache Simulation

t=1 s=2 b=1

x xx x

M=16 bytes (4-bit addresses), B=2 bytes/block, S=4 sets, E=1 Blocks/set

Address trace (reads, one byte per read):  
0 [0000₂], miss  
1 [0001₂], hit  
7 [0111₂], miss  
8 [1000₂], miss  
0 [0000₂], miss

| Set | v | Tag | Block |
|-----|---|---|-------|
| Set 0 | 1 | 0 | M[0-1] |
| Set 1 |   |   |       |
| Set 2 |   |   |       |
| Set 3 | 1 | 0 | M[6-7] |

Bryant and O’Hallaron, Computer Systems: A Programmer’s Perspective, Third Edition

## E-way Set Associative Cache (Here: E = 2)

E = 2: Two lines per set  
Assume: cache block size 8 bytes

2 lines per set

S sets

Address of short int:  
t bits | 0...01 | 100

find set

![](img/be2cf0737cec89669e7b18813ea2d3b7_579_0.png)

Bryant and O'Hallaron, Computer Systems: A Programmer's Perspective, Third Edition

valid?  +    match: yes = hit

![](img/be2cf0737cec89669e7b18813ea2d3b7_580_0.png)

compare both

Address of short int:

| t bits | 0...01 | 100 |
|---|---|---|

block offset

**E = 2:** Two lines per set  
**Assume:** cache block size 8 bytes

![](img/be2cf0737cec89669e7b18813ea2d3b7_581_0.png)

No match:

- One line in set is selected for eviction and replacement
- Replacement policies: random, least recently used (LRU), ...

## 2-Way Set Associative Cache Simulation

![](img/be2cf0737cec89669e7b18813ea2d3b7_582_0.png)

M=16 byte addresses, B=2 bytes/block, S=2 sets, E=2 blocks/set

Address trace (reads, one byte per read):

| Address | Binary address | Result |
|---:|:---:|:---:|
| 0 | `[0000_2]` | miss |
| 1 | `[0001_2]` | hit |
| 7 | `[0111_2]` | miss |
| 8 | `[1000_2]` | miss |
| 0 | `[0000_2]` | hit |

| Set | V | Tag | Block |
|:---:|:---:|:---:|:---|
| 0 | 1 | 00 | M[0-1] |
| 0 | 1 | 10 | M[8-9] |
| 1 | 1 | 01 | M[6-7] |
| 1 | 0 |  |  |

## What about writes?

- Multiple copies of data exist:
  - L1, L2, L3, Main Memory, Disk

- What to do on a write-hit?
  - Write-through (write immediately to memory)
  - Write-back (defer write to memory until replacement of line)
    - Need a dirty bit (line different from memory or not)

- What to do on a write-miss?
  - Write-allocate (load into cache, update line in cache)
    - Good if more writes to the location follow
  - No-write-allocate (writes straight to memory, does not load into cache)

- Typical
  - Write-through + No-write-allocate
  - Write-back + Write-allocate

## Intel Core i7 Cache Hierarchy

Processor package

![](img/be2cf0737cec89669e7b18813ea2d3b7_584_0.png)

**Core 0**

Regs

L1 d-cache

L1 i-cache

L2 unified cache

**Core 3**

Regs

L1 d-cache

L1 i-cache

L2 unified cache

L3 unified cache (shared by all cores)

Main memory

**L1 i-cache and d-cache:**  
32 KB, 8-way,  
Access: 4 cycles

**L2 unified cache:**  
256 KB, 8-way,  
Access: 10 cycles

**L3 unified cache:**  
8 MB, 16-way,  
Access: 40-75 cycles

**Block size:** 64 bytes for all caches.

## Example: Core i7 L1 Data Cache

32 kB 8-way set associative  
64 bytes/block  
47 bit address range

B =  
S = , s =  
E = , e =  
C =

Address of word:  
t bits | s bits | b bits  
tag | set index | block offset  

Block offset: . bits  
Set index: . bits  
Tag: . bits

Stack Address:  
0x00007f7262a1e010

Block offset: 0x??  
Set index: 0x??  
Tag: 0x??

![](img/be2cf0737cec89669e7b18813ea2d3b7_585_0.png)

| Hex | Decimal | Binary |
|-----|---------|--------|
| 0   | 0       | 0000   |
| 1   | 1       | 0001   |
| 2   | 2       | 0010   |
| 3   | 3       | 0011   |
| 4   | 4       | 0100   |
| 5   | 5       | 0101   |
| 6   | 6       | 0110   |
| 7   | 7       | 0111   |
| 8   | 8       | 1000   |
| 9   | 9       | 1001   |
| A   | 10      | 1010   |
| B   | 11      | 1011   |
| C   | 12      | 1100   |
| D   | 13      | 1101   |
| E   | 14      | 1110   |
| F   | 15      | 1111   |

Cache size:  
C = S x E x B data bytes
