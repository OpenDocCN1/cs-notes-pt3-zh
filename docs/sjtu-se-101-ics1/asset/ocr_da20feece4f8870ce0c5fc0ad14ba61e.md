# Position-Independent Code (PIC)

• PIC Data References

```
call        L1
L1:    popl    %ebx
       addl    $VAROFF, $ebx
       movl    (%ebx), %eax
       movl    (%eax), %eax
```

+   - Performance disadvantages (5 instr)
+   - An additional memory reference to the GOT
+   - An additional register to hold GOT entry