
![](img/b3f8b91675c485f1e811aa092ebbf3d4_939_0.png)

Kernel virtual memory

User stack (created at run time)

Memory mapped region for shared libraries

printf function

sbrk

Run-time heap (created at run time by malloc)

Read/write data

Read-only code and data

0x08048000 (32)
0x00400000 (64)

Memory invisible to user code

Loaded from the hello executable file

## Assumptions

- Assumptions made in this lecture
- memory is word addressed (each word can hold a pointer)

![](img/b3f8b91675c485f1e811aa092ebbf3d4_941_0.png)

## Allocation examples

```
p1 = malloc(4*sizeof(long))
```

```
p2 = malloc(5*sizeof(long))
```

```
p3 = malloc(6*sizeof(long))
```

```
free(p2)
```

```
p4 = malloc(2*sizeof(long))
```

## Requirements

- Handle arbitrary sequence of requests
- Making immediate responses to requests
- Using only the heap
- Aligning blocks
- Not modifying allocated blocks

## Goals

- Given some sequence of malloc and free requests:
- $R_0, R_1, ..., R_k, ..., R_{n-1}$
- Want to maximize throughput and peak memory utilization.
- These goals are often conflicting

## Performance goals: throughput

- Number of completed requests per unit time
- Example:
- 5,00 malloc calls and 5,00 free calls in 1 seconds
- throughput is 1,000 operations/second.

## Performance goals: peak memory utilization

- Given some sequence of malloc and free requests:
- $R_0, R_1, ..., R_k, ..., R_{n-1}$
- Def: aggregate payload $P_k$:
- malloc(p) results in a block with a payload of p bytes.
- After request $R_k$ has completed, the aggregate payload $P_k$ is the sum of currently allocated payloads.

## Performance goals: peak memory utilization

- Def: current heap size is denoted by Hₖ
- Note that Hₖ is monotonically nondecreasing (can be relaxed)
- Def: peak memory utilization:
- After k requests, peak memory utilization is:
- Uₖ = ( maxᵢ≤ₖ Pᵢ ) / Hₖ

## Fragmentation

- Poor memory utilization caused by fragmentation
- Two forms of fragmentation
- Internal fragmentation
- External fragmentation

## Internal Fragmentation

- Internal fragmentation
- For some block, internal fragmentation is the difference between the block size and the payload size

![](img/b3f8b91675c485f1e811aa092ebbf3d4_949_0.png)

## Internal Fragmentation

- Internal fragmentation
- Is caused by overhead of maintaining heap data structures, padding for alignment purposes, or explicit policy decisions (e.g., not to split the block).
- Depends only on the pattern of previous requests, and thus is easy to measure.

## External Fragmentation

- Occurs when there is enough aggregate heap memory, but no single free block is large enough

```
p1 = malloc(4*sizeof(long))
```

```
p2 = malloc(5*sizeof(long))
```

```
p3 = malloc(6*sizeof(long))
```

```
free(p2)
```

```
p4 = malloc(6*sizeof(long))
```

## External Fragmentation

- External fragmentation depends on
- the pattern of future requests
- and thus is difficult to measure

## Implementation Issues

- How do we know how much memory to free just given a pointer?
- How do we keep track of the free blocks?

![](img/b3f8b91675c485f1e811aa092ebbf3d4_953_0.png)

```
free(p0)
```

```
p1 = malloc(1)
```

## Implementation Issues

- What do we do with the extra space when allocating a structure that is smaller than the free block it is placed in?
- How do we pick a block to use for allocation
- many might fit?
- How do we reinsert freed block?

## Knowing how Much to Free

- Standard method
- keep the length of a structure in the word preceding the structure
- This word is often called the header field or header
- requires an extra word for every allocated structure
