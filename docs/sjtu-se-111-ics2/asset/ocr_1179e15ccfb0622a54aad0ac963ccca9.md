# HCL Word-Level Examples

# 4-Way Multiplexor

![](bbox=[0.05, 0.28, 0.55, 0.62])

# HCL Representation

```
int Out4 = [
  !s1&&!s0: D0;
  !s1      : D1;
  !s0      : D2;
  1        : D3;
];
```

+   - Select one of 4 inputs based on two control bits
+   - HCL case expression
+   - Simplify tests by assuming sequential matching