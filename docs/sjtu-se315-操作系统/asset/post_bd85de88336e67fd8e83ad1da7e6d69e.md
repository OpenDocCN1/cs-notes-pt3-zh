
## Operating System Meets Multicore

(Operating) systems 20 years ago

- Enjoys the free lunch provided by hardware (Moore’s Law)
- Recall the Andy-Bill’s Law

Multicore: ending the free lunch!

- Software must evolve with hardware changes

OS: a vital role to bridge the gap between apps and hardware

- Need to evolve itself with multicore
- Need to evolve for apps with multicore

## What is scalability?

Application does N times as much work on N cores as it could on 1 core

Scalability may be limited by Amdahl's Law:

Locks, shared data structures, ... Shared hardware
(DRAM, NIC, ...)

1 / ((1 - P) + P/S)

![](img/53ee1e3b0eba43505c7d530851f32f6f_31_0.png)

## Motivating example: file descriptors

## Ideal FD performance graph

## Actual FD performance

![](img/53ee1e3b0eba43505c7d530851f32f6f_32_0.png)

![](img/53ee1e3b0eba43505c7d530851f32f6f_32_1.png)

## Why throughput drops?

![](img/53ee1e3b0eba43505c7d530851f32f6f_33_0.png)

```
fd_alloc(void) {
    lock(fd_table);
    fd = get_free_fd();
    set_fd_used(fd);
    fix_smallest_fd()
    unlock(fd_table);
}
```

Load fd_table data from L1 in 3 cycles.

## Off-the-shelf 48-core server

6 core x 8 chip AMD

![](img/53ee1e3b0eba43505c7d530851f32f6f_35_0.png)

## Scale Up OS

- Better abstraction to user applications
- Eliminating non-scalable synchronization
- Minimize sharing of common data structures
- You will fill this..

## Issue#2: Security & Privacy

## Security

![](img/53ee1e3b0eba43505c7d530851f32f6f_38_0.png)

![](img/53ee1e3b0eba43505c7d530851f32f6f_38_1.png)

From Wikipedia:

Security is the degree of resistance to, or protection from, harm

## Why Operating System matters?

Operating system (including hypervisors) lies in the lowest levels in a computer

How could you protect your application & data without properly protect your OS

## Example: The do_brk() Bug

```
Asmlinkage unsigned long sys_brk(unsigned long brk) {
...
/* OK, looks good – let it rip. */
-if (do_mmap(NULL, oldbrk, newbrk-oldbrk,
-PRO T_READ|PROT_WRITE|PROT_EXEC,
-MAP_FIXED|MAP_PRIVATE, 0) != oldbrk)
+if (do_brk(oldbrk, newbrk-oldbrk) != oldbrk)
goto out;
```

- do_mmap() checked things properly, do_brk() removed almost all checking
- Purpose of do_brk() was to speed up anonymous mmap s from sys_brk()

## The do_brk() Fix

```
if (!len)
return addr;
```

```
+ if ((addr + len)) > TASK_SIZE || (addr + len) < addr
+ return -EINVAL;
+
```

- The TASK_SIZE is typically set to 0xc0000000, the start of kernel memory

## Issue#3: Power Efficiency

## Power Efficiency

Greener World, Better Life!

Again, why it has to do with OS?

OS control every computer and many devices!

Thus determines the power used by each computer

![](img/53ee1e3b0eba43505c7d530851f32f6f_42_0.png)

## Google Datacenter: Finland

![](img/53ee1e3b0eba43505c7d530851f32f6f_43_0.png)

## Power Breakdown in Server

| Component | Peak Power | Count | Total |
|---|---|---|---|
| CPU [16] | 40 W | 2 | 80 W |
| Memory [18] | 9 W | 4 | 36 W |
| Disk [24] | 12 W | 1 | 12 W |
| PCI slots [22] | 25 W | 2 | 50 W |
| Motherboard | 25W | 1 | 25 W |
| Fan | 10 W | 1 | 10 W |
| System Total |  |  | 213 W |

Table 1: Component peak power breakdown for a typical server

12 Variable Speed Fans

![](img/53ee1e3b0eba43505c7d530851f32f6f_45_0.png)

138 Air Dampers

![](img/53ee1e3b0eba43505c7d530851f32f6f_45_1.png)

312 Light Relays

![](img/53ee1e3b0eba43505c7d530851f32f6f_45_2.png)

> 6,000 Sense and Control Points

50 Electrical Sub-meters

![](img/53ee1e3b0eba43505c7d530851f32f6f_45_3.png)

151 Temperature Sensors

![](img/53ee1e3b0eba43505c7d530851f32f6f_45_4.png)

![](img/53ee1e3b0eba43505c7d530851f32f6f_45_5.png)

## Why Operating System Matters?

Dynamic voltage and frequency scaling
Adjust the frequency of CPU according to workload

Power off devices to save power
Like disk, LCD, or even memory

Problem: energy consumption doesn’t scale with workloads
Static power, leakage power

New!: Near Threshold Voltage
