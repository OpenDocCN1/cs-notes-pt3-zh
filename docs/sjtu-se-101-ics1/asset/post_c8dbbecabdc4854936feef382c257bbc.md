
## General Cache Concepts: Miss

![](img/b3f8b91675c485f1e811aa092ebbf3d4_1139_0.png)

Request: 12

Data in block b is needed

Block b is not in cache:

**Miss!**

Block b is fetched from memory

Block b is stored in cache

- **Placement policy:** determines where b goes
- **Replacement policy:** determines which block gets evicted (victim)

## Types of Cache Misses

- Cold (compulsory) miss
  - Cold misses occur because the cache is empty.
- Capacity miss
  - Occurs when the set of active cache blocks (working set) is larger than the cache.
- Conflict miss
  - Most caches limit blocks at level k+1 to a small subset (sometimes a singleton) of the block positions at level k.
    - e.g. Block i at level k+1 must be placed in block (i mod 4) at level k.
  - Conflict misses occur when the level k cache is large enough, but multiple data objects all map to the same level k block.
    - e.g. Referencing blocks 0, 8, 0, 8, 0, 8, ... would miss every time.

## Cache Memory

- History
  - At the very beginning, 3 levels
    - Registers, main memory, disk storage
  - 10 years later, 4 levels
    - Registers, SRAM cache, main DRAM memory, disk storage
  - Modern processor, 5~6 levels
    - Registers, SRAM L1, L2(,L3) cache, main DRAM memory, disk storage
  - Cache memories
    - small, fast SRAM-based memories
    - managed by hardware automatically
    - can be on-chip, on-die, off-chip

## Examples of Caching in the Hierarchy

| Cache Type | What is Cached? | Where is it Cached? | Latency (cycles) | Managed By |
|---|---|---|---|---|
| Registers | 4-8 byte words | CPU core | 0 | Compiler |
| TLB | Address translations | On-Chip TLB | 0 | Hardware |
| L1 cache | 64-byte block | On-Chip L1 | 1 | Hardware |
| L2 cache | 64-byte block | On/Off-Chip L2 | 10 | Hardware |
| Virtual Memory | 4-KB page | Main memory | 100 | Hardware + OS |
| Buffer cache | Parts of files | Main memory | 100 | OS |
| Disk cache | Disk sectors | Disk controller | 100,000 | Disk firmware |
| Network buffer cache | Parts of files | Local disk | 10,000,000 | AFS/NFS client |
| Browser cache | Web pages | Local disk | 10,000,000 | Web browser |
| Web cache | Web pages | Remote server disks | 1,000,000,000 | Web proxy server |

- Storage technologies and trends
- Locality
- The memory hierarchy
- ✓ Cache memories

## Cache Memory

- CPU looks first for data in L1, then in L2, then in main memory
  - Hold frequently accessed blocks of main memory in caches

CPU chip

![](img/b3f8b91675c485f1e811aa092ebbf3d4_1145_0.png)

## Inserting an L1 cache between the CPU and main memory

The transfer unit between the CPU register file and the cache is a **4-byte** block.

The tiny, very fast CPU register file has room for four 4-byte words.

The small, fast L1 cache has room for two 8-word blocks.

The transfer unit between the cache and main memory is an **8-word** block (32 bytes).

The big, slow main memory has room for many 8-word blocks.

![](img/b3f8b91675c485f1e811aa092ebbf3d4_1146_0.png)

## Generic Cache Memory Organization

The cache is an array of sets.

Each set contains one or more lines.

Each line holds a block of data.

```
1 valid bit per line
tag bits per line
B = 2^b bytes per cache block

S = 2^s sets

set 0:
  valid tag 0 1 ... B-1
  ...
  valid tag 0 1 ... B-1
  E lines per set

set 1:
  valid tag 0 1 ... B-1
  ...
  valid tag 0 1 ... B-1

set S-1:
  valid tag 0 1 ... B-1
  ...
  valid tag 0 1 ... B-1
```

## Cache Memory

### Fundamental parameters

| Parameters | Descriptions |
|---|---|
| S = 2^s | Number of sets |
| E | Number of lines per set |
| B = 2^b | Block size (bytes) |
| m = log₂(M) | Number of physical (main memory) address bits |

### Derived quantities

| Parameters | Descriptions |
|---|---|
| M = 2^m | Maximum number of unique memory addresses |
| s = log₂(S) | Number of set index bits |
| b = log₂(B) | Number of block offset bits |
| t = m - (s + b) | Number of tag bits |
| C = B × E × S | Cache size (bytes) not including overhead such as the valid and tag bits |
