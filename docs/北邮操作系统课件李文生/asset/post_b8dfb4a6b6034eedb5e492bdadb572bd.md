
## Network Devices

- Varying enough from block and character to have own interface
- Unix and Windows NT/9x/2000 include socket interface
  - Separates network protocol from network operation
  - The system calls in the socket interface enable an application
    - To create a socket
    - To connect a local socket to a remote address
    - To listen for any remote application to plug into the local socket
    - To send and receive packets over the connection
  - Includes select functionality: manages a set of sockets
- Approaches vary widely (pipes, FIFOs, streams, queues, mailboxes)

## Clocks and Timers

- Provide current time, elapsed time, timer
- If programmable interval time used for timings, periodic interrupts
- `ioctl` (on UNIX) covers odd aspects of I/O such as clocks and timers

## Blocking and Nonblocking I/O

- **Blocking - process suspended until I/O completed**
  - Easy to use and understand
  - Insufficient for some needs
- **Nonblocking - I/O call returns as much as available**
  - User interface, data copy (buffered I/O)
  - Overlap; Implemented via multi-threading
  - Returns quickly with count of bytes read or written
- **Asynchronous - process runs while I/O executes**
  - Difficult to use
  - I/O subsystem signals process when I/O completed

## Two I/O Methods

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_851_0.png)

Synchronous

Asynchronous

## 13.4 Kernel I/O Subsystem

Services provided by kernel I/O subsystem:

- Scheduling
- Buffering
- Caching
- Spooling
- device reservation
- error handling

## I/O Scheduling

- Some I/O request ordering via per-device queue
- Some OSs try fairness

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_853_0.png)

## Sun Enterprise 6000 Device-Transfer Rates

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_854_0.png)

## caching

- Caching - fast memory holding copy of data
  Key to performance
- difference between a buffer and a cache
  - A buffer may hold the only existing copy of a data item.
  - A cache just holds a copy on faster storage of an item that resides elsewhere.
- Sometimes, a region of memory can be used for both purposes.

## Spooling

- **Spooling - hold output for a device**
  - If device can serve only one request at a time
  - i.e., Printing

## Device reservation

- **Device reservation(预约) - provides exclusive access to a device**
  - System calls for allocation and deallocation
  - Watch out for deadlock

## Error Handling

- OS can recover from disk read, device unavailable, transient write failures
- Most return an error number or code when I/O request fails
- System error logs hold problem reports

## I/O Protection

- User process may accidentally or purposefully attempt to disrupt normal operation via illegal I/O instructions
  - All I/O instructions defined to be privileged
  - I/O must be performed via system calls
    - Memory-mapped and I/O port memory locations must be protected too

## Use of a System Call to Perform I/O

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_861_0.png)

## Kernel Data Structures

- Kernel keeps state information for I/O components, including open file tables, network connections, character device state
- Many, many complex data structures to track buffers, memory allocation, “dirty” blocks
- Some use object-oriented methods and message passing to implement I/O

## UNIX I/O Kernel Structure

user-process memory

file descriptor

per-process open-file table

kernel memory

System-wide open-file table

file-system record
inode pointer
pointer to read and write functions
pointer to select function
pointer to ioctl function
pointer to close function

active-inode table

networking (socket) record
pointer to network info
pointer to read and write functions
pointer to select function
pointer to ioctl function
pointer to close function

network-Information table
