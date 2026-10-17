
## Intel x86 Processors

- **Dominate laptop/desktop/server market**

- **Evolutionary design**
  - Backwards compatible up until 8086, introduced in 1978
  - Added more features as time goes on
    - Now 3 volumes, about 5,000 pages of documentation

- **Complex instruction set computer (CISC)**
  - Many different instructions with many different formats
    - But, only a small subset encountered with Linux programs
  - Hard to match performance of Reduced Instruction Set Computer (RISC)
  - But, Intel has done just that!
    - In terms of speed. Less so for low power.

## Intel x86 Processors, cont.

### Machine Evolution

| Processor | Year | Transistors |
|-----------|------|-------------|
| 386 | 1985 | 0.3M |
| Pentium | 1993 | 3.1M |
| Pentium/MMX | 1997 | 4.5M |
| Pentium Pro | 1995 | 6.5M |
| Pentium III | 1999 | 8.2M |
| Pentium 4 | 2000 | 42M |
| Core 2 Duo | 2006 | 291M |
| Core i7 | 2008 | 731M |

![](img/be2cf0737cec89669e7b18813ea2d3b7_149_0.png)

### Added Features

- Instructions to support multimedia operations
- Instructions to enable more efficient conditional operations
- Transition from 32 bits to 64 bits
- More cores

### Past Generations

- 1st Pentium Pro 1995
- 1st Pentium III 1999
- 1st Pentium 4 2000
- 1st Core 2 Duo 2006

### Recent Generations

1. Nehalem 2008
2. Sandy Bridge 2011
3. Ivy Bridge 2012
4. Haswell 2013
5. Broadwell 2014
6. Skylake 2015
7. Kaby Lake 2016

### Upcoming Generations

- Cannonlake 2017?

#### Process technology

- 600 nm
- 250 nm
- 180 nm
- 65 nm

- 45 nm
- 32 nm
- 22 nm
- 22 nm
- 14 nm
- 14 nm
- 14 nm

- 10 nm

> Process technology dimension = width of narrowest wires (10 nm ≈ 100 atoms wide)

Bryant and O’Hallaron, Computer Systems: A Programmer’s Perspective, Third Edition

## x86 Clones: Advanced Micro Devices (AMD)

### Historically

- AMD has followed just behind Intel
- A little bit slower, a lot cheaper

### Then

- Recruited top circuit designers from Digital Equipment Corp. and other downward trending companies
- Built Opteron: tough competitor to Pentium 4
- Developed x86-64, their own extension to 64 bits

### Recent Years

- Intel got its act together
  - Leads the world in semiconductor technology
- AMD has fallen behind
  - Relies on external semiconductor manufacturer

## Intel’s 64-Bit History

### 2001: Intel Attempts Radical Shift from IA32 to IA64

- Totally different architecture (Itanium)
- Executes IA32 code only as legacy
- Performance disappointing

### 2003: AMD Steps in with Evolutionary Solution

- x86-64 (now called “AMD64”)

### Intel Felt Obligated to Focus on IA64

- Hard to admit mistake or that AMD is better

### 2004: Intel Announces EM64T extension to IA32

- Extended Memory 64-bit Technology
- Almost identical to x86-64!

### All but low-end x86 processors support x86-64

- But, lots of code still runs in 32-bit mode

## Our Coverage

- **IA32**
  - The traditional x86
  - For 15/18-213: RIP, Summer 2015

- **x86-64**
  - The standard
  - `shark> gcc hello.c`
  - `shark> gcc -m64 hello.c`

- **Presentation**
  - Book covers x86-64
  - Web aside on IA32
  - We will only cover x86-64

## Today: Machine Programming I: Basics

- History of Intel processors and architectures
- Assembly Basics: Registers, operands, move
- Arithmetic & logical operations
- C, assembly, machine code

## Levels of Abstraction

C programmer

C code

Nice clean layers, but beware...

Assembly programmer

Computer Designer

Caches, clock freq, layout, ...

Of course, you know that: It’s why you are taking this course.

![](img/be2cf0737cec89669e7b18813ea2d3b7_156_0.png)

![](img/be2cf0737cec89669e7b18813ea2d3b7_156_1.png)

Bryant and O’Hallaron, Computer Systems: A Programmer’s Perspective, Third Edition
