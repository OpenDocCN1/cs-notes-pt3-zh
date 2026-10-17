# # Code for the procedure sort

# ## Saving registers

```
sort: addi $sp, $sp, -20 # make room on stack for 5 registers
sw $ra, 16($sp) # save $ra on stack
sw $s3, 12($sp) # save $s3 on stack
sw $s2, 8($sp) # save $s2 on stack
sw $s1, 4($sp) # save $s1 on stack
sw $s0, 0($sp) # save $s0 on stack
```

# ## Procedure body{Outer loop {Inner loop} }

# ## Restoring registers

```
exit1: lw $s0, 0($sp) # restore $s0 from stack
lw $s1, 4($sp) # restore $s1 from stack
lw $s2, 8($sp) # restore $s2 from stack
lw $s3, 12($sp) # restore $s3 from stack
lw $ra, 16($sp) # restore $ra from stack
addi $sp, $sp, 20 # restore stack pointer
```

# ## Procedure return

```
jr $ra # return to calling routine
```