# 2.6.4 Jump Instructions

# Unconditional Jump (JMP)

# Near Jump

```
JMP OPR
```

+   - Relative near jump in current segment
+   - In real mode
+     - (E)IP=(E)IP+16-bit displacement
+       - Displacement is a 2-byte signed number whose value range between +32767~-32768
+   - In protected mode for 80386 or above
+     - EIP=EIP+32-bit displacement
+       - Displacement is a 4-byte signed number whose value range between +2G~-2G
+   - We can use a label too.