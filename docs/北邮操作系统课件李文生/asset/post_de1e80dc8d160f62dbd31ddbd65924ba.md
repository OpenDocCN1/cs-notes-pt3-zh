
## Two interrupts request lines

- Nonmaskable, reserved for critical events.
- Maskable, turned off to ignore or delay some interrupts.
- Intel Pentium Processor Event-Vector Table:

| vector number | description |
|---|---|
| 0 | divide error |
| 1 | debug exception |
| 2 | null interrupt |
| 3 | breakpoint |
| 4 | INTO-detected overflow |
| 5 | bound range exception |
| 6 | invalid opcode |
| 7 | device not available |
| 8 | double fault |
| 9 | coprocessor segment overrun (reserved) |
| 10 | invalid task state segment |
| 11 | segment not present |
| 12 | stack fault |
| 13 | general protection |
| 14 | page fault |
| 15 | (Intel reserved, do not use) |
| 16 | floating-point error |
| 17 | alignment check |
| 18 | machine check |
| 19-31 | (Intel reserved, do not use) |
| 32-255 | maskable interrupt |

## Direct Memory Access

- Used to avoid programmed I/O for large data movement
- Requires DMA controller, a special-purpose processor
- Bypasses CPU to transfer data directly between I/O device and memory
  - Host writes a DMA command block into memory
  - CPU writes the address of this command block to the DMA controller
  - DMA controller operates the memory bus directly, placing address on the bus to perform transfers
- DVMA can perform a transfer between two memory-mapped devices without the intervention of the CPU or the use of main memory.

## Six Step Process to Perform DMA Transfer

1. device driver is told to transfer disk data to buffer at address X
2. device driver tells disk controller to transfer C bytes from disk to buffer at address X
3. disk controller initiates DMA transfer
4. disk controller sends each byte to DMA controller
5. DMA controller transfers bytes to buffer X, increasing memory address and decreasing C until C=0
6. when C=0, DMA interrupts CPU to signal transfer completion

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_842_0.png)

## Direct Memory Access (Cont.)

- Takes control of the system from the CPU to transfer data to and from memory over the system bus
- Cycle stealing (周期挪用) is used to transfer data on the system bus
- The instruction cycle is suspended so data can be transferred
- The CPU pauses one bus cycle
- No interrupts occur
  - Do not save context

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_843_0.png)

## 13.3 Application I/O Interface

- I/O system calls encapsulate device behaviors in generic classes
- Devices vary in many dimensions
  - Character-stream or block
  - Sequential or random-access
  - Synchronous or asynchronous
  - Sharable or dedicated
  - Speed of operation
  - read-write, read only, or write only
- Device-driver layer hides differences among I/O controllers from kernel

## A Kernel I/O Structure

software

kernel

Kernel I/O subsystem

SCSI device driver

keyboard device driver

mouse device driver

...

PCI bus device driver

floppy device driver

ATAPI device driver

hardware

SCSI device controller

keyboard device controller

mouse device controller

...

PCI bus device controller

floppy device controller

ATAPI device controller

SCSI device

keyboard

mouse

...

PCI bus

floppy disk drives

ATAPI devices (disks, tapes, drives)

## Characteristics of I/O Devices

| aspect | variation | example |
|---|---|---|
| data-transfer mode | character<br>block | terminal<br>disk |
| access method | sequential<br>random | modem<br>CD-ROM |
| transfer schedule | synchronous<br>asynchronous | tape<br>keyboard |
| sharing | dedicated<br>sharable | tape<br>keyboard |
| device speed | latency<br>seek time<br>transfer rate<br>delay between operations |  |
| I/O direction | read only<br>write only<br>read-write | CD-ROM<br>graphics controller<br>disk |

## Block and Character Devices

- **Block devices include disk drives**
  - Commands include read, write, seek
  - Raw I/O or file-system access
  - Memory-mapped file access possible
- **Character devices include keyboards, mice, serial ports**
  - Commands include `get`, `put`
  - Libraries layered on top allow line editing
