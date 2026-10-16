# 2.6.2 Arithmetic Instructions

# Addition, Subtraction, and Comparison

# Addition instruction

```
ADD DST, SRC
```

+   - DST←(DST)+(SRC)
+   - This instruction have an affect on CF, SF, OF, PF, ZF and AF

| Symbolic | Example |
|---|---|
| ADD reg8/16/32, imm8/16/32 | ADD AX,837FH |
| ADD reg8/16/32, reg8/16/32 | ADD EAX, EBX |
| ADD reg8/16/32, mem8/16/32 | ADD CX, WORD PTR[SI] |
| ADD mem8/16/32, reg8/16/32 | ADD BYTE PTR[DI],DL |
| ADD mem8/16/32, imm8/16/32 | ADD BYTE PTR[DI], 23 |