
## Example Uses of MemCheck

```
#include <stdlib.h>

void f(void)
{
    int* x = malloc(10 * sizeof(int));
    x[10] = 0;
}

int main(void)
{
    f();
    return 0;
}
```

```
==19182== Invalid write of size 4
==19182==    at 0x804838F: f (example.c:6)
==19182==    by 0x80483AB: main (example.c:11)
==19182==  Address 0x1BA45050 is 0 bytes after a block of size 40 alloc'd
==19182==    at 0x1B8FF5CD: malloc (vg_replace_malloc.c:130)
==19182==    by 0x8048385: f (example.c:5)
==19182==    by 0x80483AB: main (example.c:11)
```

```
==19182== 40 bytes in 1 blocks are definitely lost in loss record 1 of 1
==19182==    at 0x1B8FF5CD: malloc (vg_replace_malloc.c:130)
==19182==    by 0x8048385: f (a.c:5)
==19182==    by 0x80483AB: main (a.c:11)
```

## Cachegrind: a cache profiler

## Cachegrind

- Cache behavior is crucial
  - L1 misses: ~10 cycles
  - L2 misses: ~200 cycles
- But difficult to predict
- Cachegrind gives three outputs:
  - Total hit/miss counts and ratios (I1, D1, L2)
  - Per-function hit/miss counts (sorted from most to least)
  - Per-line hit/miss counts (source code annotations)
- Source code annotations are the most useful
  - Most fine-grained data
  - Data that programmers can act on to speed up their programs

## Sample output

```
Ir I1mr I2mr    Dr D1mr D2mr    Dw    D1mw    D2mw
------------------------------------------------------------
14,789,396 547 544 6,329,792 751 689 2,111,757 1,113,292 1,094,855 PROGRAM TOTALS

Ir I1mr I2mr    Dr D1mr D2mr    Dw    D1mw    D2mw file:function
------------------------------------------------------------
14,688,273 1 1 6,294,531 0 0 2,098,178 1,113,088 1,094,656 example.c:main

-- Auto-annotated source: example.c
------------------------------------------------------------
Ir I1mr I2mr    Dr D1mr D2mr    Dw    D1mw    D2mw
. . . . . . . . . int main(void)
10 0 0 0 0 0 1 0 0 {
. . . . . . . . . int i, j, a[1024][1024];
4,100 1 1 2,049 0 0 1 0 0 for (i = 0; i < 1024; i++) {
4,198,400 0 0 2,098,176 0 0 1,024 0 0   for (j = 0; j < 1024; j++) {
5,242,880 0 0 2,097,152 0 0 1,048,576 65,536 56,320     a[i][j] = 0;  // fast
5,242,880 0 0 2,097,152 0 0 1,048,576 1,047,552 1,038,336     a[j][i] = 0;  // slow
. . . . . . . . . }
. . . . . . . . . }
1 0 0 0 0 0 0 0 0 return 0;
2 0 0 2 0 0 0 0 0 }
```

## How Cachegrind works

- Each instruction is instrumented
  - Call to a C cache simulation function
  - Different functions for loads, stores, modifies
  - Some combining of C calls for efficiency
- Each source code line gets a *cost centre*
  - Holds counters: accesses, hits and misses
  - Uses debug info to map each instruction to a cost centre
- Online simulation (i.e. no trace gathering)
- Cost centres dumped to file at end
  - Simple but compact text format
  - Post-processing script produces previous slide’s output

## Cache simulation

- Approximates an AMD Athlon hierarchy
  - I1, D1, inclusive L2
  - Write-allocate
  - LRU replacement
- Each cache is command-line configurable:
  - Cache size
  - Line size
  - Associativity
- On x86/AMD64 can use CPUID to auto-detect these parameters
- Simulation can be replaced easily

## Inaccuracies

- Imperfect address trace
  - No kernel code
  - Other processes ignored (arguably good)
  - Conversion to Valgrind’s IR changes a very small number of loads/stores
- Incorrect addresses
  - Virtual addresses
  - Memory layout and thread scheduling is different under Cachegrind compared to native
- Prefetches and cache-bypassing are ignored
  - Difficult to handle well without detailed microarchitectural simulation
- Still useful for general insights

## How is it used?

- Characterization:
  - Program A vs. program B
  - Cache hierarchy A vs. cache hierarchy B
- Optimisation:
  - Identifies cache-unfriendly code
  - Fixing such code requires non-trivial insight
    - But easier (i.e. not impossible!) than fixing without this data
- Evaluation of optimizations:
  - Program A vs. optimized program A
