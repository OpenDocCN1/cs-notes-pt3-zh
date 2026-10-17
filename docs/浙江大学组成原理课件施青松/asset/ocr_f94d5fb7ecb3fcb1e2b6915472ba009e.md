# Example 2.12   Compiling a **while** loop

(Assume: i ~ k --- $s3 ~ $s5   base of save ---- $s6 )

# C code:

```
while ( save[i] == k )
    i = i + j;
```

# MIPS assembly code:

```
Loop:   add    $t1, $s3, $s3      # temp reg $t1 = 2 * i
        add    $t1, $t1, $t1      # temp reg $t1 = 4 * i
        add    $t1, $t1, $s6      # $t1 = address of save[i]
        lw     $t0, 0($t1)        # temp reg $t0 = save[i]
        bne    $t0, $s5, Exit     # go to Exit if save[i] != k
        add    $s3, $s3, $s4      # i = i + j
        j      Loop                # go to Loop
Exit:
```