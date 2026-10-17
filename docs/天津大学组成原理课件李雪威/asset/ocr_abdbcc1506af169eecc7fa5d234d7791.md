# Example Memory Hierarchy

Smaller, faster, and costlier (per byte) storage devices

Larger, slower, and cheaper (per byte) storage devices

![](bbox=[0.06, 0.048, 0.815, 0.993])

L0:

Regs

CPU registers hold words retrieved from the L1 cache.

L1:

L1 cache
(SRAM)

L1 cache holds cache lines retrieved from the L2 cache.

L2:

L2 cache
(SRAM)

L2 cache holds cache lines retrieved from L3 cache

L3:

L3 cache
(SRAM)

L3 cache holds cache lines retrieved from main memory.

L4:

Main memory
(DRAM)

Main memory holds disk blocks retrieved from local disks.

L5:

Local secondary storage
(local disks)

Local disks hold files retrieved from disks on remote servers

L6:

Remote secondary storage
(e.g., Web servers)