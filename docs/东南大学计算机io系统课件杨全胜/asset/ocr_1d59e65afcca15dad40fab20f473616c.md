# 2.6.2 Arithmetic Instructions

# Addition, Subtraction, and Comparison

# Subtraction-with-Borrow

```
SBB DST, SRC
```

+   DST <-- (DST) - (SRC) - Carry

+   This instruction have an affect on CF, SF, OF, PF, ZF and AF

# SBB Example

```
SUB AX, CX    ; sub low word
```

```
SBB DX, BX    ; sub high word
```

7456H AX
- 9428H CX
1 E11EH

0012H DX
0010H BX
- 1H CF
0001H

CF=1