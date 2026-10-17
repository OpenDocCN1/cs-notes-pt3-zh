# Example 2.4　Compiling with an operand in memory

C code:

```
g = h + A[8];        // A is an array of 100 words
(Assume: g --- $s1    h --- $s2    base address of A --- $s3)
```

MIPS code:

```
lw   $t0, 8($s3)        # temporary reg $t0 gets A[8]
add  $s1, $s2, $t0      # g = h + A[8]
```

+   - **Offset**: the constant in a data transfer instruction → `8($s3)`
+   - **Base register**: the register added to form the address

# Byte addressing

→ `8($s3)`

# Alignment restriction

+   - Addresses of words are multiples of 4 in MIPS