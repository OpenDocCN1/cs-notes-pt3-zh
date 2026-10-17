

## 7.3 Stack-based runtime environments

- For a language, in which
  - Recursive calls are allowed
  - Local variables are newly allocated at each call
  - Activation records cannot be allocated statically.
- Instead, activation records must be allocated in a stack-based fashion.

- The stack of activation records grows and shrinks with the main of calls in the executing program.
- Each procedure may have several different activation records on the call stack at one time.
- More complex strategy for bookkeeping and variable access.

![](img/1db31d392048feae2d803578b3d5a4b9_529_0.png)

![](img/1db31d392048feae2d803578b3d5a4b9_529_1.png)

# Chapter 7 Runtime Environments

![](img/1db31d392048feae2d803578b3d5a4b9_530_0.png)

![](img/1db31d392048feae2d803578b3d5a4b9_530_1.png)

## outline

- Runtime Environment:
- Three kinds of runtime environments:
  - (1) Fully static environment; FORTRAN77
  - (2) stack-based environment; C C++
  - (3) fully dynamic environment; LISP

## 7.1 Memory Organization During Program Execution

- **The memory of a typical computer:**
  - A register area;
  - Addressable Random access memory(RAM):
    - A code area
    - A data area

![](img/1db31d392048feae2d803578b3d5a4b9_532_0.png)

![](img/1db31d392048feae2d803578b3d5a4b9_532_1.png)

The general organization of runtime storage

![](img/1db31d392048feae2d803578b3d5a4b9_533_0.png)

## Procedure activation record

| Space for arguments (parameters) |
| Space for bookkeeping information, including return address |
| Space for local data |
| Space for local temporaries |

Depending on the language, activation records may be allocated in different areas:
- Fortran77 in the static area;
- C and Pascal in the stack area; referred to as stack frames
- LISP in the heap area.

## Processor registers

Processor registers are also part of the structure of the runtime environment.

Special-purpose registers to keep track of execution

- PC program counter;
- SP stack pointer;
- FP frame pointer;
- AP argument pointer

![](img/1db31d392048feae2d803578b3d5a4b9_536_0.png)

## calling sequence

- The allocation of memory for the activation record;
- The computation and storing of the arguments;
- The storing and setting of necessary registers to affect the call

returning sequence

- The placing of the return value where it can be accessed by the caller;
- The readjustment of registers;
- The possible releasing for activation record memory.

![](img/1db31d392048feae2d803578b3d5a4b9_538_0.png)

![](img/1db31d392048feae2d803578b3d5a4b9_538_1.png)

## 7.2 Fully Static Runtime Environments

The entire program memory

| Memory section | Contents |
|---|---|
| Code area | Code for main procedure<br>Code for procedure 1<br>…<br>Code for procedure n |
| | Global data area |
| Data area | Activation record of main procedure<br>Activation record of procedure 1<br>…<br>Activation record of procedure n |

![](img/1db31d392048feae2d803578b3d5a4b9_540_0.png)

![](img/1db31d392048feae2d803578b3d5a4b9_540_1.png)

# The entire program memory

- The global variables and all variables are allocated statically.
- Each procedure has only a single activation record.
- All variables ( local or global) can be accessed directly via fixed address.
- No extra information about the environment needs to be kept in an activation record.

![](img/1db31d392048feae2d803578b3d5a4b9_541_0.png)

![](img/1db31d392048feae2d803578b3d5a4b9_541_1.png)

