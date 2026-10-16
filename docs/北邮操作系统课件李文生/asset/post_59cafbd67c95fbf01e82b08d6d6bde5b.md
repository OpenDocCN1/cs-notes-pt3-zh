
## Swap-space Use

- Depending on the memory-management algorithms in use.
  - Use swap space to hold an entire process image
  - Store pages that have been pushed out of memory
- The amount of swap space needed depends on
  - the amount of physical memory
  - the amount of virtual memory it is backing
  - the way in which the virtual memory is used

## Swap-space Location

- A swap space can reside in one of two places:
  - Carved out of the normal file system, a large file
  - In a separate disk partition, raw partition
- A large file
  - Normal file-system routines can be used to create it, name it, and allocate its space.
  - Inefficient
- Raw partition
  - Swap-space storage manager allocates and deallocates
  - A fixed amount of swap space is created during disk partitioning; adding more swap space requires repartitioning the disk.

## Swap-space management

- 4.3BSD allocates swap space when a process starts; holds *text segment* (the program) and *data segment*.
- Kernel uses *swap maps* to track swap-space use.
- Solaris 2 allocates swap space only when a page is forced out of physical memory, not when the virtual memory page is first created.

## Data Structures for Swapping on Linux Systems

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_825_0.png)

## Homework (page 48)

- 12.2

## Thinking:

12.1

## Chapter 13 I/O Systems

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_827_0.png)

Teaching hours: 2h

## Strong points:

- I/O Hardware
- Application I/O Interface, Kernel I/O Subsystem
- Transforming I/O Requests to Hardware Operations

## Chapter Objectives

- Explore the structure of an operating system’s I/O subsystem
- Discuss the principles of I/O hardware and its complexity
- Provide details of the performance aspects of I/O hardware and software

## Contents

- 13.1 Overview
- 13.2 I/O Hardware
- 13.3 Application I/O Interface
- 13.4 Kernel I/O Subsystem
- 13.5 Transforming I/O Requests to Hardware Operations
- 13.6\* Streams
- 13.7\* Performance

## 13.1 Overview

- Incredible variety of I/O devices
- Two trends
  - Increasing standardization of software and hardware interfaces
  - Increasingly broad variety of I/O devices

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_830_0.png)

## A Typical PC Bus Structure

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_831_0.png)

## I/O device control

- Processor gives commands and data to a controller to accomplish an I/O transfer.
- I/O instructions control devices
- Devices have addresses, used by
  - Direct I/O instructions
  - Memory-mapped I/O

## Device I/O Port Locations on PCs (partial)

| I/O address range (hexadecimal) | device |
|---|---|
| 000-00F | DMA controller |
| 020-021 | interrupt controller |
| 040-043 | timer |
| 200-20F | game controller |
| 2F8-2FF | serial port (secondary) |
| 320-32F | hard-disk controller |
| 378-37F | parallel port |
| 3D0-3DF | graphics controller |
| 3F0-3F7 | diskette-drive controller |
| 3F8-3FF | serial port (primary) |

## I/O port

- **4 registers**
  - Status: contains bits that can be read by the host. Idle, busy, ready, error
  - Control: can be written by the host to start a command or to change the mode of a device.
  - Data-in: read by the host to get input
  - Data-out: written by the host to send output

Data registers are typically 1 to 4 bytes in size.

Some controllers have FIFO chips to expand the capacity of the controller beyond the size of the data register. FIFO chips can hold several bytes of input or output data.

## Techniques for Performing I/O

- **Programmed I/O**
  - Processor is busy-waiting for the operation to complete
- **Interrupt-driven I/O**
  - I/O command is issued
  - Processor continues executing instructions
  - I/O module sends an interrupt when done
- **Direct Memory Access (DMA)**
  - DMA module controls exchange of data between main memory and the I/O device
  - Processor is interrupted only after the entire block has been transferred

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_836_0.png)
