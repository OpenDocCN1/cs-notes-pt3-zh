
## 2.7.2 Layered Approach

- The operating system is divided into a number of layers (levels), each built on top of lower layers. The bottom layer (layer 0) is the hardware; the highest (layer N) is the user interface.
- An operating-system layer is an implementation of an abstract object that is the encapsulation of data, and of the operations that can manipulate those data.
- With modularity, layers are selected such that each uses functions (or operations) and services of only lower-level layers.

### Supplement: Summary — Layered System Structure

- View the system as a series of levels
- Each level performs a related subset of functions
- Each level relies on the next lower level to perform more primitive functions
- This decomposes a problem into a number of more manageable subproblems

## 2.7.3 Microkernels

- Moves as much from the kernel into “*user*” space.
  - Small operating system core
  - Contains only essential operating-system functions
    - address space
    - interprocess communication (IPC)
    - basic scheduling
- Many services traditionally included in the operating system are now external subsystems
  - device drivers
  - file systems
  - virtual memory manager
  - windowing system
  - security services

- The main function of the microkernel is to provide a communication facility between the client program and the various services that are running in user space.
- Communication takes place between user modules using message passing.

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_147_0.png)

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_147_1.png)

### Benefits of a Microkernel Organization

- **Uniform interface on request made by a process**
  - All services are provided by means of message passing
- **Extensibility**
  - Allows the addition of new services
- **Flexibility**
  - New features added
  - Existing features can be subtracted
- **Portability**
  - Changes needed to port the system to a new processor is changed in the microkernel - not in the other services
- **Reliability**
  - Modular design
  - Small microkernel can be rigorously tested
- **Distributed system support**
  - Messages are sent without knowing what the target machine is
- **Object-oriented operating system**
  - Components are objects with clearly defined interfaces that can be interconnected to form software
- **Detriments:**
  - Performance overhead of user space to kernel space communication

## 2.7.4 Modules

- Most modern operating systems implement kernel modules
  - Uses object-oriented approach
  - Each core component is separate
  - Each talks to the others over known interfaces
  - Each is loadable as needed within the kernel
- Overall, similar to layers but with more flexibility

### Solaris Modular Approach

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_151_0.png)

### A hybrid structure: Mac OS X Structure

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_152_0.png)

| Component | Details |
|---|---|
| application environments and common services | Graphical Interface |
| BSD | CLI, networking, file systems, implementation of POSIX APIs, including Pthreads |
| Mach | Memory management; support for RPC and IPC; message passing; thread scheduling |
| kernel environment | I/O kit for development of device drivers and dynamically loadable modules (kernel extensions) |

## 2.8 Virtual Machines (VM)

- A *virtual machine* takes the layered approach to its logical conclusion. It treats hardware and the operating system kernel as though they were all hardware.
- A virtual machine provides an interface *identical* to the underlying bare hardware.
- The operating system creates the illusion of multiple processes, each executing on its own processor with its own (virtual) memory.
  - By CPU scheduling
  - By virtual memory
