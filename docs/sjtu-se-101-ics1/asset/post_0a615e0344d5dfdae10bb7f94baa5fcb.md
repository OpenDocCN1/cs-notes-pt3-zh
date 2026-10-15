
## Integer Register
## Extend exist registers to 64bits

| %rax | %eax | %ah | %al |
| %rbx | %edx | %dh | %dl |
| %rcx | %ecx | %ch | %cl |
| %rdx | %ebx | %bh | %bl |
| %rsi | %esi |  |  |
| %rdi | %edi |  |  |
| %rsp | %esp |  |  |
| %rbp | %ebp |  |  |

## Integer Register
Add 8 new 64bits registers

| %rax | %eax | %ah | %al | %r8 | %r8d |
| %rbx | %ebx | %dh | %dl | %r9 | %r9d |
| %rcx | %ecx | %ch | %cl | %r10 | %r10d |
| %rdx | %edx | %bh | %bl | %r11 | %r11d |
| %rsi | %esi |  |  | %r12 | %r12d |
| %rdi | %edi |  |  | %r13 | %r13d |
| %rsp | %esp |  |  | %r14 | %r14d |
| %rbp | %ebp |  |  | %r15 | %r15d |

## Integer Register
## Make %ebp/%rbp general purpose

| %rax | %eax | %ah | %al |
| %rbx | %ebx | %dh | %dl |
| %rcx | %ecx | %ch | %cl |
| %rdx | %edx | %bh | %bl |
| %rsi | %esi |  |  |
| %rdi | %edi |  |  |
| %rsp | %esp |  |  |
| %rbp | %ebp |  |  |

| %r8 | %r8d |
| %r9 | %r9d |
| %r10 | %r10d |
| %r11 | %r11d |
| %r12 | %r12d |
| %r13 | %r13d |
| %r14 | %r14d |
| %r15 | %r15d |

## Instructions

- Long word l (4 Bytes) ↔ Quad word q (8 Bytes)

- New Instructions
  - `movl` → `movq`
  - `addl` → `addq`
  - `sall` → `salq`
  - etc.

- 32 - bit instructions generate 32 - bit results
  - Set higher order bits of destination register to 0
  - Example: `addl`

## Switch Statements
## Jump Table

```
long switch(long x)
{
    switch(x) {
        . . .
    }
    . . .
}
```

```
.section .rodata
.align 4
.L8:
    .long .L1 # x = 0
    .long .L2 # x = 1
    .long .L3 # x = 2
    .long .L4 # x = 3
    .long .L5 # x = 4
    .long .L6 # x = 5
    .long .L7 # x = 6
```

```
switch:
    pushl %ebp          # Setup
    movl %esp, %ebp     # Setup
    movl 8(%ebp), %edx  # edx = x
    cmpl $6, %edx       # x:6
    ja .L1              # if > goto default
    jmp *.L8(, %edx, 4) # goto JTab[x]
```

## Switch Statements

- x86-64
  - Same general idea, adapted to 64-bit code
  - Table entries 64 bits (pointers)

```
.section .rodata
    .align 4
.L8:
    .long .L1 # x = 0
    .long .L2 # x = 1
    .long .L3 # x = 2
    .long .L4 # x = 3
    .long .L5 # x = 4
    .long .L6 # x = 5
    .long .L7 # x = 6
```

IA32

```
.section .rodata
    .align 8
.L8:
    .quad .L1 # x = 0
    .quad .L2 # x = 1
    .quad .L3 # x = 2
    .quad .L4 # x = 3
    .quad .L5 # x = 4
    .quad .L6 # x = 5
    .quad .L7 # x = 6
```

x86-64

## Machine-Level Representation
of Programs (x86-64)

## Outline

- x86-64 Machine-Level Programming
  - Procedures and Stack
  - Alignment
  - Byte Ordering
- Suggested reading
  - Chap 3.13

## Example: swap()
## IA32

```
void
swap(int *xp, int *yp)
{
    int t0 = *xp;
    int t1 = *yp;
    *xp = t1;
    *yp = t0;
}
```

```
swap:
    pushl %ebp
    movl %esp,%ebp
    pushl %ebx
    movl 12(%ebp),%ecx
    movl 8(%ebp),%edx
    movl (%ecx),%eax
    movl (%edx),%ebx
    movl %eax,(%edx)
    movl %ebx,(%ecx)
    movl -4(%ebp),%ebx
    movl %ebp,%esp
    popl %ebp
    ret
```

Setup

Body

Finish

## Example: swap()
## x86-64

```
void
swap(int *xp, int *yp)
{
    int t0 = *xp;
    int t1 = *yp;
    *xp = t1;
    *yp = t0;
}
```

```
swap:
movl (%rdi), %edx
movl (%rsi), %eax
movl %eax, (%rdi)
movl %edx, (%rsi)
retq
```

## Example: swap()

Operands passed in registers

- First (xp) in %rdi
- Second (yp) in %rsi
- 64-bit pointers

```
swap:
movl (%rdi), %edx
movl (%rsi), %eax
movl %eax, (%rdi)
movl %edx, (%rsi)
retq
```

No stack operation required

32-bit data

- Data held in register %eax and %edx
- movl operation

## Example: swap()
## Swap long int in 64-bit

```
void
swap(long int *xp,
    long int *yp)
{
    long int t0 = *xp;
    long int t1 = *yp;
    *xp = t1;
    *yp = t0;
}
```

```
swap:
movq (%rdi), %rdx
movq (%rsi), %rax
movq %rax, (%rdi)
movq %rdx, (%rsi)
retq
```

64-bit data

Data held in registers %rax and %rdx

movq operation

"q" stands for quar-word
