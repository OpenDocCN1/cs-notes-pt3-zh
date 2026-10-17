```
add $s0, $s0, 1 # i = i + 1
bne $t2, $zero, L1 # if y[i] != 0, go to L1
lw $s0, 0($sp) # y[i] == 0: end of string;
# restore old $s0
add $sp, $sp, 4 # pop 1 word off stack
jr $ra # return
```

# # Optimization for example 2.17

+   - strcpy is a leaf procedure

+   - Allocate i to a temporary register $t0

# # For a leaf procedure

+   - The compiler exhausts all temporary registers

+   - Then use the registers it must save