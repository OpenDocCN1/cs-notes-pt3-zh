# 6.4.3 Type equivalence

The type expression can be represented by a syntax tree.

The type expression:

```
record
    x: pointer to real;
    y: array [10] of int
end
```

![](bbox=[0.523, 0.211, 0.812, 0.484])

The type expression:

```
proc (bool, union a:real; b:char end, int): void
```

![](bbox=[0.154, 0.648, 0.584, 0.916])