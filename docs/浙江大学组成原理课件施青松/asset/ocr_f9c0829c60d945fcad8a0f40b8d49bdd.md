# Example 2.10

# Compiling *if-then-else* into Conditional Branches

(Assume: f ~ j ---- $s0 ~ $s4)

```
C code:
if (i == j) f = g + h;
else    f = g - h;
```

```
MIPS assembly code:
bne    $s3, $s4, Else    # go to Else if i ≠ j
add    $s0, $s1, $s2    # f = g + h (Executed if i == j if)
j      Exit             # go to Exit
Else:  sub    $s0, $s1, $s2    # f = g - h (Executed if i ≠ j else)
Exit:                         # the first instruction of the next C statement
```

![](bbox=[0.644, 0.16, 0.999, 0.606])