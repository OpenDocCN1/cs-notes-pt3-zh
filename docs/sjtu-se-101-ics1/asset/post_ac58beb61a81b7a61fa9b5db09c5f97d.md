
## Line Replacement on Misses

- Check the cache line of the set indicated by the set index bits
  - If the cache line valid, it must be evicted
- Retrieve the requested block from the next level
- Current line is replaced by the newly fetched line

## Check the cache line

=1? If valid bit is set, evict the line

selected set (i):

![](img/b3f8b91675c485f1e811aa092ebbf3d4_1183_0.png)

## Get the Address of the Starting Byte

- Consider memory address looks like the following

![](img/b3f8b91675c485f1e811aa092ebbf3d4_1184_0.png)

- Clear the last bits and get the address A

![](img/b3f8b91675c485f1e811aa092ebbf3d4_1184_1.png)

## Read the Block from the Memory

Put A on the Bus (A is A'000)

![](img/b3f8b91675c485f1e811aa092ebbf3d4_1185_0.png)

## Read the Block from the Memory

Main memory reads A' from the memory bus, retrieves 8 bytes x, and places it on the bus

![](img/b3f8b91675c485f1e811aa092ebbf3d4_1186_0.png)

## Read the Block from the Memory

CPU read x from the bus and copies it into the cache line

![](img/b3f8b91675c485f1e811aa092ebbf3d4_1187_0.png)

## Read the Block from the Memory

Increase A' by 1, and copy y in A'+1 into the cache line. Repeat several times (4 or 8 )

![](img/b3f8b91675c485f1e811aa092ebbf3d4_1188_0.png)

## Cache line, set and block

- **Block**
  - A fixed-sized packet of information
    - Moves back and forth between a cache and main memory (or a lower-level cache)
- **Line**
  - A container in a cache that stores
    - A block, the valid bit, the tag bits
    - Other information
- **Set**
  - A collection of one or more lines

## Direct-mapped cache simulation

Example

M=16 byte addresses

B=2 bytes/block, S=4 sets, E=1 entry/set

t=1 s=2 b=1
x xx x

Address trace (reads):

0 [0000] 1 [0001] 13 [1101] 8 [1000] 0 [0000]

| set | v | tag | data |
|---|---|---|---|
| 0 | 0 |  |  |
| 1 | 0 |  |  |
| 2 | 0 |  |  |
| 3 | 0 |  |  |

## Direct-mapped cache simulation

Example

M=16 byte addresses

B=2 bytes/block, S=4 sets, E=1 entry/set

t=1 s=2 b=1
x xx x

Address trace (reads):

0 [0000] 1 [0001] 13 [1101] 8 [1000] 0 [0000]

miss

(1) 0 [0000] (miss)

| set | v | tag | data |
|---|---|---|---|
| 0 | 1 | 0 | m[0]m[1] |
| 1 | 0 |  |  |
| 2 | 0 |  |  |
| 3 | 0 |  |  |

## Direct-mapped cache simulation

Example

M=16 byte addresses

B=2 bytes/block, S=4 sets, E=1 entry/set

t=1 s=2 b=1
x xx x

Address trace (reads):

0 [0000] 1 [0001] 13 [1101] 8 [1000] 0 [0000]

miss hit

(2) 1 [0001] (hit)

| set | v | tag | data |
|---|---|---|---|
| 0 | 1 | 0 | m[0]m[1] |
| 1 | 0 |  |  |
| 2 | 0 |  |  |
| 3 | 0 |  |  |

## Direct-mapped cache simulation

Example

M=16 byte addresses

B=2 bytes/block, S=4 sets, E=1 entry/set

t=1 s=2 b=1
x xx x

Address trace (reads):

0 [0000] 1 [0001] 13 [1101] 8 [1000] 0 [0000]

miss hit miss

(3) 13 [1101] (miss)

| set | v | tag | data |
|---|---|---|---|
| 0 | 1 | 0 | m[0]m[1] |
| 1 | 0 |  |  |
| 2 | 1 | 1 | m[12]m[13] |
| 3 | 0 |  |  |

## Direct-mapped cache simulation

Example

M=16 byte addresses

B=2 bytes/block, S=4 sets, E=1 entry/set

t=1 s=2 b=1
x xx x

Address trace (reads):

0 [0000] 1 [0001] 13 [1101] 8 [1000] 0 [0000]

miss hit miss miss

(4) 8 [1000] (miss)

| set | v | tag | data |
|---|---|---|---|
| 0 | 1 | 1 | m[8]m[9] |
| 1 | 0 |  |  |
| 2 | 1 | 1 | m[12]m[13] |
| 3 | 0 |  |  |

## Direct-mapped cache simulation

Example

M=16 byte addresses

B=2 bytes/block, S=4 sets, E=1 entry/set

t=1 s=2 b=1
x xx x

Address trace (reads):

0 [0000] 1 [0001] 13 [1101] 8 [1000] 0 [0000]

miss hit miss miss miss

(5) 0 [0000] (miss)

| set | v | tag | data |
|---|---|---|---|
| 0 | 1 | 0 | m[0]m[1] |
| 1 | 0 |  |  |
| 2 | 1 | 1 | m[12]m[13] |
| 3 | 0 |  |  |

## Direct-mapped cache simulation

Example

M=16 byte addresses

B=2 bytes/block, S=4 sets, E=1 entry/set

t=1 s=2 b=1
x xx x

Address trace (reads):

0 [0000] 1 [0001] 13 [1101] 8 [1000] 0 [0000]
miss hit miss miss miss

(5) 0 [0000] (miss)

Thrashing!

| set | v | tag | data |
|---|---|---|---|
| 0 | 1 | 0 | m[0]m[1] |
| 1 | 0 |  |  |
| 2 | 1 | 1 | m[12]m[13] |
| 3 | 0 |  |  |
