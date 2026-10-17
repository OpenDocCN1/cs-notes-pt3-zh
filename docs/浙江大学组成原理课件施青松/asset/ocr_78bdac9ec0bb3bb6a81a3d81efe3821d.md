```
add    $t0, $a0, $a1      # register $t0 contains  g + h
add    $t1, $a2, $a3      # register $t1 contains  i + j
sub    $s0, $t0, $t1      # f = $t0 - $t1, which is (g + h) - (i + j)

add    $v0, $s0, $zero   # returns f   ( $v0 = $s0 + 0)

lw↑   $s0, 0($sp)         # restore register $s0 for caller
lw    $t0, 4($sp)         # restore register $t0 for caller
lw    $t1, 8($sp)         # restore register $t1 for caller
add   $sp, $sp, 12        # adjust stack to delete 3 items
jr    $ra                 # jump back to calling routine
```

But maybe some of the three are not used by the caller.So,this way might be inefficient.

# Two classes of registers

+   $t0 ~ $t9: 10 temporary registers , not preserved
+   $s0 ~ $s7: 8 saved registers, must be preserved