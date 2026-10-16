# 2.6.2 Arithmetic Instructions

# BCD and ASCII Arithmetic

# Decimal Adjust AL after Addition

+   - DAA

Adjusts the sum of two packed BCD values to create a packed BCD result.

```
if (AL & 0FH)>9 or (AF)=1
then (AL)+6-->AL
1-->AF
if (AL)>9FH or (CF)=1
then (AL)+60H-->AL
1-->CF
```

![](bbox=[0.66, 0.55, 0.97, 0.7])