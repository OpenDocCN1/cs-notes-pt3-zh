
## Translation Look-aside Buffer (Cont.)

- The TLB is associative, high-speed memory.
- Associative memory – parallel search

| Page # | Frame # |
| --- | --- |
|  |  |
|  |  |
|  |  |
|  |  |

- Address translation (A′, A″)
  - If A′ is in associative register, get frame # out.
  - Otherwise get frame # from page table in memory.

## Paging Hardware With TLB

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_546_0.png)

```text
CPU
logical address
p
d
page number
frame number
TLB
TLB hit
physical address
f
d
p
TLB miss
f
page table
f
f0000...0000
f1111...1111
physical memory
```

## Effective Access Time

- Associative Lookup = ε microsecond
- Assume memory cycle time is τ microsecond
- **Hit ratio** – percentage of times that a page number is found in the associative registers; ratio related to number of associative registers.
- Hit ratio = α
- **Effective Access Time (EAT)**

  EAT = (ε + τ) α + (ε + 2τ)(1 − α)

  = 2τ + ε − τα

- ε=20ns, α=0.8, τ=100ns  EAT=140ns
- ε=20ns, α=0.98, τ=100ns  EAT=122ns

## Memory Protection

- Memory protection implemented by associating protection bit with each frame.
- Normally these bits are kept in the page table.
- **R/W** bit, can define a page to be read-write or read-only.
- *Valid-invalid* bit attached to each entry in the page table:
  - “**valid**” indicates that the associated page is in the process’ logical address space, and is thus a legal page.
  - “**invalid**” indicates that the page is not in the process’ logical address space.

## Shared Pages

- **Shared code**
  - One copy of read-only (**reentrant**) code shared among processes (i.e., text editors, compilers, window systems).
  - Shared code must appear in same location in the logical address space of all processes.
- **Private code and data**
  - Each process keeps a separate copy of the code and data.
  - The pages for the private code and data can appear anywhere in the logical address space.

## 8.5 Structure of Page Table

- Hierarchical Paging
- Hashed Page Tables
- Inverted Page Tables

### Hierarchical Page Tables

- A logical address (on 32-bit machine with 4KB page size) is divided into:
  - a page number consisting of 20 bits.
  - a page offset consisting of 12 bits.
- Break up the logical address space into multiple page tables.
- A simple technique is a two-level page table.
  - the page table itself is also paged
- Since the page table is paged, the page number is further divided into:
  - a 10-bit page number.
  - a 10-bit page offset.

### Two-Level Paging Example

Thus, a logical address is as follows:

| page number | page offset |
| --- | --- |
| $p_1$ + $p_2$ | $d$ |
| 10 + 10 | 12 |

where

$p_1$ is an index into the outer page table, and

$p_2$ is the displacement within the page of the outer page table.

### Address-Translation Scheme

- Address-translation scheme for a two-level 32-bit paging architecture

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_556_0.png)

### Hashed Page Tables

- Common in address spaces > 32 bits.
- Each entry in the hash table contains a linked list of elements that hashed to the same location.
- Each element consists of three fields:
  - (a) The virtual page number
  - (b) The value of the mapped page frame (frame number)
  - (c) A pointer to the next element in the linked list
- The virtual page number is hashed into the hash table.
- The virtual page number is compared to field (a) in this chain searching for a match. If a match is found, the corresponding physical frame is extracted.

### Hashed Page Table

```text
logical address
physical address
hash function
hash table
memory
```

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_558_0.png)
