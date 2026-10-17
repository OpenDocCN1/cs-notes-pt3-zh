
## Inspiration for RAID 4

- RAID 3 relies on parity disk to discover errors on read
- But every sector has an error detection field
- Rely on error detection field to catch errors on read, not on the parity disk
- Allows independent reads to different disks simultaneously

## RAID 4: High I/O Rate Parity

Inside of 5 disks

Example: small read D0 & D5, large write D12-D15

| D0 | D1 | D2 | D3 | P |
|---|---|---|---|---|
| D4 | D5 | D6 | D7 | P |
| D8 | D9 | D10 | D11 | P |
| D12 | D13 | D14 | D15 | P |
| D16 | D17 | D18 | D19 | P |
| D20 | D21 | D22 | D23 | P |

Increasing Logical Disk Address

Stripe

Disk Columns

## Inspiration for RAID 5

- RAID 4 works well for small reads
- Small writes (write to one disk):
  - Option 1: read other data disks, create new sum and write to Parity Disk
  - Option 2: since P has old sum, compare old data to new data, add the difference to P
- Small writes are limited by Parity Disk: writes to D0 and D5 both also write to P disk

![](img/273e5640629250d9497f523c984c99c0_464_0.png)

## RAID 5: High I/O Rate Interleaved Parity

Independent writes possible because of interleaved parity

Example: write to D0, D5 uses disks 0, 1, 3, 4

![](img/273e5640629250d9497f523c984c99c0_465_0.png)

Increasing Logical Disk Addresses

Disk Columns

## Problems of Disk Arrays: Small Writes

### RAID-5: Small Write Algorithm

1 Logical Write = 2 Physical Reads + 2 Physical Writes

D0' new data
old data (1. Read)
old parity (2. Read)
XOR XOR
D0 D1 D2 D3 P
D0' D1 D2 D3 P'
(3. Write) (4. Write)

## Summary: RAID Techniques: Goal was performance, popularity due to reliability of storage

- Disk Mirroring, Shadowing (RAID 1)
  - Each disk is fully duplicated onto its "shadow"
  - Logical write = two physical writes
  - 100% capacity overhead
- Parity Data Bandwidth Array (RAID 3)
  - Parity computed horizontally
  - Logically a single high data bw disk
- High I/O Rate Parity Array (RAID 5)
  - Interleaved parity blocks
  - Independent reads and writes
  - Logical write = 2 reads + 2 writes

![](img/273e5640629250d9497f523c984c99c0_468_0.png)

## 8.3 Networks *(skim)*

Key characteristics of typical networks include the following

- **Distance:** 0.01 to 10,000 kilometers
- **Speed:** 0.001MB/sec to 100MB/sec
- **Topology:** Bus, ring, star, tree
- **Shared lines:** None (point-to-point) or shared (multidrop)

- Local area network (LAN) **e.g., Ethernet**
- Packet-switched networks, which are common in long-haul networks
  - **e.g., ARPANET**
- TCP/IP is the key to interconnecting different networks
- The bandwidths of networks are probably growing faster than the bandwidth of any other type of device at present.

## 8.4 Buses and Other Connections between Processors, Memory, and I/O Devices

- Shared communication link (one or more wires)
- Difficult design:
  - may be a bottleneck
  - length of the bus
  - number of devices
  - tradeoffs (fast bus accesses and high bandwidth)
  - support for many different devices
  - cost

### A bus contains two types of lines

- **Control lines**, which are used to signal requests and acknowledgments, and to indicate what types of information are on the data lines.
- **Data lines**, which carry information (**e.g., data, addresses, and complex commands**) between the source and the destination.

### Bus transaction

- Includes two parts: sending the address and receiving or sending the data
- Two operations:
  - **input**: inputting data from the device to memory
  - **output**: outputting data to a device from memory

### The steps of an output operation

1. Initiate a read from memory. Control lines signal a read request to memory, while the data lines contain the address.
2. Memory accesses the data.
3. Memory transfers data and signals data is available. The device stores data as it appears on the bus.

![](img/273e5640629250d9497f523c984c99c0_473_0.png)
