# Switch Statements

# Jump Table

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