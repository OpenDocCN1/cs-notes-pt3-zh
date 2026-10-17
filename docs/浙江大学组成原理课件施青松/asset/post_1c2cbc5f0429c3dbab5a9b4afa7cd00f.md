

## Types of buses:

- **processor-memory** (short high speed, custom design)
- **backplane** (high speed, often standardized, e.g., PCI)
- **I/O** (lengthy, different devices, standardized, e.g., SCSI)

Older PCs often use a single bus for processor-to-memory communication, as well as communication between I/O devices and memory.

A separate bus is used for processor-memory traffic. The I/O bus uses a bus adapter to interface to the processor-memory bus.

A separate bus is used for processor-memory traffic. A small number of backplane buses tap into the processor-memory bus.

## Synchronous vs. Asynchronous

- Synchronous bus uses a clock and a synchronous protocol, fast and small but every device must operate at same rate and clock skew requires the bus to be short
- Asynchronous bus doesn't use a clock and instead uses handshaking

## Handshaking protocol

- Our example, which illustrates how asynchronous buses use handshaking, assumes there are three control lines.
  - ReadReq: Used to indicate a read request for memory. The address is put on the data lines at the same time.
  - DataRdy: Used to indicate that data word is now ready on the data lines.
  - Ack: Used to acknowledge the ReadReq or the DataRdy signal of the other party.

❖ **Example:** The asynchronous handshaking consists of seven steps to read a word from memory and receive it in an I/O device.

1. When memory sees the ReadReq line, it reads the address from the data bus, begins the memory read operation, then raises Ack to tell the device that the ReadReq signal has been seen.
2. I/O device sees the Ack line high and releases the ReadReq data lines.
3. Memory sees that ReadReq is low and drops the Ack line.

❖ **Example:** The asynchronous handshaking consists of seven steps to read a word from memory and receive it in an I/O device.

4. When the memory has the data ready, it places the data on the data lines and raises **DataRdy**.
5. The I/O device sees **DataRdy**, reads the data from the bus, and signals that it has the data by raising **ACK**.
6. The memory sees **Ack** signals, drops **DataRdy**, and releases the data lines.
7. Finally, the I/O device, seeing **DataRdy** low, drops the **ACK** line, which indicates that the transmission is completed.

## Obtaining Access to the Bus

- “Without any control, multiple devices desiring to communicate could each try to assert the control and data lines for different transfers!”
- So, a bus master is needed. Bus masters initiate and control all bus requests.
- e.g., processor is always a bus master.
- Example: the initial steps in a bus transaction with a single master (the processor).

> First, the device generates a bus request to indicate to the processor that it wants to use the bus.

The processor responds and generates appropriate bus control signals. For example, if the device wants to perform output from memory, the processor asserts the read request lines to memory.

The processor also notifies the device that its bus request is being processed; as a result, the device knows it can use the bus and places the address for the request on the bus.

## ❖ Bus Arbitration

- 🔗 Deciding which bus master gets to use the bus next
- 🔗 In a bus arbitration scheme, a device wanting to use the bus signals a **bus request** and is later **granted** the bus.
- 🔗 four bus arbitration schemes:
  - ❖ *daisy chain arbitration* (**not very fair**)(p670)
  - ❖ **centralized, parallel arbitration** (*requires an arbiter*), *e.g.,* **PCI**
  - ❖ **self selection**, *e.g.,* **NuBus used in Macintosh**
  - ❖ **collision detection**, *e.g.,* **Ethernet**

## ❖ Two factors in choosing which device to grant the bus:

- **bus priority**
- **fairness**

