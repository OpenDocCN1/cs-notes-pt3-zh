# HCL Word-Level Examples

# Minimum of 3 Words

![](bbox=[0.07, 0.29, 0.38, 0.52])

# HCL Representation

```
int Min3 = [
  A < B && A < C : A;
  B < A && B < C : B;
  1               : C;
];
```

+   - Find minimum of three input words
+   - HCL case expression
+   - Final case guarantees match