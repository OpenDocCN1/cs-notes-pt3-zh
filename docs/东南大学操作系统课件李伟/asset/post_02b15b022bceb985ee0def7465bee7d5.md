
## Secondary-Storage Management

- **Activities for disk management**
  - Free space management
  - Storage allocation
  - Disk scheduling

## I/O System Management

- Hiding the peculiarities of specific hardware devices from the user
- The I/O subsystem consists of
  - A memory-management component including buffer, caching, spooling
  - A general device-driver interface
  - Drivers for specific hardware devices

## Outline

- Operating System Functions
- Operating System Services
- Operating System Interfaces
- Operating System Structure
- Operating System Design and Implementation

## Operating System Services(1/2)

### Services for helping Users

- **Program execution** – system capability to load a program into memory and to run it.
- **I/O operations** – since user programs cannot execute I/O operations directly, the operating system must provide some means to perform I/O.
- **File-system manipulation** – program capability to read, write, create, and delete files.
- **Communications** – exchange of information between processes (*shared memory* or *message passing*)
- **Error detection** – ensure correct computing by detecting errors in hardwares or in user programs.

## Operating System Services(2/2)

- **Services for ensuring system operations**
  - **Resource allocation** – allocating resources to multiple users or multiple jobs running at the same time.
  - **Accounting** – keep track of which users use how much and what kinds of computer resources.
  - **Protection** – ensuring that all access to system resources is controlled and recording all the connections for detection of break-ins.

## Outline

- Operating System Functions
- Operating System Services
- **Operating System Interfaces**
- Operating System Structure
- Operating System Design and Implementation

## Operating System Interfaces(1/3)

- **Interfaces to Users**
  - **Command-Line Interface** – text commands
  - **Batch Interface** – files including some commands
  - **Graphical User Interface** – window system
    - Mouse-based window and menu
  - Many systems now include both CLI and GUI interfaces
    - **Microsoft Windows** is GUI with CLI “command” shell
    - **Apple Mac OS X** as “Aqua” GUI interface with UNIX kernel underneath and shells available
    - **Linux** is CLI with optional GUI interfaces (Java Desktop, KDE)

## Operating System Interfaces(2/3)

- Command-line Interpreter (Shell)
  - The program that reads and interprets control statements
  - DOS OS: command.com
- Two ways to implement commands
  - Internal Command: The command interpreter itself contains the code to execute the command. (dir, copy)
  - External Command: System programs implement most commands. (fdisk, format)

## Operating System Interfaces(3/3)

- Interfaces to Programmes
  - System calls
    - Typically written in assembly-language instructions or a high-level language (C or C++)
    - Mostly accessed by programs via a high-level Application Program Interface (API) rather than direct system call use

## Example of System Calls

System call sequence to copy the contents of one file to another file

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_90_0.png)

- Example System Call Sequence
- Acquire input file name
- Write prompt to screen
- Accept input
- Acquire output file name
- Write prompt to screen
- Accept input
- Open the input file
- if file doesn't exist, abort
- Create output file
- if file exists, abort
- Loop
- Read from input file
- Write to output file
- Until read fails
- Close output file
- Write completion message to screen
- Terminate normally

## System Call Implementation

- **System-call Interface (SCI)**
  - Typically, a number associated with each system call
  - System-call interface maintains a table indexed according to these numbers
  - The system call interface invokes intended system call in OS kernel and returns status of the system call and any return values
