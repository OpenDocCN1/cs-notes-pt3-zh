
## CPU Clock Rates

Inflection point in computer history when designers hit the “Power Wall”

|  | 1980 | 1990 | 1995 | 2000 | 2003 | 2005 | 2010 | 2010:1980 |
|---|---|---|---|---|---|---|---|---|
| CPU | 8080 | 386 | Pentium | P-III | P-4 | Core 2 | Core i7 | --- |
| Clock rate (MHz) | 1 | 20 | 150 | 600 | 3300 | 2000 | 2500 | 2500 |
| Cycle time (ns) | 1000 | 50 | 6 | 1.6 | 0.3 | 0.50 | 0.4 | 2500 |
| Cores | 1 | 1 | 1 | 1 | 1 | 2 | 4 | 4 |
| Effective cycle time (ns) | 1000 | 50 | 6 | 1.6 | 0.3 | 0.25 | 0.1 | 10,000 |

## The CPU-Memory Gap

The gap widens between DRAM, disk, and CPU speeds.

![](img/b3f8b91675c485f1e811aa092ebbf3d4_1114_0.png)

## The CPU-Memory Gap

The gap widens between DRAM, disk, and CPU speeds.

The key to bridging this CPU-Memory gap is a fundamental property of computer programs known as locality

![](img/b3f8b91675c485f1e811aa092ebbf3d4_1115_0.png)

- Storage technologies and trends
- ✓ Locality
- The memory hierarchy
- Cache memories

## Locality

- **Principle of Locality:** Programs tend to use data and instructions with addresses near or equal to those they have used recently
  - Temporal locality
    - Recently referenced items are likely to be referenced again in the near future
  - Spatial locality
    - Items with nearby addresses tend to be referenced close together in time

![](img/b3f8b91675c485f1e811aa092ebbf3d4_1117_0.png)

![](img/b3f8b91675c485f1e811aa092ebbf3d4_1117_1.png)

## Locality

- All levels of modern computer systems are designed to exploit locality
  - Hardware
    - Cache memory (to speed up main memory accesses)
  - Operating systems
    - Use main memory to speed up virtual address space accesses
    - Use main memory to speed up disk file accesses
  - Application programs
    - Web browsers exploit temporal locality by caching recently referenced documents on a local disk

## Locality

- Locality in the example
  - sum: temporal locality
  - v: spatial locality
    - Stride-1 reference pattern
- Stride-k reference pattern
  - Visiting every k-th element of a contiguous vector
  - As the stride increases, the spatial locality decreases

## Stride-1 reference pattern

```
int sumarrayrows(int a[M][N])
{
    int i, j, sum = 0 ;

    for (i = 0 ; i < M ; i++)
        for ( j = 0 ; j < N ; j++ )
            sum += a[i][j] ;
    return sum ;
}
```

| Address | 0 | 4 | 8 | 12 | 16 | 20 |
|---|---|---|---|---|---|---|
| Contents | a₀₀ | a₀₁ | a₀₂ | a₁₀ | a₁₁ | a₁₂ |
| Access order | 1 | 2 | 3 | 4 | 5 | 6 |

## Stride-N reference pattern

```
int sumarraycols(int a[M][N]) (M=2,N=3)
{
    int i, j, sum = 0 ;

    for (j = 0 ; j < N ; j++)
        for ( i = 0 ; i < M ; i++ )
            sum += a[i][j] ;
    return sum ;
}
```

| Address | 0 | 4 | 8 | 12 | 16 | 20 |
|---|---|---|---|---|---|---|
| Contents | a₀₀ | a₀₁ | a₀₂ | a₁₀ | a₁₁ | a₁₂ |
| Access order | 1 | 3 | 5 | 2 | 4 | 6 |

## Locality

- Locality of the instruction fetch
  - Spatial locality
    - In most cases, programs are executed in sequential order
  - Temporal locality
    - Instructions in loops may be executed many times

## Locality

```
sum = 0;
for (i = 0; i < n; i++)
    sum += a[i];
return sum;
```

- Data references
  - Reference array elements in succession
    Spatial locality
  - Reference variable `sum` each iteration
    Temporal locality
- Instruction references
  - Reference instructions in sequence.
    Spatial locality
  - Cycle through loop repeatedly
    Temporal locality

- Storage technologies and trends
- Locality
- ✓ The memory hierarchy
- Cache memories

## Memory Hierarchy

- Fundamental properties of storage technology and computer software
  - Different storage technologies have widely different access times
  - Faster technologies cost more per byte than slower ones and have less capacity
  - The gap between CPU and main memory speed is widening
  - Well-written programs tend to exhibit good locality
