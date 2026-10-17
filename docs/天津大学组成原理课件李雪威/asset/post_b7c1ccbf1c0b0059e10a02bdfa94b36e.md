

## x86-64 Stack

- Region of memory managed with stack discipline
- Grows toward lower addresses
- Register `%rsp` contains lowest stack address
  - address of “top” element

![](img/be2cf0737cec89669e7b18813ea2d3b7_266_0.png)

## x86-64 Stack: Push

- **pushq Src**
  - Fetch operand at Src
  - Decrement %rsp by 8
  - Write operand at address given by %rsp

![](img/be2cf0737cec89669e7b18813ea2d3b7_267_0.png)

![](img/be2cf0737cec89669e7b18813ea2d3b7_267_1.png)

Stack Pointer: %rsp

Stack "Bottom"

Stack "Top"

Increasing Addresses

Stack Grows Down

## x86-64 Stack: Push

- **pushq Src**
  - Fetch operand at Src
  - Decrement %rsp by 8
  - Write operand at address given by %rsp

![](img/be2cf0737cec89669e7b18813ea2d3b7_268_0.png)

![](img/be2cf0737cec89669e7b18813ea2d3b7_268_1.png)

## x86-64 Stack: Pop

- **popq Dest**
  - Read value at address given by `%rsp`
  - Increment `%rsp` by 8
  - Store value at Dest (usually a register)

# Stack “Bottom”

![](img/be2cf0737cec89669e7b18813ea2d3b7_269_0.png)

Stack Pointer: `%rsp`

Stack “Top”

## x86-64 Stack: Pop

- `popq Dest`
  - Read value at address given by `%rsp`
  - Increment `%rsp` by 8
  - Store value at Dest (usually a register)

![](img/be2cf0737cec89669e7b18813ea2d3b7_270_0.png)

![](img/be2cf0737cec89669e7b18813ea2d3b7_270_1.png)

![](img/be2cf0737cec89669e7b18813ea2d3b7_270_2.png)

![](img/be2cf0737cec89669e7b18813ea2d3b7_270_3.png)

![](img/be2cf0737cec89669e7b18813ea2d3b7_270_4.png)

![](img/be2cf0737cec89669e7b18813ea2d3b7_270_5.png)

## x86-64 Stack: Pop

- **popq Dest**
  - Read value at address given by **%rsp**
  - Increment **%rsp** by 8
  - Store value at Dest (usually a register)

![](img/be2cf0737cec89669e7b18813ea2d3b7_271_0.png)

(The memory doesn’t change, only the value of **%rsp**)

## Today

### Procedures

- Stack Structure
- Calling Conventions
  - Passing control
  - Passing data
  - Managing local data
- Illustration of Recursion

## Code Examples

```c
void multstore(long x, long y, long *dest)
{
    long t = mult2(x, y);
    *dest = t;
}
```

```
0000000000400540 <multstore>:
  400540: push   %rbx              # Save %rbx
  400541: mov    %rdx,%rbx         # Save dest
  400544: callq  400550 <mult2>    # mult2(x,y)
  400549: mov    %rax,(%rbx)       # Save at dest
  40054c: pop    %rbx              # Restore %rbx
  40054d: retq                      # Return
```

```c
long mult2(long a, long b)
{
    long s = a * b;
    return s;
}
```

```
0000000000400550 <mult2>:
  400550: mov    %rdi,%rax          # a
  400553: imul   %rsi,%rax          # a * b
  400557: retq                      # Return
```

## Procedure Control Flow

- Use stack to support procedure call and return

- Procedure call: `call label`

  - Push return address on stack

  - Jump to *label*

- Return address:

  - Address of the next instruction right after call

  - Example from disassembly

- Procedure return: `ret`

  - Pop address from stack

  - Jump to address

# Control Flow Example #1

```
0000000000400540 <multstore>:
  •
  •
400544: callq  400550 <mult2>
400549: mov    %rax,(%rbx)
  •
  •
```

```
0000000000400550 <mult2>:
  400550: mov    %rdi,%rax
  •
  •
  400557: retq
```

![](img/be2cf0737cec89669e7b18813ea2d3b7_275_0.png)

## Control Flow Example #2

```
0000000000400540 <multstore>:
    ...
    ...
400544:   callq   400550 <mult2>
400549:   mov     %rax,(%rbx)
    ...
    ...
```

```
0000000000400550 <mult2>:
400550:   mov     %rdi,%rax
    ...
    ...
400557:   retq
```

![](img/be2cf0737cec89669e7b18813ea2d3b7_276_0.png)

Bryant and O’Hallaron, Computer Systems: A Programmer’s Perspective, Third Edition

# Control Flow Example #3

```
0000000000400540 <multstore>:
  •
  •
400544: callq 400550 <mult2>
400549: mov %rax,(%rbx)
  •
  •
```

```
0000000000400550 <mult2>:
  400550: mov %rdi,%rax
  •
  •
  400557: retq
```

![](img/be2cf0737cec89669e7b18813ea2d3b7_277_0.png)

