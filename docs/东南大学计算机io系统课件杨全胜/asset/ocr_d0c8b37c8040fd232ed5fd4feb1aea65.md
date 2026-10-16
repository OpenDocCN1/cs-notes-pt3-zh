# 2.6.4 Jump Instructions

# Unconditional Jump (JMP)

# Short Jump

```
JMP SHORT OPR
```

+   - Relative short jump in current segment
+   - New address is
+     - (E)IP=(E)IP+8-bit displacement
+       - Displacement is a one-byte signed number whose value range between +127~-128
+   - We can use a label (a symbolic name for a memory address) with the short jump instruction