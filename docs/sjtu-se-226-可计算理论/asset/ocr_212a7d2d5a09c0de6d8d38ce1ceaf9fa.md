# Undecidability Result

# Theorem

The problem ‘x ∈ W_x’ is undecidable.

# Proof

The characteristic function of this problem is given by

```
c(x) = { 1, if x ∈ W_x, 0, if x ∉ W_x. }
```

Suppose c(x) was computable. Then the function g(x) defined below would also be computable.

```
g(x) = { 0, if c(x) = 0, undefined, if c(x) = 1. }
```