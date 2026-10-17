

## Today

- Arrays
  - One-dimensional
  - Multi-dimensional (nested)
  - Multi-level
- Structures
  - Allocation
  - Access
  - Alignment
- Floating Point

## Background

- History
  - x87 FP
    - Legacy, very ugly
  - SSE FP
    - Supported by Shark machines
    - Special case use of vector instructions
  - AVX FP
    - Newest version
    - Similar to SSE
    - Documented in book

## Programming with SSE3

### XMM Registers

- 16 total, each 16 bytes
- 16 single-byte integers
- 8 16-bit integers
- 4 32-bit integers
- 4 single-precision floats
- 2 double-precision floats
- 1 single-precision float
- 1 double-precision float

## Scalar & SIMD Operations

### Scalar Operations: Single Precision

addss %xmm0, %xmm1

%xmm0

%xmm1

### SIMD Operations: Single Precision

addps %xmm0, %xmm1

%xmm0

%xmm1

### Scalar Operations: Double Precision

addsd %xmm0, %xmm1

%xmm0

%xmm1

Bryant and O’Hallaron, Computer Systems: A Programmer’s Perspective, Third Edition

49

## FP Basics

- Arguments passed in `%xmm0`, `%xmm1`, ...
- Result returned in `%xmm0`
- All XMM registers caller-saved

```c
float fadd(float x, float y)
{
    return x + y;
}
```

```c
double dadd(double x, double y)
{
    return x + y;
}
```

```asm
# x in %xmm0, y in %xmm1
addss   %xmm1, %xmm0
ret
```

```asm
# x in %xmm0, y in %xmm1
addsd   %xmm1, %xmm0
ret
```

## FP Memory Referencing

- Integer (and pointer) arguments passed in regular registers
- FP values passed in XMM registers
- Different mov instructions to move between XMM registers, and between memory and XMM registers

```c
double dincr(double *p, double v)
{
    double x = *p;
    *p = x + v;
    return x;
}
```

```asm
# p in %rdi, v in %xmm0
movapd  %xmm0, %xmm1    # Copy v
movsd   (%rdi), %xmm0    # x = *p
addsd   %xmm0, %xmm1    # t = x + v
movsd   %xmm1, (%rdi)    # *p = t
ret
```

## Other Aspects of FP Code

- **Lots of instructions**
  - Different operations, different formats, ...
- **Floating-point comparisons**
  - Instructions `ucomiss` and `ucomisd`
  - Set condition codes CF, ZF, and PF
- **Using constant values**
  - Set XMM0 register to 0 with instruction `xorpd %xmm0, %xmm0`
  - Others loaded from memory

## Machine-Level Programming V: Advanced Topics

15-213: Introduction to Computer Systems
9th Lecture, February 14 (Happy Valentine’s Day!)

**Instructors:**
Franz Franchetti & Seth Copen Goldstein

## Today

- Memory Layout
- Buffer Overflow
  - Vulnerability
  - Protection
- Unions

## x86-64 Linux Memory Layout

not drawn to scale

- Runtime stack (8MB limit)
- E. g., local variables

- Dynamically allocated as needed
- When call `malloc()`, `calloc()`, `new()`

- Statically allocated data
- E. g., global vars, `static` vars, string constants

- Executable machine instructions
- Read-only

| Memory Region       |
|---------------------|
| Stack               |
|                     |
|                     |
| Shared Libraries    |
|                     |
| Heap                |
| Data                |
| Text                |
|                     |

00007FFFFFFFFFFF

Hex Address

40000000000000

Bryant and O’Hallaron, Computer Systems: A Programmer’s Perspective, Third Edition

3

Carnegie Mellon

## Memory Allocation Example

```c
char big_array[1L<<24]; /* 16 MB */
char huge_array[1L<<31]; /* 2 GB */

int global = 0;

int useless() { return 0; }

int main ()
{
    void *p1, *p2, *p3, *p4;
    int local = 0;
    p1 = malloc(1L << 28); /* 256 MB */
    p2 = malloc(1L << 8); /* 256 B */
    p3 = malloc(1L << 32); /* 4 GB */
    p4 = malloc(1L << 8); /* 256 B */
    /* Some print statements ... */
}
```

![](img/be2cf0737cec89669e7b18813ea2d3b7_387_0.png)

Where does everything go?

Bryant and O’Hallaron, Computer Systems: A Programmer’s Perspective, Third Edition

