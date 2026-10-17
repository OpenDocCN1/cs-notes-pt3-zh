# # Compiling Into Assembly

# ## C Code (sum.c)

```
long plus(long x, long y);\n\nvoid sumstore(long x, long y,\n              long *dest)\n{\n    long t = plus(x, y);\n    *dest = t;\n}
```

# ## Generated x86-64 Assembly

```
sumstore:\n    pushq   %rbx\n    movq    %rdx, %rbx\n    call    plus\n    movq    %rax, (%rbx)\n    popq    %rbx\n    ret
```

**Obtain (on shark machine) with command**

```
gcc -Og -S sum.c
```

**Produces file sum.s**

**Warning:** Will get very different results on non-Shark machines (Andrew Linux, Mac OS-X, ...) due to different versions of gcc and different compiler settings.