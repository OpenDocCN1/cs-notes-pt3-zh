# MIPS assembly code:

```
```asm
slt   $t3, $s5, $zero       # test if k < 0
bne   $t3, $zero, Exit      # if k < 0, go to Exit
slt   $t3, $s5, $t2         # test if k < 4
beq   $t3, $zero, Exit      # if k >= 4, go to Exit

add   $t1, $s5, $s5         # temp reg $t1 = 2 * k (0<=k<=3)
add   $t1, $t1, $t1         # temp reg $t1 = 4 * k
add   $t1, $t1, $t4         # $t1 = address of JumpTable[k]
lw    $t0, 0($t1)           # temp reg $t0 = JumpTable[k]
jr    $t0                   # jump based on register $t0
```
```

![](bbox=[0.008, 0.455, 0.239, 0.929])

```
```asm
L0:  add   $s0, $s3, $s4       # k = 0 so t gets i + j
     j     Exit               # end of this case so go to Exit
L1:  add   $s0, $s1, $s2       # k = 1 so t gets g + h
     j     Exit               # end of this case so go to Exit
L2:  sub   $s0, $s1, $s2       # k = 2 so t gets g - h
     j     Exit               # end of this case so go to Exit
L3:  sub   $s0, $s3, $s4       # k = 3 so t gets i - j
     Exit:                    # end of switch statement
```
```