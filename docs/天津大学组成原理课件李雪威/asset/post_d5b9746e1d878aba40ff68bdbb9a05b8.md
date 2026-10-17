

# What To Do About Buffer Overflow Attacks

- Avoid overflow vulnerabilities
- Employ system-level protections
- Have compiler use “stack canaries”
- Lets talk about each...

## 1. Avoid Overflow Vulnerabilities in Code (!)

```c
/* Echo Line */
void echo()
{
    char buf[4]; /* Way too small! */
    fgets(buf, 4, stdin);
    puts(buf);
}
```

- For example, use library routines that limit string lengths
- fgets instead of gets
- strncpy instead of strcpy
- Don’t use scanf with %s conversion specification
  - Use fgets to read the string
  - Or use %ns where n is a suitable integer

## 2. System-Level Protections can help

### Randomized stack offsets

- At start of program, allocate random amount of space on stack
- Shifts stack addresses for entire program
- Makes it difficult for hacker to predict beginning of inserted code
- E.g.: 5 executions of memory allocation code
- Stack repositioned each time program executes

![](img/be2cf0737cec89669e7b18813ea2d3b7_409_0.png)

Bryant and O’Hallaron, Computer Systems: A Programmer’s Perspective, Third Edition

26

## 3. Stack Canaries can help

- **Idea**
  - Place special value (“canary”) on stack just beyond buffer
  - Check for corruption before exiting function

- **GCC Implementation**
  - `-fstack-protector`
  - Now the default (disabled earlier)

```
unix> ./bufdemo-sp
Type a string:0123456
0123456
```

```
unix> ./bufdemo-sp
Type a string:01234567
*** stack smashing detected ***
```

## Protected Buffer Disassembly

### echo:

```
40072f:   sub    $0x18,%rsp
400733:   mov    %fs:0x28,%rax
40073c:   mov    %rax,0x8(%rsp)
400741:   xor    %eax,%eax
400743:   mov    %rsp,%rdi
400746:   callq  4006e0 <gets>
40074b:   mov    %rsp,%rdi
40074e:   callq  400570 <puts@plt>
400753:   mov    0x8(%rsp),%rax
400758:   xor    %fs:0x28,%rax
400761:   je     400768 <echo+0x39>
400763:   callq  400580 <__stack_chk_fail@plt>
400768:   add    $0x18,%rsp
40076c:   retq
```

## Setting Up Canary

### Before call to gets

![](img/be2cf0737cec89669e7b18813ea2d3b7_413_0.png)

```c
/* Echo Line */
void echo()
{
    char buf[4];  /* Way too small! */
    gets(buf);
    puts(buf);
}
```

```asm
echo:
    . . .
    movq  %fs:40, %rax    # Get canary
    movq  %rax, 8(%rsp)   # Place on stack
    xorl  %eax, %eax      # Erase canary
    . . .
```

## Checking Canary

### After call to gets

```c
/* Echo Line */
void echo()
{
    char buf[4];  /* Way too small! */
    gets(buf);
    puts(buf);
}
```

![](img/be2cf0737cec89669e7b18813ea2d3b7_414_0.png)

Input: 0123456

```asm
echo:
    . . .
    movq  %rsp, %rax    # Retrieve from stack
    xorq  %fs:40, %rax    # Compare to canary
    je    .L6             # If same, OK
    call  __stack_chk_fail  # FAIL
```

## Return-Oriented Programming Attacks

- Challenge (for hackers)
  - Stack randomization makes it hard to predict buffer location
  - Marking stack nonexecutable makes it hard to insert binary code

- Alternative Strategy
  - Use existing code
    - E.g., library code from stdlib
  - String together fragments to achieve overall desired outcome
  - _Does not overcome stack canaries_

- Construct program from _gadgets_
  - Sequence of instructions ending in `ret`
    - Encoded by single byte `0xc3`
  - Code positions fixed from run to run
  - Code is executable

## Gadget Example #1

```c
long ab_plus_c
(long a, long b, long c)
{
    return a*b + c;
}
```

```
00000000004004d0 <ab_plus_c>:
   4004d0:   48 0f af fe   imul   %rsi,%rdi
   4004d4:   48 8d 04 17   lea    (%rdi,%rdx,1),%rax
   4004d8:   c3              retq
```

rax ← rdi + rdx
Gadget address = 0x4004d4

### Use tail end of existing functions

## Gadget Example #2

```c
void setval(unsigned *p) {
    *p = 3347663060u;
}
```

<setval>:
4004d9: c7 07 d4 48 89 c7 movl $0xc78948d4, (%rdi)
4004df: c3 retq

Encodes movq %rax, %rdi

rdi ← rax
Gadget address = 0x4004dc

### Repurpose byte codes

