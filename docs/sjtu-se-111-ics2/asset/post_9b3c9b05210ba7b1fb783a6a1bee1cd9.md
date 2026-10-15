
## Page tables Translation

| VPN 1 | VPN 2 | VPN 3 | VPN 4 | VPO |
|---|---|---|---|---|
| 9     | 9     | 9     | 9     | 12  |

![](img/9bd5f6161cb6607b56d2fb964d1b8794_1019_0.png)

CR3

Physical address of L1 PT

L1 PT: Page global directory

- L1 PTE
  - 512 GB region per entry

L2 PT: Page upper directory

- L2 PTE
  - 1 GB region per entry

L3 PT: Page middle directory

- L3 PTE
  - 2 MB region per entry

L4 PT: Page directory

- L4 PTE
  - 4 KB region per entry

Virtual address

- Offset into physical and virtual page
- physical address of page

Physical address

| PPN | PPO |
|---|---|
| 40  | 12  |

## Cute Trick for Speeding Up L1 Access

![](img/9bd5f6161cb6607b56d2fb964d1b8794_1020_0.png)

### Observation

- Bits that determine CI identical in virtual and physical address
- Can index into cache while address translation taking place
- Generally we hit in TLB, so PPN bits (CT bits) available next
- "Virtually indexed, physically tagged"
- Cache carefully sized to make this possible

## Linux Virtual Memory System

- Different for each process:
  - Process-specific data structures (e.g., task and mm structs, page tables, kernel stack)
- Identical for each process:
  - Physical memory
  - Kernel code and data
  - Kernel virtual memory
- Process virtual memory:
  - User stack (%esp)
  - Memory mapped region for shared libraries
  - brk
  - Run-time heap (via malloc)
  - Uninitialized data (.bss)
  - Initialized data (.data)
  - Program text (.text)
  - 0x08048000 (32)
  - 0x40000000 (64)

## Virtual Memory

## Outline

- Memory Mapping
- Suggested reading: 10.7, 10.8

## Linux Virtual Memory System

- Process-specific data structures (e.g., task and mm structs, page tables, kernel stack)
- Different for each process
- Physical memory
- Identical for each process
- Kernel code and data
- Kernel virtual memory
- User stack
- %esp
- Memory mapped region for shared libraries
- brk
- Run-time heap (via malloc)
- Uninitialized data (.bss)
- Initialized data (.data)
- Program text (.text)
- 0x08048000 (32)
- 0x40000000 (64)
- Process virtual memory

## Linux organizes VM as a collection of "areas"

- pgd:
  - page directory address
- vm_prot:
  - read/write permissions for this area
- vm_flags:
  - shared with other processes or private to this process

![](img/9bd5f6161cb6607b56d2fb964d1b8794_1026_0.png)

## Linux page fault handling

- process virtual memory
- vm_area_struct:
  - vm_end
  - vm_start
  - r/o
  - vm_next
- shared libraries:
  - vm_end
  - vm_start
  - r/w
  - vm_next
- data:
  - vm_end
  - vm_start
  - r/o
  - vm_next
- text:
  - read
  - read
  - write

- Is the VA legal?
  - i.e., is it in an area defined by a vm_area_struct?
  - if not, then signal segmentation violation (e.g., (1))

![](img/9bd5f6161cb6607b56d2fb964d1b8794_1028_0.png)

- Is the operation legal?
  - i.e., can the process read/write this area?
  - if not, then signal protection violation (e.g., (2))

![](img/9bd5f6161cb6607b56d2fb964d1b8794_1029_0.png)

- If OK, handle fault
  - e.g., (3)

## Memory mapping

- Dirty pages are copied back and forth between memory and a special swap file.

## Demand Paging

- _Key point_: no virtual pages are copied into physical memory until they are referenced!
  - known as "demand paging"
  - crucial for time and space efficiency

## Exec() revisited

- To run a new program p in the current process using exec():
  - Free all vm_area_structs and page tables for old areas.
- process-specific data structures (page tables, task and mm structs, kernel stack)
- physical memory
- kernel code/data
- stack
- Memory mapped region for shared libraries
- runtime heap (via malloc)
- uninitialized data (.bss)
- initialized data (.data)
- program text (.text)
- forbidden
- same for each process
- 0xc0000000
- %esp
- brk
- kernel VM
- process VM
- demand-zero
- demand-zero
- .data
- .text
- libc.so
- .data
- .text
- p
