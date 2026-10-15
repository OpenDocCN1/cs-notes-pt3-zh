# Implementation Issues

+   1. How do we know how much memory to free just given a pointer?
+   2. How do we keep track of the free blocks?

![](bbox=[0.238, 0.496, 0.851, 0.643])

```
free(p0)

p1 = malloc(1)
```